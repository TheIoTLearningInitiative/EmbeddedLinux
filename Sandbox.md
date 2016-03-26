### Input Inject + Output Debug

#### @ Node-Red Flow Space

> Input Inject
> > Payload Timestamp
> > Repeat Interval 1 Second

> Output Debug
> > Output Message Property
> > msg.payload

#### Source

```js
[{"id":"c89cadcc.37635","type":"debug","z":"98b49c15.674b6","name":"","active":true,"console":"false","complete":"false","x":591,"y":130,"wires":[]},{"id":"eb9bef99.14641","type":"inject","z":"98b49c15.674b6","name":"","topic":"","payload":"","payloadType":"date","repeat":"1","crontab":"","once":false,"x":206,"y":130,"wires":[["c89cadcc.37635"]]}]
```

#### @ Intel Edison Console

```sh
    26 Mar 14:20:30 - [info] Started flows
```

#### @ Node-Red Debug Tab

```sh
    3/26/2016, 8:47:43 AM8b89cb10.747638
    Hi : msg.payload : string [0]
```

### Input Mqtt + Output Debug

#### @ Node-Red Flow Space

> Input Mqtt
> > Server test.mosquitto.org:1883
> > Topic IBMIoT/NodeRed/IntelEdison

> Output Debug
> > Output Message Property
> > msg.payload

#### Source

```js
[{"id":"744af6bf.8bb508","type":"mqtt-broker","z":"98b49c15.674b6","broker":"test.mosquitto.org ","port":"1883","clientid":"","usetls":false,"verifyservercert":true,"compatmode":true,"keepalive":"60","cleansession":true,"willTopic":"","willQos":"0","willRetain":"false","willPayload":"","birthTopic":"","birthQos":"0","birthRetain":"false","birthPayload":""},{"id":"c89cadcc.37635","type":"debug","z":"98b49c15.674b6","name":"","active":true,"console":"false","complete":"false","x":591,"y":130,"wires":[]},{"id":"7f0cbf12.80f34","type":"mqtt in","z":"98b49c15.674b6","name":"","topic":"IBMIoT/NodeRed/IntelEdison","broker":"744af6bf.8bb508","x":356,"y":130,"wires":[["c89cadcc.37635"]]}]
```

#### @ Intel Edison Console

```sh
    26 Mar 14:37:38 - [info] Started flows
    26 Mar 14:37:40 - [info] [mqtt-broker:744af6bf.8bb508] Connected to broker: mqtt://test.mosquitto.org :1883
```

#### @ Another Device

```sh
    $ mosquitto_pub -h test.mosquitto.org -t IBMIoT/NodeRed/IntelEdison -m "Hello World!"
```
#### @ Node-Red Debug Tab

```sh
    3/26/2016, 8:41:18 AMc89cadcc.37635
    IBMIoT/NodeRed/IntelEdison : msg.payload : string [12]
    Hello World!
```

### Input Mqtt + Output Debug + Function Function 

#### @ Node-Red Flow Space

> Input Mqtt
> > Server test.mosquitto.org:1883
> > Topic IBMIoT/NodeRed/IntelEdison

> Output Debug
> > Output Message Property
> > msg.payload

> Function Function
> > Name MyFunction
> > Function Code See Below

```js
if (msg.payload == 'On')
{
    msg.payload = 1
}
if (msg.payload == 'Off')
{
    msg.payload = 0
}
return msg;
```

> Output Gpio
> > Board galileo-io
> > > Nodebot Galileo/Edison
> > Type Digital (0/1)
> > Pin 13

#### Source

```js
[{"id":"e7025d5c.18fda","type":"nodebot","z":"98b49c15.674b6","name":"","username":"","password":"","boardType":"galileo-io","serialportName":"","connectionType":"local","mqttServer":"","socketServer":"","pubTopic":"","subTopic":"","tcpHost":"","tcpPort":"","sparkId":"","sparkToken":"","beanId":"","impId":"","meshbluServer":"https://meshblu.octoblu.com","uuid":"","token":"","sendUuid":""},{"id":"744af6bf.8bb508","type":"mqtt-broker","z":"98b49c15.674b6","broker":"test.mosquitto.org ","port":"1883","clientid":"","usetls":false,"verifyservercert":true,"compatmode":true,"keepalive":"60","cleansession":true,"willTopic":"","willQos":"0","willRetain":"false","willPayload":"","birthTopic":"","birthQos":"0","birthRetain":"false","birthPayload":""},{"id":"c89cadcc.37635","type":"debug","z":"98b49c15.674b6","name":"","active":true,"console":"false","complete":"payload","x":591,"y":130,"wires":[]},{"id":"7f0cbf12.80f34","type":"mqtt in","z":"98b49c15.674b6","name":"","topic":"IBMIoT/NodeRed/IntelEdison","broker":"744af6bf.8bb508","x":232,"y":130,"wires":[["c89cadcc.37635","a439a46b.5bc658"]]},{"id":"a439a46b.5bc658","type":"function","z":"98b49c15.674b6","name":"MyFunction","func":"if (msg.payload == 'On')\n{\n    msg.payload = 1\n}\nif (msg.payload == 'Off')\n{\n    msg.payload = 0\n}\nreturn msg;","outputs":1,"noerr":0,"x":444,"y":186,"wires":[["5366e815.ac9918"]]},{"id":"5366e815.ac9918","type":"gpio out","z":"98b49c15.674b6","name":"","state":"OUTPUT","pin":"13","i2cDelay":"0","i2cAddress":"","i2cRegister":"","outputs":0,"board":"e7025d5c.18fda","x":628,"y":186,"wires":[]}]
```

#### @ Intel Edison Console

```sh
    1459004673454 Connected Intel Edison  
    26 Mar 15:04:33 - [info] [mqtt-broker:744af6bf.8bb508] Connected to broker: mqtt://test.mosquitto.org :1883
```

#### @ Another Device

```sh
    $ mosquitto_pub -h test.mosquitto.org -t IBMIoT/NodeRed/IntelEdison -m "On"
    $ mosquitto_pub -h test.mosquitto.org -t IBMIoT/NodeRed/IntelEdison -m "Off"
```
#### @ Node-Red Debug Tab

```sh
    3/26/2016, 9:06:37 AMc89cadcc.37635
    IBMIoT/NodeRed/IntelEdison : msg.payload : string [2]
    On
    3/26/2016, 9:06:41 AMc89cadcc.37635
    IBMIoT/NodeRed/IntelEdison : msg.payload : string [3]
    Off
```

#### @ Intel Edison Board

Check the Led tight to GPIO 13 (DS2)

## Intel Edison + Grove Starter Kit

- [Node-RED nodes to support a few Grove Sensors for Intel Edison Arduino Board](http://flows.nodered.org/node/node-red-contrib-socialogix4edison)

```sh
    root@edison:~# npm install node-red-contrib-socialogix4edison
    -\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-n
    ��└��─��─ q@1.4.1
    root@edison:~# 
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
