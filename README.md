# TTGO T-Display ESPhome Weather
ESPHome configuration to use TTGO T-Display for show curent weather from Home Assistant.

## Demo: 
![Project Picture](https://github.com/anton-semeniak/Esphome-TTGO-T-Display-Weather/blob/master/documents/images/project_weather.jpg)

## Components: 
* [TTGO T-Display](https://github.com/Xinyuan-LilyGO/TTGO-T-Display)

# Home Assistant entities:
* Screen Backlight - switch for backlight 
* left_button - left onboard button on TTGO T-Display, turn off screen 
* right_button - right onboard button on TTGO T-Display, turn on screen

# Usage
* Change secrets.yaml file for WiFi, OTA and API credentials. 
* Apply ESPhome configuration
* Register new device in Home Assistant.
* Change and include sensors to the Home Assistant.


Display custom component based on [musk95](https://github.com/musk95/esphome)
