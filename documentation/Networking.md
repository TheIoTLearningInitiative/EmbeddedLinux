Networking
==

## Automatic WiFi Connection

```sh
    root@edison:~# configure_edison -wifi
    root@edison:~# systemctl enable wpa_supplicant
    root@edison:~# systemctl start wpa_supplicant
```

## Butterfly

> A sleek web based terminal emulator

> Butterfly is a xterm compatible terminal that runs in your browser

[Butterfly Github](https://github.com/paradoxxxzero/butterfly)

```sh
    root@edison:~# pip install butterfly
    root@edison:~# pip install pyserial
    root@edison:~# pip install npyscreen
    root@edison:~# butterfly.server.py --unsecure --host=192.168.1.71 --port=8885
    butterfly.conf installed in /etc/butterfly/butterfly.conf
    [W 160321 05:41:44 butterfly.server:317] Butterfly is ready, open your browser to: http://192.168.1.71:8885/
```

### 

```sh
    root@edison:~#  cd /etc/systemd/system
    root@edison:~#  curl -O https://raw.githubusercontent.com/paradoxxxzero/butterfly/master/butterfly.service
    root@edison:~#  curl -O https://raw.githubusercontent.com/paradoxxxzero/butterfly/master/butterfly.socket
    root@edison:~#  systemctl enable butterfly.socket
    root@edison:~#  systemctl start butterfly.socket
```

## Others

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

## Links

- https://software.intel.com/en-us/connecting-to-a-network-intel-edison-board
- http://pagealh.com/2015/09/12/getting-started-with-edison-static-ip-address/

## Controller Area Network

- https://communities.intel.com/message/294647#294647
- https://www.sparkfun.com/products/13262
- https://store.digilentinc.com/?NavPath=2,892,942&Prod=CHIPKIT-NETWORK-SHIELD
