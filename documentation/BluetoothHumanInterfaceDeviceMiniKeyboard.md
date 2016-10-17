# Human Interface Device Mini Keyboard

[Linux Kernel Drivers HID Kconfig](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/drivers/hid/Kconfig)

```sh
#
# HID driver configuration
#
menu "HID support"
     depends on INPUT

config HID
	tristate "HID bus support"
	depends on INPUT
	default y
	---help---
	  A human interface device (HID) is a type of computer device that
	  interacts directly with and takes input from humans. The term "HID"
	  most commonly used to refer to the USB-HID specification, but other
	  devices (such as, but not strictly limited to, Bluetooth) are
	  designed using HID specification (this involves certain keyboards,
	  mice, tablets, etc). This option adds the HID bus to the kernel,
	  together with generic HID layer code. The HID devices are added and
	  removed from the HID bus by the transport-layer drivers, such as
	  usbhid (USB_HID) and hidp (BT_HIDP).

	  For docs and specs, see http://www.usb.org/developers/hidpage/

```

```sh
config HID_GENERIC
	tristate "Generic HID driver"
	depends on HID
	default HID
	---help---
	Support for generic devices on the HID bus. This includes most
	keyboards and mice, joysticks, tablets and digitizers.

	To compile this driver as a module, choose M here: the module
	will be called hid-generic.
```

```sh
[ 2619.263744] pmic_ccsm pmic_ccsm: USB ID Detected. Notifying OTG driver
[ 2619.816228] dwc3-host dwc3-host.2: xHCI Host Controller
[ 2619.817019] dwc3-host dwc3-host.2: new USB bus registered, assigned bus numb
er 1
[ 2619.817279] dwc3-host dwc3-host.2: irq 34, io mem 0xf9100000
[ 2619.817420] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[ 2619.817444] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber
=1
[ 2619.817465] usb usb1: Product: xHCI Host Controller
[ 2619.817484] usb usb1: Manufacturer: Linux 3.10.98-poky-edison+ dwc-xhci
[ 2619.817503] usb usb1: SerialNumber: dwc3-host.2
[ 2619.818295] xHCI xhci_add_endpoint called for root hub
[ 2619.818316] xHCI xhci_check_bandwidth called for root hub
[ 2619.818590] hub 1-0:1.0: USB hub found
[ 2619.818634] hub 1-0:1.0: 1 port detected
[ 2619.819221] dwc3-host dwc3-host.2: xHCI Host Controller
[ 2619.819658] dwc3-host dwc3-host.2: new USB bus registered, assigned bus numb
er 2
[ 2619.819818] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[ 2619.819843] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 2619.819863] usb usb2: Product: xHCI Host Controller
[ 2619.819882] usb usb2: Manufacturer: Linux 3.10.98-poky-edison+ dwc-xhci
[ 2619.819901] usb usb2: SerialNumber: dwc3-host.2
[ 2619.820560] xHCI xhci_add_endpoint called for root hub
[ 2619.820580] xHCI xhci_check_bandwidth called for root hub
[ 2619.820859] hub 2-0:1.0: USB hub found
[ 2619.820903] hub 2-0:1.0: 1 port detected
[ 2619.883948] pmic_ccsm pmic_ccsm: USB VBUS Detected. Notifying OTG driver
[ 2624.725743] usb 1-1: new full-speed USB device number 2 using dwc3-host
[ 2624.749104] usb 1-1: New USB device found, idVendor=1997, idProduct=2433
[ 2624.749137] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2624.749158] usb 1-1: Product: Mini Keyboard
[ 2624.749177] usb 1-1: Manufacturer:  
[ 2624.762180] input:   Mini Keyboard as /devices/pci0000:00/0000:00:11.0/dwc3-host.2/usb1/1-1/1-1:1.0/input/input5
[ 2624.762980] hid-generic 0003:1997:2433.0003: input,hidraw1: USB HID v1.01 Keyboard [  Mini Keyboard] on usb-dwc3-host.2-1/input0
[ 2624.768056] input:   Mini Keyboard as /devices/pci0000:00/0000:00:11.0/dwc3-host.2/usb1/1-1/1-1:1.1/input/input6
[ 2624.768798] hid-generic 0003:1997:2433.0004: input,hidraw2: USB HID v1.01 Mouse [  Mini Keyboard] on usb-dwc3-host.2-1/input1
root@edison:~# 
```

```sh
root@edison:~# cat /sys/class/input/event3/device/name 
  Mini Keyboard
root@edison:~# cat /sys/class/input/event4/device/name 
  Mini Keyboard
```

