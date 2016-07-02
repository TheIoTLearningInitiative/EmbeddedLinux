# MRAA

> Low Level Skeleton Library for IO Communication on GNU/Linux platforms

> C/C++ library with bindings to JavaScript and Python to interface with the I/O on the Intel® Galileo board, Intel® Edison board, and other platforms. With board detection done at runtime, you can create portable code that works across multiple platforms.

* AIO Sensors requiring an ADC value to be read
* I2C Modules using the i2c bus
* SPI Modules using the SPI bus
* GPIO Modules using GPIOs directly
* PWM Modules using a PWM capable GPIO pin
* UART Modules using a serial connection (RX/TX)

- [MRAA Github](https://github.com/intel-iot-devkit/mraa)

## Manual Installation, Latest Github

### Yocto

```sh
    root@edison:~# git clone https://github.com/intel-iot-devkit/mraa.git
    root@edison:~# mkdir mraa/build && cd $_
    root@edison:~# cmake ..
    root@edison:~# make
    root@edison:~# make install
    root@edison:~# nano /etc/ld.so.conf
    /usr/local/lib/i386-linux-gnu/
    root@edison:~# ldconfig
    root@edison:~# ldconfig -p | grep mraa
    root@edison:~# export PYTHONPATH=$PYTHONPATH:$(dirname $(find /usr/local -name mraa.py))
    root@edison:~# nano ~/.bashrc
    export PYTHONPATH=$PYTHONPATH:$(dirname $(find /usr/local -name mraa.py))
```

### Ubilinux

```sh
    root@ubilinux:~# apt-get update
    root@ubilinux:~# apt-cache search pcre
    root@ubilinux:~# apt-get install libpcre3-dev
    root@ubilinux:~# apt-get install git
    root@ubilinux:~# apt-get install cmake
    root@ubilinux:~# apt-get install python-dev
    root@ubilinux:~# apt-get install swig
    root@ubilinux:~# git clone https://github.com/intel-iot-devkit/mraa.git
    root@ubilinux:~# mkdir mraa/build && cd $_
    root@ubilinux:~# cmake .. -DBUILDSWIGNODE=OFF
    root@ubilinux:~# make
    root@ubilinux:~# make install
    root@ubilinux:~# cd
    root@ubilinux:~# nano /etc/ld.so.conf
    /usr/local/lib/i386-linux-gnu/
    root@ubilinux:~# ldconfig
    root@ubilinux:~# ldconfig -p | grep mraa
    root@ubilinux:~# export PYTHONPATH=$PYTHONPATH:$(dirname $(find /usr/local -name mraa.py))
    root@ubilinux:~# nano ~/.bashrc
    export PYTHONPATH=$PYTHONPATH:$(dirname $(find /usr/local -name mraa.py))
```

Based on [Installing libmraa on Ubilinux for Edison](https://learn.sparkfun.com/tutorials/installing-libmraa-on-ubilinux-for-edison)
 
## Upgrade, Opkg

```sh
root@edison:~# opkg list-installed | grep mraa
libmraa-dev - 0.7.2-r0
libmraa-doc - 0.7.2-r0
libmraa0 - 0.7.2-r0
root@edison:~# opkg install mraa
Upgrading mraa from 0.9.5-r0 to 1.0.0 on root.
Downloading http://iotdk.intel.com/repos/3.0/intelgalactic/opkg/i586//mraa_1.0.0_i586.ipk.
Removing package mraa-dev from root...
Removing package mraa-doc from root...
Removing obsolete file /usr/lib/libmraa.so.0.9.5.
Removing obsolete file /usr/bin/mraa-gpio.
Removing obsolete file /usr/lib/libmraa.so.0.
Configuring mraa.
root@edison:~#
```

## Hello Mraa

```sh
    root@edison:~# git clone https://github.com/intel-iot-devkit/mraa.git
    root@edison:~# cd mraa/examples
    root@edison:~# gcc -lmraa hellomraa.c -o hellomraa
    root@edison:~# ./hellomraa
     hello mraa
      Version: v0.7.3
      Running on Intel Edison
```
