# Basic WeMos ESP8266/ESP32 Teleinfo Shield (aka TIC)

This shield is used to get French energy meter called Teleinfo data with an [WeMos D1][22] ESP8266 or MH et Live ESP32 Mini Kit.

it has just few minimal features.

**New in v1.1**

- Default RX goes to GPIO13 on ESP8266 and GPIO23 on ESP32
- Reduded WS2812 RGB Led size
- Added visual LED on teleinfo receive signal
- Reverted Signal 3V3 and GND on I2C connector now "standard" looks more like that

**v1.0**

- Teleinfo Reader interface
- I2C Pullups placement
- Footprint for WS2812B RGB LED
- Classic I2C 128x64 OLED or sensors connector
- pad to solder components if needed to

WeMos provide 3 D1, [D1 Mini Lite][20], [D1 Mini][21] or [D1 Mini Pro][22].

**Boards are tested from [PCBs.io][4], all works as expected**

# Detailed Description

Look at the schematics for more informations.

# Schematic  

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-sch.png">

# Boards  

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-top.png" alt="Top" width="40%" height="40%">&nbsp;
<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-bot.png" alt="Bottom" width="40%" height="40%">

You can order the PCB of this board at [PCBs.io][4]. PCBs.io give me some reward when you order my designed boards from their site. This is pretty good, because I can use these rewards to create and design new boards and order them for free, so if you don't care about PCB manufacturer please use PCBs.io.

# Assembled boards

Here boards one connected to WeMos D1 mini (right) and other on MH ET Live ESP32 Mini Kit (left)

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-assembled.png" alt="WeMos Teleinfo Assembled">&nbsp;

# Firmware 

## Tasmota

I strongly suggest using amazing [Tasmota](https://tasmota.github.io/docs/) firmware. 
Please check Teleinfo official tasmota [documentation](https://tasmota.github.io/docs/Teleinfo/)

## Tasmota templates

Use the following templates depending on version of shield and ESP board

### Shield Version 1.1

Teleinfo RX is on GPIO13 for ESP8266 and GPIO23 on ESP32

ESP8266
```
{"NAME":"TICShield","GPIO":[1,1,1,1,640,608,1,1,1,5152,1,1,1,1],"FLAG":0,"BASE":18}
```

ESP32
```
{"NAME":"TICShield32","GPIO":[1,1,1,1,1,1,1,1,1,1,1,1,1,1,1376,1,1,640,608,5632,1,1,0,1,0,0,0,1,1,1,1,1,1,1,1,1],"FLAG":0,"BASE":1}
```

### Shield Version 1.0

Teleinfo RX is on GPIO3 for each board

ESP8266
```
{"NAME":"TICShield","GPIO":[1,1,1,5152,640,608,1,1,1,1,1376,1,1,1],"FLAG":0,"BASE":18}
```

ESP32
```
{"NAME":"TICShield32","GPIO":[1,1,1,5632,1,1,1,1,1,1,1,1,1,1,1376,1,1,640,608,1,1,1,0,1,0,0,0,1,1,1,1,1,1,1,1,1],"FLAG":0,"BASE":1}
```

# License

<img alt="Creative Commons Attribution-NonCommercial 4.0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png">   

This work is licensed under a [Creative Commons Attribution-NonCommercial 4.0 International License](http://creativecommons.org/licenses/by-nc/4.0/)    
If you want to do commercial stuff with this project, please contact [CH2i company](https://ch2i.eu/en#support) so we can organize an simple agreement.

# Misc

See news and other projects on my [blog][2] 
 
[2]: https://hallard.me
[4]: https://PCBs.io/share/8gb6y

[20]: https://wiki.wemos.cc/products:d1:d1_mini_lite
[21]: https://wiki.wemos.cc/products:d1:d1_mini
[22]: d1_mini_prohttps://wiki.wemos.cc/products:d1: