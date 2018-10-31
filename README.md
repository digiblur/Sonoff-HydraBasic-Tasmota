# Sonoff-HydraBasic-Tasmota
Sonoff Basic Expansion Mod - Capacitive Buttons, PIR Motion Sensors, Tasmota Firmware Rules and more!

Video of the Sonoff Hydra-Basic and Setup - https://www.youtube.com/watch?v=WsatPkC2Hf0

### Parts List
- [Sonoff Basic 6 pack](https://amzn.to/2CRop5O) 
- [or 4 pack](https://amzn.to/2PuXovH)
- [USB FTDI Adapter to Flash the Unit](https://amzn.to/2Rpu9rx)
- [Male Headers](https://amzn.to/2JtX1fB)
- [AM312 PIR Sensor](https://amzn.to/2DhrkpA)
- [Capacitive Touch Button (Red)](https://amzn.to/2PyiglV)
- [or (Green)](https://amzn.to/2DduD0R)
- [Jumper Wires](https://amzn.to/2DcCiMX)
- [Fuses (optional but recommended)](https://amzn.to/2JvHeNy)

DrZzs video on step by step how to flash a Sonoff - https://www.youtube.com/watch?v=KMiP9Ku71To

### Tasmota Rules Commands Used:
```
backlog switchmode1 3;switchmode2 1;switchmode3 1

rule1 on switch2#state=1 do publish cmnd/S20Beta/POWER TOGGLE endon
rule1 on

rule2 on switch3#state=1 do publish HydraBasic/PIR/state YES endon on switch3#state=0 do publish HydraBasic/PIR/state NO endon
rule2 on

rule3 on switch3#state=1 do publish cmnd/TuyaDimTest/Dimmer 75 endon on switch3#state=0 do publish cmnd/TuyaDimTest/Dimmer 25 endon
rule3 on
```
### HomeAssistant Binary Sensor Config YAML
```yaml
- platform: mqtt
    name: "HydraBasic Motion"
    state_topic: "HydraBasic/PIR/state"
    availability_topic: "tele/HydraBasic/LWT"
    qos: 1
    payload_on: "YES"
    payload_off: "NO"
    payload_available: "Online"
    payload_not_available: "Offline"
    retain: false
    device_class: motion
```

### Disclaimer
:warning: **DANGER OF ELECTROCUTION** :warning:

The dimmer uses Mains AC power!  There is a danger of electrocution if not installed properly. If you don't know how to install it, please call an electrician. Remember: _**SAFETY FIRST**_. It is not worth to risk yourself, your family and your home if you don't know exactly what you are doing. Never try to flash, open, or service the dimmer device while it is connected to any power source.

We don't take any responsibility nor liability for using this software nor for the installation or any tips, advice, videos, etc. given by anyone on this site or any other site.
