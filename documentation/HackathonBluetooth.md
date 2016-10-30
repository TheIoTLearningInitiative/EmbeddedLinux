# Hackathon

Install Android BlueTerm Application 

```sh
root@edison:~# rfkill unblock bluetooth
root@edison:~#  bluetoothctl
[NEW] Controller 98:4F:EE:04:21:2A edison [default]
[NEW] Device F8:CF:C5:D4:CB:BC Nexus 6
[bluetooth]# agent KeyboardDisplay
Agent registered
[bluetooth]# default-agent
Default agent request successful
[bluetooth]# scan on
[bluetooth]# scan off
[bluetooth]# pair F8:CF:C5:D4:CB:BC
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