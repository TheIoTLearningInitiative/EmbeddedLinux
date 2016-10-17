# Input

> This is a collection of drivers that is designed to support all input devices under Linux. While it is currently used only on for USB input devices, future use (say 2.5/2.6) is expected to expand to replace most of the existing input system, which is why it lives in drivers/input/ instead of drivers/usb/. The centre of the input drivers is the input module, which must be loaded before any other of the input modules - it serves as a way of communication between two groups of modules [Linux Kernel Drivers Input Documentation](https://www.kernel.org/doc/Documentation/input/input.txt)

- [Bluetooth Controller Input](http://2ld.de/edidoom/)

```sh
root@edison:~#wget https://raw.githubusercontent.com/TheIoTLearningInitiative/EmbeddedLinux/master/tools/evtest.c
--2016-10-17 02:33:48--  https://raw.githubusercontent.com/TheIoTLearningInitiative/EmbeddedLinux/master/tools/evtest.c
Resolving raw.githubusercontent.com... 151.101.48.133
Connecting to raw.githubusercontent.com|151.101.48.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15169 (15K) [text/plain]
Saving to: 'evtest.c'

100%[======================================>] 15,169      --.-K/s   in 0.1s    

2016-10-17 02:33:50 (124 KB/s) - 'evtest.c' saved [15169/15169]

FINISHED --2016-10-17 02:33:50--
Total wall clock time: 17s
Downloaded: 1 files, 15K in 0.1s (124 KB/s)
```

```sh
root@edison:~# gcc -o evtest evtest.c 
```

# Lab

> Daemon listening to Edison PWR long button press, and starting OOBE service when it happens [Power Button Handler](http://git.yoctoproject.org/cgit/cgit.cgi/meta-intel-edison/tree/meta-intel-edison-bsp/recipes-support/pwr-button-handler)
