---
layout: post
title: Writing a Ground Station interface for CUInspace
date: 2018-02-01
categories: [Robotics]
icon: icon-unity
---

I have recently joined [CUInSpace](https://www.facebook.com/pg/cuinspace/about/), Carleton University's rocketry team. The team's objective is to build a rocket that will fly a 8.8 pound payload to 10,000 feet. The engine team plans on designing a multistage rocket that implements a hybrid fuel system. More information regarding the competition may be found at [IREC](http://www.soundingrocket.org). The competition is annually held at [Spaceport America](https://spaceportamerica.com)
in New Mexico and features over 600 students from 6 continents. 

I have joined the team building a ground control station. Our goal is to design an interface that receives information from the radio systems on-board the rocket and displays this in a user-friendly manner.

The current working idea is to create a graphical rendering of the rocket's flight path in real-time. This will involve generating a physics simulation using the sensor data provided by the radio systems. Furthermore, there will be a properties window that displays data from each of the on-board sensors. Near the bottom there will also be a debug console that will display information that cannot easily be digested in a graphical manner. This may include error messages and raw packet data.

<img src="{{ site.img_path }}/cuinspace_ground_station/prototype.png" alt="Prototype of the ground station interface"  style="width:100%; height:100%;">

Possible improvements to this design include adding interfaces for the various fail-safes available. Also, adding control elements for the engine, sensors and reset mechanisms for on-board systems may be implemented in the future.

The groundstation software will be designed in a server-client model. There are a few reasons for choosing this model. First of all, it is imperative that the GUI be decoupled from the data processing. In particular, although we are hoping to have access to a high performance graphics machine on site, it is likely we will have to run the software on consumer hardware. If we are able to modularize the processing elements we are then able to run the server on one machine, and attach a GUI client on another in order to make maximal use of the available computing resources. 

The server will be written in [NodeJS](https://nodejs.org/en/) because it is trivial to design an asynchronous server based on Websockets. Also, libraries exist for accessing the serial port and decoding the Xbee signals API. This greatly speeds up development while maintaining an agile process. 

More details will follow once work has begun on a demo.

Image Sources:
- https://pixabay.com/en/rocket-spaceship-launch-space-528071/
- https://shop.spreadshirt.com/vexworldwide/3d+gizmo-A10231276
