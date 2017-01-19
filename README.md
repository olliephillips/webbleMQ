# webbleMQ
## Web Bluetooth relay for devices supporting Nordic UART service, Puck.js in particular

[Application is running here](https://olliephillips.github.io/webbleMQ/)

My experiments with Web Bluetooth. Designed primarily for use with Puck.js. Currently supports `Relay` and `Console` mode.
It should be possible to add a HTTP gateway and MQTT proxy, but likely a server backend required.

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

## Roadmap
HTTP Proxy. Have Pucks listen for intructions over HTTP

MQTT Gateway. Have Pucks publish to MQTT and subscribe to each other (possibly direct from browser to broker using [this](http://test.mosquitto.org/ws.html) 

## Contributions
Are welcome!

## License 
MIT

