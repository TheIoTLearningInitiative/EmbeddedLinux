BlueTooth
==

> The host processor on the Intel® Edison development board is connected to a Broadcom* BCM43340 combo chip via UART (uart0 mapped to /dev/MFD0) as transport layer and uses additional GPIOs to handle power (on, reset, etc.), OOB (
out-of-band) signaling for UART to support low power mode. ...

- [Intel® Edison Board Getting Started with Bluetooth](https://software.intel.com/en-us/articles/intel-edison-board-getting-started-with-bluetooth)
- [Intel® Edison Bluetooth Guide](http://download.intel.com/support/edison/sb/edisonbluetooth_331704004.pdf)

> rfkill is a small userspace tool to query the state of the rfkill switches, buttons and subsystem interfaces. Some devices come with a hard switch that lets you kill different types of RF radios: 802.11 / Bluetooth / NFC / UWB / WAN / WIMAX / FM. Some times these buttons may kill more than one RF type. The Linux kernel rfkill subsystem exposes these hardware buttons and lets userspace query its status and set its status through a /dev/rfkill. Given that at times some RF devices do not have hardware rfkill buttons rfkill the Linux kernel also exposes software rfkill capabilities that allows userspace to mimic a hardware rfkill event and turn on or off RF. 

- [Rfkill Homepage](https://wireless.wiki.kernel.org/en/users/documentation/rfkill)

## Required Applications

### Opkg

```sh
    root@edison:~# opkg install bluez5-dev
    root@edison:~# pip install pybluez
```

### Apt-Get

```sh
    root@edison:~# apt-get install bluetooth
    root@edison:~# /etc/init.d/bluetooth start
```

## Kernel Integration

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
    root@edison:/tmp# lsmod
    Module                  Size  Used by
    usb_f_acm              14335  1 
    ...
    bcm_bt_lpm             13708  0 
    bcm4334x              587105  0 
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

## Userspace Applications

- bluetooth-agent
- bluetoothctl
- hciconfig
- hcitool

```sh
    root@edison:~# systemctl status bluetooth.service
    root@edison:~# systemctl stop bluetooth
    root@edison:~# systemctl start bluetooth
    root@edison:~# systemctl enable bluetooth
    root@edison:~# rfkill unblock bluetooth
    root@edison:~# rfkill list bluetooth
    2: bcm43xx Bluetooth: bluetooth
    ...
    3: hci0: bluetooth
    ...
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

## Userspace Applications Usage Models

### Device Pairing

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

### Text

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

### Audio

```sh
    root@edison:~# apt-get install pulseaudio pulseaudio-module-bluetooth pavucontrol bluez-firmware
```

### Serial Port Profile (SPP)

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

## Links

- [Intel® Edison Boards Bluetooth® User Guide](http://www.intel.com/support/edison/sb/CS-035381.htm)
- http://alextgalileo.altervista.org/blog/install-kernel-from-repo-onto-edison-official-image/
- https://software.intel.com/en-us/articles/intel-edison-board-getting-started-with-bluetooth
- http://rexstjohn.com/lets-turn-intel-edison-into-an-ibeacon/
- http://unix.stackexchange.com/questions/53546/debian-squeeze-connect-to-a2dp-bluetooth-through-command-line
- https://software.intel.com/en-us/articles/using-the-generic-attribute-profile-gatt-in-bluetooth-low-energy-with-your-intel-edison
- https://software.intel.com/en-us/articles/connecting-the-intel-edison-board-to-your-android-phone-with-serial-port-profile-spp
- [Profiles](https://downloadmirror.intel.com/24909/eng/edison-bsp_rn_332032-007.pdf)
- https://learn.sparkfun.com/tutorials/bluetooth-basics
- [PyBluez API Ddoc](http://pybluez.googlecode.com/svn/www/docs-0.7/index.html)
- [PIP package manager](https://pip.pypa.io/en/stable/)
- http://shawnhymel.com/665/using-python-and-ble-to-receive-data-from-the-rfduino/
- http://shawnhymel.com/703/bluetooth-low-energy-peripherals-with-javascript/
- http://stephaniemoyerman.com/?p=100
- https://github.com/w4ilun/edison-guides/wiki/Configure-Intel-Edison-for-BLE---Bluetooth-Smart-Development
- https://software.intel.com/en-us/articles/connecting-to-intel-edison-from-android-with-bluetooth-le-ble
- http://stephaniemoyerman.com/?p=100

## SandBox

- Intel® Edison to a Bluetooth Network
- Intel® Edison from a peer device 

```sh
    root@edison:~# rfcomm bind - 40:78:6A:26:4A:C2 1
    root@edison:~# ls /dev/rfcomm0
```