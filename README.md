# ESPHome-Hunter-Flowmeter-Interface
ESP32 Hunter HC075FLOW Irrigation Flow Meter Monitoring

# Background
Purchased a Hunter HC075FLOW Irrigation Flow Meter to monitor my irrigation system for leaks via my Yardian Pro irrigation controller.  The Hunter is a Yardian Pro supported flow sensor.  Water usage tracking isn't a priority at this time.  A master valve controls water to the main irrigation line to prevent any unknown leaking when not watering.  Unable to find documentation if the Yardian will alert if the there is water usage while not watering is the driver to this project.

# Disclaimer
Not responsible for any damages to yourself or your equipment.  You assume all responsibilities for any actions and damages.

# Requirements
1) ESP32 board (I used an Inland ESP-WROOM-32D module - SKU: 027466 Mfr Part#: KS0413)
2) Power Supply
3) Flash ESP32 board to ESPHome (since I'll be using Home Assistant to drive automation rules)
4) Home Assistant with ESPHome add-on installed

# Implementation Steps
1) Install ESPHome on Home Assistant.  In Home Assistant click on Settings/Devices & services, then "Add Integration", find ESPHome Builder and install.
2) Create a New Device using the ESP32 S3 dev model and flash ESP32 board with ESPHome (there are plenty of tutorials on the web on how to to this and multiboard support/options).
3) After flashing ESPHome on the ESP32 you now have Over-The-Air (OTA) capability to upload yaml instructions.
4) Once you have the ESP32 online (shown in the Home Assistant ESPHome Builder screen) you can now upload the code.
5) Install the following yaml code to the ESP32, modifying as necessary.  The ESPHome Device Builder will lead you through the different fields, such as what you want to call it, your WIFI settings, etc..
6) Once the code has been flashed you can now tap the wires going from the Hunter Flow Meter to the Yardian.  The Flow Meter uses 2 wires (blue and white, the red per Hunder is just capped).
7) For my setup I have the following wire confirguration - Hunter blue wire connected to the Yardian Pro S1 right terminal, Hunter white wire connected to the Yardian Pro S1 left terminal, ESP32 GPIO#4 taps into the Hunter blue wire, ESP32 GND taps into the Hunter white wire.
8) Boot up the ESP32 module
9) Home Assistant should have an entity under the settings/Devices & services, the click on the Integration tab, click on the ESPHome card, then the ESP32 device name you configurated above.
10) You will see Under the Sensors section the status of your Hunter Flow Meter and it will show "Irrigation Water Flowing" either "Not Running" or "Running".  You can create Home Assistant automation based on this entity.
