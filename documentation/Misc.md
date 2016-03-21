Misc
==

## Squid Proxy, Ubilinux

> Squid is a caching proxy for the Web supporting HTTP, HTTPS, FTP, and more. It reduces bandwidth and improves response times by caching and reusing frequently-requested web pages. Squid has extensive access controls and makes a great server accelerator. It runs on most available operating systems, including Windows and is licensed under the GNU GPL.

- [Squid Proxy on Debian Linux](http://linuxaria.com/pills/how-to-setup-a-squid-proxy-on-your-debian-linux)

```sh
    apt-get install squid3 squid3-common
```

## DHCP, Ubilinux

```sh
    apt-get install dhcpd
```

## Apache, Ubilinux


```sh
    apt-get install apache2
    apache2 -k restart # Wrong
    /etc/init.d/apache2 restart # Ok
```

## WifiDog

```sh
    root@ubilinux:~# git clone https://github.com/wifidog/wifidog-gateway.git
    root@ubilinux:~# cd wifidog-gateway
    root@ubilinux:~/wifidog-gateway# ./autogen.sh
    root@ubilinux:~/wifidog-gateway# ./configure
    root@ubilinux:~/wifidog-gateway# make
    root@ubilinux:~/wifidog-gateway# make install
    root@ubilinux:~/wifidog-gateway# wifidog 
    [6][Fri Jan  8 23:23:20 2016][16159](conf.c:651) Reading configuration file '/usr/local/etc/wifidog.conf'
    [3][Fri Jan  8 23:23:20 2016][16159](conf.c:654) Could not open configuration file '/usr/local/etc/wifidog.conf', exiting...

    root@ubilinux:~# git clone https://github.com/wifidog/wifidog-auth.git
    
    root@ubilinux:~# apt-get install postgresql-9.1
    root@ubilinux:~# apt-get install php5-pgsql
    root@ubilinux:~# apt-get install php-pear
    root@ubilinux:~# apt-get install php5-curl
    root@ubilinux:~# wget http://prdownloads.sourceforge.net/phlickr/Phlickr-0.2.5.tgz?download
    root@ubilinux:~# pear install Phlickr-0.2.5.tgz\?download
```