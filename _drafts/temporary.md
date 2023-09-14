![Tower Sensor Unit]

SPOT consists of individual tower sensor units grouped around a gateway unit. Each parking spot has a sensing unit that monitors vehicle occupancy. Each sensor unit has a microcontroller with a Bluetooth module to connect to the gateway unit, a Raspberry Pi. We use this architecture to keep sensor units low cost with shorter range Bluetooth and push more expensive responsibilities to the gateway unit. Gateway units can act as a mesh network to connect far away sensor unit groups. A gateway unit close to dedicated Wifi will be responsible for communicating with the cloud hosted backend. Alternatives like GSM mobile connection or satellite Internet could be used instead depending on the cost; a few gateway units can chosen as dedicated gateway nodes to the web application.

![Hardware Block Diagram]

We built an acrylic tower to house our hardware: a Raspberry Pi, external battery, and gateway unit for networking.

![Ultrasonic Sensor]

We used an ultrasonic distance sensor connected to a Raspberry Pi for sensing the proximity of a vehicle. If the sensor was blocked for a certain amount of time and distance, we set the status of the parking spot as occupied.


The Raspberry Pi handles the sensor logic and networking to the gateway unit.  

![Microcontroller wiring]
