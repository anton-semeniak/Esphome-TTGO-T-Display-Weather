
```
NOTE: The goal of this fork is to work towards fix TTGO Weather so it works w/ ESPHome 1.17-dev and also tidy it up a bit
NOTE #2: Image output is scrambled showing 3 grayscale ghosts instead of proper RGB565 (16-bits per pixel)
NOTE #3: To make this work with ESPHome stock, all pngs must be converted to RGB24 (24-bits per pixel), this increases the size of the binary such that not all images can be used; some weather condition icons have been conflated in ttgo_weather.yaml
```

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
# cp -r Esphome-TTGO-T-Display-Weather/custom_components/ . # Disabled using stock RGB24
echo '<<: !include Esphome-TTGO-T-Display-Weather/ttgo_weather.yaml' > ttgo_tdisplay_weather.yaml
```
* edit `Esphome-TTGO-T-Display-Weather/secrets.yaml` using `nano` (terminal) or `code` (in a vscode shell)
* Within the ESPHome addon UI compile ttgo_tdisplay_weather, download the binary and flash it onto your TTGO T-Display using [esphomeflasher](https://github.com/esphome/esphome-flasher) over a USB-C on a non-hassio machine (hassio does not passthrough USB to ESPHome Addon)
* If wifi is configured correctly, the device should appear as discovered in the `Configuration -> Integrations` screen

## Feeding Weather Data from HASSIO to ESPHome

In the sensors.yaml section of your HA instance you'll need to provide your own values for esphome_current_weather_condition, esphome_current_weather_location, esphome_current_weather_temperature, and esphome_current_weather_temperature_units

Here's an example of this from my configuration, I have a `weather.toronto` entity provided by the Environment Canada integration; your settings would need to come from your configuration's weather entity 

```yaml
- platform: template
  sensors:
    esphome_current_weather_condition:
      friendly_name: 'ESPHome Weather Condition'
      value_template: 
        '{{ states.weather.toronto.state }}'
    esphome_current_weather_location:
      friendly_name: 'ESPHome Weather Location'
      value_template: 
        '{{ states.weather.toronto.attributes.friendly_name }}'
    esphome_current_weather_temperature:
      friendly_name: 'ESPHome Weather Temperature'
      value_template: 
        '{{ states.weather.toronto.attributes.temperature | float }}'
    esphome_current_weather_temperature_units:
      friendly_name: 'ESPHome Weather Temperature Units'
      # TODO: is there a way to get this from HA's system_units setting?
      value_template: 
        '°C'
```

# Usage
* ~~Change secrets.yaml file for WiFi, OTA and API credentials.~~
* ~~Apply ESPhome configuration~~
* ~~Register new device in Home Assistant.~~
* ~~Change and include sensors to the Home Assistant.~~

Display custom component based on [musk95](https://github.com/musk95/esphome)
