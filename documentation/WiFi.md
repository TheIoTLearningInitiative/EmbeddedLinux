# WiFi

> Wi-Fi (or WiFi) is a local area wireless computer networking technology that allows electronic devices to connect to the network, mainly using the 2.4 gigahertz (12 cm) UHF and 5 gigahertz (6 cm) SHF ISM radio bands. Wikipedia

> Intel Edison Features

> > Wi-Fi peer-to-peer connectivity with Wi-Fi Direct, Allows two Intel® Edison devices (or one Intel® Edison device and a smartphone) to create a direct Wi-Fi connection to each other without an access point.

> > Wi-Fi multirole, Allows a connection to an access point simultaneously with Wi-Fi Direct operation. 

> > Wi-Fi IBSS mode, Allows creation of multinode ad hoc networks that contain no access point.

- [WiFi Wikipedia](https://en.wikipedia.org/wiki/Wi-Fi)
- [Intel® Edison Boards Wi-Fi User Guide](http://www.intel.com/support/edison/sb/CS-035380.htm)
- [Intel® Edison Network Access](https://software.intel.com/en-us/connecting-to-a-network-intel-edison-board)
- [Edison Wi-Fi Configuration](http://rwx.io/blog/2015/08/16/edison-wifi-config/)
- [Realtek 8192 chipset driver, ported to kernel 3.11](https://github.com/pvaret/rtl8192cu-fixes)

## Kernel Integration

### Kernel Display Message

```sh
    root@edison:~# dmesg | grep -i wifi
    [    0.189658] Using generic wifi platform data
    [    0.189675] wifi_platform_data: GPIO == 64
    [    3.850154] found wifi platform device wlan
    [    4.171606] wifi_platform_set_power = 1
    [    4.373687] wifi_platform_bus_enumerate device present 1
    [    4.412928] wifi_platform_get_mac_addr
    [    4.413069] wifi_get_mac_addr_intel: unable to open /config/wifi/mac.txt
    [    4.420354] wifi_platform_set_power = 0
    [    4.421428] wifi_platform_bus_enumerate device present 0
    [   38.194385] wl_android_wifi_on in
    [   38.194403] wifi_platform_set_power = 1
    [   39.117444] wifi_platform_get_mac_addr
    [   39.117488] wifi_get_mac_addr_intel: unable to open /config/wifi/mac.txt
```

### Kernel Modules

```sh
    root@edison:~# lsmod
    Module                  Size  Used by0
    usb_f_acm              14335  1 
    ...
    bcm_bt_lpm             13708  0 
    bcm4334x              587105  0 
```

## Applications / Libraries

> RFKill
> > rfkill is a small userspace tool to query the state of the rfkill switches, buttons and subsystem interfaces. Some devices come with a hard switch that lets you kill different types of RF radios: 802.11 / Bluetooth / NFC / UWB / WAN / WIMAX / FM. Some times these buttons may kill more than one RF type. The Linux kernel rfkill subsystem exposes these hardware buttons and lets userspace query its status and set its status through a /dev/rfkill. Given that at times some RF devices do not have hardware rfkill buttons rfkill the Linux kernel also exposes software rfkill capabilities that allows userspace to mimic a hardware rfkill event and turn on or off RF.  [Rfkill Homepage](https://wireless.wiki.kernel.org/en/users/documentation/rfkill)

```sh
    root@edison:~# rfkill list 
    0: phy0: wlan
            Soft blocked: no
            Hard blocked: no
    1: brcmfmac-wifi: wlan
            Soft blocked: no
            Hard blocked: no
    2: bcm43xx Bluetooth: bluetooth
            Soft blocked: yes
            Hard blocked: no
```

### Usage Models, Ubilinux

```sh
    edison@ubilinux:~$ su
    Password: edison
    root@ubilinux:/home/edison# cd 
    root@ubilinux:~# nano /etc/network/interfaces
    # interfaces(5) file used by ifup(8) and ifdown(8)
    auto lo
    iface lo inet loopback

    #auto usb0
    #iface usb0 inet static
    #    address 192.168.2.15
    #    netmask 255.255.255.0
    
    auto wlan0
    iface wlan0 inet dhcp
        # For WPA
        wpa-ssid INFINITUMxxxx
        wpa-psk yyyy
        # For WEP
        #wireless-essid itesm
        #wireless-mode Managed
        #wireless-key s:""
    
    root@ubilinux:~# ifup wlan0
    root@ubilinux:~# reboot

    <reboot your board, sign in and become root>
```

### Usage Models, Yocto

#### Default Configuration

```sh
    root@Edison:~# configure_edison --wifi
     Configure Edison: WiFi Connection
    root@edison:~# ifconfig
     lo        Link encap:Local Loopback
               inet addr:127.0.0.1  Mask:255.0.0.0
     ...
     usb0      Link encap:Ethernet  HWaddr 5a:2a:15:c5:5f:7b
               inet addr:192.168.2.15  Bcast:192.168.2.255  Mask:255.255.255.0
     ...
     wlan0     Link encap:Ethernet  HWaddr 78:4b:87:a6:cf:5e
               inet addr:192.168.1.68  Bcast:0.0.0.0  Mask:255.255.255.0
    root@edison:~# ping -c 3 8.8.8.8
    PING google.com (173.194.115.196): 56 data bytes
    64 bytes from 173.194.115.196: seq=0 ttl=58 time=28.487 ms
    64 bytes from 173.194.115.196: seq=1 ttl=58 time=29.391 ms
    64 bytes from 173.194.115.196: seq=2 ttl=58 time=29.773 ms
    
    --- google.com ping statistics ---
    3 packets transmitted, 3 packets received, 0% packet loss
    round-trip min/avg/max = 28.487/29.217/29.773 ms
    root@edison:~# 
```

#### Persistent Connection

```sh
    root@edison:~# configure_edison -wifi
    ...
    root@edison:~# systemctl enable wpa_supplicant
    root@edison:~# systemctl start wpa_supplicant
```

#### Manual Persistent Configuration

Make sure there are no soft blocks

```sh
    root@edison:~# rfkill list
```

Make sure wlan0 is loaded and see IP

```sh
    root@edison:~# ifconfig
```

Load the wlan0 device driver

```sh
    root@edison:~# wpa_supplicant -B -Dnl80211 -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf
```

Get DHCP and DNS

```sh
    root@edison:~# busybox udhcpc -i wlan0
```

Move usb0 to a different non-conflicting subnet

```sh
    root@edison:~# vi /etc/system/system/basic.target.wants/network-gadget-init.service
```

Disable usb0 device from loading

```sh
    root@edison:~# systemctl disable network-gadget-init.service
```

Ensure there is a wpa_supplicant network{} definition and remove unneeded networks

```sh
    root@edison:~# vi /etc/wpa_supplicant/wpa_supplicant.conf
```

Enable first network definition

```sh
    root@edison:~# wpa_cli
         > enable_network 0
         > select_network 0
         > save
         > quit
```

Example WEP key wpa_supplicant.conf

```sh
    ctrl_interface=/var/run/wpa_supplicant
    ctrl_interface_group=0
    update_config=1
    network={
         ssid="YOURSSID"
         scan_ssid=1
         key_mgmt=NONE
         auth_alg=OPEN
         wep_key0=f0039faded348299992344be23
    }
```

Remove soft block on wlan0

```sh
    root@edison:~# rfkill unblock wlan
```

Enable wifi on boot once config is confirmed correct

```sh
    root@edison:~# systemctl enable wa_supplicant
```

WiFi to connect at power up:

```sh
    systemctl enable wpa_supplicant
    systemctl start wpa_supplicant
```

### Password Lenght

> ... I am asked for a 5 or 13 character network password, but my network's password is 10 characters long ... [Edison WiFi setup - password must be either 5 or 13 characters](https://communities.intel.com/thread/59888?start=0&tstart=0)

```sh
--- configure_edison.orig
+++ configure_edison
@@ -60,6 +60,15 @@
   wep_key0="%s"
}
'''  
+  WEP_26HEX =  '''
+network={
+  ssid="%s"
+  %s
+  key_mgmt=NONE
+  group=WEP104 WEP40
+  wep_key0=%s
+}
+'''
   WPAPSK =  '''
network={
   ssid="%s"
@@ -359,10 +368,13 @@
       return wpa_templates.OPEN % (ssid, "scan_ssid=1")
     elif security == 1:
       password = ''
-      while len(password) != 5 and len(password) != 13:
-        print "Password must be either 5 or 13 characters."
+      while len(password) != 5 and len(password) != 13 and len(password) != 26:
+        print "Password must be either 5 or 13 ascii characters or 26 hex."
         password = getNetworkPassword()
-      return wpa_templates.WEP % (ssid, "scan_ssid=1", password)
+        if len(password) == 26:
+          return wpa_templates.WEP_26HEX % (ssid, "scan_ssid=1", password)
+        else:
+          return wpa_templates.WEP % (ssid, "scan_ssid=1", password)
     elif security == 2:
       password = ''
       while len(password) < 8 or len(password) > 63:
@@ -384,10 +396,13 @@
     return wpa_templates.OPEN % (ssid, "")
   elif network_map[ssid] == "WEP":
     password = ''
-    while len(password) != 5 and len(password) != 13:
-        print "Password must be either 5 or 13 characters."
+    while len(password) != 5 and len(password) != 13 and len(password) != 26:
+        print "Password must be either 5 or 13 ascii characters or 26 hex."
         password = getNetworkPassword()
-    return wpa_templates.WEP % (ssid, "", password)
+        if len(password) == 26:
+          return wpa_templates.WEP_26HEX % (ssid, "", password)
+        else:
+          return wpa_templates.WEP % (ssid, "", password)
   elif network_map[ssid] == "WPA-PSK":
     password = ''
     while len(password) < 8 or len(password) > 63:
@@ -409,10 +424,13 @@
     return wpa_templates.OPEN % (ssid, "scan_ssid=1")
   elif protocol == "WEP":
     password = changewifi[2]
-    if len(password) != 5 and len(password) != 13:
-        print "Password must be either 5 or 13 characters."
+    if len(password) != 5 and len(password) != 13 and len(password) != 26:
+        print "Password must be either 5 or 13 ascii characters or 26 hex."
         return None
-    return wpa_templates.WEP % (ssid, "scan_ssid=1", password)
+    if len(password) == 26:
+      return wpa_templates.WEP_26HEX % (ssid, "scan_ssid=1", password)
+    else:
+      return wpa_templates.WEP % (ssid, "scan_ssid=1", password)
   elif protocol == "WPA-PSK":
     password = changewifi[2]
     if len(password) < 8 or len(password) > 63:
```

### Mode Access Point @ Ubilinux

- [Ubilinux Access Point Hostapd](http://www.emutexlabs.com/forum/ubilinux/85-ubilinux-access-point-hostapd)

## Testing

ToDo iPerf ... 