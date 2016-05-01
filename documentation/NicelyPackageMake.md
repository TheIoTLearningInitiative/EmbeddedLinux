Nicely Package Make
==

> npm makes it easy for JavaScript developers to share and reuse code, and it makes it easy to update the code that you're sharing. [NPM JS Homepage](https://www.npmjs.com/)

- [Npm Getting Started](https://docs.npmjs.com/getting-started/)

## Update Npm

```sh
root@edison:~# npm install npm -g
-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-s
npm@3.8.3 /usr/lib/node_modules/npm
```

## Install Npm Package

```sh
root@edison:~# npm install mqtt -g
-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\-\|/-\|/-\|/-\|/-\|/-\|-\|/-\|/-\|/-\|/-\|/--\|/-\|/-\|/-\|/usr/bin/mqtt_pub -> /usr/lib/nos
/usr/bin/mqtt_sub -> /usr/lib/node_modules/mqtt/bin/sub.js
/usr/bin/mqtt -> /usr/lib/node_modules/mqtt/mqtt.js
mqtt@1.7.4 /usr/lib/node_modules/mqtt
��├��─��─ inherits@2.0.1
��├��─��─ reinterval@1.0.2
��├��─��─ xtend@4.0.1
��├��─��─ minimist@1.2.0
��├��─��─ commist@1.0.0 (leven@1.0.2)
��├��─��─ end-of-stream@1.1.0 (once@1.3.3)
��├��─��─ mqtt-connection@2.1.1 (through2@0.6.5, reduplexer@1.1.0)
��├��─��─ readable-stream@1.0.33 (isarray@0.0.1, string_decoder@0.10.31, core-util-is@1.0.2)
��├��─��─ mqtt-packet@3.4.6 (bl@0.9.5)
��├��─��─ help-me@0.1.0 (pump@1.0.1)
��├��─��─ concat-stream@1.5.1 (typedarray@0.0.6, readable-stream@2.0.6)
��└��─��─ websocket-stream@3.1.0 (ws@1.0.1, through2@2.0.1, duplexify@3.4.3)
root@edison:~# mqtt sub -t 'hello' -h 'test.mosquitto.org' -v &
[2] 653
root@edison:~# mqtt pub -t 'hello' -h 'test.mosquitto.org' -m 'from MQTT.js'
hello coolbjhbjbjkbm m m 
hello from MQTT.js
```
