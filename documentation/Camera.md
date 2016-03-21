Camera
==

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

### FFMpeg

> A complete, cross-platform solution to record, convert and stream audio and video. [FFMpeg Homepage](https://www.ffmpeg.org/)

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
```

#### Pip

```sh
    root@edison:~# pip install flask
    root@edison:~# pip install opencv python-opencv
```

### Programs

#### OpenCv Live Stream

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

#### Online Examples

- [Github Smoyerman Video Capture](https://github.com/smoyerman/EdisonOpenCVVideo/blob/master/VideoCapture.py)
- [Github Smoyerman Live Stream Processed](https://raw.githubusercontent.com/smoyerman/EdisonWebVideoProcessed/master/LiveStreamProcessed.py)
- [Rustem Iskuzhin Making your own live streaming camera](http://rustemiskuzhin.com/?p=1)
