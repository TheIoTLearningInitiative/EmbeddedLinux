Networking
==

```sh
    root@edison:~# systemctl start connman
    root@edison:~# systemctl start wpa_supplicant
    root@edison:~# connmanctl
    connmanctl> enable_wifi
    connmanctl> scan_wifi
    connmanctl> agent_on
    connmanctl> connect ...
```

```sh
    root@edison:~# vi /lib/systemd/system/sshd.socket
    [Unit]
    Conflicts=sshd.service
    
    [Socket]
    ExecStartPre=/bin/mkdir -p /var/run/sshd
    ListenStream=22
    # restrict access to wired access for security reasons
    # comment this line to remove restriction
    BindToDevice=usb0
    Accept=yes

    [Install]
    WantedBy=sockets.target
```

## Automatic WiFi Connection

```sh
    root@edison:~# configure_edison -wifi
    root@edison:~# systemctl enable wpa_supplicant
    root@edison:~# systemctl start wpa_supplicant
```

## Anaconda

```sh
    root@edison:~# wget http://09c8d0b2229f813c1b93-c95ac804525aac4b6dba79b00b39d1d3.r79.cf1.rackcdn.com/Anaconda-2.1.0-Linux-x86.sh
    root@edison:~# opkg install python-pip
    root@edison:~# pip install butterfly
    root@edison:~# pip install pyserial
    
```

- [The most important stuff to know about Intel Edison](http://tiredhacker.blogspot.mx/2015/01/the-most-important-stuff-to-know-about.html)

## Links

- https://software.intel.com/en-us/connecting-to-a-network-intel-edison-board
- http://pagealh.com/2015/09/12/getting-started-with-edison-static-ip-address/

## CAN

- https://communities.intel.com/message/294647#294647
- https://www.sparkfun.com/products/13262
- https://store.digilentinc.com/?NavPath=2,892,942&Prod=CHIPKIT-NETWORK-SHIELD
