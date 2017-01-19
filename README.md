# webbleMQ
## Web Bluetooth relay for devices supporting Nordic UART service, Puck.js in particular

My experiments with Web Bluetooth. Designed primarily for use with Puck.js, supports currently supports `Relay` and `Console` mode.
It should be possible to add a HTTP gateway and MQTT proxy, but likely a server backend required.

Relay mode - One device as master can control several devices as slave. For example turning LEDs on

Console mode - All devices listen to input from the console. Programtically control several devices at one

## Roadmap
HTTP Proxy. Have Pucks listen for intructions over HTTP
MQTT Gateway. Have Pucks publish to MQTT and subscribe to each other (possibly direct from browser to broker using [this](http://test.mosquitto.org/ws.html) 

## Contributions
Are welcome!

## License 
MIT

