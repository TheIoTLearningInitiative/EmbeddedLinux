# Flashing

- [Intel® Edison Board Software Downloads](https://software.intel.com/en-us/iot/hardware/edison/downloads)
- [Flashing the firmware on a system with Windows* (manual process)](https://software.intel.com/en-us/flashing-firmware-on-your-intel-edison-board-windows)

## Board Support Package Update in a Nutshell

### Intel® Edison

> Download drivers, installers, new firmware images, IDEs and components like cloud analytics and gateway software.

- [Intel® Edison Board Software Downloads](https://software.intel.com/en-us/iot/hardware/edison/downloads)
- [Latest Release 3.0 Yocto Complete Image iot-devkit-prof-dev-image-edison-20160315.zip](https://downloadmirror.intel.com/25871/eng/iot-devkit-prof-dev-image-edison-20160315.zip)
- [Intel® Edison Board Software Release 3.0 Release Notes](https://software.intel.com/en-us/blogs/2016/03/30/intel-iot-developer-kit-30-release-notes)

```sh
xe1gyq@jessie:~/Downloads/edison/20160606$ unzip iot-devkit-prof-dev-image-edison-20160606.zip 
Archive:  iot-devkit-prof-dev-image-edison-20160606.zip
  inflating: edison_dnx_fwr.bin      
  inflating: edison_dnx_osr.bin      
  inflating: edison_ifwi-dbg-00.bin  
  inflating: edison_ifwi-dbg-00-dfu.bin  
  inflating: edison_ifwi-dbg-01.bin  
  inflating: edison_ifwi-dbg-01-dfu.bin  
  inflating: edison_ifwi-dbg-02.bin  
  inflating: edison_ifwi-dbg-02-dfu.bin  
  inflating: edison_ifwi-dbg-03.bin  
  inflating: edison_ifwi-dbg-03-dfu.bin  
  inflating: edison_ifwi-dbg-04.bin  
  inflating: edison_ifwi-dbg-04-dfu.bin  
  inflating: edison_ifwi-dbg-05.bin  
  inflating: edison_ifwi-dbg-05-dfu.bin  
  inflating: edison_ifwi-dbg-06.bin  
  inflating: edison_ifwi-dbg-06-dfu.bin  
  inflating: edison-image-edison.ext4  
  inflating: edison-image-edison.hddimg  
  inflating: filter-dfu-out.js       
  inflating: flashall.bat            
  inflating: flashall.sh             
  inflating: FlashEdison.json        
   creating: helper/
  inflating: helper/helper.html      
   creating: helper/images/
  inflating: helper/images/Edison-arduino-blink-led.png  
  inflating: helper/images/Edison-arduino.png  
  inflating: helper/images/Edison-breakout-board.png  
  inflating: ota_update.scr          
  inflating: package-list.txt        
  inflating: u-boot-edison.bin       
  inflating: u-boot-edison.img       
   creating: u-boot-envs/
  inflating: u-boot-envs/edison-prod.bin  
  inflating: u-boot-envs/edison-blankrndis.bin  
  inflating: u-boot-envs/edison-blankcdc.bin  
  inflating: u-boot-envs/edison-ifwi.bin  
xe1gyq@jessie:~/Downloads/edison/20160606$ 
```

```sh
xe1gyq@jessie:~/Downloads/latestedison$ unzip iot-devkit-prof-dev-image-edison-20160315.zip 
Archive:  iot-devkit-prof-dev-image-edison-20160315.zip
  inflating: edison_dnx_fwr.bin      
  inflating: edison_dnx_osr.bin      
  inflating: edison_ifwi-dbg-00.bin  
  inflating: edison_ifwi-dbg-00-dfu.bin  
  inflating: edison_ifwi-dbg-01.bin  
  inflating: edison_ifwi-dbg-01-dfu.bin  
  inflating: edison_ifwi-dbg-02.bin  
  inflating: edison_ifwi-dbg-02-dfu.bin  
  inflating: edison_ifwi-dbg-03.bin  
  inflating: edison_ifwi-dbg-03-dfu.bin  
  inflating: edison_ifwi-dbg-04.bin  
  inflating: edison_ifwi-dbg-04-dfu.bin  
  inflating: edison_ifwi-dbg-05.bin  
  inflating: edison_ifwi-dbg-05-dfu.bin  
  inflating: edison_ifwi-dbg-06.bin  
  inflating: edison_ifwi-dbg-06-dfu.bin  
  inflating: edison-image-edison.ext4  
  inflating: edison-image-edison.hddimg  
  inflating: edison-image-edison.manifest  
  inflating: filter-dfu-out.js       
  inflating: flashall.bat            
  inflating: flashall.sh             
  inflating: FlashEdison.json        
   creating: helper/
  inflating: helper/helper.html      
   creating: helper/images/
  inflating: helper/images/Edison-arduino.png  
  inflating: helper/images/Edison-arduino-blink-led.png  
  inflating: helper/images/Edison-breakout-board.png  
  inflating: ota_update.scr          
  inflating: package-list.txt        
  inflating: u-boot-edison.bin       
  inflating: u-boot-edison.img       
   creating: u-boot-envs/
  inflating: u-boot-envs/edison-ifwi.bin  
  inflating: u-boot-envs/edison-blankcdc.bin  
  inflating: u-boot-envs/edison-prod.bin  
  inflating: u-boot-envs/edison-blankrndis.bin  
```

The flashing process is in your Host Computer:

 - Download the Latest Release Yocto Complete Image
 - Unzip its content
 - Within the terminal, go to the directory where the content has been unzipped
 - And flash the image with flashall.[sh/bat] script

#### Windows based Development Workstation

```sh
    C:\Users\aarcemor\Downloads\edison-image-ww25.5-15>flashall.bat
```

#### Linux based Development Workstation

```sh
    user@host:~$ flashall.sh
```

It the Edison, connect both USB cables and wait for flashall.[sh/bat] script to start the flashing process

```sh
xe1gyq@jessie:~/Downloads/latestedison$ ./flashall.sh 
Using U-Boot target: edison-blankcdc
Now waiting for dfu device 8087:0a99
Please plug and reboot the board
Flashing IFWI
Download	[=========================] 100%      4194304 bytes
Download	[=========================] 100%      4194304 bytes
Flashing U-Boot
Download	[=========================] 100%       237568 bytes
Flashing U-Boot Environment
Download	[=========================] 100%        65536 bytes
Flashing U-Boot Environment Backup
Download	[=========================] 100%        65536 bytes
Rebooting to apply partition changes
Now waiting for dfu device 8087:0a99
Flashing boot partition (kernel)
Download	[=========================] 100%      6127616 bytes
Flashing rootfs, (it can take up to 5 minutes... Please be patient)
Download	[=========================] 100%   1302792192 bytes
Rebooting
U-boot & Kernel System Flash Success...
Your board needs to reboot to complete the flashing procedure, please do not unplug it for 2 minutes.
```

Finally, connect Intel® Edison to your Development Workstation using the registered COM / TTY device
