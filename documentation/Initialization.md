Initialization
==

Connect Intel Edison to your Host Computer using the registered COM / TTY device and launch your serial interface, e.g. Linux

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

## Bootup Linux Login

```sh
    Poky (Yocto Project Reference Distro) 1.7.2 edison ttyMFD2
    
    edison login: root
    root@edison:~# 
```

## Bootup Kernel Display Message

- [Linux Kernel Dmesg](https://en.wikipedia.org/wiki/Dmesg)

```sh
    root@edison:~# dmesg
    root@edison:~# dmesg > dmesg.file
    root@edison:~# vi dmesg.file
    
    [    0.000000] Initializing cgroup subsys cpuset
    [    0.000000] Initializing cgroup subsys cpu
    ...
    [   17.842227] snd_intel_sst: runtime_idle called                               
    [   19.841555] snd_intel_sst: runtime_suspend called
```

__Homework__ Review the content under dmesg.file, identify which drivers/services are executed/started

## Bootup Initial Configuration

Check your kernel version

```sh
    root@edison:~# uname -r
    3.10.17-poky-edison+
```

Configure your WiFi

```sh
    root@edison:~# configure_edison --wifi
    Configure Edison: WiFi Connection
    
    Scanning: 1 seconds left  
    
    0 :     Rescan for networks
    1 :     Exit WiFi Setup
    2 :     Manually input a hidden SSID
    3 :     INFINITUM914E
    
    
    Enter 0 to rescan for networks.
    Enter 1 to exit.
    Enter 2 to input a hidden network SSID.
    Enter 3 to choose INFINITUM9###: 3
    Is INFINITUM9### correct? [Y or N]: Y
    Password must be between 8 and 63 characters.
    What is the network password?: 
    What is the network password?: **********
    Initiating connection to INFINITUM9###. Please wait...
    Attempting to enable network access, please check 'wpa_cli status' after a minute to confirm.
    Done. Please connect your laptop or PC to the same network as this device and go to http://192.168.1.72 or http://edison.local in your browser.
    Warning: SSH is not yet enabled on the wireless interface. To enable SSH access to this device via wireless run configure_edison --password first.
    root@edison:~# 
```

Configure also password to enable SSH on the wireless interface

```
    root@edison:~# configure_edison --password
    
    Configure Edison: Device Password
    
    Enter a new password (leave empty to abort)
    This will be used to connect to the access point and login to the device.
    Password:       ********
    Please enter the password again:        ********
    First-time root password setup complete. Enabling SSH on WiFi interface.
    The device password has been changed.
```

Check IP address assigned

```sh
    root@edison:~# ifconfig
    lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
    wlan      Link encap:Ethernet  HWaddr 00:1C:C0:AE:B5:E6  
              inet addr:192.168.1.74  Bcast:192.168.0.255  Mask:255.255.255.0
```
