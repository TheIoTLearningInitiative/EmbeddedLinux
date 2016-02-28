Open Source Computer Vision
==

> OpenCV is released under a BSD license and hence it’s free for both academic and commercial use. It has C++, C, Python and Java interfaces and supports Windows, Linux, Mac OS, iOS and Android. OpenCV was designed for computational efficiency and with a strong focus on real-time applications. Written in optimized C/C++, the library can take advantage of multi-core processing. Enabled with OpenCL, it can take advantage of the hardware acceleration of the underlying heterogeneous compute platform. Adopted all around the world, OpenCV has more than 47 thousand people of user community and estimated number of downloads exceeding 9 million. Usage ranges from interactive art, to mines inspection, stitching maps on the web or through advanced robotics. Homepage

- [OpenCV Homepage](http://opencv.org/)

## Required Applications

### Opkg Installation

```sh
    root@Edison:~# opkg update
    root@Edison:~# opkg install opencv opencv-samples opencv-apps
    root@Edison:~# opkg install opencv-dev opencv-samples-dev
    root@Edison:~# opkg install libopencv-imgproc-dev
    root@Edison:~# opkg install python-numpy python-opencv
```

### Apt-Get Installation

```sh
    root@Edison:~# apt-get update
    root@Edison:~# apt-get install git python-pip python-serial python-pyparsing
    root@Edison:~# apt-get install opencv opencv-samples opencv-apps
    root@Edison:~# apt-get install opencv-dev opencv-samples-dev 
    root@Edison:~# apt-get install libopencv-imgproc-dev
    root@Edison:~# apt-get install python-numpy python-opencv
```

## Testing

    Tbd

## Hands-On

    Tbd

## Links

- [OpenCV 3.0.0-Beta ( IPP & TBB enabled ) on Yocto with Intel® Edison](https://software.intel.com/en-us/articles/opencv-300-beta-ipp-tbb-enabled-on-yocto-with-intel-edison)
- [OpenCV 3.0.0 ( IPP & TBB enabled ) on Yocto with Intel® Edison with new Yocto image release](https://software.intel.com/en-us/articles/opencv-300-ipp-tbb-enabled-on-yocto-with-intel-edison)