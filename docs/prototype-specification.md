#🌺 Smart flower pot - Prototype 🌺#

Created by Attila Kiss, Daniel Tombor
Created on Jun 19., 2017

##Table of contents##
1. [Outline][]
    1. [Purpose of this document][]
    2. [Purpose of the project][]
2. [Hardware specification][]
    1. [Functionalities][]
    2. [Components][]
    3. [Behaviors][]
3. [Software specification][]
    1. [Serverside][]
    2. [Mobile client][]
4. [Schedule][]
5. [Further development opportunities][]
    1. [First production version - v1][]
        1. [Hardware][]
        2. [Server][]
        3. [Client][]
    2. [Enhanced version - v2][]

##Outline##

###Purpose of this document###

This document is the functional specification of the project.
It is a guide for the development which we can refer to.
It has to cointain the main purposes, use-cases and functionalities of the components.

###Purpose of the project###

The main purpose of the project is as simple as to keep developers' flowers alive.
The smart flowerpot wets the potting soil when it's needed and notifies the user when to refil the tank of the pot.
The main goal is reducing the time consumption of taking care of a flower.
Some other extra features are 
- wetting the soil by a smart algorithm using multiple sensors
- display current status & statistics in a mobile app connected to the hardware
- IoT capabilites

##Hardware specification##

The prototype is not design by professional product and electric engineers. It's a proof-of-concept with out-of-the-box components, like a Raspberry Pi with some extra accessories (sensors).

###Functionalities###

The functionality of the hardware is quite simple. 
Observing it from a high abstraction level, it should be able to do only 3 things:
* wetting the flower automatically
* notifing the user to fill the water tank
* share sensors' data with the connected devices

###Components###

To achive the desired functionalites the hardware has to contain the following components:
* RaspberryPi Zero W
    * bluetooth capability - connecting to a mobile client
    * humidity sensor - for the soil
    * water sensor - for water level in the tank
    * electronic water tap - which leaks water from the tank when its needed
    * temperature & light sensor - for statistics
    * 5 leds & a speaker - notify user to fill water tank
* a battery - power source for RaspberryPi
* *a huge* water tank with a water tap

###Behaviors###

The hardware needs power supply to operate, which should be a battery in order to avoid cabels and make the flowerpot more portable. Once a charged battery is installed, the flowerpot should just work without having to switch it on. This means no buttons are needed at all.
When the flowerpot is operating, leds should indicate the water level in the tank. When every led emits white light, the tank is full, and when its getting empty, leds start to goes out. If the water reaches a critical level in the tank, the hardware should beep in every 8 hours and when its (nearly) empty it should beep in every 2 hours.
The first prototype wont have a complex wetting algorythm, it will only check the humidity of the potting soil.
A read-only bluetooth interface is going to be available as well to which a smartphone can connect. The bluetooth interface shoud provide data about the battery status, the current humidity of the soil, the water level and the temperature.

##Software specification##

The project contains both server and client side applications.

###Serverside###

The purpose of the server side application is storing data to make it avaiablre from multiple devices of the user.
The prototype hardware will not communicate to the server directly, since it's not a requirement to have WiFi capabilities.
Only the mobile application will cominicate to the server, which autenticates the user and stores data for later statistics.

Functionalities of the serverside:
* User handling (register, login, logout, forget password, delete account)
* Store data for authenticated user:
    * User related info (name, email, geolocation)
    * Type of the flower planted in the pot
    * Daily sensor data (humidity, temperature, light, water consumption)

###Mobile Client###

Functinalities of the mobile client:
* User management
* Connecting to hardware (and read data) by bluetooth
* Wire data to user & sync to the server

##Schedule##

**Development**
* Jun 22. - Specification
* Jun 29. - Application wireframe
* Jul 3. - API specification
* Jul 3. - Jul 30. - Developer is on holiday
* Aug 12. - Server side
* Aug 30. - Hardware development
* Sept 10. - iOS App

**Collecting background knowledge**
* ???

##Further development opportunities##

###First production version - v1###

Hardware should handle multiple users & connections (prepare for family usage).
A great function would be a soical platform where everybody could be share their experiences/statistics/pictures of their flowers.
So a user can search for a type of flower and see what conditions are good for them to live in.
Or vicaversa, user can search for a condition and the application suggests flowers to buy.
(This will be reffered to as 'social features' at platform improvements below)

####Hardware####

By extending the connectivity by WiFi, the hardware would be able to connect to the server directly. 
By this it could sync the sensors' data without mobile client, and the user could check the flowerpot from remote.

####Server####

* In the production version the server should handle Social login as well (Facebook, Twitter, Google).
* Social features

####Client####

* Client should be list & reach remote pots.
* Social features

###Enhanced version - v2###

Fine tuning the wetting system, tailored for the current conditions (flower type, daylight length & power of the light, temperature, humidity, water consumption).
This automated tailored wetting should be reached by processing the collected statistics and analized with machine learning.

🌺 🌺 🌺