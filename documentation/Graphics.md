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

```sh
-----------------------------------------------------------------------
Example #1:
 To open an UVC webcam "/dev/video1" and stream it via HTTP:
  mjpg_streamer -i "input_uvc.so -d /dev/video1" -o "output_http.so"
-----------------------------------------------------------------------
Example #2:
 To open an UVC webcam and stream via HTTP port 8090:
  mjpg_streamer -i "input_uvc.so" -o "output_http.so -p 8090"
-----------------------------------------------------------------------
Example #3:
 To get help for a certain input plugin:
  mjpg_streamer -i "input_uvc.so --help"
-----------------------------------------------------------------------
In case the modules (=plugins) can not be found:
 * Set the default search path for the modules with:
   export LD_LIBRARY_PATH=/path/to/plugins,
 * or put the plugins into the "/lib/" or "/usr/lib" folder,
 * or instead of just providing the plugin file name, use a complete
   path and filename:
   mjpg_streamer -i "/path/to/modules/input_uvc.so"
-----------------------------------------------------------------------
```

```
root@edison:~# mjpg_streamer -i "input_uvc.so -d /dev/video0" -o "output_http.so" -f "15" -r "640x480" -w "./www"
mjpg_streamer -i "input_uvc.so -f "15" -r "640x480" -w "./www"
```
