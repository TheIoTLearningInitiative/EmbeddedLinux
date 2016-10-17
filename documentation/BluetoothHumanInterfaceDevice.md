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