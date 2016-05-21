SandBox
==

## ToDo

ToDo Important Topics To Cover

- Example Project
- Adding Recipes to the Build System
- Adding New Recipes to the Build System
- Build an Example Package based on a Git Repository Commit
- Build an example package based on a Remote Source Archive
- Build an example package based on a Local Source Archive


ToDo Explain Linux Kernel Version, do we have this under Operating System?, Explain how we give support ot Linux Kernel

## Kernel Interfaces

### SFI Simple Firmware Interface

> How does SFI relate to ACPI? While some modern platforms can used SFI instead of using ACPI, SFI is not intended to replace ACPI on general purpose systems. If a platform were to export both SFI and ACPI booted an OS that also supports both, the OS should use the platform's ACPI support and ignore SFI.

```sh
    User Linux Next
    git clone git://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git
    v4.1-rc6 tag, mrproper'd and rebuilt, 
```

## Links

- http://www.h-online.com/open/news/item/Intel-develops-simpler-alternative-to-ACPI-for-Linux-742161.html    
- https://en.wikipedia.org/wiki/Simple_Firmware_Interface
- https://simplefirmware.org/
- https://www.kernel.org/doc/ols/2009/ols2009-pages-55-60.pdf
- https://lwn.net/Articles/406228/
- https://simplefirmware.org/faq
- http://geektimes.ru/post/255136/
- https://communities.intel.com/message/273743
- https://edison.internet-share.com/w/index.php?title=Using_a_stock_Linux_kernel_with_Intel_Edison&redirect=no

## Blkuetooth
## Links

