# WeMos Teleinfo ESP8266/ESP32/S2/C3/S3 Shield

This shield is used to get French energy meter called Teleinfo data with any of the following boards:

- [WeMos D1 Mini][22] ESP8266
- [MH et Live ESP32 Mini Kit][23]
- [WeMos Mini S2][25] 
- [WeMos Mini C3][26]
- [WeMos Mini S3][27]

Take care the check wiring, because there is a lot of clone boards so please be sure to order the correct ones. If you want to be sure you can add it as option when you order this shield on [tindie][24], in bonus it will be flashed with tasmota teleinfo firmware.

Since price difference between ESP32 and ESP8266 boards is so small, to be able to use all future features such as Tamota with TLS, [Berry language](https://tasmota.github.io/docs/Berry/) or even tasmota new applications, I strongly suggest to use with ESP32 only. In the meanwhilen due to lack of ressources and Serial for debug (when using teleinfo), **no support for ESP8266 will be provided**. Of course it works fine, but I spent too much time each time to reproduce and track issues so I let it behind for now to focus on ESP32.  


**New in v1.2**

- Changed R3 by adjustable 2K resistor (trimer) to adjust Teleinfo signal sensitivity for Standard/Historique modes
- Added QWIIC/STEMA I2C classic connector
- Changed Blue Led resistor to decrease light intensity
- Placed easy cutting trace to disable Teleinfo Blue LED

**v1.1**

- Default RX goes to GPIO13 on ESP8266, GPIO23 on ESP32 (see other below)
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

Look at the schematics for more informations, easy to understand. Wiring on the WeMos Teleinfo shield is as follow:

| Pin Function | ESP32   | ESP8266 | ESP32-S2 | ESP32-C3 | ESP32-S3 |
|  :---        |  :---:  |  :---:  |  :---:   |  :---:   |  :---:   |
| Téléinfo Rx  |  GPIO23 | GPIO13  | GPIO11   | GPIO4    | GPIO11   |
| RGB Led      |  GPIO18 | GPIO14  | GPIO7    | GPIO2    | GPIO12   |
| I2C SDA      |  GPIO21 | GPIO4   | GPIO33   | GPIO8    | GPIO35   |
| I2C SCL      |  GPIO22 | GPIO5   | GPIO35   | GPIO10   | GPIO36   |

You can change default Rx to `GPIO3` with solder pad `tic-rx`, but in this case, you need to cut the default trace and put solder between center pad and `IO3`, It's for advanced users, do it only if you need it and if you know what you are doing.

Default wiring on [ESP8266 Mini D1][21], [ESP32 Mini Dev board][23], [ESP32 S2 Mini][25] or [ESP32 C3 Mini][26] or [ESP32 S3 Mini][27]

| Pin Function    | ESP32  | ESP8266 | ESP32-S2 | ESP32-C3 | ESP32-S3 |
|  :---           |  :---: |  :---:  |  :---:   |  :---:   |  :---:   |
| On Board LED    |  GPIO2 | GPIO16  | GPIO15   |  GPIO7   |  GPIO47  |
| On Board Button |  GPIO0 | GPIO16  |  GPIO0   |  GPIO9   |  GPIO0   |


Note : On ESP32-S3 the On Board LED is RGB WS2812 (same than on this shield) so to drive Shield LED use IO12 and to drive S3 Led use IO47

# Schematics

## V1.2
<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-sch.png">

## V1.1
<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-v11-sch.png">

# Boards (V1.1)

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-top.png" alt="Top" width="40%" height="40%">&nbsp;
<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-bot.png" alt="Bottom" width="40%" height="40%">

# Assembled boards

Here an example of boards connected with wiring on [ESP32 Mini Dev board][23]

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-assembled-top.png" width="40%" height="40%" alt="WeMos Teleinfo Assembled TOP">&nbsp;
<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-assembled-bot.png" width="40%" height="40%" alt="WeMos Teleinfo Assembled Bottom">

# Assembling

Nothing complicated, just use and solder headers. I suggest to use the small ones I sell with shield on Tindie, takes less place and you can either fix for life with just one part of the header soldered on both shield and ESP32.

Here boards connected to [ESP32 Mini Dev board][23]

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-soldering-shield.png" width="40%" height="40%">&nbsp;
<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-soldering-esp32.png" width="40%" height="40%">

# 3D Print enclosure

@barbudor was kind enough to build and share awesome 3D enclosure for this shield. you can find `stl` file to print your own [here](3dprinted_enclosure). see pictures below

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC_enclosure.png">
<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC_inside_enclosure.png">

:warning: This enclosure fit perfelctly shield connected with WemMos ESP32 or D1 Mini ESP8266 **only when assembled with small headers**
<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC_small_headers.png">

You can add these headers when you order this shield on my [tindie store][24]

# Firmware 

You can write your own and use with [LibTeleinfo](https://github.com/hallard/LibTeleinfo) library I wrote if you want to get rid of driving teleinfo stuff (chekout some [examples](ttps://github.com/hallard/LibTeleinfo/tree/master/examples)).

## Tasmota

But I strongly suggest using amazing [Tasmota](https://tasmota.github.io/docs/) firmware, all is already done and well done.

Please check Teleinfo official tasmota [documentation](https://tasmota.github.io/docs/Teleinfo/) so see how to configure your device depending on smartmeter type and what options you need.

### Nicolas's builds

Nicolas @NicolasBernaerts has made awesome changes on Tasmota to be able to show graph of consumption, history and other great features such has:

- Ecowatt server to publish RTE Ecowatt signals
- TCP server to live stream teleinfo data
- FTP server to easily retrieve graph data

You can find more information on his dedicated [repo](https://github.com/NicolasBernaerts/tasmota/tree/master/teleinfo) and also ready made build for all compatible ESP boards.

### Unofficial builds

Teleinfo is not member of official Tasmota builds. So you need to build your own with `USE_TELEINFO` define. 
But Tasmota team agreed it's not simple to build for end users, and they now provide unofficial build that follow developement branch, this mean you always have an up to date build with latest code available. Of course we added Teleinfo (ESP8266 and ESP32) builds in this unofficial build process so you have nothing to install and compile/link (building). You can't go easier.

And as a cherry on the cake, easy flasher tools (web version and executable one) will present Teleinfo firmware so you are able to flash teleinfo firmware in less than 1 minute. You can check detail [here](https://github.com/Jason2866/Tasmota-specials) but here how to do that.

- Launch [Web Flasher here](https://jason2866.github.io/Tasmota-specials/) 
- Select Teleinfo (flash will auto detect if you need ESP8266 or ESP32 and will flash the correct one)
- Select Serial port, and click `install`

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-web_flasher.png">

Once done something like that

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-web_flasher_ok.png">

After flashed, you should now see a new access point named `tasmota_aabbcc_xxxx` where you can connect to configure your WiFi for the device to connect on.

Alternatively, if you connect serial console and reset the device you should see Serial logs like that
```
00:00:00.003 HDW: ESP32-D0WDQ6 
00:00:00.037 UFS: FlashFS mounted with 308 kB free
00:00:00.109 CFG: Loaded from File, Count 12
00:00:00.124 QPC: Count 1
00:00:00.257 CFG: no '*.autoconf' file found
00:00:00.263 BRY: Berry initialized, RAM used=3620
00:00:00.282 BRY: no 'preinit.be'
00:00:00.291 Project tasmota - Tasmota Version 10.0.0.3(teleinfo)-2_0_1_1(2021-11-30T14:22:47)
00:00:00.379 BRY: no 'autoexec.be'
00:00:00.447 WIF: WifiManager active for 3 minutes
00:00:01.139 HTP: Web server active on tasmota-090F8C-3980 with IP address 192.168.4.1
00:00:06.827 QPC: Reset
```

If you want to deep into this process or just curious, you can check out it's [here](https://github.com/Jason2866/Tasmota-specials)

:memo: If you have some issues flashing with Web Flasher, do not hesitate to use another awesome tool [ESP Flasher](https://github.com/Jason2866/ESP_Flasher), with this one you can see exactly what's going on in case of issue because it has built in console. Usefull also after reboot of the device because console still active. This is the one I'm using day by day. In this case you need to download firmware to flash first [here](https://github.com/Jason2866/Tasmota-specials/tree/firmware/firmware/tasmota/other). Download firmware `tasmota-teleinfo`

You can take a look on `autoconf` [folder](https://github.com/tasmota/autoconf/tree/main/raw/esp32/Wemos_Teleinfo) to see some of init commands used on ESP32. For ESP8266 you can copy content of `autoexec.bat` and manually apply to you ESP8266 teleinfo.

:memo: Don't forget to reset Energy counters on first boot with console command `EnergyTotal 0` if you have erratic values. 


### I2C Display

You can add fancy I2C display (or even I2C sensors), take care of wiring of the display. They are not all usin the same order wiring the 4 pins on I2C connector. You need to use one with this order `GND VCC SDL SDA`. Since I2C VCC is conencted to 3.3V, your I2C device is compatible with 3.3V or 5V ones (They all have shifter since majorty of sensors works at 3.3V)

Then with tasmota you need to select correct one, in my example below it's an SHT1106 128x64 so config is (use only one time). Pleasy check Tasmota documentation for [display](https://tasmota.github.io/docs/Displays/) and associaed [commands](https://tasmota.github.io/docs/Commands/#displays).

```
DisplayMode 2
; 2 for SSD1306 and 7 for SH1106
DisplayModel 2
displaycols 21
displayrows 8
```

Don't forget to toggle ON on tasmota WEB UI since it's like a device. If not nothing will be displayed. You can also check the OLED presence using command `i2cScan` from console, something loke below sounds good, seen on `0x3c`

```
13:09:39.490 CMD: i2cscan
13:09:39.531 MQT: stat/tasmota_EF58A0/RESULT = {"I2CScan":"Device(s) found at 0x3c"}
```

And here is a picture of the whole working.

<img src="https://github.com/hallard/WeMos-TIC/raw/master/pictures/WeMos-TIC-oled.png">

### Autoconf (ESP32 Only)

Another awesome feature of Tasmota is the ability to download configuration profile, and guess what, we done it for this shield, just go to configuration option, select Autoconfig and then choose in the list `Wemos Teleinfo` and here you are, ne need to copy/paste template, it's done by autoconfig.
If you want to deep into this process or just curious, you can check out it's [here](https://github.com/tasmota/autoconf)

### Berry Scripting (ESP32 Only)

Now you can personalize code with [Berry language](https://tasmota.github.io/docs/Berry/). Check out some Berry samples [here](https://github.com/arendst/Tasmota/blob/development/tasmota/berry/examples/)

You can do that by going to Berry console from Tasmota WEB user interface.

#### Drive RGB LED depending on actual power

Here is a Berry example, goal is to follow real time consumption driving on board RGB Led depending on current Power consumption (low green then going to red when reaching maximum current of your contract)

```python
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

#### Send data to Emoncms with Berry (ESP32 only)

What's magic with Berry is the ability to do basic stuff with data, in this example we will intercept MQTT send message by Energy driver, do some calc and send data to Emoncms every 15 seconds and also to drive RGB Led from Green (low load) to Red (approach max subscription)

Modifiy API key with your, and copy paste the following code into Berry Console. Tst and validate if all is okay for you.

Once all is fine, you paste the code into a file named `autoexec.be` on the Tasmota Filesystem so it will be executed each time Tasmota device starting.

### Mode Historique (contrat heures creuses)

```python
import json

var api_url = "https://emoncms.org/input/post"
var api_key = "YOUR_EMON_API_WRITE_KEY"
var node_name = "NODE_NAME"
var post_every = 15000 # post evert 15 seconds
var payload = {}

def send_emoncms()
  # Convert JSON object to string 
  var obj_json = json.dump(payload)

  # Create URL to call
  var param="?fulljson="+obj_json + "&node="+node_name + "&apikey="+api_key 
  # Post Data to EMONCMS
  var cl = webclient()
  cl.begin( api_url + param)
  var r =  cl.GET()
  tasmota.set_timer(post_every, send_emoncms)
end

def setcolor(iinst, isousc)
  var red = tasmota.scale_uint(iinst, 0, isousc, 0, 255)
  var green = 255 - red
  var channels = [red, green, 0]
  light.set({"channels":channels, "bri":64, "power":true})
end

# set global payload the field we need
def rule_tic(value, trigger)
  # Got Heures Creuses contract so I will calculate total consumption
  # adding Heures Creuses (HCHC) + Heures Pleines (HCHP) and create new value for emoncms 
  # Change label depending on name for your contract type
  var htot = value['HCHP'] + value['HCHC'] # mode historique
  # Create new value HTOT converted to kWH
  payload['HTOT'] = htot / 1000.0
  # Calculate current percent Load 
  var iinst = value['IINST']  # mode historique
  var isousc= value['ISOUSC'] # mode historique

  if iinst != nil && isousc != nil 
    # Drive RGB LED
    setcolor(iinst, isousc)
    if isousc > 0
      load = 100 * iinst / isousc
      payload['LOAD'] = load
    end
  end

  # Set values we need to send to emoncms
  payload['ADCO']  = value['ADCO']
  payload['HCHP']  = value['HCHP']
  payload['HCHC']  = value['HCHC']
  payload['ISOUSC']= isousc
  payload['PAPP']  = value['PAPP']
  payload['IINST'] = iinst

end

def start()
  # Callback on each frame interception
  tasmota.add_rule("TIC",rule_tic)
  # fire 1st post in 5s 
  tasmota.set_timer(5000, send_emoncms)
end

# delay start to have time to get full frame
tasmota.set_timer(10000, start)

```


### Mode Standard (contrat heures creuses)

```python
import json

var api_url = "https://emoncms.org/input/post"
var api_key = "YOUR_EMON_API_WRITE_KEY"
var node_name = "NODE_NAME"
var post_every = 15000 # post evert 15 seconds
var payload = {}

def send_emoncms()
  # Convert JSON object to string 
  var obj_json = json.dump(payload)

  # Create URL to call
  var param="?fulljson="+obj_json + "&node="+node_name + "&apikey="+api_key 
  # Post Data to EMONCMS
  var cl = webclient()
  cl.begin( api_url + param)
  var r =  cl.GET()
  tasmota.set_timer(post_every, send_emoncms)
end

def setcolor(iinst, isousc)
  var red = tasmota.scale_uint(iinst, 0, isousc, 0, 255)
  var green = 255 - red
  var channels = [red, green, 0]
  light.set({"channels":channels, "bri":64, "power":true})
end

# set global payload the field we need
def rule_tic(value, trigger)
  # Got Heures Creuses contract so I will calculate total consumption
  # Calculate current percent Load 
  var iinst = value['IRMS1']  
  var isousc= value['PREF']*5 

  if iinst != nil && isousc != nil 
    # Drive RGB LED
    setcolor(iinst, isousc)
    if isousc > 0
      load = 100 * iinst / isousc
      payload['LOAD'] = load
    end
  end

  # Here I keep name of historique mode
  payload['ADCO']  = value['ADSC']
  payload['HTOT']  = value['EAST'] / 1000 # I need kWh
  payload['HCHP']  = value['EASF01']
  payload['HCHC']  = value['EASF02']
  payload['ISOUSC']= isousc
  payload['PAPP']  = value['SINSTS']
  payload['IINST'] = iinst

end

def start()
  # Callback on each frame interception
  tasmota.add_rule("TIC",rule_tic)
  # fire 1st post in 5s 
  tasmota.set_timer(5000, send_emoncms)
end

# delay start to have time to get full frame
tasmota.set_timer(10000, start)

```

### Tasmota templates

Use the following templates depending on version of shield and ESP board (but I strongly suggest using autoconf if you have a ESP32 board)

#### Shield Version 1.1

ESP8266
```
{"NAME":"Wemos Teleinfo","GPIO":[1,1,1,1,640,608,1,1,1,5152,1376,1,1,1],"FLAG":0,"BASE":18}
```

ESP32
```
{"NAME":"Wemos Teleinfo","GPIO":[1,1,1,1,1,1,1,1,1,1,1,1,1,1,1376,1,1,640,608,5632,1,1,0,1,0,0,0,1,1,1,1,1,1,1,1,1],"FLAG":0,"BASE":1}
```

ESP32-S2-Mini
```
{"NAME":"Wemos Teleinfo","GPIO":[1,1,1,1,1,1,1,1376,1,1,1,5632,1,1,1,1,1,1,1,5632,1,1,640,1,608,1,0,1,1,1,1,1,1,1,1,1],"FLAG":0,"BASE":1}
```

ESP32-C3-Mini
```
{"NAME":"Wemos Teleinfo","GPIO":[1,1,1376,1,5632,1,1,288,640,1,608,1,1,1,1376,1,1,640,1,0,1,1],"FLAG":0,"BASE":1}
```

ESP32-S3-Mini
```
{"NAME":"Wemos Teleinfo","GPIO":[32,1,1,0,0,1,1,1,1,1,1,5632,1376,1,0,1,1,1,1,1,1,1,0,0,640,608,0,0,0,0,0,0,1,1,0,0,1377,0],"FLAG":0,"BASE":1}
```


#### Shield Version 1.0

Teleinfo RX is on GPIO3 for each board

ESP8266
```
{"NAME":"TICShield","GPIO":[1,1,1,5152,640,608,1,1,1,1,1376,1,1,1],"FLAG":0,"BASE":18}
```

ESP32
```
{"NAME":"TICShield32","GPIO":[1,1,1,5632,1,1,1,1,1,1,1,1,1,1,1376,1,1,640,608,1,1,1,0,1,0,0,0,1,1,1,1,1,1,1,1,1],"FLAG":0,"BASE":1}
```

# Support and discussion

If you have any issue or just want to discuss on this project, please use community [forum](https://community.ch2i.eu/category/19/wemos-teleinfo)

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
[25]: https://www.wemos.cc/en/latest/s2/s2_mini.html
[26]: https://www.wemos.cc/en/latest/c3/c3_mini.html
[27]: https://www.wemos.cc/en/latest/s3/s3_mini.html

