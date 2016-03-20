UPM
==

> Sensor/Actuator repository for libmraa

> High-level repository for sensors and actuators that use libmraa. In other words, UPM gives you easy function calls to use your sensors, such as reading temperature values or writing data to an LCD screen. With over a hundred sensors and more being added, this library speeds up your development time. 

- [UPM Documentation](http://iotdk.intel.com/docs/master/upm/index.html)
- [UPM Sensor Categories](http://iotdk.intel.com/docs/master/upm/modules.html)
- [UPM Github](https://github.com/intel-iot-devkit/upm)
- [UPM Python Exampes](https://github.com/intel-iot-devkit/upm/tree/master/examples/python)

UPD Updates

- Protocols such as ModBus and BACNet
- Radio/wireless modules
- XBee socket devices
- ZigBee, WiFi, WiFly
- LoRa—the SX1276 chip
- ZWave—USB Controllers
- ISM (Industrial, Scientific & Medical) Frequency Shift Keying (FSK) at 434 and 915 MHz

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

```sh
    root@edison:~# opkg install upm
    Upgrading upm from 0.3.1-r0 to 0.3.2 on root.
    Downloading http://iotdk.intel.com/repos/1.5/intelgalactic/upm_0.3.2_i586.ipk.
    Removing package upm-dev from root...
    Removing obsolete file /usr/lib/libupm-wt5001.so.0.3.1.
    ...
    Configuring upm.
    root@edison:~# 
```
