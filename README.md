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

# Setup under Hass.io
* Open a terminal using either Terminal or VSCode addons
```sh
cd /config/esphome
git clone THIS_REPOSITORY_URI
cp -r Esphome-TTGO-T-Display-Weather/fonts .
cp -r Esphome-TTGO-T-Display-Weather/images .
cp -r Esphome-TTGO-T-Display-Weather/custom_components/ .
echo '<<: !include Esphome-TTGO-T-Display-Weather/ttgo_weather.yaml' > ttgo_tdisplay_weather.yaml
```
* edit `Esphome-TTGO-T-Display-Weather/secrets.yaml` using `nano` (terminal) or `code` (in a vscode shell)
* Within the ESPHome addon UI compile ttgo_tdisplay_weather and flash it onto your TTGO T-Display using [esphomeflasher](https://github.com/esphome/esphome-flasher)
* If wifi is configured correctly, the device should appear as discovered in the `Configuration -> Integrations` screen

# Usage
* ~~Change secrets.yaml file for WiFi, OTA and API credentials.~~
* ~~Apply ESPhome configuration~~
* ~~Register new device in Home Assistant.~~
* ~~Change and include sensors to the Home Assistant.~~

Display custom component based on [musk95](https://github.com/musk95/esphome)
