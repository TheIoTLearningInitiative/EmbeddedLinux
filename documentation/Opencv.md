Open Source Computer Vision
==

> OpenCV is released under a BSD license and hence it’s free for both academic and commercial use. It has C++, C, Python and Java interfaces and supports Windows, Linux, Mac OS, iOS and Android. OpenCV was designed for computational efficiency and with a strong focus on real-time applications. Written in optimized C/C++, the library can take advantage of multi-core processing. Enabled with OpenCL, it can take advantage of the hardware acceleration of the underlying heterogeneous compute platform. Adopted all around the world, OpenCV has more than 47 thousand people of user community and estimated number of downloads exceeding 9 million. Usage ranges from interactive art, to mines inspection, stitching maps on the web or through advanced robotics. Homepage

- [OpenCV Homepage](http://opencv.org/)
- [OpenCV 3.0.0-Beta ( IPP & TBB enabled ) on Yocto with Intel® Edison](https://software.intel.com/en-us/articles/opencv-300-beta-ipp-tbb-enabled-on-yocto-with-intel-edison)
- [OpenCV 3.0.0 ( IPP & TBB enabled ) on Yocto with Intel® Edison with new Yocto image release](https://software.intel.com/en-us/articles/opencv-300-ipp-tbb-enabled-on-yocto-with-intel-edison)
- [Maker Garage Facial Recognition with Intel® Edison Guide](https://www-ssl.intel.com/content/www/us/en/do-it-yourself/garage-content/garage-facial-recognition-instructions.html)
- [Learn OpenCV](http://www.learnopencv.com/)

## Required Applications

### Opkg Installation

```sh
    root@edison:~# opkg update
    root@edison:~# opkg install opencv opencv-samples opencv-apps
    root@edison:~# opkg install opencv-dev opencv-samples-dev
    root@edison:~# opkg install libopencv-imgproc-dev
    root@edison:~# opkg install python-numpy python-opencv
```

### Apt-Get Installation

```sh
    root@edison:~# apt-get update
    root@edison:~# apt-get install git python-pip python-serial python-pyparsing
    root@edison:~# apt-get install opencv opencv-samples opencv-apps
    root@edison:~# apt-get install opencv-dev opencv-samples-dev 
    root@edison:~# apt-get install libopencv-imgproc-dev
    root@edison:~# apt-get install python-numpy python-opencv
```

## Hello OpenCV, Face Recognition

```sh
    root@edison:~# mkdir opencv
    root@edison:~# cd opencv/
    root@edison:~/opencv# wget https://raw.githubusercontent.com/xe1gyq/core/master/configuration/haarcascade_frontalface_alt.xml
    root@edison:~/opencv# nano facerecognition.py
```

```sh
import cv2
import os
import sys

class xFaceRecognition(object):

    def __init__(self, imageinput="in.jpeg", imageoutput="out.jpeg"):
        self.directorycurrent = os.path.dirname(os.path.realpath(__file__))
        self.directoryoutput = self.directorycurrent
        self.imageinput = imageinput
        self.cascPath = "haarcascade_frontalface_alt.xml"
        self.imageoutput = imageoutput

    def detect(self):
        faceCascade = cv2.CascadeClassifier(self.cascPath)
        image = cv2.imread(self.imageinput)
        gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
        faces = faceCascade.detectMultiScale(
            gray,
            scaleFactor=1.1,
            minNeighbors=5,
            minSize=(30, 30),
            flags = cv2.cv.CV_HAAR_SCALE_IMAGE
        )

        print "Found {0} faces!".format(len(faces))

        for (x, y, w, h) in faces:
            cv2.rectangle(image, (x, y), (x+w, y+h), (0, 255, 0), 2)
        cv2.imwrite(self.imageoutput, image)
        cv2.waitKey(0)

if __name__ == "__main__":

    idFaceRecognition = xFaceRecognition(imageinput='in.jpeg', imageoutput='out.jpeg')
    idFaceRecognition.detect()
```

## Low Resolution Picture

```sh
    root@edison:~/opencv# wget https://raw.githubusercontent.com/xe1gyq/core/master/output/in.jpeg
    --2016-03-20 00:49:32--  https://raw.githubusercontent.com/xe1gyq/core/master/output/in.jpeg
    Resolving raw.githubusercontent.com... 23.235.40.133
    Connecting to raw.githubusercontent.com|23.235.40.133|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 13400 (13K) [image/jpeg]
    Saving to: 'in.jpeg'
    
    100%[======================================>] 13,400      --.-K/s   in 0s      
    
    2016-03-20 00:49:33 (27.5 MB/s) - 'in.jpeg' saved [13400/13400]
    root@edison:~/opencv# time python facerecognition.py                       
    Found 17 faces!
    
    real    0m2.249s
    user    0m2.010s
    sys     0m0.220s
    root@edison:~/opencv# cp out.jpeg /usr/lib/edison_config_tools/public/
    root@edison:~/opencv# 
```

Look at <>

## High Resolution Picture

```sh
    root@edison:~/opencv# wget https://upload.wikimedia.org/wikipedia/commons/5/5d/Barack_Obama_family_portrait_2011.jpg
    --2016-03-20 00:24:03--  https://upload.wikimedia.org/wikipedia/commons/5/5d/Barack_Obama_family_portrait_2011.jpg
    Resolving upload.wikimedia.org... 208.80.153.240, 2620:0:860:ed1a::2:b
    Connecting to upload.wikimedia.org|208.80.153.240|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 1972894 (1.9M) [image/jpeg]
    Saving to: 'Barack_Obama_family_portrait_2011.jpg'
    
    100%[======================================>] 1,972,894    264KB/s   in 16s
    
    2016-03-20 00:24:20 (122 KB/s) - 'Barack_Obama_family_portrait_2011.jpg' saved [1972894/1972894]
    
    root@edison:~/opencv# mv Barack_Obama_family_portrait_2011.jpg in.jpeg
    root@edison:~/opencv# time python facerecognition.py
    ...
```

