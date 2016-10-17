# Human Interface Device

```sh
root@edison:~# bluetoothctl
[NEW] Controller 98:4F:EE:04:21:2A edison [default]
[NEW] Device 58:51:00:00:41:4D BT MINI
[NEW] Device 6F:E8:92:3B:FB:06 6F-E8-92-3B-FB-06
[NEW] Device F1:C1:83:A4:17:0C Evolutel
```

```sh
[bluetooth]# scan on
Discovery started
[CHG] Controller 98:4F:EE:04:21:2A Discovering: yes
[CHG] Device F1:C1:83:A4:17:0C RSSI: -53
[CHG] Device F1:C1:83:A4:17:0C TxPower: -12
[NEW] Device 20:16:04:13:03:CE 20-16-04-13-03-CE
[CHG] Device 20:16:04:13:03:CE LegacyPairing: no
[CHG] Device 20:16:04:13:03:CE Name: VR-PARK
[CHG] Device 20:16:04:13:03:CE Alias: VR-PARK
[CHG] Device 20:16:04:13:03:CE LegacyPairing: yes
```

```sh
[bluetooth]# scan off
[CHG] Device 20:16:04:13:03:CE RSSI is nil
[CHG] Device F1:C1:83:A4:17:0C TxPower is nil
[CHG] Device F1:C1:83:A4:17:0C RSSI is nil
[CHG] Controller 98:4F:EE:04:21:2A Discovering: no
Discovery stopped
[bluetooth]# 
```

```sh
[bluetooth]# pair 20:16:04:13:03:CE
Attempting to pair with 20:16:04:13:03:CE
[CHG] Device 20:16:04:13:03:CE Connected: yes
[CHG] Device 20:16:04:13:03:CE Modalias: usb:v05ACp3232d0001
[CHG] Device 20:16:04:13:03:CE UUIDs: 00001124-0000-1000-8000-00805f9b34fb
[CHG] Device 20:16:04:13:03:CE UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Device 20:16:04:13:03:CE Paired: yes
Pairing successful
[CHG] Device 20:16:04:13:03:CE Connected: no
```

```sh
[bluetooth]# connect 20:16:04:13:03:CE
Attempting to connect to 20:16:04:13:03:CE
[CHG] Device 20:16:04:13:03:CE Connected: yes
Connection successful
[VR-PARK]# [ 1811.274092] hid-generic 0005:05AC:3232.0002: unknown main item tag 0x0
```