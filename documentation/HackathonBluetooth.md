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

root@edison:~# cat /dev/rfcomm0
ythgffuuhgghhgg
```

```sh
root@edison:~# rfkill unblock bluetooth
root@edison:~# hciconfig hci0 up
root@edison:~# bluetoothctl
[NEW] Controller 98:4F:EE:04:1A:8C MyEdison [default]
[NEW] Device 98:4F:EE:06:1B:99 edison
[NEW] Device 2C:D0:5A:80:7A:44 AARCEMOR-MOBL3
[NEW] Device 40:78:6A:26:4A:C2 XT1008
[bluetooth]# discoverable on
Changing discoverable on succeeded
[bluetooth]# pairable on
Changing pairable on succeeded
[CHG] Device 40:78:6A:26:4A:C2 Connected: yes
[CHG] Device 40:78:6A:26:4A:C2 Connected: no
[bluetooth]# agent on
Agent registered
[bluetooth]# default-agent
Default agent request successful
[bluetooth]# quit
Agent unregistered
[DEL] Controller 98:4F:EE:04:1A:8C MyEdison [default]
root@edison:~# rfcomm listen hci0 &
[1] 377
root@edison:~# Waiting for connection on channel 1
Connection from 40:78:6A:26:4A:C2 to /dev/rfcomm0
Press CTRL-C for hangup
root@edison:~# 
```

Connect from Android device from BlueTerm application

```sh
root@edison:~# cat /dev/rfcomm0
```

Write data from Android device from BlueTerm application

```python
#! /usr/bin/python

import serial
from time import sleep

bluetoothSerial = serial.Serial( "/dev/rfcomm0", baudrate=9600 )

count = None
while count == None:
    try:
        count = int(raw_input( "Please enter the number of times to blink the LED" ))
    except:
        pass

while True:
    bluetoothSerial.write( str("hola") )
    sleep(2)
print bluetoothSerial.readline()
```
