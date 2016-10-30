# Advanced Audio Distribution Profile

```sh
root@edison:~# rfkill unblock bluetooth
  root@edison:~# bluetoothctl
```

```sh
[bluetooth]# scan on
Discovery started
[CHG] Controller 98:4F:EE:04:21:2A Discovering: yes
[NEW] Device F1:C1:83:A4:17:0C Evolutel
[NEW] Device 58:51:00:00:41:4D BT MINI
[CHG] Device F1:C1:83:A4:17:0C RSSI: -83
[CHG] Device F1:C1:83:A4:17:0C RSSI: -73
```

```sh
[bluetooth]# scan off
[CHG] Device 58:51:00:00:41:4D RSSI is nil
[CHG] Device F1:C1:83:A4:17:0C TxPower is nil
[CHG] Device F1:C1:83:A4:17:0C RSSI is nil
[CHG] Controller 98:4F:EE:04:21:2A Discovering: no
Discovery stopped
```

```sh
[bluetooth]# pair 58:51:00:00:41:4D
Attempting to pair with 58:51:00:00:41:4D
[CHG] Device 58:51:00:00:41:4D Connected: yes
[CHG] Device 58:51:00:00:41:4D UUIDs: 00001108-0000-1000-8000-00805f9b34fb
[CHG] Device 58:51:00:00:41:4D UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Device 58:51:00:00:41:4D UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Device 58:51:00:00:41:4D UUIDs: 0000111e-0000-1000-8000-00805f9b34fb
[CHG] Device 58:51:00:00:41:4D Paired: yes
Pairing successful
[CHG] Device 58:51:00:00:41:4D Connected: no
```

```sh
[bluetooth]# connect 58:51:00:00:41:4D
Attempting to connect to 58:51:00:00:41:4D
[CHG] Device 58:51:00:00:41:4D Connected: yes
Connection successful
[CHG] Device 58:51:00:00:41:4D UUIDs: 00001108-0000-1000-8000-00805f9b34fb
[CHG] Device 58:51:00:00:41:4D UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Device 58:51:00:00:41:4D UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Device 58:51:00:00:41:4D UUIDs: 0000111e-0000-1000-8000-00805f9b34fb
[CHG] Device 58:51:00:00:41:4D UUIDs: 0000111f-0000-1000-8000-00805f9b34fb
```

```sh
[BT MINI]# quit
[DEL] Controller 98:4F:EE:04:21:2A edison [default]
```

