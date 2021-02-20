# Klipper_Flsun_Q5
This is my Flsun Q5 config for Klipper. __My Flsun Q5 is not stock__, I changed the extruder driver to TMC2209 and enabled UART mode for all axis and extruder.
Use this config on your own risk!
__Use it on your own risk!__

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
