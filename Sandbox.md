Installation
==


- [A set of node-red nodes for connecting to johnny-five IO Plugins](https://github.com/monteslu/node-red-contrib-gpio)
- [Intel Galileo & Intel Edison IO Plugin for Johnny-Five](https://github.com/rwaldron/galileo-io/)

## i386

```sh
    # apt-get install npm nodejs nodejs-legacy
    # npm install -g node-red
    $ node-red
```

## Intel Edison

```sh

    root@edison:~# ifconfig # Get board.ip.adress
    ...
    wlan0     Link encap:Ethernet  HWaddr 78:4b:87:a5:3a:73  
              inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
    ...
    root@edison:~# npm install node-red-contrib-gpio
     -\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/--\|/-\|/-\|/-\|/-\|/-\|/-\|/|
     > meshblu@1.32.0 preinstall /home/root/node_modules/node-red-contrib-gpio/node_modules/meshblu
     ...
     ��├��─��─ serialport@2.0.6 (bindings@1.2.1, sf@0.1.7, async@0.9.0, nan@2.0.9, debug@2.2.0, optimist@0.6.1)
     ��└��─��─ meshblu@1.32.0 (backo@1.1.0, debug@2.2.0, json-stable-stringify@1.0.1, url@0.10.3, node-rsa@0.2.30, socket.io-c)
    root@edison:~# ls /usr/lib/node_modules/
    iotkit                    jsupm_grovevdiv           jsupm_mpl3115a2
    jsupm_grovespeaker        jsupm_mma7660
    root@edison:~# npm install galileo-io
    -\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|-\|/-\|/-\|/-\|/-
    > galileo-io@0.9.4 postinstall /home/root/node_modules/galileo-io
    > node scripts/postinstall
    ...
      Galileo-IO needs to install a trusted version of libmraa0.
    ...
    ��├��─��─ remapped@0.2.1 (getobject@0.1.0, traverse@0.6.6)
    ��└��─��─ es6-shim@0.35.0
    root@edison:~# npm install -g --unsafe-perm node-red
     \|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|//
     > bcrypt@0.8.5 install /usr/lib/node_modules/node-red/node_modules/bcrypt
     > node-gyp rebuild
     ...
     ��├��─��─ ws@0.8.1 (options@0.0.6, ultron@1.0.2, utf-8-validate@1.2.1, bufferutil@1.2.1)
     ��└��─��─ node-red-node-serialport@0.1.2 (serialport@2.0.6)
    root@edison:~# node-red &
root@edison:~# ./node_modules/node-red/bin/node-red-pi 
    
    Welcome to Node-RED
    ===================
    
    26 Mar 14:02:36 - [info] Node-RED version: v0.13.4
    26 Mar 14:02:36 - [info] Node.js  version: v0.10.38
    26 Mar 14:02:36 - [info] Linux 3.10.17-poky-edison+ ia32 LE
    26 Mar 14:02:36 - [info] Loading palette nodes
    ...
    26 Mar 14:02:47 - [info] Started flows
    26 Mar 14:02:47 - [info] Server now running at http://127.0.0.1:1880/
     
    Go to http://<board.ip.adress>:1880/#
     
```
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
