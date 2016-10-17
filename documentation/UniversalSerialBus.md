# Universal Serial Bus

> USB, short for Universal Serial Bus, is an industry standard developed in the mid-1990s that defines the cables, connectors and communications protocols used in a bus for connection, communication, and power supply between computers and electronic devices.[4] It is currently developed by the USB Implementers Forum. [Wikipedia](https://en.wikipedia.org/wiki/USB)

- [Intel Edison USB Host](http://pagealh.com/2015/08/09/getting-started-intel-edison-usb-host/)
- [Linux Journal Greg Kroah-Hartman Writing a Simple USB Driver](http://www.linuxjournal.com/article/7353?page=0,0)
- [Linux Journal Greg Kroah-Hartman How to Write a Linux USB Device Driver](http://www.linuxjournal.com/article/4786)
- [Persistent Names](https://github.com/KurtE/Intel-Edison-and-Galileo)
- [Persistent Names](http://hintshop.ludvig.co.nz/show/persistent-names-usb-serial-devices/)

> Yoctopuce
> > Yoctopuce designs, manufactures and sells USB devices to let your computer sit in the real world, not in the cloud. Our USB modules are tiny, easy to install and easy to drive programmatically. [Homepage](http://www.yoctopuce.com/)

## Kernel Integration

### Kernel Display Message

```sh
    root@edison:~# dmesg | grep -i usb
    [    0.207321] usbcore: registered new interface driver usbfs
    [    0.207421] usbcore: registered new interface driver hub
    [    0.207628] usbcore: registered new device driver usb
    [    0.742079] usbcore: registered new interface driver asix
    [    0.742161] usbcore: registered new interface driver cdc_subset
    [    0.742291] usbcore: registered new interface driver cdc_ncm
    [    0.744743] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
    [    0.745063] usbcore: registered new interface driver cdc_acm
    [    0.745081] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
    [    0.745196] usbcore: registered new interface driver usb-storage
    [    0.745383] usbcore: registered new interface driver usbserial
    [    0.745454] usbcore: registered new interface driver pl2303
    [    0.745521] usbserial: USB Serial support registered for pl2303
    [    1.666307] usbcore: registered new interface driver usbhid
    ...
```

### Kernel Modules

```sh
    root@edison:~# lsmod
    Module                  Size  Used by
    ...
    usb_f_acm              14335  1 
    u_serial               18582  6 usb_f_acm
    g_multi                70924  0 
    libcomposite           39245  2 usb_f_acm,g_multi
    ...
```
## Userspace Interfaces

### Sysfs

```sh
    root@edison:~# ls -l /sys/bus/usb/drivers/
    drwxr-xr-x    2 root     root             0 Jan  1  2000 asix
    drwxr-xr-x    2 root     root             0 Jan  1  2000 cdc_acm
    drwxr-xr-x    2 root     root             0 Jan  1  2000 cdc_ncm
    drwxr-xr-x    2 root     root             0 Jan  1  2000 cdc_subset
    drwxr-xr-x    2 root     root             0 Jan  1  2000 hub
    drwxr-xr-x    2 root     root             0 Jan  1  2000 pl2303
    drwxr-xr-x    2 root     root             0 Jan  1  2000 snd-usb-audio
    drwxr-xr-x    2 root     root             0 Jan  1  2000 usb
    drwxr-xr-x    2 root     root             0 Jan  1  2000 usb-storage
    drwxr-xr-x    2 root     root             0 Jan  1  2000 usbfs
    drwxr-xr-x    2 root     root             0 Jan  1  2000 usbhid
    drwxr-xr-x    2 root     root             0 Jan  1  2000 usbserial
    drwxr-xr-x    2 root     root             0 Mar 21 18:21 uvcvideo
    root@edison:~# cat /sys/bus/usb/drivers/option/***/bInterface*
    root@edison:~# cat /proc/bus/usb/devices
```
## Applications / Libraries

> libusb
> > C library that gives applications easy access to USB devices on many different operating systems. [libusb homepage](http://www.libusb.org/)

### Setup

#### Opkg

```sh
    root@edison:~# opkg install libusb-1.0-dev
```

```sh
root@edison:~# pip install pyusb
Downloading/unpacking pyusb
  Downloading PyUSB-1.0.0.tar.gz (52kB): 52kB downloaded
  Running setup.py egg_info for package pyusb
    
Installing collected packages: pyusb
  Running setup.py install for pyusb
    
Successfully installed pyusb
Cleaning up...
root@edison:~# 
```

#### Apt-Get

```sh
    root@edison:~# apt-get install libusb-1.0-dev libudev-dev
    root@edison:~# apt-get install libtool
```

### Programs

#### Lsusb

If USB-host is not powered

```sh
root@edison:~# lsusb
    unable to initialize libusb: -99
```

If USB-host is powered

```sh
    root@edison:~# lsusb
    Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    root@edison:~# ls -l /sys/bus/usb/drivers
    total 0
    drwxr-xr-x 2 root root 0 Jan  1 00:01 asix
    drwxr-xr-x 2 root root 0 Jan  1 00:01 cdc_acm
    drwxr-xr-x 2 root root 0 Jan  1 00:01 cdc_ncm
    drwxr-xr-x 2 root root 0 Jan  1 00:01 cdc_subset
    drwxr-xr-x 2 root root 0 Jan  1 00:01 ftdi_sio
    drwxr-xr-x 2 root root 0 Jan  1 00:01 hub
    drwxr-xr-x 2 root root 0 Jan  1 00:01 pl2303
    drwxr-xr-x 2 root root 0 Jan  1 00:01 snd-usb-audio
    drwxr-xr-x 2 root root 0 Jan  1 00:01 usb
    drwxr-xr-x 2 root root 0 Jan  1 00:01 usbfs
    drwxr-xr-x 2 root root 0 Jan  1 00:01 usbhid
    drwxr-xr-x 2 root root 0 Jan  1 00:01 usbserial
    drwxr-xr-x 2 root root 0 Jan  1 00:01 usb-storage
    drwxr-xr-x 2 root root 0 Jan  1 00:01 uvcvideo
```

##### Libusb Git Repository

```sh
    root@edison:~# git clone https://github.com/libusb/libusb.git
    root@edison:~# cd libusb
    root@edison:~# ./autogen.sh -disable-udev
    root@edison:~# make
    root@edison:~# cd examples
    root@edison:~# ./listdevs
    1d6b:0003 (bus 2, device 1)
    0458:708a (bus 1, device 3) path: 1.1
    05e3:0606 (bus 1, device 2) path: 1
    1d6b:0002 (bus 1, device 1)
```
