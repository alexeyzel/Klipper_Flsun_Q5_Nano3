# Klipper_Flsun_Q5
This is my Flsun Q5 config for Klipper. __My Flsun Q5 is not stock__, it has:
- built in Raspberry Pi 3 runnin Klipper inside with 5 inch 800*480 IPS TFT screen 
- Makerbase MKS Robin Nano v3 board
- TMC2209 drivers on all axes and extruder 
- Trianglelab TCHC TD6 PT1000 Hotend
- Trianglelab Dual Drive Extruder (BMG clone)
- Trianglelab Titanium alloy Bi-Metal Heatbreak
- Trianglelab hotend PTFE Tube
- Noctua fan for board cooling and Sunon fan for hotend
- LED lights driven by Wemos D1 mini board with ESPHome (Home Assistant)


  
__Use it on your own risk!__
For stock Flsun Q5 it is advised to change microstep setting to 16 and other changes that I might not know about may be necessary.

## What to check:
### 1. Remove my auto-config values

Delete everything starting from  
```
<---------------------- SAVE_CONFIG ----------------------> 
```
line and bellow.
Those are my configuration results for z-offset, delta calibration and bed leveling.

### 2. Enable default values

In [stepper_a] section:
```
#position_endstop: 200
#arm_length: 215.0
```

In [probe] section:
```
#z_offset: 19.586 
```
Careful with probe offset value, it can cause crashing hotend into the hotbed.

In [printer] section:
```
#delta_radius: 106.58
```
This is my value i got from Marlin Delta calibration, your may be 105, but it will be auto-calibrated.

### 3. Disable input shaper

Comment out this section
```
[input_shaper]
shaper_freq_x: 40.8
shaper_type_x: 2hump_ei
shaper_freq_y: 40.0
shaper_type_y: 2hump_ei
```
You have to do your own calibration of these values, u used ADXL345 accelerometer to get those.
You can find my accelerometer mount design for Flsun Q5 here: https://www.thingiverse.com/thing:4765232

### 4. Do your own auto-calibration

- perform [config checks](https://github.com/KevinOConnor/klipper/blob/master/docs/Config_checks.md)
- [calibrate probe offsets and z offset](https://github.com/KevinOConnor/klipper/blob/master/docs/Probe_Calibrate.md)
- perform [delta calibration](https://github.com/KevinOConnor/klipper/blob/master/docs/Delta_Calibrate.md)
- create [bed mesh](https://github.com/KevinOConnor/klipper/blob/master/docs/Bed_Mesh.md)
- calibrate input_shaper and pressure advance
- calibrate hotend and bed PID
