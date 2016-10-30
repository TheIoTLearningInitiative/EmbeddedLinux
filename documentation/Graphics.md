# Graphics

- [Edidoom Intel Edison Homepage](http://2ld.de/edidoom/)
- [Edidoom Intel Edison Display driver code and test program](https://github.com/llatta/edison-graphics)

```sh
v4l-utils-dbg_1.0.1-r0_core2-32.ipk
v4l-utils-dev_1.0.1-r0_core2-32.ipk
v4l-utils-doc_1.0.1-r0_core2-32.ipk
v4l-utils-staticdev_1.0.1-r0_core2-32.ipk
v4l-utils_1.0.1-r0_core2-32.ipk
v4l2grab-dbg_20141109-r0_core2-32.ipk
v4l2grab_20141109-r0_core2-32.ipk
```

```sh
root@edison:~# sudo opkg install imagemagick libv4l-dev
Package imagemagick (6.9.2-r0) installed in root is up to date.
Package libv4l-dev (1.0.1-r0) installed in root is up to date.
root@edison:~# sudo opkg install libjpeg-dev 
Package libjpeg-dev (8d-r1) installed in root is up to date.
```

```sh
root@edison:~# opkg install  v4l-utils
Installing v4l-utils (1.0.1-r0) on root.
Downloading http://iotdk.intel.com/repos/3.5/iotdk/edison/core2-32/v4l-utils_1.0.1-r0_core2-32.ipk.
Configuring v4l-utils.
root@edison:~# opkg install v4l-utils-dev
Installing v4l-utils-dev (1.0.1-r0) on root.
Downloading http://iotdk.intel.com/repos/3.5/iotdk/edison/core2-32/v4l-utils-dev_1.0.1-r0_core2-32.ipk.
Configuring v4l-utils-dev.
root@edison:~# 
```

```sh
root@edison:~s# sudo opkg install mjpg-streamer
Installing mjpg-streamer (r182-r0) on root.
Downloading http://repo.opkg.net/edison/repo/core2-32/mjpg-streamer_r182-r0_core2-32.ipk.
Configuring mjpg-streamer.
mjpg-streamer-dbg
```

```
root@edison:~# mjpg_streamer -i "input_uvc.so -d /dev/video0" -o "output_http.so"
```
