BlueTooth
==

> Bluetooth is a wireless technology standard for exchanging data over short distances from fixed and mobile devices, and building personal area networks ... [Wikipedia](https://en.wikipedia.org/wiki/Bluetooth)

- [Intel® Edison Boards Bluetooth® User Guide](http://www.intel.com/support/edison/sb/CS-035381.htm)

## Kernel Integration

### BlueZ

> BlueZ. Official Linux Bluetooth Protocol Stack
> > Bluetooth tools and daemons. This package contains tools and system daemons for using Bluetooth devices. BlueZ is the official Linux Bluetooth protocol stack. It is an Open Source project distributed under GNU General Public License (GPL). [Bluez Homepage](http://www.bluez.org/)

- [BlueZ’ GIT Repository](http://git.kernel.org/cgit/bluetooth/bluez.git/tree/)

Bluetooth Kernel Subsystem

- [bluetooth.git](http://git.kernel.org/?p=linux/kernel/git/bluetooth/bluetooth.git;a=summary)
- [bluetooth-next.git](http://git.kernel.org/?p=linux/kernel/git/bluetooth/bluetooth-next.git;a=summary)

Bluez Tools

- **hciconfig** - HCI device configuration utility
- **hciattach** - HCI UART driver initialization utility
- **l2ping** - L2CAP ping
- **hcidump** - HCI packet analyzer
- **hcitool** - Generic writing and monitoring to the HCI interface
- bluetooth-agent
- bluetoothctl

```sh
    root@edison:~# dmesg | grep -i blue
    [    0.235619] Bluetooth: Core ver 2.16
    [    0.235722] Bluetooth: HCI device and connection manager initialized
    [    0.235752] Bluetooth: HCI socket layer initialized
    [    0.235778] Bluetooth: L2CAP socket layer initialized
    [    0.235876] Bluetooth: SCO socket layer initialized
    [    0.922994] Bluetooth: HCI UART driver ver 2.2
    [    0.923015] Bluetooth: HCI H4 protocol initialized
    [    1.588016] Bluetooth: RFCOMM TTY layer initialized
    [    1.588081] Bluetooth: RFCOMM socket layer initialized
    [    1.588100] Bluetooth: RFCOMM ver 1.11
    [    1.588116] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
    [    1.588130] Bluetooth: BNEP filters: protocol multicast
    [    1.588160] Bluetooth: BNEP socket layer initialized
    [    1.588175] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
    [    1.588202] Bluetooth: HIDP socket layer initialized
    root@edison:~# lsmod
    Module                  Size  Used by
    usb_f_acm              14335  1 
    ...
    bcm_bt_lpm             13708  0 
    bcm4334x              587105  0 
```

## Applications / Libraries

### ConnMan

> ConnMan is a daemon for managing Internet connections within embedded device and integrates a vast range of communication features usually split between many daemons such as DHCP, DNS and NTP. The result of this consolidation is low memory consumption with a fast, coherent, synchronized reaction to changing network conditions. [ConnMan Homepage](https://01.org/connman)

### RFKill

> rfkill is a small userspace tool to query the state of the rfkill switches, buttons and subsystem interfaces. Some devices come with a hard switch that lets you kill different types of RF radios: 802.11 / Bluetooth / NFC / UWB / WAN / WIMAX / FM. Some times these buttons may kill more than one RF type. The Linux kernel rfkill subsystem exposes these hardware buttons and lets userspace query its status and set its status through a /dev/rfkill. Given that at times some RF devices do not have hardware rfkill buttons rfkill the Linux kernel also exposes software rfkill capabilities that allows userspace to mimic a hardware rfkill event and turn on or off RF. [Rfkill Homepage](https://wireless.wiki.kernel.org/en/users/documentation/rfkill)

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

### Opkg

```sh
    root@edison:~# opkg install bluez5-dev
```
### Pip

```sh
    root@edison:~# pip install pybluez
```

### Apt-Get

```sh
    root@edison:~# apt-get install bluetooth
    root@edison:~# /etc/init.d/bluetooth start
```

## Applications

### Programs

```sh
    root@edison:~# systemctl status bluetooth.service
    root@edison:~# systemctl stop bluetooth
    root@edison:~# systemctl start bluetooth
    root@edison:~# systemctl enable bluetooth
    root@edison:~# rfkill unblock bluetooth
    root@edison:~# rfkill list bluetooth
    2: bcm43xx Bluetooth: bluetooth
        Soft blocked: no
        Hard blocked: no
    4: hci0: bluetooth
        Soft blocked: no
        Hard blocked: no
    root@edison:~# hciconfig hci0 down
    root@edison:~# hciconfig hci0 up
    root@edison:~# hciconfig hci0 status
    hci0:   Type: BR/EDR  Bus: UART
        BD Address: 98:4F:EE:03:39:02  ACL MTU: 1021:8  SCO MTU: 64:1
        UP RUNNING PSCAN 
    ...
    root@edison:~# hciconfig hci0 piscan
    ...
    root@edison:~# hcitool scan
```
### Python

```Python
    root@edison:~# git clone https://github.com/karulis/pybluez
    Cloning into 'pybluez'...
    remote: Counting objects: 1082, done.
    remote: Compressing objects: 100% (19/19), done.
    remote: Total 1082 (delta 5), reused 0 (delta 0), pack-reused 1061
    Receiving objects: 100% (1082/1082), 415.85 KiB | 407.00 KiB/s, done.
    Resolving deltas: 100% (658/658), done.
    Checking connectivity... done.
    root@edison:~# cd pybluez/examples
    root@edison:~/pybluez/examples# 

```

### Usage Models

#### Device Pairing

```sh
    root@galileo:~# rfkill unblock bluetooth
    root@galileo:~# bluetoothctl
    [bluetooth]# scan on
    [bluetooth]# scan off
    [bluetooth]# pair 40:78:6A:26:4A:C2
    [bluetooth]# connect 40:78:6A:26:4A:C2
    [bluetooth]# paired-devices
    [bluetooth]# info 40:78:6A:26:4A:C2
    [bluetooth]# exit
```

#### Text

```sh
    root@edison:~# systemctl status bluetooth.service
    root@edison:~# systemctl start bluetooth
    root@edison:~# systemctl enable bluetooth
    root@edison:~# rfkill unblock bluetooth
    root@edison:~# rfkill list bluetooth
    root@edison:~# hciconfig hci0 status
    Make Your Device Discoverable
    root@edison:~# hcitool scan
    root@edison:~# rfcomm bind 0 40:78:6A:26:4A:C2
```

#### Audio

```sh
    root@edison:~# apt-get install pulseaudio pulseaudio-module-bluetooth pavucontrol bluez-firmware
```

#### Bluetooth Sound

```sh
    root@edison:~# opkg install alsa-utils kernel-module-snd-usb-audio bluez5 gstreamer pulseaudio
    root@edison:~# opkg install kernel-module-ftdi-sio
    root@edison:~# rfkill unblock bluetooth
    root@edison:~# bluetoothctl
    [NEW] Controller 98:4F:EE:04:1A:8C edison [default]
    [bluetooth]# power on
    [bluetooth]# agent on
    [bluetooth]# scan on
    [bluetooth]# pair <id you find>
    [bluetooth]# trust <id>
    [bluetooth]# connect <id you paired with>
```

#### Serial Port Profile (SPP)

Libraries

For C Bluetooth Development:

```sh
    root@edison:~# sudo apt-get install libbluetooth-dev
```

For Python Bluetooth Development:

```sh
    root@edison:~# sudo apt-get install python-bluez
```

For Python Bluetooth in Edison (using pip, if for some reason you don't have it, learn [How-To Install Pip](https://pip.pypa.io/en/stable/installing/#pip-included-with-python)):

```sh
    root@edison:~# pip install pybluez
```

There are two common ways to test SPP, one is by using D-BUS, the other is by using RFCOMM transport protocol.

To test using D-Bus we can use [this python script](http://downloadmirror.intel.com/24909/eng/SPP-loopback.py), copy it to Edison, enable the bluetooth device and run it:

```sh
    root@edison:~# rfkill unblock bluetooth
    root@edison:~# python SPP-loopback.py &
```

Then in an android device install a [Bluetooth SPP Manager](https://play.google.com/store/apps/details?id=at.rtcmanager).

At this point you need to pair the Intel Edison with your android device (see example above on how to use **bluetoothctl**, **hcicontrol** or any other user level application in your Edison).

Once paired, open the Bluetooth SPP Manager app, hit search, and when the Intel Edison appears  tap on in to connect.  now you can send text messages to Edison which can be seen on the terminal window of the Edison.

--

I know this need a lil' bit further explanation. just dropped here so i won't forget.
Also what is going to be added is  how to  programmatically do the device discovering, pairing  and SPP using c and python

