Services
==

## SystemD

> systemd is a suite of basic building blocks for a Linux system. It provides a system and service manager that runs as PID 1 and starts the rest of the system. [Homepage](https://freedesktop.org/wiki/Software/systemd/)

> systemd is an init system used by some Linux distributions to bootstrap the user space and manage all processes subsequently, instead of the UNIX System V or Berkeley Software Distribution (BSD) init systems. The name systemd adheres to the Unix convention of naming daemons by appending the letter d. [Wikipedia](https://en.wikipedia.org/wiki/Systemd)

> Systemd is an init system and system manager that is widely becoming the new standard for Linux machines. While there are considerable opinions about whether systemd is an improvement over the traditional SysV init systems it is replacing, the majority of distributions plan to adopt it or have already done so. [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units)

- [ArchLinux systemd System and Service Manager](https://wiki.archlinux.org/index.php/systemd)

## Systemctl

> systemctl — Control the systemd system and service manager. systemctl may be used to introspect and control the state of the "systemd" system and service manager. [Homepage](https://www.freedesktop.org/software/systemd/man/systemctl.html)

> systemctl command, the central management tool for controlling the init system


## Services, Disable/Enable

```sh
root@edison:~# systemctl stop xdk-daemon
root@edison:~# systemctl disable xdk-daemon
rm '/etc/systemd/system/multi-user.target.wants/xdk-daemon.service'
root@edison:~# systemctl enable xdk-daemon
ln -s '/lib/systemd/system/xdk-daemon.service' '/etc/systemd/system/multi-user.target.wants/xdk-daemon.service'
```

```sh
root@edison:~# systemctl status rsmb
  rsmb.service
   Loaded: not-found (Reason: No such file or directory)
   Active: inactive (dead)
root@edison:~# systemctl status mdns
● mdns.service - Zero-configuration networking
   Loaded: loaded (/lib/systemd/system/mdns.service; enabled)
   Active: active (running) since Sun 2016-05-08 04:15:14 UTC; 53min ago
 Main PID: 265 (mdnsd)
   CGroup: /system.slice/mdns.service
           └─265 /usr/sbin/mdnsd

May 08 04:54:08 edison mDNSResponder[265]: mDNSPlatformSendUDP got error 99 ...3
May 08 04:54:08 edison mDNSResponder[265]: mDNSPlatformSendUDP got error 99 ...3
May 08 04:54:12 edison mDNSResponder[265]: mDNSPlatformSendUDP got error 101...3
May 08 05:00:00 edison mDNSResponder[265]: mDNSPlatformSendUDP got error 99 ...3
May 08 05:00:00 edison mDNSResponder[265]: mDNSPlatformSendUDP got error 99 ...3
May 08 05:00:01 edison mDNSResponder[265]: mDNSPlatformSendUDP got error 99 ...3
May 08 05:00:01 edison mDNSResponder[265]: mDNSPlatformSendUDP got error 99 ...3
May 08 05:00:08 edison mDNSResponder[265]: mDNSPlatformSendUDP got error 99 ...3
May 08 05:00:08 edison mDNSResponder[265]: mDNSPlatformSendUDP got error 99 ...3
May 08 05:00:09 edison mDNSResponder[265]: mDNSPlatformSendUDP got error 99 ...3
Hint: Some lines were ellipsized, use -l to show in full.
root@edison:~# systemctl status edison_config
```
systemctl disable and systemctl stop on edison_config, xdk-daemon, rsmb, and mdns


## Services, Start Up Script Execution

```sh
    root@edison:~# cd /home/root/
    root@edison:~# nano hello-world.sh
```

```sh
    echo "Hello World!"
```

```sh
    root@edison:~# chmod +x hello-world.sh
    root@edison:~# cd /lib/systemd/system
    root@edison:~# nano hello-world.service
```

```sh
    [Unit]
    Description=Hello World
    After=sys-subsystem-net-devices-%i.device

    [Service]
    ExecStart=/bin/bash /home/root/hello-world.sh
    Restart=always
    RestartSec=10 

    [Install]
    Alias=HelloWorld
    WantedBy=multi-user.target
```

```sh
    root@edison:~# systemctl daemon-reload
    root@edison:~# systemctl --system enable hello-world
    root@edison:~# systemctl start hello-world
    root@edison:~# systemctl status hello-world.service -l
```

- [Musings from Stephanie Automatic Scripting at Boot-Up](http://stephaniemoyerman.com/?p=41)
- [Tektyte Running a Script On Startup](http://www.tektyte.com/docs/docpages/edison-reference/runonstartup.html)

## Services, Web Server

Location of the web server content

```sh
    root@edison:~# ls /usr/lib/edison_config_tools/public/
```

Location of the web server configuration script 

```sh
    root@edison:~# ls /usr/lib/edison_config_tools/edison-config-server.js
```

To stop actual webserver

```sh
    root@edison:~# systemctl disable edison_config
    root@edison:~# systemctl stop edison_config
    root@edison:~# systemctl status edison_config
```

## Services, Butterfly

> A sleek web based terminal emulator

> Butterfly is a xterm compatible terminal that runs in your browser

[Butterfly Github](https://github.com/paradoxxxzero/butterfly)

```sh
    root@edison:~# pip install butterfly pyserial npyscreen
    root@edison:~# butterfly.server.py --unsecure --host=192.168.1.65 --port=8885
    butterfly.conf installed in /etc/butterfly/butterfly.conf
    [W 160321 05:41:44 butterfly.server:317] Butterfly is ready, open your browser to: http://192.168.1.65:8885/
```

### SystemD Automatic Run

```sh
    root@edison:~#  cd /etc/systemd/system
    root@edison:~#  curl -O https://raw.githubusercontent.com/paradoxxxzero/butterfly/master/butterfly.service
    root@edison:~#  curl -O https://raw.githubusercontent.com/paradoxxxzero/butterfly/master/butterfly.socket
    root@edison:~#  systemctl enable butterfly.socket
    root@edison:~#  systemctl start butterfly.socket
```
