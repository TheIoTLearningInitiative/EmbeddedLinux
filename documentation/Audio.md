# Audio

> An audio signal is a representation of sound, typically as an electrical voltage. Audio signals have frequencies in the audio frequency range of roughly 20 to 20,000 Hz (the limits of human hearing). [wikipedia](https://en.wikipedia.org/wiki/Audio_signal)

- [Intel Edison Audio Setup Guide](http://download.intel.com/support/edison/sb/edisonaudio_332434001.pdf)
- [Edidoom Intel Edison Audio](https://github.com/llatta/edison-audio)
- [Play Audio from your Intel® Edison via Bluetooth* using Advanced Audio Distribution Profile (A2DP)](https://software.intel.com/en-us/articles/play-audio-from-your-intel-edison-via-bluetooth-using-advanced-audio-distribution-profile)

### Required Hardware

USB Audio Dongle USB PnP Sound Device

## Kernel Integration

> Advanced Linux Sound Architecture
> > The Advanced Linux Sound Architecture (ALSA) provides audio and MIDI functionality to the Linux operating system.

- [Advanced Linux Sound Architecture Homepage](http://www.alsa-project.org/main/index.php/Main_Page)

### Kernel Display Message

```sh
root@edison:~# dmesg
...
[ 3750.683557] hub 1-0:1.0: USB hub found
[ 3750.683602] hub 1-0:1.0: 1 port detected
[ 3750.684174] dwc3-host dwc3-host.2: xHCI Host Controller
[ 3750.684573] dwc3-host dwc3-host.2: new USB bus registered, assigned bus number 2
[ 3750.684764] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[ 3750.684789] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 3750.684809] usb usb2: Product: xHCI Host Controller
[ 3750.684829] usb usb2: Manufacturer: Linux 3.10.98-poky-edison+ dwc-xhci
[ 3750.684848] usb usb2: SerialNumber: dwc3-host.2
[ 3750.688503] xHCI xhci_add_endpoint called for root hub
[ 3750.688527] xHCI xhci_check_bandwidth called for root hub
[ 3750.688852] hub 2-0:1.0: USB hub found
[ 3750.688899] hub 2-0:1.0: 1 port detected
[ 3750.749302] pmic_ccsm pmic_ccsm: USB VBUS Detected. Notifying OTG driver
[ 3751.001112] usb 1-1: new full-speed USB device number 2 using dwc3-host
[ 3751.023554] usb 1-1: New USB device found, idVendor=0d8c, idProduct=013c
[ 3751.023585] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 3751.023607] usb 1-1: Product: USB PnP Sound Device
[ 3751.055963] input: USB PnP Sound Device as /devices/pci0000:00/0000:00:11.0/dwc3-host.2/usb1/1-1/1-1:1.3/input/input7
[ 3751.056818] hid-generic 0003:0D8C:013C.0005: input,hidraw0: USB HID v1.00 Device [USB PnP Sound Device] on usb-dwc3-host.2-1/input3
```

### USB Devices

```sh
root@edison:~# lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0d8c:013c C-Media Electronics, Inc. CM108 Audio Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

## Userspace Interfaces

### ProcFs

```sh
root@edison:~# cat /proc/asound/cards
 0 [Loopback       ]: Loopback - Loopback
                      Loopback 1
 1 [dummyaudio     ]: dummy-audio - dummy-audio
                      dummy-audio
 2 [Device         ]: USB-Audio - USB PnP Sound Device
                      USB PnP Sound Device at usb-dwc3-host.2-1, full speed
root@edison:~# 
```

## Applications / Libraries

### Setup

#### Opkg

```sh
root@edison:~# opkg install alsa-utils mpg123 espeak
...
Configuring libsamplerate0.
Configuring libjack.
Configuring alsa-utils-alsaloop.
Configuring alsa-utils-alsaucm.
Configuring alsa-utils-midi.
Configuring alsa-utils-iecset.
Configuring alsa-utils-aconnect.
Configuring libportaudio2.
Configuring espeak.
Configuring alsa-utils-speakertest.
Configuring alsa-utils-aseqnet.
Configuring alsa-utils-aseqdump.
Configuring alsa-utils.
Configuring mpg123.
...
```

```sh
root@edison:~# opkg install --nodeps jack-dev 
Installing jack-dev (0.121.0-r0) on root.
Downloading http://repo.opkg.net/edison/repo/core2-32/jack-dev_0.121.0-r0_core2-32.ipk.
Configuring jack-dev.
```

```sh
root@edison:~# opkg install --nodeps libportaudio-dev
Installing libportaudio-dev (v19+svnr1387-r0) on root.
Downloading http://repo.opkg.net/edison/repo/core2-32/libportaudio-dev_v19+svnr1387-r0_core2-32.ipk.
Configuring libportaudio-dev.
root@edison:~# 
```

#### Apt-Get

```sh
    root@edison:~# apt-get install alsa-utils mpg123 espeak
```

### Free Sound Effects

- [Soundbible](http://soundbible.com/)
- [Soundjay](http://www.soundjay.com/)
- [freeSFX](http://www.freesfx.co.uk/)

### Programs

- [Mad](http://www.underbit.com/products/mad/)

#### Audio Files

```sh
    root@edison:~# ls /usr/share/sounds/alsa/
    Front_Center.wav  Noise.wav         Rear_Right.wav
    Front_Left.wav    Rear_Center.wav   Side_Left.wav
    Front_Right.wav   Rear_Left.wav     Side_Right.wav
```

#### List Capture Hardware Devices

```sh
root@edison:~# arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Loopback [Loopback], device 0: Loopback PCM [Loopback PCM]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Loopback [Loopback], device 1: Loopback PCM [Loopback PCM]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: dummyaudio [dummy-audio], device 0: 14 []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: dummyaudio [dummy-audio], device 1: ((null)) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: dummyaudio [dummy-audio], device 2: ((null)) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Device [USB PnP Sound Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@edison:~# 
```

#### List Playback Hardware Devices

```sh
root@edison:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Loopback [Loopback], device 0: Loopback PCM [Loopback PCM]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Loopback [Loopback], device 1: Loopback PCM [Loopback PCM]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: dummyaudio [dummy-audio], device 0: 14 []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: dummyaudio [dummy-audio], device 1: ((null)) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: dummyaudio [dummy-audio], device 2: ((null)) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Device [USB PnP Sound Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

#### Arecord / Aplay

```sh
root@edison:~# arecord -f cd -D plughw:2,0 -d 20 test.wav # USB
Recording WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
^CAborted by signal Interrupt...
root@edison:~# aplay -D hw:2,0 test.wav # USB
Playing WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
```

#### Device Configuration

```sh
root@edison:~# vi ~/.asoundrc
```

```sh
pcm.!default {
    type plug
       slave {
           pcm "hw:2,0"
       }
}
ctl.!default {
    type plug
        slave {
           pcm "hw:2,0"
       }
}
```

```sh
root@edison:~# arecord -f cd -d 20 test.wav
Recording WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
^CAborted by signal Interrupt...
root@edison:~# aplay test.wav
Playing WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
```

```sh
pcm.!default {
        type asym
        playback.pcm {
                type plug
                slave.pcm "hw:2,0"
        }
        capture.pcm {
                type plug
                slave.pcm "hw:3,0"
        }
}

ctl.!default {
    type plug
        slave {
           pcm "hw:2,0"
       }
}
```

#### Play Wav Sample File

```sh
root@edison:~# aplay /usr/share/sounds/alsa/Front_Center.wav                                        Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mo
root@edison:~# aplay /usr/share/sounds/alsa/Rear_Center.wav 
Playing WAVE '/usr/share/sounds/alsa/Rear_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Moo
root@edison:~# 
```

#### Speaker-Test

```sh
    root@edison:~# speaker-test 
    speaker-test 1.0.28
    Playback device is default
    Stream parameters are 48000Hz, S16_LE, 1 channels
    Using 16 octaves of pink noise
    ...
    ...
    ^C
    root@edison:~# 
```

#### Mpg123

```sh
    root@edison:~# mpg123 
```

#### Espeak

```sh
    root@edison:~# espeak
```

#### Other Configuration

```sh
pcm.!default {
        type asym
        playback.pcm {
                type plug
                slave.pcm "hw:2,0"
        }
        capture.pcm {
                type plug
                slave.pcm "hw:2,0"
        } 
}
```

```sh
    root@edison:~# vi /etc/asound.conf
    pcm.!default sysdefault:Device
```

```
    root@edison:~# aplay -Ll
    root@edison:~# vi ~/.asoundrc
    root@edison:~# vi /etc/asound.conf
    pcm.!default sysdefault:Device
    root@edison:~# aplay /usr/share/sounds/alsa/Front_Center.wav
    root@edison:~# aplay -D hw:1,0 /usr/share/sounds/alsa/Front_Center.wav
```

