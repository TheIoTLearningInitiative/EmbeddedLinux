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

```sh
[VR-PARK]# paired-devices
Device 20:16:04:13:03:CE VR-PARK
[VR-PARK]# exit
[DEL] Controller 98:4F:EE:04:21:2A edison [default]
```

```sh
root@edison:~# cat /sys/class/bluetooth/hci0/name
edison
root@edison:~# ls /sys/class/bluetooth/hci0     
hci0/    hci0:11/ 
root@edison:~# ls /sys/class/bluetooth/hci0:11/
0005:05AC:3232.0002  device    input4  subsystem  uevent
address              features  power   type
root@edison:~# cat /sys/class/bluetooth/hci0:11/type  
ACL
root@edison:~# ls /sys/class/bluetooth/hci0:11/input4/ 
capabilities  event2  modalias  phys   properties  uevent
device        id      name      power  subsystem   uniq
root@edison:~# cat /sys/class/bluetooth/hci0:11/input4/name
VR-PARK
root@edison:~# 
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
root@edison:~# ./evtest /dev/input/event2
```
