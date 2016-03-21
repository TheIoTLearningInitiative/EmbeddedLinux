Serial
==

> In telecommunication and computer science, serial communication is the process of sending data one bit at a time, sequentially, over a communication channel or computer bus. This is in contrast to parallel communication, where several bits are sent as a whole, on a link with several parallel channels. [Wikipedia](https://en.wikipedia.org/wiki/Serial_communication)

- [Intel Edison: using UART ttyMFD1 serial port](https://scivision.co/intel-edison-using-uart-ttymfd1-serial-port/)
- [Using USB-serial FTDI adapters with Intel Edison](https://scivision.co/using-usb-serial-ftdi-adapters-with-intel-edison/)
- [Intel Edison Types of Serial Ports](https://communities.intel.com/thread/54236)
- [Sparkfun Serial Terminal Basics](https://learn.sparkfun.com/tutorials/terminal-basics/all)
- [TLDP Serial HOWTO](http://www.tldp.org/HOWTO/Serial-HOWTO.html)

## Kernel Integration

### Kernel Display Message

```sh
    root@edison:~# dmesg | grep -i serial
    [    0.000000] Kernel command line: rootwait root=PARTUUID=012b3303-34ac-284d-99b4-34e03a2335f4 rootfstype=ext4 console=ttyMFD2 earlyprintk=ttyMFD2,keep loglevel=4 g_multi.ethernet_config=cdc systemd.unit=multi-user.target hardware_id=00 g_multi.iSerialNumber=5e7bb54a65035af180191c2d7bd527b6 g_multi.dev_addr=02:00:86:d5:27:b6 platform_mrfld_audio.audio_codec=dummy
    [    0.704157] HSU serial 0000:00:04.0: FUNC: 0 driver: 0 addr:ff010000 len:80
    [    0.704215] HSU serial 0000:00:04.1: FUNC: 1 driver: 0 addr:ff010080 len:80
    [    0.705663] HSU serial 0000:00:04.2: FUNC: 2 driver: 0 addr:ff010100 len:80
    [    0.707102] HSU serial 0000:00:04.3: FUNC: 3 driver: 0 addr:ff010180 len:80
    [    0.744061] usbcore: registered new interface driver usbserial
    [    0.744199] usbserial: USB Serial support registered for pl2303
    [    3.758915] systemd[1]: Starting system-serial\x2dgetty.slice.
    [    3.833730] systemd[1]: Created slice system-serial\x2dgetty.slice.

    root@edison:~# dmesg | grep -i tty
    [    0.000000] Kernel command line: rootwait root=PARTUUID=012b3303-34ac-284d-99b4-34e03a2335f4 rootfstype=ext4 console=ttyMFD2 earlyprintk=ttyMFD2,keep loglevel=4 g_multi.ethernet_config=cdc systemd.unit=multi-user.target hardware_id=00 g_multi.iSerialNumber=5e7bb54a65035af180191c2d7bd527b6 g_multi.dev_addr=02:00:86:d5:27:b6 platform_mrfld_audio.audio_codec=dummy
    [    0.705116] 0000:00:04.1: ttyMFD0 at MMIO 0xff010080 (irq = 28) is a hsu_bt_port_p
    [    0.706565] 0000:00:04.2: ttyMFD1 at MMIO 0xff010100 (irq = 29) is a hsu_uart1_port_p
    [    0.707871] 0000:00:04.3: ttyMFD2 at MMIO 0xff010180 (irq = 54) is a hsu_uart2_port_p
    [    0.713301] console [ttyMFD2] enabled
    [    1.969453] Bluetooth: RFCOMM TTY layer initialized
    [    2.776422] systemd[1]: Expecting device dev-ttyMFD2.device...
    [    3.758915] systemd[1]: Starting system-serial\x2dgetty.slice.
    [    3.833730] systemd[1]: Created slice system-serial\x2dgetty.slice.
    [    3.833870] systemd[1]: Starting system-getty.slice.
    [    3.883637] systemd[1]: Created slice system-getty.slice.
```
## Userspace Interfaces

### Sysfs

```sh
    root@edison:~# find /sys/ -name 'tty:ttyS*'
    /sys/devices/pci0000:00/0000:00:04.1/tty
    /sys/devices/pci0000:00/0000:00:04.1/tty/ttyMFD0
    /sys/devices/pci0000:00/0000:00:04.2/tty
    /sys/devices/pci0000:00/0000:00:04.2/tty/ttyMFD1
    /sys/devices/pci0000:00/0000:00:04.3/tty
    /sys/devices/pci0000:00/0000:00:04.3/tty/ttyMFD2
    /sys/devices/pci0000:00/0000:00:12.0/tty
    /sys/devices/pci0000:00/0000:00:12.0/tty/ttyPTI0
    /sys/devices/pci0000:00/0000:00:12.0/tty/ttyPTI1
    /sys/devices/virtual/tty
    /sys/devices/virtual/tty/tty
    /sys/devices/virtual/tty/tty0
    /sys/devices/virtual/tty/tty1
    ...
    /sys/devices/virtual/tty/ttyXX
    /sys/devices/platform/intel_mcu/tty             
    /sys/devices/platform/intel_mcu/tty/ttymcu0     
    /sys/devices/platform/intel_mcu/tty/ttymcu1     
    /sys/devices/platform/intel_mcu/tty/ttymcu2     
    /sys/class/tty                                  
    /sys/class/tty/tty                         
    /sys/class/tty/tty0                        
    /sys/class/tty/tty63                       
    /sys/class/tty/ttyMFD0                     
    /sys/class/tty/ttyMFD1                     
    /sys/class/tty/ttyMFD2                     
    /sys/class/tty/ttyPTI0                     
    /sys/class/tty/ttyPTI1                     
    /sys/class/tty/ttymcu0                     
    /sys/class/tty/ttymcu1                     
    /sys/class/tty/ttymcu2                     
    /sys/class/tty/ttyGS0
```

### Devfs

```sh
    root@edison:~# ls /dev/tty*
    /dev/tty      /dev/tty2     /dev/tty31    /dev/tty43    /dev/tty55    /dev/ttyGS0
    /dev/tty0     /dev/tty20    /dev/tty32    /dev/tty44    /dev/tty56    /dev/ttyMFD0
    /dev/tty1     /dev/tty21    /dev/tty33    /dev/tty45    /dev/tty57    /dev/ttyMFD1
    /dev/tty10    /dev/tty22    /dev/tty34    /dev/tty46    /dev/tty58    /dev/ttyMFD2
    /dev/tty11    /dev/tty23    /dev/tty35    /dev/tty47    /dev/tty59    /dev/ttyPTI0
    /dev/tty12    /dev/tty24    /dev/tty36    /dev/tty48    /dev/tty6     /dev/ttyPTI1
    /dev/tty13    /dev/tty25    /dev/tty37    /dev/tty49    /dev/tty60    /dev/ttymcu0
    /dev/tty14    /dev/tty26    /dev/tty38    /dev/tty5     /dev/tty61    /dev/ttymcu1
    /dev/tty15    /dev/tty27    /dev/tty39    /dev/tty50    /dev/tty62    /dev/ttymcu2
    /dev/tty16    /dev/tty28    /dev/tty4     /dev/tty51    /dev/tty63
    /dev/tty17    /dev/tty29    /dev/tty40    /dev/tty52    /dev/tty7
    /dev/tty18    /dev/tty3     /dev/tty41    /dev/tty53    /dev/tty8
    /dev/tty19    /dev/tty30    /dev/tty42    /dev/tty54    /dev/tty9
```

## Applications / Libraries

### Setup

#### Opkg

```sh
    root@edison:~# opkg install screen
    Installing screen (4.0.3-r4) on root.
    ...
    Configuring screen.
    root@edison:~# 
```
#### Pip

```sh
    root@edison:~# pip install pyserial
    Cleaning up...
    root@edison:~# 
```

#### Apt-Get

```sh
    root@edison:~# apt-get install screen minicom cu setserial stty
    root@edison:~# pip install pyserial
```

### Programs

```sh
    root@edison:~# screen /dev/ttyS0
    root@edison:~# minicom /dev/ttyS0
    root@edison:~# cu /dev/ttyUSB0 115200
    root@edison:~# setserial -g /dev/ttyS[0123]
    root@edison:~# setserial -g /dev/ttyUSBS[0123]
    root@edison:~# setserial -g /dev/ttyMFD[0123]
    root@edison:~# setserial /dev/ttyS0 115200
    root@edison:~# stty -F /dev/ttyUSB0 115200
    root@edison:~# stty -F /dev/ttyMFD 115200
```

### Python

```python
#!/usr/bin/python

import serial

ser = serial.Serial("/dev/ttyMFD0", timeout=10)
lines = ser.readlines()
for i in range(10):
    print(lines[i].strip())
```
