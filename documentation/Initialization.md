Initialization
==

Connect Intel Edison to your Host Computer using the registered COM / TTY device and launch your serial interface, e.g. Linux

In Linux

```sh
    $ dmesg
    [11940.538090] ftdi_sio 6-1:1.0: FTDI USB Serial Device converter detected
    [11940.538137] usb 6-1: Detected FT232RL
    [11940.538139] usb 6-1: Number of endpoints 2
    [11940.538142] usb 6-1: Endpoint 1 MaxPacketSize 64
    [11940.538144] usb 6-1: Endpoint 2 MaxPacketSize 64
    [11940.538147] usb 6-1: Setting MaxPacketSize 64
    [11940.540185] usb 6-1: FTDI USB Serial Device converter now attached to ttyUSB0
```

```sh
    $ sudo minicom -D /dev/ttyUSB0 115200
```

## Bootup U-Boot

```sh
    ******************************
    PSH KERNEL VERSION: b0182b2b
                    WR: 20104000
    ******************************
    
    SCU IPC: 0x800000d0  0xfffce92c
    
    PSH miaHOB version: TNG.B0.VVBD.0000000c
    
    microkernel built 11:24:08 Feb  5 2015
    
    ******* PSH loader *******CM page cache size = 192 KB 
    Cache Constrais
    Arming IPC driver ..
    Adding page store pool ..
    PagestoreAddr(IMR Start Address) = 0x04899000
    pagIMR Size)          = 0dy to receive application *** 
    
    
    U-Boot 2014.04 (Dec 19 2015 - 23:30:32)

           Watchdog enabled
    DRAM:  980.6 MiB
    MMC:   tangier_sdhci: 0
    In:    serial
    Out:   serial
    Err:   serial
    Hit any key to stop autoboot:  0 
    Target:blank
    Partitioning already done...
    Flashing already done...
    GADGET DRIVER: usb_dnl_dfu
    reading vmlinuz
    5385504 bytes read in 133 ms (38.6 MiB/s)
    Valid Boot Flag
    Setup Size = 0x00003c00
    Magic signature found
    Using boot protocol version 2.0c
    Linux kernel version 3.10.17-yocto-standard (abraham@aarcemor-desk) #1 SMP PREEMPT Sat Dec 19 23:23:25 CST 2015
    Building boot_params at 0x00090000
    Loading bzImage at address 00100000 (5370144 bytes)
    Magic signature found
    Kernel command line: "rootwait root=PARTUUID=012b3303-34ac-284d-99b4-34e03a2335f4 rootfstype=ext4 console=ttyMFD2 earlyprintk=ttyMFD2,k"
```

## Bootup Linux Kernel

```sh
    Starting kernel ...
    
    [    0.766587] pca953x 1-0020: failed reading register
    [    0.771661] pca953x 1-0021: failed reading register
    [-0022: failed reading register
    [    0.781845] pca953x 1-0023: failed reading register
    [    1.621706] snd_soc_sst_platform: Enter:sst_soc_probe
    [    2.026053] pmic_ccsm pmic_ccsm: Error reading battery profile from battid frmwrk
    [    2.044225] pmic_ccsm pmic_ccsm: Battery Over heat exception

    Welcome to Linux!
    
             Expecting device dev-ttyMFD2.device...
    [  OK  ] Mounted Debug File System.
    [  OK  ] Found device /dev/ttyMFD2.
    [  OK  ] Started Network Time Synchronization.
         Bluetooth service...
         Starting File System Check on /dev/disk/by-partlabel/boot...
         Starting Serial Getty on ttyMFD2...
    [  OK  ] Started Serial Getty on ttyMFD2.
         Starting Getty on tty1...
    [  OK  ] Started Getty on tty1.
    [  OK  ] Reached target Login Prompts.
         Mounting /home...
         Starting Network Name Resolution...
    [  OK  ] Reached target Network.
         Starting Zero-configuration networking...
         Starting Mosquitto - lightweight server implementati...SN protocols...
    [  OK  ] Mounted /home.
    [  OK  ] Started Mosquitto - lightweight server implementatio...T-SN protocols.
    [  OK  ] Started Zero-configuration networking.
    [  OK  ] Started Bluetooth service.
    [  OK  ] Started Restore Sound Card State.
         Starting PulseAudio Sound System...
         Starting Horting The Edison status and configuration service...
    [  OK  ] Started The Edison onfiguration service.
         Starting Intel_XDK_Daemon...
    [  OK  ] Started Intel_XDK_Daemon.
         Mounting /boot...
    [  OK  ] Started Hostname Service.
    [  OK  ] Mounted /boot.
    [  OK  ] Started PulseAudio Sound System.
    [[0m] Reached target Multi-User System.
    
    Poky (Yocto Project Reference Distro) 1.7.2 edison ttyMFD2
    
    edison login: 
```
