# Bar Codes

- [](https://software.intel.com/en-us/blogs/2015/11/30/barcodescanner-with-webcam-on-intel-edison)
- [](http://blog.ayoungprogrammer.com/2014/04/real-time-qr-code-bar-code-detection.html/)

```sh
root@edison:~# opkg install libv4l-dev
Installing libv4l-dev (1.0.1-r0) on root.
Downloading http://iotdk.intel.com/repos/3.5/iotdk/edison/core2-32/libv4l-dev_1.0.1-r0_core2-32.ipk.
Installing libv4l (1.0.1-r0) on root.
Downloading http://iotdk.intel.com/repos/3.5/iotdk/edison/core2-32/libv4l_1.0.1-r0_core2-32.ipk.
Configuring libv4l.
Configuring libv4l-dev.
root@edison:~# cd /usr/include/linux
root@edison:/usr/include/linux# ln -s /home/root/usr/src/linux-headers-3.10.98-poky-edison/include/linux/videodev2.h videodev.h
root@edison:/usr/include/linux# cd -
/home/root/zbar-0.10
```

```sh
root@edison:~# opkg install http://repo.opkg.net/edison/repo/core2-32/imagemagick_6.9.2-r0_core2-32.ipk
root@edison:~# opkg install http://repo.opkg.net/edison/repo/core2-32/imagemagick-dev_6.9.2-r0_core2-32.ipk
root@edison:~# opkg install 
```

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
root@edison:~# tar xvf zbar-0.10.tar.bz2
root@edison:~# cd zbar-0.10
root@edison:~/zbar-0.10# ls
COPYING      Makefile.in     config        include  test            zbar.pc.in
ChangeLog    NEWS            configure     perl     zbar            zbarcam
HACKING      README          configure.ac  plugin   zbar-gtk.pc.in  zbarimg
INSTALL      README.windows  doc           pygtk    zbar-qt.pc.in
LICENSE      TODO            examples      python   zbar.ico
Makefile.am  aclocal.m4      gtk           qt       zbar.nsi
root@edison:~/zbar-0.10# ./configure --without-qt --without-gtk --without-xv --without-xshm --with-imagemagick --with-x=no --prefix="/usr"
```

```
please verify that the detected configuration matches your expectations:
------------------------------------------------------------------------
X                 --with-x=disabled
pthreads          --enable-pthread=yes
v4l               --enable-video=no
        => zbarcam video scanner will *NOT* be built
jpeg              --with-jpeg=yes
Magick++          --with-imagemagick=yes
Python            --with-python=yes
GTK+              --with-gtk=no
        => the GTK+ widget will *NOT* be built
Qt4               --with-qt=no
        => the Qt4 widget will *NOT* be built
```

```sh
root@edison:~/zbar-0.10# make
make  all-am
make[1]: Entering directory '/home/root/zbar-0.10'tp://repo.opkg.net/edison/repo/core2-32/i
/bin/sh ./libtool --tag=CC   --mode=link gcc -Wall -Wno-parentheses -g -O2   -o zbarimg/zbarimg zbarimg/zbarimg_zbarimg-zbarimg.o  -lMagickWand-6.Q16 -lMagickCore-6.Q16  zbar/libzbar.la  -ljpeg -lpthread 
libtool: link: cannot find the library `=/usr/lib/libMagickCore-6.Q16.la' or unhandled argument `=/usr/lib/libMagickCore-6.Q16.la'
Makefile:1270: recipe for target 'zbarimg/zbarimg' failed
make[1]: *** [zbarimg/zbarimg] Error 1
make[1]: Leaving directory '/home/root/zbar-0.10'
Makefile:820: recipe for target 'all' failed
make: *** [all] Error 2
root@edison:~/zbar-0.10# cd
root@edison:~# 
```

```sh
root@edison:~# wget opkg install http://repo.opkg.net/edison/repo/core2-32/zbar_0.10-r0_core2-32.ipk
Downloading http://repo.opkg.net/edison/repo/core2-32/zbar_0.10-r0_core2-32.ipk.
Installing zbar (0.10-r0) on root.
Configuring zbar.
root@edison:~/zbar-0.10# zbarcam
ERROR: zbar processor in _zbar_video_open():
    system error: opening video device '/dev/video0': No such file or directory (2)
root@edison:~/zbar-0.10# zbarcam^C
root@edison:~/zbar-0.10# 
```