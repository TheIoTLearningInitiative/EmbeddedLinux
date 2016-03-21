# Misc

## Squid Proxy

> Squid is a caching proxy for the Web supporting HTTP, HTTPS, FTP, and more. It reduces bandwidth and improves response times by caching and reusing frequently-requested web pages. Squid has extensive access controls and makes a great server accelerator. It runs on most available operating systems, including Windows and is licensed under the GNU GPL.

- [Squid Proxy on Debian Linux](http://linuxaria.com/pills/how-to-setup-a-squid-proxy-on-your-debian-linux)

    apt-get install squid3 squid3-common


## DHCP


    apt-get install dhcpd


## Apache


    apt-get install apache2
    apache2 -k restart # Wrong
    /etc/init.d/apache2 restart # Ok