- [Intel® Edison Boards Bluetooth® User Guide](http://www.intel.com/support/edison/sb/CS-035381.htm)
- http://alextgalileo.altervista.org/blog/install-kernel-from-repo-onto-edison-official-image/
- https://software.intel.com/en-us/articles/intel-edison-board-getting-started-with-bluetooth
- http://rexstjohn.com/lets-turn-intel-edison-into-an-ibeacon/
- http://unix.stackexchange.com/questions/53546/debian-squeeze-connect-to-a2dp-bluetooth-through-command-line
- https://software.intel.com/en-us/articles/using-the-generic-attribute-profile-gatt-in-bluetooth-low-energy-with-your-intel-edison
- https://software.intel.com/en-us/articles/connecting-the-intel-edison-board-to-your-android-phone-with-serial-port-profile-spp
- [Profiles](https://downloadmirror.intel.com/24909/eng/edison-bsp_rn_332032-007.pdf)
- https://learn.sparkfun.com/tutorials/bluetooth-basics
- [PyBluez API Ddoc](http://pybluez.googlecode.com/svn/www/docs-0.7/index.html)
- [PIP package manager](https://pip.pypa.io/en/stable/)
- http://shawnhymel.com/665/using-python-and-ble-to-receive-data-from-the-rfduino/
- http://shawnhymel.com/703/bluetooth-low-energy-peripherals-with-javascript/
- http://stephaniemoyerman.com/?p=100
- https://github.com/w4ilun/edison-guides/wiki/Configure-Intel-Edison-for-BLE---Bluetooth-Smart-Development
- https://software.intel.com/en-us/articles/connecting-to-intel-edison-from-android-with-bluetooth-le-ble
- http://stephaniemoyerman.com/?p=100
- https://software.intel.com/en-us/articles/connecting-the-intel-edison-board-to-your-android-phone-with-serial-port-profile-spp
- https://github.com/smoyerman/edison-ibeacon

## SandBox

- Intel® Edison to a Bluetooth Network
- Intel® Edison from a peer device 
- [Raspberry Pi & Bluetooth LE part 1 with Tony D! @adafruit #LIVE](https://youtu.be/5fQR2PHMDWE)
- [Bluetooth on the Intel Edison](https://scivision.co/bluetooth-on-the-intel-edison/)

```sh
    root@edison:~# rfcomm bind - 40:78:6A:26:4A:C2 1
    root@edison:~# ls /dev/rfcomm0
```

### PCI


## Links

- https://communities.intel.com/thread/61150?wapkw=intel+edison+mpcie
- https://communities.intel.com/thread/89971?start=0&tstart=0
- https://www.aisler.net/projects/7252
- http://pinball-mods.com/blogs/?p=580
- https://hackaday.io/project/4571-intel-edison-usb-storage-sled
- https://wiki.archlinux.org/index.php/Huawei_E220
- https://techship.se/products/mpcie-usb-adapt-9-pin/
- https://techship.se/products/pci-express-mini-card-to-usb-adapter/
- https://techship.se/products/pci-express-mini-card-to-usb-adapter-with-external-voltage/
- http://www.amazon.com/Mini-PCIe-mSATA-Micro-Adapter/dp/B00KZIANT0
- http://www.newegg.com/Product/Product.aspx?Item=N82E16815158354

## Modems
    
- https://boundarydevices.com/cellular-modems-on-i-mx6-boards/
- https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/211095
- http://www.monblocnotes.com/node/1943
- http://www.paoli.cz/en/lte-modules-1/huawei-me909u-521-mini-pcie.html?cur=1&lang=1&&redirected=1
- http://www.paoli.cz/out/media/Guide_to_Kernel_Driver_Integration_in_Linux_for_Huawei_Modules(1).pdf

## Compilation

## Others

```sh
    root@edison:~# journalctl 
    root@edison:~# cat /etc/modprobe.d/bcm4334x.conf 
    options bcm4334x firmware_path=/etc/firmware/fw_bcmdhd.bin nvram_path=/etc/firmware/bcmdhd.cal op_mode=4
    root@edison:~# cat /etc/modprobe.d/g_multi.conf  
    options g_multi file=/dev/mmcblk0p9 stall=0 idVendor=0x8087 idProduct=0x0A9E iProduct=Edison iManufacturer=Intel
```

## Links

- [Intel® Edison Native Application Guide](http://www.intel.com/support/edison/sb/CS-035382.htm)
- http://dev.ardupilot.com/wiki/edison-for-drones/
- https://github.com/catmaker/chippy
- https://github.com/MakersTeam/Edison
- https://github.com/tokoro10g/galileo-makefile
- https://software.intel.com/en-us/articles/opencv-300-ipp-tbb-enabled-on-yocto-with-intel-edison
- http://flask.pocoo.org/

## Audio

## Links

- http://repo.opkg.net/edison/repo/edison/kernel-module-snd-usb-audio_3.10.17+git0+6ad20f049a_c03195ed6e-r0_edison.ipk
- http://www.tektyte.com/docs/docpages/edison-reference/ALSA.html
- http://blog.niise.idv.tw/2015/01/intel-edison-mini-breakout-board-w-mpd.html?m=1
- http://hackaday.com/2015/12/02/audio-effects-on-the-intel-edison/


## Tbd

```sh
    sudo modprobe -v snd_usb_audio
    sudo modprobe --force-vermagic snd-usb-audio.ko
    sudo depmod -a
    sudo alsactl init
    sudo alsa-utils stop/start
    sudo dpkg-reconfigure alsa-base
    cat /dev/sndstat
    cat /proc/asound/cards
```sh

## Links


## Under investigation?
    
    - What is it create-debian-image.sh
    user@host:~$ edison-src/meta-intel-edison/utils

- https://software.intel.com/en-us/articles/opencv-300-beta-ipp-tbb-enabled-on-yocto-with-intel-edison
- http://download.intel.com/support/edison/sb/edisonbsp_ug_331188007.pdf
- https://hayestech.files.wordpress.com/2015/01/intel-edison-bsd.pdf
- http://www.instructables.com/id/Securing-IoT-applications-built-on-Intel-Galileo-a/
- http://www.embarcados.com.br/intel-edison-yocto-como-construir-sua-propria-distribuicao-linux-embarcado/
- http://www.embarcados.com.br/raspberry-pi-qt5-yocto-parte-1/
- https://communities.intel.com/docs/DOC-23391
- https://software.intel.com/en-us/articles/intel-edison-developer-resources
- http://download.intel.com/support/edison/sb/edisonbsp_ug_331188007.pdf
- http://drejkim.com/blog/2014/11/22/building-an-edison-image-and-changing-the-root-partition-size/
- https://hayestech.wordpress.com/2015/01/26/building-custom-intel-edison-images/
http://www.yoctoproject.org/docs/1.1/yocto-project-qs/yocto-project-qs.html
http://edplay.weebly.com/how-to/building-linux-for-intel-edison
- https://wiki.debian.org/EmDebian/CrossDebootstrap
- https://communities.intel.com/message/273743
- http://layers.openembedded.org/layerindex/branch/master/layer/meta-intel-edison-bsp/
- http://shawnhymel.com/724/creating-a-custom-linux-kernel-for-the-edison-yocto-2-1/
- http://events.linuxfoundation.org/sites/events/files/slides/LinuxCon2015_meta-debian_r7.pdf


    user@host:~$ tar xvf edison-src-weekly-68.tgz
    user@host:~$ ls edison-src
    arduino  broadcom_cws  device-software  mw

- user@host:~$ ./device-software/setup.sh
- File name: edison-src-weekly-68.tgz @ https://downloadcenter.intel.com/download/24357


- https://scratchbuffer.wordpress.com/2015/09/01/yocto-linux-image-build-for-intel-edison-simple-and-easy/
- https://wiki.lsr.ei.tum.de/nst/documentation/inteledison
- https://hayestech.wordpress.com/2015/01/26/building-custom-intel-edison-images/

### Tbd

    user@host:~$ cd edison-src/meta-intel-edison/
    user@host:~$ git clone https://github.com/openembedded/meta-openembedded.git
    user@host:~$ cd meta-openembedded/
    user@host:~$ git checkout fido
    user@host:~$ cd ../../
    user@host:~$ nano out/current/build/conf/bblayers.conf
    /home/xe1gyq/Projects/edison-src/meta-intel-edison/meta-openembedded \
    user@host:~$ nano meta-intel-edison/meta-intel-edison-distro/recipes-core/images/edison-image.bb
    IMAGE_INSTALL += “opencv”
    PACKAGECONFIG_pn-opencv="eigen jpeg libav png tiff v4l”
    user@host:~$ cd out/current
    user@host:~$ source poky/oe-init-build-env
    user@host:~$ bitbake edison-image
