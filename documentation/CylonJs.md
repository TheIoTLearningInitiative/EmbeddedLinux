Cylon JS
==

> JavaScript framework for robotics, physical computing, and the Internet of Things (IoT)

> JavaScript Robotics, By Your Command. Next generation robotics framework with support for 43 different platforms Get Started

- [Cylon.Js](https://cylonjs.com/)
- [Cylon.Js OpenCv](https://npm.taobao.org/package/cylon-opencv)
- [Cylon.Js Intel® Edison](http://cylonjs.com/documentation/platforms/edison/)


## Cylon Intel IoT

> Cylon module for Intel-IoT platforms
> > This repository contains the Cylon adaptor for the Intel Edison and Intel Galileo IoT platforms. It uses the MRAA node module (https://github.com/intel-iot-devkit/mraa)

- [NPM JS Intel IoT](https://www.npmjs.com/package/cylon-intel-iot)

```sh
    root@edison:~# npm install cylon cylon-intel-iot
    -\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/cylon@1.2.0 node_modules/cylon
    
    cylon-intel-iot@0.8.1 node_modules/cylon-intel-iot
    ��├��─��─ cylon-gpio@0.27.0
    ��└��─��─ cylon-i2c@0.23.0
    root@edison:~# vi c.js
```

```js
var Cylon = require('cylon');
 
Cylon.robot({
  connections: {
    edison: { adaptor: 'intel-iot' }
  },
 
  devices: {
    led: { driver: 'led', pin: 13 }
  },
 
  work: function(my) {
    every((1).second(), my.led.toggle);
  }
}).start();
```    

## Cylon OpenCV

```sh
    root@edison:~# npm install cylon cylon-opencv
```