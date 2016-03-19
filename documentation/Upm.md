UPM
==

> Sensor/Actuator repository for libmraa

> High-level repository for sensors and actuators that use libmraa. In other words, UPM gives you easy function calls to use your sensors, such as reading temperature values or writing data to an LCD screen. With over a hundred sensors and more being added, this library speeds up your development time. 

- [UPM Github](https://github.com/intel-iot-devkit/upm)

## Setup

### Ubilinux Compilation

#### Cmake

    root@ubilinux:~$ wget http://www.cmake.org/files/v3.2/cmake-3.2.2.tar.gz
    root@ubilinux:~$ tar xvf cmake-3.2.2.tar.gz
    root@ubilinux:~$ cd cmake-3.2.2
    root@ubilinux:~$ ./bootstrap
    root@ubilinux:~$ make
    root@ubilinux:~# make install

#### Upm

    root@ubilinux:~$ git clone https://github.com/intel-iot-devkit/upm.git
    root@ubilinux:~$ cd upm
    root@ubilinux:~$ mkdir build
    root@ubilinux:~$ cd build
    root@ubilinux:~$ cmake ..
    root@ubilinux:~$ make
    root@ubilinux:~# make install
    root@ubilinux:~$ nano ~/.bashrc
    export PYTHONPATH=$PYTHONPATH:/usr/local/lib/python2.7/site-packages/

Testing

Tbd
Hands-On

Tbd
Links

UPM Documentation
UPM Sensor Categories
UPM Github
UPM Python Exampes