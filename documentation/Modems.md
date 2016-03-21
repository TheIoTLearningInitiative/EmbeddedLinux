Modems
==

> A modem (modulator-demodulator) is a network hardware device that modulates one or more carrier wave signals to encode digital information for transmission and demodulates signals to decode the transmitted information. The goal is to produce a signal that can be transmitted easily and decoded to reproduce the original digital data. [Wikipedia](https://en.wikipedia.org/wiki/Modem)

### Required Hardware

T & A Mobile Phones

## Applications / Libraries

### Setup

#### Apt-Get

```sh
    root@ubilinux:~# apt-get update
    root@ubilinux:~# apt-get install ppp bzip2 usb-modeswitch
    
    <Connect Modem>
    
    root@ubilinux:~# dmesg
    [  450.792009] usb 1-1.3: new high-speed USB device number 3 using dwc3-host
    [  450.817656] usb 1-1.3: New USB device found, idVendor=1bbb, idProduct=f017
    [  450.817688] usb 1-1.3: New USB device strings: Mfr=3, Product=2, SerialNumber=0
    [  450.817709] usb 1-1.3: Product: Mobile Broad Band
    [  450.817727] usb 1-1.3: Manufacturer: USBModem
    [  450.821346] usb-storage 1-1.3:1.0: USB Mass Storage device detected
    [  450.821851] scsi0 : usb-storage 1-1.3:1.0
    [  450.822947] usb-storage 1-1.3:1.1: USB Mass Storage device detected
    [  450.823370] scsi1 : usb-storage 1-1.3:1.1
    [  451.823343] scsi 0:0:0:0: Direct-Access     USBModem MMC Storage      2.31 PQ: 0 ANSI: 2
    [  451.824283] scsi 1:0:0:0: CD-ROM            USBModem MMC Storage      2.31 PQ: 0 ANSI: 2
    [  451.827155] sd 0:0:0:0: Attached scsi generic sg0 type 0
    [  451.828944] sr0: scsi-1 drive
    [  451.828967] cdrom: Uniform CD-ROM driver Revision: 3.20
    [  451.830033] sr 1:0:0:0: Attached scsi CD-ROM sr0
    [  451.830818] sr 1:0:0:0: Attached scsi generic sg1 type 5
    [  451.831854] sd 0:0:0:0: [sda] Attached SCSI removable disk
    root@ubilinux:~# lsusb
    Bus 001 Device 002: ID 8564:4000  
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 001 Device 003: ID 1bbb:f017 T & A Mobile Phones
    root@ubilinux:~# nano /etc/udev/rules.d/50-myrules.rules
    ATTRS{idVendor}=="1bbb",ATTRS{idProduct}=="0017", RUN+="/sbin/modprobe usbserial  vendor=0x1bbb product=0x0017"
```

```sh
    <Disconnect Modem>
    root@ubilinux:~# reboot
    <Connect Modem>
```

```sh
    root@ubilinux:~# tail -f /var/log/messages
    ...
    Jan 10 04:44:44 ubilinux usb_modeswitch: switching device 1bbb:f017 on 001/005
    Jan 10 04:44:44 ubilinux kernel: [  678.066175] usb 1-1.3: USB disconnect, device number 5
    Jan 10 04:44:47 ubilinux kernel: [  681.341248] usb 1-1.3: new high-speed USB device number 6 using dwc3-host
    Jan 10 04:44:47 ubilinux kernel: [  681.367432] usb 1-1.3: New USB device found, idVendor=1bbb, idProduct=011e
    Jan 10 04:44:47 ubilinux kernel: [  681.367464] usb 1-1.3: New USB device strings: Mfr=3, Product=2, SerialNumber=0
    Jan 10 04:44:47 ubilinux kernel: [  681.367485] usb 1-1.3: Product: Mobile Broad Band
    Jan 10 04:44:47 ubilinux kernel: [  681.367503] usb 1-1.3: Manufacturer: USBModem
    Jan 10 04:44:47 ubilinux kernel: [  681.386865] option 1-1.3:1.0: GSM modem (1-port) converter detected
    Jan 10 04:44:47 ubilinux kernel: [  681.387472] usb 1-1.3: GSM modem (1-port) converter now attached to ttyUSB0
    Jan 10 04:44:47 ubilinux kernel: [  681.388296] option 1-1.3:1.1: GSM modem (1-port) converter detected
    Jan 10 04:44:47 ubilinux kernel: [  681.388843] usb 1-1.3: GSM modem (1-port) converter now attached to ttyUSB1
    Jan 10 04:44:47 ubilinux kernel: [  681.389475] usb-storage 1-1.3:1.2: USB Mass Storage device detected
    Jan 10 04:44:47 ubilinux kernel: [  681.390829] scsi5 : usb-storage 1-1.3:1.2
    Jan 10 04:44:47 ubilinux kernel: [  681.392186] option 1-1.3:1.3: GSM modem (1-port) converter detected
    Jan 10 04:44:47 ubilinux kernel: [  681.392818] usb 1-1.3: GSM modem (1-port) converter now attached to ttyUSB2
    Jan 10 04:44:48 ubilinux kernel: [  682.392520] scsi 5:0:0:0: Direct-Access     USBModem MMC Storage      2.31 PQ: 0 ANSI: 2
    Jan 10 04:44:48 ubilinux kernel: [  682.394153] sd 5:0:0:0: Attached scsi generic sg0 type 0
    Jan 10 04:44:48 ubilinux kernel: [  682.396784] sd 5:0:0:0: [sda] Attached SCSI removable disk
```

Sakis 3G

    root@ubilinux:~# wget "http://www.sakis3g.com/downloads/sakis3g.tar.gz" -O sakis3g.tar.gz
    root@ubilinux:~# tar -xzvf sakis3g.tar.gz
    root@ubilinux:~# chmod +x sakis3g
    root@ubilinux:~# ./sakis3g --interactive
    ...
    root@ubilinux:~# ping google.com

## Links  
    
- https://boundarydevices.com/cellular-modems-on-i-mx6-boards/
- https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/211095
- http://www.monblocnotes.com/node/1943
- http://www.paoli.cz/en/lte-modules-1/huawei-me909u-521-mini-pcie.html?cur=1&lang=1&&redirected=1
- http://www.paoli.cz/out/media/Guide_to_Kernel_Driver_Integration_in_Linux_for_Huawei_Modules(1).pdf