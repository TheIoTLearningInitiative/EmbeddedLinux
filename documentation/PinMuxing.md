Pin Muxing
==

> When working with the ports on the Linux-level, Pin Muxing are performed by MRAA library. In the case of the microcontroller it is necessary to take care with scripts...

> MRAA Low Level Skeleton Library for IO Communication on GNU/Linux platforms

## Configuring all 4 of the PWM pins

```sh
    root@edison:~# vi pinmuxpwm.sh

    #!/bin/bash
    
    # Configuring PWM pins
    # The Intel Edison SoC offers only four PWM pins.
    
    # Setup shield pins of arduino as a PWM output
    
    # the TRI_STATE_ALL signal is controlled by GPIO 214
    # Before setting up any muxing, set pin 214 (TRI_STATE_ALL) to HIGH, 
    # make all of your changes, then set pin 214 to LOW.
    
    # all GPIO pin-mux must be set to 'mode1' to select PWM
    
    # Shield_Pin  |  Linux_GPIO | Output=High | Pullup_enable
    #       IO3         12          251             219
    #       IO5         13          253             221
    #       IO6         182         254             222
    #       IO9         183         257             225
    
    #Export the relevant pins
    echo 251 > /sys/class/gpio/export
    echo 219 > /sys/class/gpio/export
    echo 253 > /sys/class/gpio/export
    echo 221 > /sys/class/gpio/export
    echo 254 > /sys/class/gpio/export
    echo 222 > /sys/class/gpio/export
    echo 257 > /sys/class/gpio/export
    echo 225 > /sys/class/gpio/export
    echo 214 > /sys/class/gpio/export
    
    echo "Exports Done"
    
    # FIRST Shield_pinIO3
    echo low > /sys/class/gpio/gpio214/direction
    echo high > /sys/class/gpio/gpio251/direction
    echo in > /sys/class/gpio/gpio219/direction
    echo mode1 > /sys/kernel/debug/gpio_debug/gpio12/current_pinmux
    echo high > /sys/class/gpio/gpio214/direction
    
    # SECOND Shield_pinIO5
    echo low > /sys/class/gpio/gpio214/direction
    echo high > /sys/class/gpio/gpio253/direction
    echo in > /sys/class/gpio/gpio221/direction
    echo mode1 > /sys/kernel/debug/gpio_debug/gpio13/current_pinmux
    echo high > /sys/class/gpio/gpio214/direction
    
    # THIRD Shield_pinIO6
    echo low > /sys/class/gpio/gpio214/direction
    echo high > /sys/class/gpio/gpio254/direction
    echo in > /sys/class/gpio/gpio222/direction
    echo mode1 > /sys/kernel/debug/gpio_debug/gpio182/current_pinmux
    echo high > /sys/class/gpio/gpio214/direction
    
    # FOURTH Shield_pinIO9
    echo low > /sys/class/gpio/gpio214/direction
    echo high > /sys/class/gpio/gpio257/direction
    echo in > /sys/class/gpio/gpio225/direction
    echo mode1 > /sys/kernel/debug/gpio_debug/gpio183/current_pinmux
    echo high > /sys/class/gpio/gpio214/direction
    
    echo "PWM pins configured"
```

You should be able to use any of the PWM pins as output. For example pin IO6:

```sh
    root@edison:~# echo 2 > /sys/class/pwm/pwmchip0/export
    root@edison:~# echo 2000000 > /sys/class/pwm/pwmchip0/pwm2/duty_cycle
    root@edison:~# echo 1 > /sys/class/pwm/pwmchip0/pwm2/enable
```


