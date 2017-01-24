# webbleMQ
## Web Bluetooth relay for devices supporting Nordic UART service, Puck.js in particular

[Application is running here](https://olliephillips.github.io/webbleMQ/)

My experiments with Web Bluetooth. Designed primarily for use with Puck.js. Currently supports `Relay`, `Console` and `MQTT (Unannounced)` mode.

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

MQTT mode - currently both unannounced and announced mode do same thing. Each device has a publish and subsribe topic of its own at moment. I've tested both publishing and subsription listeners with two connected devices. The plan for announced mode is that connected pucks announce what topic they are publishing on and listened to.

Note MQTT uses a public MQTT broker - iot.eclipse.org. You could fork the repo and change this to a broker of your choosing, but authentication is not supported.

## Roadmap
- HTTP Proxy. Have Pucks listen for intructions over HTTP, may assume HTTP resource controlled so a CORS policy can be set. This way can do it all on the client - no server.
- MQTT subscribe to each other. Announced mode

## Contributions
Are welcome!

## License 
MIT

