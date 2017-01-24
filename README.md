# webbleMQ
## Web Bluetooth relay for devices supporting Nordic UART service, Puck.js in particular

[Application is running here](https://olliephillips.github.io/webbleMQ/)

My experiments with Web Bluetooth. Designed primarily for use with Puck.js. Currently supports `Relay`, `Console` and two `MQTT` modes.

Relay mode - One device as master can control several devices as slave. For example turning LEDs on and off with a program running on master device such as this:

```
var prog1 = "LED1.set();LED2.set();LED3.set();\n";
var prog2 = "LED1.reset();LED2.reset();LED3.reset();\n";
var on = false;
setInterval(function(){
  var prog = prog2;
  if(!on){prog = prog1;}
  Bluetooth.write(prog);
  on = !on;
}, 5000);
```

Console mode - All devices listen to input from the console. Programtically control several devices at once.

MQTT "unannounced" - Each device has own publish and subscribe topic. 

MQTT "announced" - Each device has own publish and subscribe topic. Device advertises its presence, both the topic it is publishing on and subscribed to, every 10 seconds on a third topic: `/wmq/playing`. This topic is used by all connected devices in MQTT announced mode. 

Note both MQTT modes uses a public MQTT broker - iot.eclipse.org. In unannounced mode, though hard to guess, the data is still public. In announced mode, devices actively advertise their presence. You can fork the repo and change the broker to one of your choosing, but authentication is not supported.

## Roadmap
- HTTP Proxy. Have Pucks listen for intructions over HTTP, may assume HTTP resource controlled so a CORS policy can be set. This way can do it all on the client - no server.
- MQTT subscribe to each other.

## Contributions
Are welcome!

## License 
MIT

