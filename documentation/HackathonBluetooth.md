# Hackathon

```sh
root@edison:~# rfkill unblock bluetooth
root@edison:~# bluetoothctl
[NEW] Controller 98:4F:EE:04:1A:8C edison [default]
[bluetooth]# power on
[bluetooth]# agent on
[bluetooth]# scan on
[bluetooth]# pair <id android device>
[bluetooth]# trust <id android device>
[bluetooth]# connect <id you paired with>
[bluetooth]# exit
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
        pass    # Ignore any errors that may occur and try again

while True:
    bluetoothSerial.write( str("hola") )
    sleep(2)
print bluetoothSerial.readline()
```
