Inter Integrated Circuit
==

> I²C (Inter-Integrated Circuit), pronounced I-squared-C, is a multi-master, multi-slave, single-ended, serial computer bus invented by Philips Semiconductor (now NXP Semiconductors). It is typically used for attaching lower-speed peripheral ICs to processors and microcontrollers. [Wikipedia](https://en.wikipedia.org/wiki/I%C2%B2C)

### Required Hardware

One I2C sensor

## Kernel Integration

### Kernel Display Message

```sh
    root@edison:~/libusb# dmesg | grep -i i2c
    [    0.190675] I2C bus = 1, name =      pcal9555a-1, irq = 0x 0, addr = 0x20
    [    0.190711] I2C bus = 1, name =      pcal9555a-2, irq = 0x 0, addr = 0x21
    [    0.190743] I2C bus = 1, name =      pcal9555a-3, irq = 0x 0, addr = 0x22
    [    0.190774] I2C bus = 1, name =      pcal9555a-4, irq = 0x 0, addr = 0x23
    [    0.746686] i2c /dev entries driver
```

```sh
    i2cdetect -y -r 1
```
