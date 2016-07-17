# Services

```sh
root@edison:~# mkdir /etc/init.d 
```

```sh
root@edison:~# nano /etc/init.d/helloservice.sh
```

```
#!/bin/sh

echo "Hello Service At Startup"
```

```sh
root@edison:~# chmod 755 /etc/init.d/helloservice.sh
root@edison:~# update-rc.d helloservice.sh defaults
```

```sh
root@edison:~# shutdown -r now
```

# SystemD

> systemd is a suite of basic building blocks for a Linux system. It provides a system and service manager that runs as PID 1 and starts the rest of the system. [Homepage](https://freedesktop.org/wiki/Software/systemd/)

> systemd is an init system used by some Linux distributions to bootstrap the user space and manage all processes subsequently, instead of the UNIX System V or Berkeley Software Distribution (BSD) init systems. The name systemd adheres to the Unix convention of naming daemons by appending the letter d. [Wikipedia](https://en.wikipedia.org/wiki/Systemd)

> Systemd is an init system and system manager that is widely becoming the new standard for Linux machines. While there are considerable opinions about whether systemd is an improvement over the traditional SysV init systems it is replacing, the majority of distributions plan to adopt it or have already done so. [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units)

- [ArchLinux systemd System and Service Manager](https://wiki.archlinux.org/index.php/systemd)

```sh
root@edison:~# ls /lib/systemd/system
...
...nano /etc/systemd/journald.conf
poweroff.target                         timers.target
poweroff.target.wants                   timers.target.wants
printer.target                          tmp.mount
pulseaudio.service                      udhcpd-for-hostapd.service
pwr-button-handler.service              umount.target
quotaon.service                         user.slice
rc-local.service                        user@.service
reboot.target                           watchdog-sample.service
reboot.target.wants                     wpa_supplicant.service
redis.service                           wpa_supplicant_p2p_event.service
remote-fs-pre.target                    wpa_supplicant_wlan0_event.service
remote-fs.target                        wyliodrin-hypervisor.service
rescue.service                          wyliodrin-server.service
rescue.target                           xdk-daemon.service
```

# Systemctl

> systemctl — Control the systemd system and service manager. systemctl may be used to introspect and control the state of the "systemd" system and service manager. [Homepage](https://www.freedesktop.org/software/systemd/man/systemctl.html)

> systemctl command, the central management tool for controlling the init system

```sh
root@edison:~# systemctl list-unit-files --type=service
...
```

```sh
root@edison:~# ls /etc/systemd/system/*.wants/
...
```

# Services, Disable/Enable

```sh
root@edison:~# systemctl stop xdk-daemon
root@edison:~# systemctl disable xdk-daemon
rm '/etc/systemd/system/multi-user.target.wants/xdk-daemon.service'
root@edison:~# systemctl enable xdk-daemon
ln -s '/lib/systemd/system/xdk-daemon.service' '/etc/systemd/system/multi-user.target.wants/xdk-daemon.service'
```

# Services, Running by Default, Disable?

```sh
root@edison:~# systemctl status clloader     
● clloader.service - Daemon to handle arduino sketches
   Loaded: loaded (/lib/systemd/system/clloader.service; enabled)
   Active: active (running) since Sun 2016-05-08 04:15:11 UTC; 54min ago
 Main PID: 209 (launcher.sh)
   CGroup: /system.slice/clloader.service
           ├─209 /bin/sh /opt/edison/launcher.sh
           └─210 /opt/edison/clloader --escape --binary --zmodem --disable-ti...

May 08 04:15:11 edison systemd[1]: Started Daemon to handle arduino sketches.
May 08 04:15:11 edison launcher.sh[209]: Opened /dev/ttyGS0 as inputOpened /...s
Hint: Some lines were ellipsized, use -l to show in full.
```

```sh
root@edison:~# systemctl status sketch_reset
● sketch_reset.service - Daemon to reset sketches
   Loaded: loaded (/lib/systemd/system/sketch_reset.service; enabled)
   Active: active (running) since Sun 2016-05-08 04:15:11 UTC; 55min ago
 Main PID: 211 (sketch_reset)
   CGroup: /system.slice/sketch_reset.service
           └─211 /opt/edison/sketch_reset -i 207 -o 215 -s /opt/edison/sketch...

May 08 04:15:11 edison systemd[1]: Started Daemon to reset sketches.
```

```sh
root@edison:~# systemctl status rsmb
● rsmb.service
   Loaded: not-found (Reason: No such file or directory)
   Active: inactive (dead)
```

```sh
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
```

```sh
root@edison:~# systemctl status edison_config
● edison_config.service - The Edison status and configuration service
   Loaded: loaded (/lib/systemd/system/edison_config.service; enabled)
   Active: active (running) since Sun 2016-05-08 04:15:15 UTC; 54min ago
 Main PID: 289 (su)
   CGroup: /system.slice/edison_config.service
           ‣ 289 /bin/su root -c node /usr/lib/edison_config_tools/edison-con...

May 08 04:15:15 edison systemd[1]: Started The Edison status and configurat...e.
May 08 04:15:15 edison su[289]: Successful su for root by root
May 08 04:15:15 edison su[289]: + ??? root:root
May 08 04:15:15 edison su[289]: pam_unix(su:session): session opened for us...0)
Hint: Some lines were ellipsized, use -l to show in full.
```

```sh
root@edison:~# systemctl status systemd-resolved
● systemd-resolved.service - Network Name Resolution
   Loaded: loaded (/lib/systemd/system/systemd-resolved.service; enabled)
   Active: active (running) since Sun 2016-05-08 04:15:14 UTC; 56min ago
     Docs: man:systemd-resolved.service(8)
 Main PID: 253 (systemd-resolve)
   Status: "Processing requests..."
   CGroup: /system.slice/systemd-resolved.service
           └─253 /lib/systemd/systemd-resolved

May 08 04:15:14 edison systemd[1]: Started Network Name Resolution.
```

# Services, Start Up Script Execution

- [Musings from Stephanie Automatic Scripting at Boot-Up](http://stephaniemoyerman.com/?p=41)
- [Tektyte Running a Script On Startup](http://www.tektyte.com/docs/docpages/edison-reference/runonstartup.html)

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
    root@edison:~# systemctl status hello-world
```

Reboot your Intel Edison

```sh
    root@edison:~# reboot
```

Once booted, verify again hello-world service status

```sh
    root@edison:~# systemctl status hello-world
```

# Services, Web Server

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

# Services, Butterfly, Web Based Terminal Emulator

> A sleek web based terminal emulator

> Butterfly is a xterm compatible terminal that runs in your browser

[Butterfly Github](https://github.com/paradoxxxzero/butterfly)

```sh
    root@edison:~# pip install butterfly pyserial npyscreen
    root@edison:~# butterfly.server.py --unsecure --host=192.168.1.65 --port=8885
    butterfly.conf installed in /etc/butterfly/butterfly.conf
    [W 160321 05:41:44 butterfly.server:317] Butterfly is ready, open your browser to: http://192.168.1.65:8885/
```

## SystemD Automatic Run

```sh
    root@edison:~#  cd /etc/systemd/system
    root@edison:~#  curl -O https://raw.githubusercontent.com/paradoxxxzero/butterfly/master/butterfly.service
    root@edison:~#  curl -O https://raw.githubusercontent.com/paradoxxxzero/butterfly/master/butterfly.socket
    root@edison:~#  systemctl enable butterfly.socket
    root@edison:~#  systemctl start butterfly.socket
```