```sh
root@edison:~# pactl list sinks
Sink #0
        State: SUSPENDED
        Name: alsa_output.platform-merr_dpcm_dummy.0.analog-stereo
        Description: dummy-audio Analog Stereo
        Driver: module-alsa-card.c
        Sample Specification: s16le 2ch 48000Hz
        Channel Map: front-left,front-right
        Owner Module: 1
        Mute: no
        Volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100%$
                balance 0.00
        Base Volume: 65536 / 100% / 0.00 dB
        Monitor Source: alsa_output.platform-merr_dpcm_dummy.0.analog-stereo.mo$
        Latency: 0 usec, configured 0 usec
        Flags: HARDWARE DECIBEL_VOLUME LATENCY
        Properties:
                alsa.resolution_bits = "16"
                device.api = "alsa"
                device.class = "sound"
                alsa.class = "generic"
                alsa.subclass = "generic-mix"
                alsa.name = ""
                alsa.id = "1"
                alsa.subdevice = "0"
                alsa.subdevice_name = "subdevice #0"
                alsa.device = "0"
                alsa.card = "1"
                alsa.card_name = "dummy-audio"
                alsa.long_card_name = "dummy-audio"
                device.bus_path = "platform-merr_dpcm_dummy.0"
                sysfs.path = "/devices/platform/merr_dpcm_dummy.0/sound/card1"
                device.string = "hw:1"
...
...
Sink #1
        State: SUSPENDED
        Name: alsa_output.0.analog-stereo
        Description: Loopback Analog Stereo  
        Driver: module-alsa-card.c
        Sample Specification: s16le 2ch 44100Hz
        Channel Map: front-left,front-right
        Owner Module: 2
        Mute: no
        Volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100%$
        Base Volume: 65536 / 100% / 0.00 dB
        Monitor Source: alsa_output.0.analog-stereo.monitor
        Latency: 0 usec, configured 0 usec
        Flags: HARDWARE HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY
        Properties:
                alsa.resolution_bits = "16"
                device.api = "alsa"
                device.class = "sound"
                alsa.class = "generic"
                alsa.subclass = "generic-mix"
                alsa.name = "Loopback PCM"
                alsa.id = "Loopback PCM"
                alsa.subdevice = "0"
                alsa.subdevice_name = "subdevice #0"
                alsa.device = "0"
                alsa.card = "0"
                alsa.card_name = "Loopback"
                alsa.long_card_name = "Loopback 1"
                device.bus_path = "/devices/virtual/sound/card0"

...
...
Sink #2
        State: SUSPENDED
        Name: bluez_sink.58_51_00_00_41_4D
        Description: BT MINI
        Driver: module-bluez5-device.c
        Sample Specification: s16le 2ch 44100Hz
        Channel Map: front-left,front-right
        Owner Module: 13
        Mute: no
        Volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100%$
                balance 0.00
        Base Volume: 65536 / 100% / 0.00 dB
        Monitor Source: bluez_sink.58_51_00_00_41_4D.monitor
        Latency: 0 usec, configured 0 usec
        Flags: HARDWARE DECIBEL_VOLUME LATENCY
        Properties:
                bluetooth.protocol = "a2dp_sink"
                device.description = "BT MINI"
                device.string = "58:51:00:00:41:4D"
                device.api = "bluez"
                device.class = "sound"
                device.bus = "bluetooth"
                device.form_factor = "headset"

```

```sh
root@edison:~# pactl list sinks | grep "Name:"
        Name: alsa_output.platform-merr_dpcm_dummy.0.analog-stereo
        Name: alsa_output.0.analog-stereo
        Name: bluez_sink.58_51_00_00_41_4D
root@edison:~#  
```

```sh
root@edison:~# pactl set-default-sink
You have to specify a sink name
root@edison:~# pactl set-default-sink bluez_sink.58_51_00_00_41_4D
```

```sh
root@edison:~# wget http://www.wavsource.com/snds_2016-10-09_1797402624934163/animals/bear_growl_y.wav
```

```sh
  root@edison:~# gst-launch-1.0 filesrc location=bear_growl_y.wav  ! wavparse ! pulsesink
Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
Pipeline is PREROLLED ...
Setting pipeline to PLAYING ...
New clock: GstPulseSinkClock
Got EOS from element "pipeline0".
Execution ended after 0:00:04.593652623
Setting pipeline to PAUSED ...
Setting pipeline to READY ...
root@edison:~# 
```

```sh
root@edison:~# wget https://dl.last.fm/static/1477806840/131211148/80e73bda617b3f102999b714b5515dc57d8c33986ea28b4a3a8395b62f15700c/Death+Grips+-+Get+Got.mp3
root@edison:~# mv Death+Grips+-+Get+Got.mp3 music.mp3
root@edison:~# gst-launch-1.0 filesrc location=music.mp3  ! mad
WARNING: erroneous pipeline: no element "mad"

```

```sh
root@edison:~# bluetoothctl
[NEW] Controller 98:4F:EE:04:21:2A edison [default]
[NEW] Device 58:51:00:00:41:4D BT MINI
[bluetooth]# 
```

```sh
[bluetooth]# paired-devices
Device 58:51:00:00:41:4D BT MINI
```

```sh
[bluetooth]# remove 58:51:00:00:41:4D
[bluetooth]# paired-devices
Device 58:51:00:00:41:4D BT MINI
Device has been removed
[CHG] Device 58:51:00:00:41:4D Connected: no
[DEL] Device 58:51:00:00:41:4D BT MINI
[bluetooth]# paired-devices
[bluetooth]# 
```