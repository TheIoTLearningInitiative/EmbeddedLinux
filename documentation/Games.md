Games
==

```sh
abraham@aarcemor-desk:~$ sudo rfkill block bluetooth
abraham@aarcemor-desk:~$ dmesg | tail -5
[341098.027225] usb 3-11: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[341098.041129] Bluetooth: hci0: read Intel version: 370710018002030d00
[341098.041186] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[341098.221297] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[341113.327102] usb 3-11: USB disconnect, device number 21
abraham@aarcemor-desk:~$ sudo rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
abraham@aarcemor-desk:~$ sudo hciconfig -a
abraham@aarcemor-desk:~$ sudo rfkill unblock bluetooth
abraham@aarcemor-desk:~$ sudo hciconfig -a
hci0:	Type: BR/EDR  Bus: USB
	BD Address: E8:B1:FC:09:6A:FE  ACL MTU: 1021:5  SCO MTU: 96:5
	UP RUNNING PSCAN ISCAN 
	RX bytes:1183 acl:0 sco:0 events:131 errors:0
	TX bytes:21230 acl:0 sco:0 commands:130 errors:0
	Features: 0xff 0xfe 0x0f 0xfe 0xdb 0xff 0x7b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF 
	Link mode: SLAVE ACCEPT 
	Name: 'ubuntu-gnome-0'
	Class: 0x600100
	Service Classes: Audio, Telephony
	Device Class: Computer, Uncategorized
	HCI Version: 4.0 (0x6)  Revision: 0x500
	LMP Version: 4.0 (0x6)  Subversion: 0x500
	Manufacturer: Intel Corp. (2)

abraham@aarcemor-desk:~$ sudo rfkill list
abraham@aarcemor-desk:~$ dmesg | tail -5
[341153.123617] usb 3-11: New USB device found, idVendor=8087, idProduct=07dc
[341153.123624] usb 3-11: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[341153.137572] Bluetooth: hci0: read Intel version: 370710018002030d00
[341153.137624] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[341153.317738] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
abraham@aarcemor-desk:~$ 
```
