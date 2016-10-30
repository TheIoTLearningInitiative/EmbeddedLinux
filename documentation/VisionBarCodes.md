# Bar Codes

```sh
root@edison:~# opkg install imagemagick imagemagick-dev
Installing imagemagick (6.8.9-r0) on root.
Downloading http://iotdk.intel.com/repos/3.5/iotdk/edison/core2-32/imagemagick_6.8.9-r0_core2-32.ipk.
...
Configuring libtiff5.
Configuring lcms.
Configuring libfftw.
Configuring libfontconfig1.
Configuring imagemagick.
Configuring gdk-pixbuf-dev.
Configuring libharfbuzz0.
Configuring libcroco.
Configuring libxft2.
Configuring libtiff-dev.
Configuring libpixman-1-0.
Configuring libcairo2.
Configuring pango.
Configuring pango-module-basic-fc.
Configuring lcms-dev.
Configuring libfontconfig-dev.
Configuring librsvg-2-2.
Configuring libcairo-gobject2.
Configuring libcairo-script-interpreter2.
Configuring libcairo-perf-utils.
Configuring libpixman-1-dev.
Configuring libcairo-dev.
Configuring libcroco-dev.
Configuring libharfbuzz-dev.
Configuring libxft-dev.
Configuring pango-dev.
Configuring librsvg-2-dev.
Configuring imagemagick-dev.
root@edison:~# 
```

```sh
root@edison:~# wget http://sourceforge.net/projects/zbar/files/zbar/0.10/zbar-0.10.tar.bz2
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ufpr.dl.sourceforge.net/project/zbar/zbar/0.10/zbar-0.10.tar.bz2 [following]
--2016-10-30 15:57:31--  http://ufpr.dl.sourceforge.net/project/zbar/zbar/0.10/zbar-0.10.tar.bz2
Resolving ufpr.dl.sourceforge.net... 200.236.31.2, 2801:82:80ff:8000::3
Connecting to ufpr.dl.sourceforge.net|200.236.31.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 592602 (579K) [application/x-bzip2]
Saving to: 'zbar-0.10.tar.bz2'

100%[======================================>] 592,602      273KB/s   in 2.1s   

2016-10-30 15:57:34 (273 KB/s) - 'zbar-0.10.tar.bz2' saved [592602/592602]

root@edison:~# 
```