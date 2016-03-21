Audio
==
> An audio signal is a representation of sound, typically as an electrical voltage. Audio signals have frequencies in the audio frequency range of roughly 20 to 20,000 Hz (the limits of human hearing). [wikipedia](https://en.wikipedia.org/wiki/Audio_signal)

### Required Hardware

USB Audio Dongle

## Kernel Integration

### Advanced Linux Sound Architecture

> The Advanced Linux Sound Architecture (ALSA) provides audio and MIDI functionality to the Linux operating system.

- [Advanced Linux Sound Architecture Homepage](http://www.alsa-project.org/main/index.php/Main_Page)

### Kernel Display Message

```sh
    root@edison:~# dmesg | grep -i audio
    [ 9635.624279] usb 1-1.2: new full-speed USB device number 4 using dwc3-host
    [ 9635.646994] usb 1-1.2: New USB device found, idVendor=0d8c, idProduct=013c
    [ 9635.647025] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
    [ 9635.647046] usb 1-1.2: Product: USB PnP Sound Device
    [ 9635.647065] usb 1-1.2: Manufacturer: C-Media Electronics Inc.      
    [ 9636.203053] input: C-Media Electronics Inc.       USB PnP Sound Device as /devices/pci0000:00/0000:00:11.0/dwc3-host.2/
    usb1/1-1/1-1.2/1-1.2:1.3/input/input3
    [ 9636.203880] hid-generic 0003:0D8C:013C.0001: input,hidraw0: USB HID v1.00 Device [C-Media Electronics Inc.       USB Pn
    P Sound Device] on usb-dwc3-host.2-1.2/input3
    root@edison:~# lsusb
    Bus 001 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 001 Device 003: ID 0458:708a KYE Systems Corp. (Mouse Systems) 
    Bus 001 Device 004: ID 0d8c:013c C-Media Electronics, Inc. CM108 Audio Controller
```

### Kernel Modules

```sh
    root@edison:~# lsmod
    ...
```

```sh
    root@edison:~# lsusb 
    Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 001 Device 002: ID 0d8c:013c C-Media Electronics, Inc. CM108 Audio Controller
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    root@edison:~# 
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
                          C-Media Electronics Inc. USB PnP Sound Device at usb-dwc3-host.2-1, full speed
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
    root@edison:~# ls /usr/share/sounds/alsa/
    Front_Center.wav  Noise.wav         Rear_Right.wav
    Front_Left.wav    Rear_Center.wav   Side_Left.wav
    Front_Right.wav   Rear_Left.wav     Side_Right.wav
```

#### Apt-Get

```sh
    root@edison:~# apt-get install alsa-utils mpg123 espeak
```

### Programs

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
    pcm.!default {
        type plug
        slave {
            pcm “hw:1,0”
        }
    }
    ctl.!default {
    type plug
        slave {
            pcm “hw:2,0”
        }
    }

    root@edison:~# vi /etc/asound.conf
    pcm.!default sysdefault:Headset
```

### Speaker-Test

```sh
    root@edison:~# speaker-test 
    speaker-test 1.0.28
    Playback device is default
    Stream parameters are 48000Hz, S16_LE, 1 channels
    Using 16 octaves of pink noise
```

## Links

- http://repo.opkg.net/edison/repo/edison/kernel-module-snd-usb-audio_3.10.17+git0+6ad20f049a_c03195ed6e-r0_edison.ipk
- http://www.tektyte.com/docs/docpages/edison-reference/ALSA.html
- http://blog.niise.idv.tw/2015/01/intel-edison-mini-breakout-board-w-mpd.html?m=1
- http://hackaday.com/2015/12/02/audio-effects-on-the-intel-edison/


## Tbd

```sh
    sudo modprobe -v snd_usb_audio
    sudo modprobe --force-vermagic snd-usb-audio.ko
    sudo depmod -a
    sudo alsactl init
    sudo alsa-utils stop/start
    sudo dpkg-reconfigure alsa-base
    cat /dev/sndstat
    cat /proc/asound/cards
```sh