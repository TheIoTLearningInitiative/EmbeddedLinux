Clock
==

> A Linux system actually has two clocks: One is the battery powered "Real Time Clock" (also known as the "RTC", "CMOS clock", or "Hardware clock") which keeps track of time when the system is turned off but is not used when the system is running. The other is the "system clock" (sometimes called the "kernel clock" or "software clock") which is a software counter based on the timer interrupt. It does not exist when the system is not running, so it has to be initialized from the RTC (or some other time source) at boot time. References to "the clock" in the ntpd documentation refer to the system clock, not the RTC. [The Clock Mini-HOWTO](http://tldp.org/HOWTO/Clock.html)

## Kernel Integration

### Kernel Display Message

```sh
    root@edison:~# dmesg | grep -i clock
    [    0.190320] SDIO bus = 1, name = bcm43xx_clk_vmmc, ref_clock = 26000000, addr =0x401
    [    0.208133] PTP clock support registered
    [    0.240814] hsu core clock 38 M
    [    0.242400] Switching to clocksource refined-jiffies
    [    1.534698] Switching to clocksource tsc
    [    2.076269] rtc_cmos rtc_cmos: setting system clock to 2000-01-01 00:00:09 UTC (946684809)
```

```sh
    apt-get ntp server
```

