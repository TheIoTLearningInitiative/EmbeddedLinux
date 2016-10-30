# Hackathon

Install Android BlueTerm Application 

```sh
root@edison:~# rfkill unblock bluetooth
root@edison:~# bluetoothctl
[NEW] Controller 98:4F:EE:04:21:2A edison [default]
[NEW] Device F8:CF:C5:D4:CB:BC Nexus 6
[bluetooth]# agent KeyboardDisplay
Agent registered
[bluetooth]# default-agent
Default agent request successful
[bluetooth]# scan on
Discovery started
[CHG] Controller 98:4F:EE:04:21:2A Discovering: yes
[CHG] Device F1:C1:83:A4:17:0C RSSI: -57
[CHG] Device F1:C1:83:A4:17:0C TxPower: -12
[NEW] Device F8:CF:C5:D4:CB:BC Nexus 6
[bluetooth]# scan off 
[CHG] Device F8:CF:C5:D4:CB:BC RSSI is nil
[CHG] Device F1:C1:83:A4:17:0C TxPower is nil
[CHG] Device F1:C1:83:A4:17:0C RSSI is nil
[CHG] Controller 98:4F:EE:04:21:2A Discovering: no
Discovery stopped
Attempting to pair with F8:CF:C5:D4:CB:BC
[CHG] Device F8:CF:C5:D4:CB:BC Connected: yes
Request confirmation
[agent] Confirm passkey 061443 (yes/no): yes
[CHG] Device F8:CF:C5:D4:CB:BC Modalias: bluetooth:v000Fp1200d1436
[CHG] Device F8:CF:C5:D4:CB:BC UUIDs: 00001105-0000-1000-8000-00805f9b34fb
[CHG] Device F8:CF:C5:D4:CB:BC UUIDs: 0000110a-0000-1000-8000-00805f9b34fb
[CHG] Device F8:CF:C5:D4:CB:BC UUIDs: 0000110c-0000-1000-8000-00805f9b34fb
[CHG] Device F8:CF:C5:D4:CB:BC UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Device F8:CF:C5:D4:CB:BC UUIDs: 00001112-0000-1000-8000-00805f9b34fb
[CHG] Device F8:CF:C5:D4:CB:BC UUIDs: 00001115-0000-1000-8000-00805f9b34fb
[CHG] Device F8:CF:C5:D4:CB:BC UUIDs: 00001116-0000-1000-8000-00805f9b34fb
[CHG] Device F8:CF:C5:D4:CB:BC UUIDs: 0000111f-0000-1000-8000-00805f9b34fb
[CHG] Device F8:CF:C5:D4:CB:BC UUIDs: 0000112f-0000-1000-8000-00805f9b34fb
[CHG] Device F8:CF:C5:D4:CB:BC UUIDs: 00001132-0000-1000-8000-00805f9b34fb
[CHG] Device F8:CF:C5:D4:CB:BC UUIDs: 00001200-0000-1000-8000-00805f9b34fb
[CHG] Device F8:CF:C5:D4:CB:BC UUIDs: 00001800-0000-1000-8000-00805f9b34fb
[CHG] Device F8:CF:C5:D4:CB:BC UUIDs: 00001801-0000-1000-8000-00805f9b34fb
[CHG] Device F8:CF:C5:D4:CB:BC Paired: yes
Pairing successful
[CHG] Device F8:CF:C5:D4:CB:BC Connected: no
[bluetooth]# disconnect F8:CF:C5:D4:CB:BC
Attempting to disconnect from F8:CF:C5:D4:CB:BC
Successful disconnected
[bluetooth]# exit
Agent unregistered
[DEL] Controller 98:4F:EE:04:21:2A edison [default]
```

```sh
root@edison:~# rfcomm listen 0 1 &
[1] 400
root@edison:~# Waiting for connection on channel 1

root@edison:~# Connection from F8:CF:C5:D4:CB:BC to /dev/rfcomm0
Press CTRL-C for hangup
```

Connect from Android device from BlueTerm application

```sh
root@edison:~# cat /dev/rfcomm0
```

Write data from Android device to BlueTerm application

```python
#! /usr/bin/python

import serial
from time import sleep

bluetoothSerial = serial.Serial("/dev/rfcomm0", baudrate=9600)

while True:

    bluetoothSerial.write(str("Hola!"))
    sleep(2)
```

# Node

```sh
root@edison:~# npm install bluetooth-serial-port
```