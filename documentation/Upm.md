# UPM

> Sensor/Actuator repository for libmraa

> High-level repository for sensors and actuators that use libmraa. In other words, UPM gives you easy function calls to use your sensors, such as reading temperature values or writing data to an LCD screen. With over a hundred sensors and more being added, this library speeds up your development time. 

- [UPM Documentation](http://iotdk.intel.com/docs/master/upm/index.html)
- [UPM Sensor Categories](http://iotdk.intel.com/docs/master/upm/modules.html)
- [UPM Github](https://github.com/intel-iot-devkit/upm)
- [UPM Python Examples](https://github.com/intel-iot-devkit/upm/tree/master/examples/python)

## UPM Updates

- Protocols such as ModBus and BACNet
- Radio/wireless modules
- XBee socket devices
- ZigBee, WiFi, WiFly
- LoRa—the SX1276 chip
- ZWave—USB Controllers
- ISM (Industrial, Scientific & Medical) Frequency Shift Keying (FSK) at 434 and 915 MHz

## Manual Installation, Latest Github

### Ubilinux

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

## Testing, Opkg

Check if RMAA and UPM Libraries are installed and upgrade them

```sh
root@edison:~# opkg list-installed | grep upm
upm - 0.7.0-r0
upm-dev - 0.7.0-r0
```

## Upgrade, Opkg

```sh
root@edison:~# opkg install upm                                                 
Package upm (0.7.0-r0) installed in root is up to date.                         
root@edison:~# 
```
