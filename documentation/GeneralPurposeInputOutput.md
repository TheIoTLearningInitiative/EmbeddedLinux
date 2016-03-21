# General Purpose Input Output (GPIO)
==

> General-purpose input/output (GPIO) is a generic pin on an integrated circuit whose behavior—including whether it is an input or output pin—is controllable by the user at run time. Wikipedia

- [Linux Kernel GPIO Documentation](https://www.kernel.org/doc/Documentation/gpio/)
- [LWN GPIO In The Kernel: An Introduction](https://lwn.net/Articles/532714/)
- [Wikipedia GPIO](https://en.wikipedia.org/wiki/General-purpose_input/output)

## Kernel Integration

### Kernel Display Message

```sh
    root@edison:~# dmesg | grep -i gpio
    [    0.000000] SFI: GPIO E3A27, 0964 (v1  INTEL INTELFDK)
    [    0.189472] wifi_platform_data: GPIO == 64
    [    0.189618] IPC bus, name =        msic_gpio, irq = 0x31
    [    0.209216] virtio_rpmsg_bus virtio0: creating channel rpmsg_msic_gpio addr 0x5
    [    1.584512] vwlan gpio 96
    [    1.971456] info[ 0]: name = power_btn, gpio = -1
    [    1.971473] info[ 1]: name = SW1UI4, gpio = 61
    [    2.004409] input: gpio-keys as /devices/platform/gpio-keys/input/input0
```

## Userspace Interfaces

```sh
    root@edison:~# ls /sys/class/gpio/
    export     gpio125    gpio127    gpio129    gpio131    gpio133    gpiochip0
    gpio124    gpio126    gpio128    gpio130    gpio132    gpio134    unexport
```

You are seeing 3 kind of entries: 

   - Control interfaces used to get userspace control over GPIOs;
   - GPIOs themselves; and
   - GPIO controllers ("gpio_chip" instances).

- [GPIO Sysfs](https://www.kernel.org/doc/Documentation/gpio/sysfs.txt)

### Watching it change (a primer on GPIO and GPIO configuration this content is moving to GPIO Subsystem)

To see the status of our exported pins in the Edison, type this your Edison's terminal:

```sh
    root@edison:~# watch -n 1 cat /sys/kernel/debug/gpio
```

Basically, it will output the configured GPIO's to console every second:

```sh
    Every 1s: cat /sys/kernel/debug/gpio                        2015-10-13 21:02:27
    
    PIOs 0-191, pci/0000:00:0c.0, 0000:00:0c.0:
     gpio-61  (SW1UI4              ) in  hi
     gpio-64  (bcm43xx_irq         ) in  hi
     gpio-71  (bcm_bt_lpm          ) out lo
     gpio-77  (sd_cd               ) in  hi
     gpio-96  (vwlan               ) out hi
     gpio-111 (Arduino Shield SS   ) out hi
     gpio-124 (hsu                 ) in  hi
     gpio-125 (hsu                 ) in  hi
     gpio-126 (hsu                 ) in  hi
     gpio-127 (hsu                 ) in  hi
     gpio-128 (hsu                 ) in  hi
     gpio-129 (hsu                 ) in  hi
     gpio-130 (hsu                 ) in  hi
     gpio-131 (hsu                 ) in  hi
     gpio-132 (hsu                 ) in  lo
     gpio-133 (hsu                 ) out lo
     gpio-134 (hsu                 ) in  hi
     gpio-184 (bcm_bt_lpm          ) out lo
     gpio-185 (bcm_bt_lpm          ) in  lo
    
    GPIOs 200-215, i2c/1-0020, pcal9555a, can sleep:
     gpio-207 (sysfs               ) in  hi
     gpio-215 (sysfs               ) out lo
    
    GPIOs 216-231, i2c/1-0021, pcal9555a, can sleep:
    
    GPIOs 232-247, i2c/1-0022, pcal9555a, can sleep:
    
    GPIOs 248-263, i2c/1-0023, pcal9555a, can sleep:
```

The gpio's displayed above, are the ones reserved (AKA exported) by default in a newly flashed  yocto image **Poky (Yocto Project Reference Distro) 1.7.2 edison**,  kernel  **3.10.17-poky-edison+**

To reserve and use a GPIO, 
Before:

```sh
    root@edison:~# ls /sys/class/gpio
    export       gpio127      gpio131      gpio207        gpiochip216
    gpio124      gpio128      gpio132      gpio215        gpiochip232
    gpio125      gpio129      gpio133      gpiochip0      gpiochip248
    gpio126      gpio130      gpio134      gpiochip200    unexport
```

let's say 48 lets type the following:

    root@edison:/# echo 48 > /sys/class/gpio/export

by this mechanism, a new directory is created in **/sys/class/gpio**, which should be **gpio48**:
After:

```sh
    root@edison:/# ls sys/class/gpio/
    export       gpio127      gpio131      gpio207      gpiochip200  unexport
    gpio124      gpio128      gpio132      gpio215      gpiochip216
    gpio125      gpio129      gpio133      gpio48       gpiochip232
    gpio126      gpio130      gpio134      gpiochip0    gpiochip248
```

This directory, is a control interface used to get userspace control over GPIO48, therefore can have the following read/write attributes:

```sh
	"direction" ... reads as either "in" or "out". This value may
		normally be written. Writing as "out" defaults to
		initializing the value as low. To ensure glitch free
		operation, values "low" and "high" may be written to
		configure the GPIO as an output with that initial value.

		Note that this attribute *will not exist* if the kernel
		doesn't support changing the direction of a GPIO, or
		it was exported by kernel code that didn't explicitly
		allow userspace to reconfigure this GPIO's direction.

	"value" ... reads as either 0 (low) or 1 (high). If the GPIO
		is configured as an output, this value may be written;
		any nonzero value is treated as high.

		If the pin can be configured as interrupt-generating interrupt
		and if it has been configured to generate interrupts (see the
		description of "edge"), you can poll(2) on that file and
		poll(2) will return whenever the interrupt was triggered. If
		you use poll(2), set the events POLLPRI and POLLERR. If you
		use select(2), set the file descriptor in exceptfds. After
		poll(2) returns, either lseek(2) to the beginning of the sysfs
		file and read the new value or close the file and re-open it
		to read the value.

	"edge" ... reads as either "none", "rising", "falling", or
		"both". Write these strings to select the signal edge(s)
		that will make poll(2) on the "value" file return.

		This file exists only if the pin can be configured as an
		interrupt generating input pin.

	"active_low" ... reads as either 0 (false) or 1 (true). Write
		any nonzero value to invert the value attribute both
		for reading and writing. Existing and subsequent
		poll(2) support configuration via the edge attribute
		for "rising" and "falling" edges will follow this
		setting.
```

### Exercise Change GPIO Direction

As explained before the GPIO control interface has some read/write attributes, so lets go ahead and change the default direction of the **GPIO48**.

1. Review the current GPIO direction using the command  to debug GPIO statuses; If the direction is **"out"** let's change it to **"in"**, if it is **"in"**, change it to **"out"**

2. To change it, from **"in"** to  **"out "** we only have to  write "out" to attribute **GPIO48/direction** like this:

```sh
    echo out > /sys/class/gpio/gpio48/direction
```

Then checking again the GPIO status we can see, that direction has changed. Here is a table that shows the direction before and after the change: 

```sh
    | GPIO48  Previous Direction | GPIO48  New Direction |
    | -- | -- |
    | gpio-48  (sysfs               ) **in**  lo| gpio-48  (sysfs               ) **out**  lo |
```

### Exercise Use Python Bindings

```sh
    mraa
    apt-get install python-smbus
```