# Boot Up

## Bootup Linux Login

```sh
    Poky (Yocto Project Reference Distro) 1.7.2 edison ttyMFD2
    
    edison login: root
    root@edison:~# 
```

## Bootup Initial Configuration

Check your kernel version

```sh
    root@edison:~# uname -a
    Linux edison 3.10.17-poky-edison+ #2 SMP PREEMPT Mon Mar 14 15:26:16 PDT 2016 i686 GNU/Linux
```

Configure your WiFi

```sh
    root@edison:~# configure_edison --wifi
    Configure Edison: WiFi Connection
    
    Scanning: 1 seconds left  
    
    0 :     Rescan for networks
    1 :     Exit WiFi Setup
    2 :     Manually input a hidden SSID
    3 :     INFINITUM914E
    
    
    Enter 0 to rescan for networks.
    Enter 1 to exit.
    Enter 2 to input a hidden network SSID.
    Enter 3 to choose INFINITUM9###: 3
    Is INFINITUM9### correct? [Y or N]: Y
    Password must be between 8 and 63 characters.
    What is the network password?: 
    What is the network password?: **********
    Initiating connection to INFINITUM9###. Please wait...
    Attempting to enable network access, please check 'wpa_cli status' after a minute to confirm.
    Done. Please connect your laptop or PC to the same network as this device and go to http://192.168.1.72 or http://edison.local in your browser.
    Warning: SSH is not yet enabled on the wireless interface. To enable SSH access to this device via wireless run configure_edison --password first.
    root@edison:~# 
```

Configure also password to enable SSH on the wireless interface

```
    root@edison:~# configure_edison --password
    
    Configure Edison: Device Password
    
    Enter a new password (leave empty to abort)
    This will be used to connect to the access point and login to the device.
    Password:       ********
    Please enter the password again:        ********
    First-time root password setup complete. Enabling SSH on WiFi interface.
    The device password has been changed.
```

Check IP address assigned

```sh
    root@edison:~# ifconfig
    lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
    usb0      Link encap:Ethernet  HWaddr 02:00:86:58:c2:af  
              inet addr:192.168.2.15  Bcast:192.168.2.255  Mask:255.255.255.0
    wlan      Link encap:Ethernet  HWaddr 00:1C:C0:AE:B5:E6  
              inet addr:192.168.1.74  Bcast:192.168.0.255  Mask:255.255.255.0
```

Shutdown USB0 interface

```sh
    root@edison:~# ifconfig usb0 down
    root@edison:~# 
```

## Dual Boot

