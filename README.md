# Domoticz GoodWe Modbus UDP plugin

A Domoticz plugin that connects to GoodWe inverters over LAN or WLAN via UDP that supports Modbus.

The plugin uses a goodwe library from https://pypi.org/project/goodwe/ (https://github.com/marcelblijleven/goodwe) to communicate with the inverter.

## Features
* Auto detect singlephase or 3 phase model
* Port number is fixed at 8899
* Supports inverter shutdown and (temporary) disconnect
* Reset power sensors to 0 if state is wait mode
* Auto detects the inverter family
* Setting the inverter family manually speeds up the connection time
* Change output limit from 10-100% (NS Only)

## Requirements
For XS inverter is firmware 1.xx.14 or higher required. Other GoodWe inverter model series (ET, EH, BT, BH, ES, EM, BP, DT, MS, NS) might work as well. This software is currently in a beta stage.

First try adjusting the Power Limit using the SolarGo app. If that doesn't work, your firmware is probably too old.
Request a firmware update: https://goodwetechnology.zendesk.com/hc/en-gb/requests/new

## Download and install requirements:


### Linux
Prepare Domoticz for Virtual Environment:

``` shell
cd
mkdir domoticz_venv
sudo nano /etc/init.d/domoticz.sh

* Note: look for the following line:
export PYTHONPATH=/home/pi/domoticz_venv:$PYTHONPATH

sudo systemctl daemon-reload
sudo service domoticz restart
```

Install the Goodwe Modbus UDP plugin:

``` shell
cd domoticz/plugins
git clone https://github.com/azsystem/domoticz-goodwe-modbusudp-plugin.git
```
* Note: Some Domoticz installation have other plugin paths (such as `domoticz/userdata/plugins`).

Install required dependencies:
``` shell
cd
cd domoticz/plugins/domoticz-goodwe-modbusudp-plugin
python3 -m pip install -r requirements.txt --upgrade -t /home/pi/domoticz_venv
```

### Windows
not supported by azsystem

## After installation
Restart your Domoticz, and add the hardware via Setup->Hardware and select Type: "GoodWe ModbusUDP", enter a name and IP address and optionally select the inverter family for a faster connection time. Set the interval to your needs and then press the "Add" button.
Then all of the inverter sensors should now be visible in "Utility" and "Temperature".

## Inverters reported to work with this plugin
* GW1000-XS Wifi
* GW3600T-DS Wifi
* GW3000D-NS
* GW3600D-NS
* GW10K-ET
