# MQTT Distance Indicator, with on-board LED
![Alt Text](/diagram.png)

## Table of Contents
- [Overview](#overview)
- [Hardware Components](#hardware-components)
- [Software Setup](#software-setup)
- [Usage](#usage)
- [Useful Links](#useful-links)
  
## Overview
The project demonstrates the use of MQTT, where a publisher (ESP8266) is physically connected to an ultrasound sensor, while the subscriber (ESP8266) has an on-board LED light. The Raspberry Pi 4 acts as the MQTT broker, facilitating wireless communication between the publisher and subscriber.

The ultrasonic sensor measures the distance to an object, and based on the measured distance, it publishes messages to the MQTT broker (Raspberry Pi) using the topic "esp/distance". The subscriber ESP8266 board subscribes to the "esp/distance" topic and receives these distance messages. If the distance received is less than 20cm, the subscriber ESP8266 turns on its on-board LED. If the distance is greater than or equal to 20cm, the LED turns off.

The project can be applied to a range of use cases, such as security systems (indicating intrusion), object detection/avoidance, proximity sensing for machinery and environmental monitoring. Note, it is important to consider the limitations of components when implementing the project to your specific use case. 

## Hardware Components
- 1x Raspberry Pi 4
- 2x ESP8266 (NodeMCU)
- 1x Ultrasonic Sensor (HC-SR04)
- 1x Breadboard
- 4x jumper wires for connection

## Software Setup
1. Connect ultrasonic sensor to publisher ESP8266 board
2. Connect LED to subscriber ESP8266 board, if on-board light unavailable
3. Set up Rasbperry Pi as broker, such as flashing Pi with Ubuntu Server and configure an MQTT broker software, I used Eclipse Mosquitto
4. Write and upload code to the respective ESP8266 boards, I used the Arduino IDE
5. Ensure that credentials for the Raspberry Pi (such as IP address, username, password etc.) is configured, and is updated in code written
6. Turn on the Raspberry Pi and ESP8266 boards
   
## Usage
1. The publisher ESP8266 board reads the distance from the ultrasonic sensor and publishes the distance value to the "esp/distance" topic on the MQTT broker (Raspberry Pi).
2. The subscriber ESP8266 board subscribes to the "esp/distance" topic and receives the distance messages.
3. If the distance received is less than 20cm, the subscriber ESP8266 turns on the LED. If the distance is greater than or equal to 20cm, the LED turns off.

*Ensure the MQTT broker (Raspberry Pi) is running and accessible to both publisher and subscriber ESP8266 boards for successful communication.*

## Useful Links
- [NodeMCU with HC-SR04](https://randomnerdtutorials.com/esp8266-nodemcu-hc-sr04-ultrasonic-arduino/)
- [Install Broker on Pi](https://randomnerdtutorials.com/how-to-install-mosquitto-broker-on-raspberry-pi/)
- [Testing Broker and Client on Pi](https://randomnerdtutorials.com/testing-mosquitto-broker-and-client-on-raspbbery-pi/)
- [Basic Blink LED](https://www.instructables.com/NodeMCU-Basic-Project-Blink-a-LED/)

- [Download Arduino IDE](https://www.arduino.cc/en/software)
- [Ubuntu](https://ubuntu.com/download/server)
- [ECLIPSE Mosquitto](https://mosquitto.org/)
- [Install Raspberry Pi Imager](https://www.raspberrypi.com/software/)




