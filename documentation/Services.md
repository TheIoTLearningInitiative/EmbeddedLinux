Services
==

> Systemd is an init system and system manager that is widely becoming the new standard for Linux machines. While there are considerable opinions about whether systemd is an improvement over the traditional SysV init systems it is replacing, the majority of distributions plan to adopt it or have already done so

> systemctl command, the central management tool for controlling the init system

## Start Up Script Execution, Direct



## Start Up Script Execution, Service

```sh
    root@edison:~# cd /home/root/
    root@edison:~# nano hello-world.sh
    echo "Hello World!"
    <Save Changes>
    root@edison:~# chmod +x hello-world.sh
    root@edison:~# cd /lib/systemd/system
    root@edison:~# nano hello-world.service
```

```sh
    [Unit]
    Description=Python Main
    After=sys-subsystem-net-devices-%i.device

    [Service]
    ExecStart=/bin/bash /home/root/python-main.sh
    Restart=always
    RestartSec=10 

    [Install]
    Alias=pythonmain
    WantedBy=multi-user.target
```

```sh
    root@edison:~# systemctl daemon-reload
    root@edison:~# systemctl --system enable python-main
    root@edison:~# systemctl start python-main
    root@edison:~# systemctl status python-main.service -l
```

- [Musings from Stephanie Automatic Scripting at Boot-Up](http://stephaniemoyerman.com/?p=41)
- [Tektyte Running a Script On Startup](http://www.tektyte.com/docs/docpages/edison-reference/runonstartup.html)

## Web Server

To stop actual webserver

```sh
    root@edison:~# systemctl disable edison_config
    root@edison:~# systemctl stop edison_config 
```
