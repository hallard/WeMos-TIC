# WeMos Teleinfo ESP8266/ESP32 Shield

This shield is used to get French energy meter called Teleinfo data with an [WeMos D1][22] ESP8266 or [MH et Live ESP32 Mini Kit][23]. Take care the check wiring, because there is a lot of clone boards so please be sure to order the correct ones. If you want to be sure you can add it as option when you order this shield on [tindie][24], in bonus it will be flashed with tasmota teleinfo firmware.

Since price difference between ESP32 and ESP8266 boards is so small, to be able to use all future features such as Tamota with TLS, [Berry language](https://tasmota.github.io/docs/Berry/) or even tasmota new applications, I strongly suggest to use with ESP32 only. In the meanwhilen due to lack of ressources and Serial for debug (when using teleinfo), **no support for ESP8266 will be provided**. Of course it works fine, but I spent too much time each time to reproduce and track issues so I let it behind for now to focus on ESP32.  

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

WeMos provide three types of D1, [D1 Mini Lite][20], [D1 Mini][21] or [D1 Mini Pro][22] and also new [MH et Live ESP32 Mini Kit][23]

# Detailed Description

Look at the schematics for more informations.

Wiring on the WeMos Teleinfo shield

| Pin Function | ESP32   | ESP8266 |
|  :---        |  :---:  |  :---:  |
| Téléinfo Rx  |  GPIO32 | GPIO13  |
| RGB Led      |  GPIO18 | GPIO14  |
| I2C SDA      |  GPIO21 | GPIO4   |
| I2C SDL      |  GPIO22 | GPIO5   |
| OnBoard LED  |  GPIO22 | GPIO16  |

You can change default Rx to `GPIO3` with solder pad `tic-rx`, but in this case, you need to cut the default trace and put solder between center pad and `IO3`, It's for advanced users, do it only if you need it and if you know what you are doing.

Default wiring on [ESP8266 Mini D1][21] or [ESP32 Mini Dev board][23]

| Pin Function   | ESP32   | ESP8266 |
|  :---          |  :---:  |  :---:  |
| OnBoard LED    |  GPIO2 | GPIO16  |
| OnBoard Button |  GPIO0 | GPIO16  |


# Schematics  

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-sch.png">

# Boards (V1.1)

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-top.png" alt="Top" width="40%" height="40%">&nbsp;
<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-bot.png" alt="Bottom" width="40%" height="40%">

# Assembled boards

Here boards connected to Default wiring on [ESP32 Mini Dev board][23]

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-assembled-top.png" width="40%" height="40%" alt="WeMos Teleinfo Assembled TOP">&nbsp;
<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-assembled-bot.png" width="40%" height="40%" alt="WeMos Teleinfo Assembled Bottom">

# Assembling

Nothing complicated, just use headers. I suggest to use the small ones I sell with shield on Tindie, takes less place and you can either fix for life with just one part of the header soldered on both shield and ESP32.

Here boards connected to [ESP32 Mini Dev board][23]

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-soldering-shield.png" width="40%" height="40%">&nbsp;
<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-soldering-esp32.png" width="40%" height="40%">


# Firmware 

## Tasmota

I strongly suggest using amazing [Tasmota](https://tasmota.github.io/docs/) firmware. 

Please check Teleinfo official tasmota [documentation](https://tasmota.github.io/docs/Teleinfo/)

### Berry (ESP32 Only)

Soon you'll be able to personalize code with some examples with [Berry language](https://tasmota.github.io/docs/Berry/). Check out some berry sample code [here](https://github.com/arendst/Tasmota/blob/development/tasmota/berry/examples/)


For example driving RGB Led function of Power consumption

```berry
#-
# example of using Berry script to change the led color
# accordingly to power consumption
# using Denky or WeMos Teleinfo (French Teleinfo reader)
-#

#- define the global symbol for reference -#
runcolor = nil

def runcolor()
  var max_contrat = 30 # contrat 30A
  var i = energy.current
  #print(i)
  var red = tasmota.scale_uint(int(i), 0, max_contrat, 0, 255)
  var green = 255 - red
  var channels = [red, green, 0]
  light.set({"channels":channels, "bri":64, "power":true})
  tasmota.set_timer(2000, runcolor)
end

#- run animation -#
runcolor()
```


## Tasmota templates

Use the following templates depending on version of shield and ESP board

### Shield Version 1.1


#### ESP8266
```
{"NAME":"Wemos Teleinfo","GPIO":[1,1,1,1,640,608,1,1,1,5152,1,1,1,1],"FLAG":0,"BASE":18}
```

#### ESP32
```
{"NAME":"Wemos Teleinfo32","GPIO":[1,1,1,1,1,1,1,1,1,1,1,1,1,1,1376,1,1,640,608,5632,1,1,0,1,0,0,0,1,1,1,1,1,1,1,1,1],"FLAG":0,"BASE":1}
```

### Shield Version 1.0

Teleinfo RX is on GPIO3 for each board

#### ESP8266
```
{"NAME":"TICShield","GPIO":[1,1,1,5152,640,608,1,1,1,1,1376,1,1,1],"FLAG":0,"BASE":18}
```

#### ESP32
```
{"NAME":"TICShield32","GPIO":[1,1,1,5632,1,1,1,1,1,1,1,1,1,1,1376,1,1,640,608,1,1,1,0,1,0,0,0,1,1,1,1,1,1,1,1,1],"FLAG":0,"BASE":1}
```

# License

<img alt="Creative Commons Attribution-NonCommercial 4.0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png">   

This work is licensed under a [Creative Commons Attribution-NonCommercial 4.0 International License](http://creativecommons.org/licenses/by-nc/4.0/)    
If you want to do commercial stuff with this project, please contact [CH2i company](https://ch2i.eu/en#support) so we can organize an simple agreement.

# Lazy building your own? 

You can order this shield fully assembled with some extra on [tindie][24]

<a href="https://www.tindie.com/products/25467/"><img src="https://d2ss6ovg47m0r5.cloudfront.net/badges/tindie-mediums.png" alt="I sell on Tindie" width="150" height="78"></a>

# Misc

See news and other projects on my [blog][2] 
 
[2]: https://hallard.me

[20]: https://www.wemos.cc/en/latest/d1/d1_mini_lite.html
[21]: https://www.wemos.cc/en/latest/d1/d1_mini.html
[22]: https://www.smart-prototyping.com/Mini-D1-PRO-Development-Board-ESP8266-4M-16M
[23]: https://www.az-delivery.de/fr/products/esp32-d1-mini
[24]: https://www.tindie.com/products/25467/