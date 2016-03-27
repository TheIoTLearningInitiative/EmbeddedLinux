Johnny Five
==

> The JavaScript "Tessel 2" Programming Framework

> Johnny-Five is the original JavaScript Robotics programming framework. Released by Bocoup in 2012, Johnny-Five is maintained by a community of passionate software developers and hardware engineers. Over 75 developers have made contributions towards building a robust, extensible and composable ecosystem.

- [Johnny Five Homepage](http://johnny-five.io/)
- [Johnny Five Github](https://github.com/rwaldron/johnny-five)


```sh
    root@edison:~# npm install galileo-io johnny-five
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
```