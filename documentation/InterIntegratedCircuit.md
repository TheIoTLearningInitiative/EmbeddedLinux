Inter Integrated Circuit
==

> I²C (Inter-Integrated Circuit), pronounced I-squared-C, is a multi-master, multi-slave, single-ended, serial computer bus invented by Philips Semiconductor (now NXP Semiconductors). It is typically used for attaching lower-speed peripheral ICs to processors and microcontrollers. [Wikipedia](https://en.wikipedia.org/wiki/I%C2%B2C)

- [Linux Journal Greg Kroah-Hartman I2C Drivers Part I](http://www.linuxjournal.com/article/7136)
- [Linux Journal Greg Kroah-Hartman I2C Drivers Part II](http://www.linuxjournal.com/article/7252)

### Required Hardware

One I2C sensor

## Kernel Integration

### Kernel Display Message

```sh
    root@edison:~# dmesg | grep -i i2c
    [    0.190675] I2C bus = 1, name =      pcal9555a-1, irq = 0x 0, addr = 0x20
    [    0.190711] I2C bus = 1, name =      pcal9555a-2, irq = 0x 0, addr = 0x21
    [    0.190743] I2C bus = 1, name =      pcal9555a-3, irq = 0x 0, addr = 0x22
    [    0.190774] I2C bus = 1, name =      pcal9555a-4, irq = 0x 0, addr = 0x23
    [    0.746686] i2c /dev entries driver
```
## Userspace Interfaces

### DevFs

```sh
    root@edison:~# ls /dev/i2c-*
    /dev/i2c-1  /dev/i2c-2  /dev/i2c-3  /dev/i2c-4  /dev/i2c-5  /dev/i2c-6  /dev/i2c-7
```

### ProcFs

```sh
    root@edison:~# cat /proc/interrupts | grep i2c
      7:         44          0   IO-APIC-fasteoi   i2c-designware-1
     10:          0          0   IO-APIC-fasteoi   i2c-designware-2
     12:          0          0   IO-APIC-fasteoi   watchdog, i2c-designware-3
     13:          0          0   IO-APIC-fasteoi   i2c-designware-4
     14:          0          0   IO-APIC-fasteoi   i2c-designware-5
     15:          0          0   IO-APIC-fasteoi   i2c-designware-6
     16:          0          0   IO-APIC-fasteoi   i2c-designware-7
```

```sh
    i2cdetect -y -r 1
```
