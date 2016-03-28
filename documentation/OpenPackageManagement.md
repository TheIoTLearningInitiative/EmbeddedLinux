Open Package Management
==

> Opkg (Open PacKaGe Management) is a lightweight package management system based upon ipkg. It is written in C and resembles APT/dpkg in operation. It is intended for use on embedded Linux devices and is used in this capacity in the OpenEmbedded and OpenWrt projects. Wikipedia

- [Open Package Management Wikipedia](https://en.wikipedia.org/wiki/Opkg)

## Package Installation via Remote Repositories

Update Opkg Repositories

```sh
    root@edison:~# opkg update
    Downloading http://iotdk.intel.com/repos/1.5/intelgalactic/Packages.
    Updated list of available packages in /var/lib/opkg/iotkit.
    root@edison:~#
```

Enable a Opkg feed and update package list, we will not upgrade to avoid consuming disk space

```sh
    root@edison:~# vi /etc/opkg/base-feeds.conf # Add the below lines to the opened file
```

```sh
src/gz all http://repo.opkg.net/edison/repo/all
src/gz edison http://repo.opkg.net/edison/repo/edison
src/gz core2-32 http://repo.opkg.net/edison/repo/core2-32
```

```sh
    root@edison:~# opkg update
    Downloading http://repo.opkg.net/edison/repo/all/Packages.gz.
    Inflating http://repo.opkg.net/edison/repo/all/Packages.gz.
    Updated list of available packages in /var/lib/opkg/all.
    Downloading http://repo.opkg.net/edison/repo/edison/Packages.gz.
    Inflating http://repo.opkg.net/edison/repo/edison/Packages.gz.
    Updated list of available packages in /var/lib/opkg/edison.
    Downloading http://repo.opkg.net/edison/repo/core2-32/Packages.gz.
    Inflating http://repo.opkg.net/edison/repo/core2-32/Packages.gz.
    Updated list of available packages in /var/lib/opkg/core2-32.
    Downloading http://iotdk.intel.com/repos/1.5/intelgalactic/Packages.
    Updated list of available packages in /var/lib/opkg/iotkit.
    root@edison:~# 
```

Install Git, Version Control System

```sh
    root@edison:~# opkg install git
```

Check if RMAA and UPM Libraries are installed

```sh
    root@edison:~# opkg list-installed | grep mraa
    root@edison:~# opkg list-installed | grep upm
```

Install and configure extra packages required

```sh
    root@edison:~# opkg install nano git python-pip
    root@edison:~# git config --global user.name "Name LastName"
    root@edison:~# git config --global user.email email@adress.com
```

## Package Installation via Local Files

```sh
    root@edison:~# wget http://repo.opkg.net/edison/repo/core2-32/less_458-r0_core2-32.ipk
    root@edison:~# opkg install less_458-r0_core2-32.ipk
```
