Flashing
==

- [Intel® Edison Board Software Downloads](https://software.intel.com/en-us/iot/hardware/edison/downloads)

## Board Support Package Update in a Nutshell

### Intel® Edison

> Download drivers, installers, new firmware images, IDEs and components like cloud analytics and gateway software.

- [Intel® Edison Board Software Downloads](https://software.intel.com/en-us/iot/hardware/edison/downloads)

The flashing process is in your Host Computer:

 - Download the latest Yocto Image
 - Unzip its content
 - Within the terminal, go to the directory where the content has been unzipped
 - And flash the image

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
    U-Boot 2014.04 (Aug 20 2014 - 16:08:32)
       Watchdog enabled
    DRAM:  980.6 MiB
    MMC:   tangier_sdhci: 0
    In:    serial
    Out:   serial
    Err:   serial
    Hit any key to stop autoboot:  0
    boot > run do_ota
    reading ota_update.scr
    14747 bytes read in 31 ms (463.9 KiB/s)
    ## Executing script at 00100000
    ...
```

Finally, connect Intel® Edison to your Development Workstation using the registered COM / TTY device


