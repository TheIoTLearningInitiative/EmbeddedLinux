# NodeJS

> In software development, Node.js is an open-source, cross-platform runtime environment for developing server-side Web applications. Although Node.js is not a JavaScript framework, many of its basic modules are written in JavaScript, and developers can write new modules in JavaScript. The runtime environment interprets JavaScript using Google's V8 JavaScript engine. [Wikipedia](https://en.wikipedia.org/wiki/Node.js)

- [Principles of Writing Consistent, Idiomatic JavaScript](https://github.com/rwaldron/idiomatic.js)
- [A set of node-red nodes for connecting to johnny-five IO Plugins](https://github.com/monteslu/node-red-contrib-gpio)
- [Intel Galileo & Intel Edison IO Plugin for Johnny-Five](https://github.com/rwaldron/galileo-io/)
- [Debug Node js remotely on Intel Edison with Jetbrains Idea](https://m2aglabs.com/2015/11/04/debug-node-js-remotely-on-intel-edison-with-jetbrains-idea/)
- [Arduino Experimenter's Guide for NodeJS](http://node-ardx.org/)
- [JavaScript: The Perfect Language for the Internet of Things (IoT)](https://blog.jscrambler.com/javascript-the-perfect-language-for-the-internet-of-things-iot/)
- [Node.Js for Embedded Systems](http://embeddednodejs.com/chapters.html)
- [Programming the Internet of Things with Node.Js](http://cdn.oreillystatic.com/en/assets/1/event/127/Programming%20the%20Internet%20of%20Things%20with%20Node_js%20and%20HTML5%20Presentation.pdf)
- [Fast, reliable, and secure dependency management](https://github.com/yarnpkg/yarn)

## Mraa

```sh
    root@edison:~# nano mr.js
```

```js
var mraa = require('mraa');
var pinDigital = new mraa.Gpio(13);

console.log('MRAA Version: ' + m.getVersion());

pinDigital.dir(mraa.DIR_OUT);
pinDigital.write(1);
```

```sh
    root@edison:~# node mr.js
```

## Nodejs, Socket.io and Intel Edison

```sh
    root@edison:~# npm install -g express socket.io
    -\|/-\|/-\|/-\-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/--\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\s
    ��├��─��─ escape-html@1.0.3
    ��├��─��─ range-parser@1.0.3
    ...
    ��├��─��─ socket.io-adapter@0.4.0 (socket.io-parser@2.2.2)
    ��└��─��─ socket.io-client@1.4.5 (to-array@0.1.4, indexof@0.0.1, component-
    root@edison:~# git clone https://github.com/m2aglabs/socket.io-demo.git
    Cloning into 'socket.io-demo'...
    remote: Counting objects: 22, done.
    remote: Total 22 (delta 0), reused 0 (delta 0), pack-reused 22
    Unpacking objects: 100% (22/22), done.
    Checking connectivity... done.
    root@edison:~# cd socket.io-demo/
    root@edison:~/socket.io-demo# ls
    LICENSE.md        icon.png          package.json
    README.md         index.html        thermo_demo.xdk
    app.js            js                thermo_demo.xdke
    root@edison:~/socket.io-demo# node app.js 
    MRAA Version: v0.8.0
```

In a web browser go to http://192.168.1.65:8085/

## Using a Rotary Encoder on Intel Edison, XDK

- [Rotary Encoder Demo](https://github.com/m2aglabs/rotary_encoder_demo)

Requirements

- Grove Rotary Encoders on D2
- Grove Button on D4

```sh
itot@edison:~# git clone https://github.com/m2aglabs/rotary_encoder_demo.git
Cloning into 'rotary_encoder_demo'...
remote: Counting objects: 25, done.
remote: Total 25 (delta 0), reused 0 (delta 0), pack-reused 25
Unpacking objects: 100% (25/25), done.
Checking connectivity... done.
root@edison:~/trash# cd rotary_encoder_demo/
root@edison:~/trash/rotary_encoder_demo# ls
LICENSE.md        index.html        rotary_demo.xdk
README.md         js                rotary_demo.xdke
icon.png          package.json      server.js
root@edison:~/rotary_encoder_demo# node server.js 
MRAA Version: v0.8.0
```

In a web browser go to http://192.168.1.65:8085/

## NodeJS Modules

```sh
root@edison:~# ls /usr/lib/node_modules/
iotkit                    jsupm_grovevdiv           jsupm_mpl3115a2
iotkit-agent              jsupm_grovewater          jsupm_mpr121
iotkit-comm               jsupm_grovewfs            jsupm_mpu9150
jsupm_a110x               jsupm_guvas12d            jsupm_mq303a
jsupm_ad8232              jsupm_h3lis331dl          jsupm_my9221
jsupm_adafruitms1438      jsupm_hcsr04              jsupm_nrf24l01
jsupm_adafruitss          jsupm_hm11                jsupm_nrf8001
jsupm_adc121c021          jsupm_hmc5883l            jsupm_nunchuck
jsupm_adis16448           jsupm_hmtrp               jsupm_otp538u
jsupm_adxl335             jsupm_hp20x               jsupm_pca9685
jsupm_adxl345             jsupm_ht9170              jsupm_pn532
jsupm_am2315              jsupm_htu21d              jsupm_ppd42ns
jsupm_apds9002            jsupm_hx711               jsupm_pulsensor
jsupm_at42qt1070          jsupm_i2clcd              jsupm_rfr359f
jsupm_biss0001            jsupm_ina132              jsupm_rgbringcoder
jsupm_bmpx8x              jsupm_isd1820             jsupm_rotaryencoder
jsupm_buzzer              jsupm_itg3200             jsupm_rpr220
jsupm_cjq4435             jsupm_joystick12          jsupm_servo
jsupm_ds1307              jsupm_l298                jsupm_si114x
jsupm_ecs1030             jsupm_ldt0028             jsupm_sm130
jsupm_enc03r              jsupm_lm35                jsupm_st7735
jsupm_flex                jsupm_lol                 jsupm_stepmotor
jsupm_gas                 jsupm_loudness            jsupm_sx6119
jsupm_gp2y0a              jsupm_lpd8806             jsupm_ta12200
jsupm_grove               jsupm_lsm303              jsupm_tcs3414cs
jsupm_grovecircularled    jsupm_lsm9ds0             jsupm_th02
jsupm_grovecollision      jsupm_m24lr64e            jsupm_tm1637
jsupm_groveehr            jsupm_max31723            jsupm_tsl2561
jsupm_groveeldriver       jsupm_max31855            jsupm_ttp223
jsupm_groveelectromagnet  jsupm_max44000            jsupm_ublox6
jsupm_groveemg            jsupm_max5487             jsupm_uln200xa
jsupm_grovegprs           jsupm_maxds3231m          jsupm_waterlevel
jsupm_grovegsr            jsupm_maxsonarez          jsupm_wheelencoder
jsupm_grovelinefinder     jsupm_mg811               jsupm_wt5001
jsupm_grovemd             jsupm_mhz16               jsupm_yg1006
jsupm_grovemoisture       jsupm_mic                 jsupm_zfm20
jsupm_groveo2             jsupm_mlx90614            mraa
jsupm_grovescam           jsupm_mma7455             npm
jsupm_grovespeaker        jsupm_mma7660
root@edison:~# 
```

## NodeJS Edison-Cli

```sh
xe1gyq@jessie:~$ sudo npm install -g edison-cli
npm WARN deprecated graceful-fs@3.0.8: graceful-fs v3.0.0 and before will fail on node releases >= v6.0. Please update to graceful-fs@^4.0.0 as soon as possible. Use 'npm ls graceful-fs' to find it in the tree.
 
> ws@0.4.32 install /usr/local/lib/node_modules/edison-cli/node_modules/ws
> (node-gyp rebuild 2> builderror.log) || (exit 0)

make: Entering directory '/usr/local/lib/node_modules/edison-cli/node_modules/ws/build'
  CXX(target) Release/obj.target/bufferutil/src/bufferutil.o
  SOLINK_MODULE(target) Release/obj.target/bufferutil.node
  SOLINK_MODULE(target) Release/obj.target/bufferutil.node: Finished
  COPY Release/bufferutil.node
  CXX(target) Release/obj.target/validation/src/validation.o
  SOLINK_MODULE(target) Release/obj.target/validation.node
  SOLINK_MODULE(target) Release/obj.target/validation.node: Finished
  COPY Release/validation.node
make: Leaving directory '/usr/local/lib/node_modules/edison-cli/node_modules/ws/build'
/usr/local/bin/edison-cli -> /usr/local/lib/node_modules/edison-cli/bin/edison-cli
edison-cli@2.0.0 /usr/local/lib/node_modules/edison-cli
├── commander@2.9.0 (graceful-readlink@1.0.1)
├── temporary@0.0.8 (package@1.0.1)
├── mdns-js@0.1.5 (debug@0.8.1)
├── fstream@1.0.8 (inherits@2.0.1, graceful-fs@4.1.3, mkdirp@0.5.1, rimraf@2.5.2)
├── tar-edison@0.1.16 (inherits@1.0.2, block-stream@0.0.8, fstream@0.1.31)
└── ws@0.4.32 (tinycolor@0.0.1, options@0.0.6, commander@2.1.0, nan@1.0.0)
xe1gyq@jessie:~$ edison-cli list
Edison Devices Found: 2
1 - 192.168.1.70
2 - 192.168.1.70
xe1gyq@jessie:~$ 
```