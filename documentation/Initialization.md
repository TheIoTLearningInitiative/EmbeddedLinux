# Initialization

- [Gitbook Linux Initialization by 0xAX](https://0xax.gitbooks.io/linux-insides/content/)

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
    
    Poky (Yocto Project Reference Distro) 1.7.3 edison ttyMFD2
    
    edison login: 
    
```
