# Johnny Five

> The JavaScript "Tessel 2" Programming Framework

> Johnny-Five is the original JavaScript Robotics programming framework. Released by Bocoup in 2012, Johnny-Five is maintained by a community of passionate software developers and hardware engineers. Over 75 developers have made contributions towards building a robust, extensible and composable ecosystem.

- [Johnny Five Homepage](http://johnny-five.io/)
- [Johnny Five Github](https://github.com/rwaldron/johnny-five)
- [Johnny Five IO Plugins](https://github.com/rwaldron/johnny-five#io-plugins)
- [Intel Galileo & Intel Edison IO Plugin for Johnny-Five](https://github.com/rwaldron/galileo-io/)

## galileo-io

> Intel Galileo IO Plugin for Johnny-Five JavaScript Robotics

- [NPM JS Galileo-Io](https://www.npmjs.com/package/galileo-io)

```sh
    root@edison:~# npm install galileo-io johnny-five
    -\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\-\|/-\|/--\|/-\|
    > galileo-io@0.9.4 postinstall /home/root/node_modules/galileo-io
    > node scripts/postinstall
    ...
    ��├��─��─ es6-shim@0.35.0
    ��└��─��─ serialport@2.0.6 (bindings@1.2.1, sf@0.1.7, async@0.9.0, debug@2.2.0, optimist@0.6.1, nan@2.0.9)
    root@edison:~# vi jf.js
```

```js
var five = require("johnny-five");
var Edison = require("galileo-io");
var board = new five.Board({
  io: new Edison()
});
 
board.on("ready", function() {
  var led = new five.Led(13);
  led.blink(500);
});
```

```sh
    root@edison:~# node jf.js
    1459102398059 Device(s) Intel Edison  
    1459102398074 Connected Intel Edison  
    1459102398097 Repl Initialized  
    >> 
    ^C
    >> 1459102426530 Board Closing. 
    root@edison:~# 
```

## edison-io

> Intel Edison IO Plugin for Johnny-Five JavaScript Robotics

Requirements:

- Grove Button @ D4

```sh
    root@edison:~/trash# npm install johnny-five edison-io
    -\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-
    ...
    npm WARN engine edison-io@0.9.4: wanted: {"node":"latest"} (current: {"node":"0.10.38",")
    edison-io@0.9.4 ../node_modules/edison-io
    root@edison:~/trash# vi edi.js
```

```js
var five = require("johnny-five");
var Edison = require("edison-io");
var board = new five.Board({
  io: new Edison()
});

board.on("ready", function() {

  var button = new five.Button(8);
  var led = new five.Led(13);

  button.on("press", function() {
    led.on();
  });

  button.on("release", function() {
    led.off();
  });
});
```

```sh
    root@edison:~/trash# node edi.js
    1459107445851 Device(s) Intel Edison  
    1459107445867 Connected Intel Edison  
    1459107445892 Repl Initialized  
    >> 
```

Push Grove Button and see Board Led

```sh
    ^C
    (^C again to quit)
    >> 
    1459107452651 Board Closing.  
```

## LCD I2C

Requirements:

- Grove LCD RGB Backlight @ I2C

```js
var five = require("johnny-five");
var Edison = require("edison-io");
var board = new five.Board({
  io: new Edison()
});

board.on("ready", function() {

  var lcd = new five.LCD({
    controller: "JHD1313M1"
  });

  lcd.useChar("heart");
  lcd.cursor(0, 0).print("hello :heart:");
  lcd.blink();
  lcd.cursor(1, 0).print("Blinking? ");
});
```