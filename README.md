# pile

## Introduction
The purpose of this document is collecting some generic techniques about how to lower the power consumption of Raspberry pi's. The name 'pile' comes from 'Raspberry Pi, low energy'.

## Optimization of a Raspberry Pi zero W
### Power measurements of a Raspberry Pi zero W

This table represents some measurements of the power consumption of Raspberry Pi zero W connected to WiFi, with no other USB devices, or other peripherals connected. These measurements have been taken from a USB power monitor.

| Power draw with no optimization | Power draw with optimization |
| :-:              		   | :-:                           |
| ~0,583W                          | ~0,500W                       |


### Procedure for power optimization

#### Disable the HDMI port:

Add ```/usr/bin/tvservice -o``` to ```/etc/rc.local```

#### Disable ACT LED:

Add these parameters to ```/boot/config.txt```:
```
# Disable the ACT LED on the Pi Zero.
dtparam=act_led_trigger=none
dtparam=act_led_activelow=on
```

#### Disable Bluetooth:

Add these parameters to ```/boot/config.txt```:
```
# Disable Bluetooth
dtoverlay=pi3-disable-bt
```

Disable Bluetooth services:
```
sudo systemctl disable hciuart.service
sudo systemctl disable bluealsa.service
sudo systemctl disable bluetooth.service
```
