Clock
==

> A Linux system actually has two clocks: One is the battery powered "Real Time Clock" (also known as the "RTC", "CMOS clock", or "Hardware clock") which keeps track of time when the system is turned off but is not used when the system is running. The other is the "system clock" (sometimes called the "kernel clock" or "software clock") which is a software counter based on the timer interrupt. It does not exist when the system is not running, so it has to be initialized from the RTC (or some other time source) at boot time. References to "the clock" in the ntpd documentation refer to the system clock, not the RTC. [The Clock Mini-HOWTO](http://tldp.org/HOWTO/Clock.html)


```sh
    apt-get ntp server
```

