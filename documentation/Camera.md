Camera
==

## Kernel Integration

```sh
    root@edison:~# lsmod
    Module                  Size  Used by
    uvcvideo               71516  0 
    videobuf2_vmalloc      13003  1 uvcvideo
    videobuf2_memops       13001  1 videobuf2_vmalloc
    videobuf2_core         37707  1 uvcvideo
    root@edison:~# find /lib/modules/* -name 'uvc'
    /lib/modules/3.10.17-yocto-standard/kernel/drivers/media/usb/uvc
    /lib/modules/3.10.17-yocto-standard-r2/kernel/drivers/media/usb/uvc
    root@edison:~# ls -l /dev/video0
```

## Userspace Applications

```sh
    root@edison:~# ffmpeg
```

## Setup

```sh
    root@edison:~# find /lib/modules/* -name 'uvc'
```

### Opkg

```sh
    root@edison:~# opkg install kernel-module-uvcvideo
    root@edison:~# lsmod | grep uvc
```

### Apt-Get

## Device Configuration

```sh
    root@edison:~# lsmod | grep uvc
    root@edison:~# ls -al /dev/video0
```

## Usage Models

### IP Webcam

## Links

- https://www.ffmpeg.org/
