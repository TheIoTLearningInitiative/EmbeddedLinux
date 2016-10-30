# Camera

> USB Video Device Class Webcam UVC-compatible. The USB video device class (also USB video class or UVC) is a USB device class that describes devices capable of streaming video like webcams, digital camcorders, transcoders, analog video converters and still-image cameras. [Wikipedia](https://en.wikipedia.org/wiki/List_of_USB_video_class_devices)

### Required Hardware

USB Camera HD Webcam C525

## Kernel Integration

### Kernel Display Message

```sh
    root@edison:~# dmesg
    ...
    [ 1857.820461] usb 1-1: new high-speed USB device number 3 using dwc3-host
    [ 1858.108224] usb 1-1: New USB device found, idVendor=046d, idProduct=0826
    [ 1858.108256] usb 1-1: New USB device strings: Mfr=0, Product=2, SerialNumber=1
    [ 1858.108277] usb 1-1: Product: HD Webcam C525
    [ 1858.108296] usb 1-1: SerialNumber: 99DB4F90
    [ 1858.458453] set resolution quirk: cval->res = 384
    [ 1858.568064] uvcvideo: Found UVC 1.00 device HD Webcam C525 (046d:0826)
    [ 1858.582220] input: HD Webcam C525 as /devices/pci0000:00/0000:00:11.0/dwc3-host.2/usb1/1-1/1-1:1.2/input/input3
    [ 1858.582896] usbcore: registered new interface driver uvcvideo
    [ 1858.582915] USB Video Class driver (1.1.1)
```

```sh
root@edison:~# dmesg
...
[31587.442854] usb 1-1: new high-speed USB device number 4 using dwc3-host
[31587.498763] usb 1-1: New USB device found, idVendor=0458, idProduct=708a
[31587.498795] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[31587.498816] usb 1-1: Product: FaceCam 320X
[31587.498835] usb 1-1: Manufacturer: KYE Systems Corp.
[31587.510744] uvcvideo: Found UVC 1.00 device FaceCam 320X (0458:708a)
[31587.518655] input: FaceCam 320X as /devices/pci0000:00/0000:00:11.0/dwc3-host.2/usb1/1-1/1-1:1.0/input/input6
root@edison:~# 
```

```sh
Driver Info (not using libv4l2):
        Driver name   : uvcvideo
        Card type     : FaceCam 320X
        Bus info      : usb-dwc3-host.2-1
        Driver version: 3.10.98
        Capabilities  : 0x84000001
                Video Capture
                Streaming
                Device Capabilities
        Device Caps   : 0x04000001
                Video Capture
                Streaming
Priority: 2
Video input : 0 (Camera 1: ok)
Format Video Capture:
        Width/Height  : 640/480
        Pixel Format  : 'YUYV'
        Field         : None
        Bytes per Line: 1280
        Size Image    : 614400
        Colorspace    : SRGB
Crop Capability Video Capture:
        Bounds      : Left 0, Top 0, Width 640, Height 480
        Default     : Left 0, Top 0, Width 640, Height 480
        Pixel Aspect: 1/1
Streaming Parameters Video Capture:
        Capabilities     : timeperframe
        Frames per second: 5.000 (5/1)
        Read buffers     : 0
                     brightness (int)    : min=-255 max=255 step=1 default=0 va
lue=0
                       contrast (int)    : min=0 max=30 step=1 default=15 value
=15
                     saturation (int)    : min=0 max=127 step=1 default=32 valu
e=32
                            hue (int)    : min=-16000 max=16000 step=1 default=
0 value=0
 white_balance_temperature_auto (bool)   : default=1 value=1
                          gamma (int)    : min=20 max=250 step=1 default=100 va
lue=100
           power_line_frequency (menu)   : min=0 max=2 default=1 value=1
      white_balance_temperature (int)    : min=2800 max=6500 step=1 default=500
0 value=5000 flags=inactive
        
```

### Kernel Modules

```sh
    root@edison:~# lsmod
    Module                  Size  Used by
    uvcvideo               71516  0 
    videobuf2_vmalloc      13003  1 uvcvideo
    videobuf2_memops       13001  1 videobuf2_vmalloc
    videobuf2_core         37707  1 uvcvideo
    ...
    root@edison:~# find /lib/modules/* -name 'uvc'
    /lib/modules/3.10.17-poky-edison+/kernel/drivers/media/usb/uvc
```

## Userspace Interfaces

### DevFs

```sh
    root@edison:~# ls -l /dev/video0
    crw-rw----    1 root     video      81,   0 Mar 21 18:21 /dev/video0
```
## Applications / Libraries

> fswebcam
> > a  small  and  simple webcam app for *nix. It can capture images  from  a  number  of  different  sources  and   perform   simple manipulation  on  the  captured image. The image can be saved as one or more PNG or JPEG files.
       
> ffmpeg
> > A complete, cross-platform solution to record, convert and stream audio and video. [FFMpeg Homepage](https://www.ffmpeg.org/)

### Setup

#### Manual

Install ffmpeg by following [Video Streaming on Intel Edison](https://github.com/drejkim/edi-cam)

#### Opkg

```sh
    root@edison:~# opkg install kernel-module-uvcvideo
    Package kernel-module-uvcvideo (3.10.17-r0) installed in root is up to date.
    root@edison:~# opkg install libx264-133 libx264-bin libx264-dev libx264-staticdev
    Installing libx264-133 (r2265+git0+ffc3ad4945-r0) on root.
    Installing libx264-bin (r2265+git0+ffc3ad4945-r0) on root.
    Installing libx264-dev (r2265+git0+ffc3ad4945-r0) on root.
    Installing libx264-staticdev (r2265+git0+ffc3ad4945-r0) on root.
    root@edison:~# opkg install opencv python-opencv
    Package opencv (2.4.11+git0+2c9547e314-r0) installed in root is up to date.
    Package python-opencv (2.4.11+git0+2c9547e314-r0) installed in root is up to date.
    root@edison:~# opkg install fswebcam
    Installing fswebcam (20140113-r0) on root.
    Installing libgd3 (2.1.0-r0) on root.
    Installing libvpx (1.3.0-r0) on root.
    
```

#### Pip

```sh
    root@edison:~# pip install flask
```

### Programs

#### Fswebcam

```sh
    root@edison:~# fswebcam -r 1280x1024 -s brightness=65% -s Contrast=50% -s Gamma=100% --jpeg 100 --no-banner image.jpg
```

#### Python OpenCv Live Stream

From [Github Smoyerman Live Stream Processed](https://raw.githubusercontent.com/smoyerman/EdisonWebVideoProcessed/master/LiveStreamProcessed.py)

```sh
    root@edison:~# vi livestream.py
```

```Python
from flask import Flask, Response
import cv2
import numpy as np

class Camera(object):
    def __init__(self):
        self.cap = cv2.VideoCapture(0)
        # Reset camera capture size for faster processing
	    self.cap.set(3,480)
	    self.cap.set(4,360)

    def get_frame(self):
	    ret, frame = self.cap.read()
        # Apply laplacian edge detection to image
	    laplacian = cv2.Laplacian(frame,cv2.CV_64F)
        # Write out original and edge detected images at once
	    cv2.imwrite('blah.jpg',np.hstack((frame,laplacian)))
	    return open('blah.jpg', 'rb').read()

app = Flask(__name__)

def gen(camera):
    while True:
        frame = camera.get_frame()
        yield (b'--frame\r\n'
               b'Content-Type: image/jpeg\r\n\r\n' + frame + b'\r\n')

@app.route('/')
def video_feed():
    return Response(gen(Camera()),
                    mimetype='multipart/x-mixed-replace; boundary=frame')

if __name__ == '__main__':
    app.run(host='0.0.0.0', debug=True)
```

```sh
    root@edison:~# python livestream.py
     * Running on http://0.0.0.0:5000/ (Press CTRL+C to quit)
     * Restarting with stat
     * Debugger is active!
     * Debugger pin code: 775-529-825
```

See Live Stream by connecting from a web browser to http://youripaddress:5000/


```sh
    192.168.1.70 - - [21/Mar/2016 18:48:16] "GET / HTTP/1.1" 200 -
    192.168.1.70 - - [21/Mar/2016 18:48:17] "GET / HTTP/1.1" 200 -
```
#### Online Examples

- [Github Smoyerman Video Capture](https://github.com/smoyerman/EdisonOpenCVVideo/blob/master/VideoCapture.py)
- [Rustem Iskuzhin Making your own live streaming camera](http://rustemiskuzhin.com/?p=1)

### OpenCV

#### USB Camera

#### IP Camera