```sh
root@edison:~# ./evtest /dev/input/event3
...
Testing ... (interrupt to exit)
Event: time 1476672494.485588, type 4 (Misc), code 4 (ScanCode), value 70004
Event: time 1476672494.485588, type 1 (Key), code 30 (A), value 1
Event: time 1476672494.485588, -------------- Report Sync ------------
Event: time 1476672494.709656, type 4 (Misc), code 4 (ScanCode), value 70004
Event: time 1476672494.709656, type 1 (Key), code 30 (A), value 0
Event: time 1476672494.709656, -------------- Report Sync ------------
Event: time 1476672496.885543, type 4 (Misc), code 4 (ScanCode), value 70005
Event: time 1476672496.885543, type 1 (Key), code 48 (B), value 1
Event: time 1476672496.885543, -------------- Report Sync ------------
Event: time 1476672497.117568, type 4 (Misc), code 4 (ScanCode), value 70005
Event: time 1476672497.117568, type 1 (Key), code 48 (B), value 0
Event: time 1476672497.117568, -------------- Report Sync ------------
...
```

```sh
root@edison:~#wget https://raw.githubusercontent.com/TheIoTLearningInitiative/EmbeddedLinux/master/tools/evtest.c
--2016-10-17 02:33:48--  https://raw.githubusercontent.com/TheIoTLearningInitiative/EmbeddedLinux/master/tools/evtest.c
Resolving raw.githubusercontent.com... 151.101.48.133
Connecting to raw.githubusercontent.com|151.101.48.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15169 (15K) [text/plain]
Saving to: 'evtest.c'

100%[======================================>] 15,169      --.-K/s   in 0.1s    

2016-10-17 02:33:50 (124 KB/s) - 'evtest.c' saved [15169/15169]

FINISHED --2016-10-17 02:33:50--
Total wall clock time: 17s
Downloaded: 1 files, 15K in 0.1s (124 KB/s)
```

```sh
root@edison:~# gcc -o evtest evtest.c 
```

```sh
root@edison:~# ./evtest /dev/input/event4
...
Testing ... (interrupt to exit)
Event: time 1476672547.074346, type 4 (Misc), code 4 (ScanCode), value 90001
Event: time 1476672547.074346, type 1 (Key), code 272 (LeftBtn), value 1
Event: time 1476672547.074346, -------------- Report Sync ------------
Event: time 1476672547.082311, type 4 (Misc), code 4 (ScanCode), value 90001
Event: time 1476672547.082311, type 1 (Key), code 272 (LeftBtn), value 0
Event: time 1476672547.082311, -------------- Report Sync ------------
Event: time 1476672550.842835, type 4 (Misc), code 4 (ScanCode), value 90001
Event: time 1476672550.842835, type 1 (Key), code 272 (LeftBtn), value 1
Event: time 1476672550.842835, -------------- Report Sync ------------
Event: time 1476672551.032624, type 4 (Misc), code 4 (ScanCode), value 90001
Event: time 1476672551.032624, type 1 (Key), code 272 (LeftBtn), value 0
Event: time 1476672551.032624, -------------- Report Sync ------------
Event: time 1476672551.748106, type 4 (Misc), code 4 (ScanCode), value 90002
Event: time 1476672551.748106, type 1 (Key), code 273 (RightBtn), value 1
Event: time 1476672551.748106, -------------- Report Sync ------------
Event: time 1476672551.923169, type 4 (Misc), code 4 (ScanCode), value 90002
Event: time 1476672551.923169, type 1 (Key), code 273 (RightBtn), value 0
Event: time 1476672551.923169, -------------- Report Sync ------------
...
```

```sh
root@edison:~# dmesg
[ 3208.262322] usb 1-1: USB disconnect, device number 2
[ 3208.292448] pmic_ccsm pmic_ccsm: USB ID Removed. Notifying OTG driver
[ 3208.551732] dwc3-host dwc3-host.2: remove, state 4
[ 3208.551797] usb usb2: USB disconnect, device number 1
[ 3208.552429] xHCI xhci_drop_endpoint called for root hub
[ 3208.552449] xHCI xhci_check_bandwidth called for root hub
[ 3208.553238] dwc3-host dwc3-host.2: USB bus 2 deregistered
[ 3208.553678] dwc3-host dwc3-host.2: remove, state 1
[ 3208.553720] usb usb1: USB disconnect, device number 1
[ 3208.563867] xHCI xhci_drop_endpoint called for root hub
[ 3208.563893] xHCI xhci_check_bandwidth called for root hub
[ 3208.565069] dwc3-host dwc3-host.2: USB bus 1 deregistered
[ 3209.377983] pmic_ccsm pmic_ccsm: USB VBUS Removed. Notifying OTG driver
```