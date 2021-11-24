# Basic WeMos ESP8266/ESP32 Teleinfo Shield

This shield is used to get French energy meter called Teleinfo data with an [WeMos D1][22] ESP8266 or MH et Live ESP32 Mini Kit.

Since price difference between ESP32 and ESP8266 is so small, to be able to use all future features such as Tamota with TLS or Berry language we strongly suggest to use with ESP32. I, the meanwhile no support for ESP8266 will be provided.

**New in v1.1**

- Default RX goes to GPIO13 on ESP8266 and GPIO23 on ESP32
- Reduded WS2812 RGB Led size, 4.3V powered, better brigtness 
- Added visual LED on teleinfo receive signal
- Reverted Signal 3V3 and GND on I2C connector, now "standard" looks more like that
- Replaced 2 GND pins by 5V and 3.3V to get more external power pins

**v1.0**

- Teleinfo Reader interface
- I2C Pullups placement
- Footprint for WS2812B RGB LED
- Classic I2C 128x64 OLED or sensors connector
- pad to solder components if needed to

WeMos provide 3 D1, [D1 Mini Lite][20], [D1 Mini][21] or [D1 Mini Pro][22].

# Detailed Description

Look at the schematics for more informations.

# Schematics  

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-sch.png">

# Boards (V1.1)

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-top.png" alt="Top" width="40%" height="40%">&nbsp;
<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-bot.png" alt="Bottom" width="40%" height="40%">

# Assembled boards (V1.0)

Here boards connected to MH ET Live ESP32 Mini Kit

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-assembled-top.png" width="40%" height="40%" alt="WeMos Teleinfo Assembled TOP">&nbsp;
<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-assembled-bot.png" width="40%" height="40%" alt="WeMos Teleinfo Assembled Bottom">

# Assembling

Nothing complicated, just use headers. I suggest to use the small ones I sell with shield on Tindie, takes less place and you can either fix for life with just one part of the header soldered on both shield and ESP32.

Here boards connected to MH ET Live ESP32 Mini Kit

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-soldering-shield.png">&nbsp;
<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-soldering-shield-esp32.png">


# Firmware 

## Tasmota

I strongly suggest using amazing [Tasmota](https://tasmota.github.io/docs/) firmware. 
Please check Teleinfo official tasmota [documentation](https://tasmota.github.io/docs/Teleinfo/)

## Tasmota templates

Use the following templates depending on version of shield and ESP board

### Shield Version 1.1

Teleinfo RX is on GPIO13 for ESP8266 and GPIO23 on ESP32
RGB led goes to GPIO14 for ESP8266 and GPIO18 on ESP32

ESP8266
```
{"NAME":"Wemos Teleinfo","GPIO":[1,1,1,1,640,608,1,1,1,5152,1,1,1,1],"FLAG":0,"BASE":18}
```

ESP32
```
{"NAME":"Wemos Teleinfo32","GPIO":[1,1,1,1,1,1,1,1,1,1,1,1,1,1,1376,1,1,640,608,5632,1,1,0,1,0,0,0,1,1,1,1,1,1,1,1,1],"FLAG":0,"BASE":1}
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

[20]: https://wiki.wemos.cc/products:d1:d1_mini_lite
[21]: https://wiki.wemos.cc/products:d1:d1_mini
[22]: d1_mini_prohttps://wiki.wemos.cc/products:d1: