# Human Interface Device Mini Keyboard

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


```