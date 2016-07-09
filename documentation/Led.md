# LED

> If you are using Linux as your kernel on a SoC design, you’ll be glad to know that it has an entire subsystem dedicated to LEDs! [Fabio Baltieri Linux LED Subsystem](https://fabiobaltieri.com/2011/09/21/linux-led-subsystem/)

> [Linux Kernel GPIO Documentation](https://www.kernel.org/doc/Documentation/gpio/00-INDEX)

```sh
menuconfig LEDS_TRIGGERS
	bool "LED Trigger support"
	depends on LEDS_CLASS
	help
	  This option enables trigger support for the leds class.
	  These triggers allow kernel events to drive the LEDs and can
	  be configured via sysfs. If unsure, say Y.

if LEDS_TRIGGERS

...

config LEDS_TRIGGER_HEARTBEAT
	tristate "LED Heartbeat Trigger"
	depends on LEDS_TRIGGERS
	help
	  This allows LEDs to be controlled by a CPU load average.
	  The flash frequency is a hyperbolic function of the 1-minute
	  load average.
	  If unsure, say Y.

...
```