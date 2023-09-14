---
title: SPOT Hardware
layout: post
date: 2023-09-13 14:00 -800
categories: [hardware]
tags: [SPOT]
image:
  path: /assets/SPOT_Hardware/microcontroller.png
---
![Tower Sensor Unit](/assets/SPOT_Hardware/cad_spot_unit.png)
_CAD Tower Sensor Unit_

SPOT consists of individual tower sensor units grouped around a gateway unit. Each parking spot has a sensing unit that monitors vehicle occupancy. Each sensor unit has a microcontroller with a Bluetooth module to connect to the gateway unit, a Raspberry Pi. We use this architecture to keep sensor units low cost with shorter range Bluetooth and push more expensive responsibilities to the gateway unit. Gateway units can act as a mesh network to connect far away sensor unit groups. A gateway unit close to dedicated Wifi will be responsible for communicating with the cloud hosted backend. Alternatives like GSM mobile connection or satellite Internet could be used instead depending on the cost; a few gateway units can chosen as dedicated gateway nodes to the web application.

![Hardware Block Diagram](/assets/SPOT_Hardware/Hardware Block Diagram.png)
_Hardware Block Diagram_

We built an acrylic tower to house our hardware: microcontroller, external battery, and Raspberry Pi gateway unit for networking.

![Microcontroller wiring](/assets/SPOT_Hardware/mc_wiring.png)
_Wiring Diagram for Microcontroller_

We used an ultrasonic distance sensor connected to a microcontroller for sensing the proximity of a vehicle. If the sensor was blocked for a certain amount of time and distance, we set the status of the parking spot as occupied.

![Ultrasonic Sensor](/assets/SPOT_Hardware/ultrasonic_sensor.png)
_HC-SR04 Ultrasonic Distance Sensor Module_

The microcontroller handles the sensor logic and networking to our Raspberry Pi gateway unit. Gateway units can be chained to a dedicated Wifi router or attached to a GSM connection to communicate with the web application.
