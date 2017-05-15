# 2017-05 - Windows IoT

## An introduction to IoT, where Windows 10 IoT fits in, and what Azure IoT gives us

First it's worth defining the term: IoT.

Believe it or not, the term "Internet of Things" was actually coined in 1999, by a Proctor & Gamble researcher. It was just a reference to the "connection" of physical devices to each other and the global internet. 

Almost 15 years later, the "Global Standards Initiative on the Internet of Things" came up with this wonderfully vague definition of a "thing": 

> "An object of the physical world (physical things) or the information world (virtual things), which is capable of being identified and integrated into communication networks".

Followed by this definition of the Internet of Things:

> "A global infrastructure for the information society, enabling advanced services by interconnecting (physical and virtual) things based on existing and evolving interoperable information and communication technologies." 

### What is the point of IoT?

But for our purposes, the Internet of Things enables objects to be sensed and controlled remotely, and thus allows computer systems to interact with the phsical world, and integrate better into our daily lives. Many will ask "why" and the simplest answer is this: by improving remote sensing, we improve accuracy and efficiency of systems which are controlled by computers (everythin), and we can provide increased economic benefit from our computing resources while reducing direct human interaction with them.

Perhaps an example would help.

#### Consider the "Nest learning thermostat"

https://upload.wikimedia.org/wikipedia/commons/thumb/8/87/Nest_Learning_Thermostat_%28cropped%29.JPG/755px-Nest_Learning_Thermostat_%28cropped%29.JPG

The Nest Thermostat is a programmable thermostat -- that you don't have to program. Rather than trying to set up a schedule and set hours and days to control the temperature, users simply change the temperature by hand for a few weeks, and the Nest learns your schedule automatically.  Further, it uses built-in motion and presence sensors, plus location information from your phones, and weather information to shift the house into energy saving modes when no one is at home, and stil get the house warm (or cool) before you return.

In a very concrete sense, it saves you money by integrating awareness of your presence and temperature preferences, and eliminates your need to interact with the thermostat...

### The hobbyist IoT

In the world of IoT, there are a bewildering array of devices and chips to power them, and an awful lot of development kits based around everything from temperature and humidity sensors 

for everthing from building [your own Nest](https://blog.particle.io/2014/01/17/open-source-thermostat/)
There are so many different ways to get started that I can't even begin to list them, so I will simply mention the two biggest influences, and then provide you with a lot of links...

#### Arduino

While not inherently IoT-capable (basic arduinos don't include connectivity options), the low-cost ARM chips (ATmega328, Cortex-M0) have made these very cheap (UNO compatible boards $3/ea from china, or [$8 on Amazon](http://amzn.to/2rfZHE2)), and with BLE (nRF8001, [nRF5182](https://www.nordicsemi.com/eng/Products/Bluetooth-Smart-Bluetooth-low-energy/nRF51822)) and other connectivity options as cheap as $4, these form the basis for many of the sensors used with more sophisticated micro computers.

Newer (and alternative) models include bluetooth, ethernet (POE?), and form-factors as small as a thumbdrive.

The Arduino was, without question, the first truly mass-produced hobbyist system-on-chip devices, and along with the BBC's new microbit, is one of the most commonly used SoC devices in education. It also has the lowest power requirements, sipping energy at 10-30 mA.

#### Raspberry Pi

Perhaps even more famous than the Arduino, but certainly at the other end of the scale of micro-computers, is the Raspberry Pi.  Physically similar (and competitively priced) to the Arduino, the Pi is a completely different beast: with ethernet, USB, HDMI and stereo, the Raspberry Pi is truly a micro computer -- more capable than the first computer most of us owned...

Despite being incredibly powerful compared to the Arduino, the Pi is not exactly a heavyweight in the IoT world -- in the full-blown compute end of the spectrum, the Pi is [competing with](https://learn.adafruit.com/embedded-linux-board-comparison/performance) Intel's Gallileo, the Beaglebone Black, the new Arduino Yun, and is by far the most popular and cheapest option among the first group of devices Microsoft has targeted for Windows IoT, along with the Arrow Dragonboard, Intel Joule, and Minnowboard Max.

#### Others

There are larger and smaller devices out there. 

Consider the amazing [ESP8266 chip](http://makezine.com/2015/04/01/esp8266-5-microcontroller-wi-fi-now-arduino-compatible/), a miniature WiFi chip with a tiny onboard processor that's apparently being used in Amazon's "Dash" buttons (and in hobbyists projects all over the world, now). This thing was virtually unheard of at first, but the actual chip is so cheap (under $2, even without a bulk discount) that even with a breakout board you can get one for [less than $7](https://www.sparkfun.com/products/13678) in the US. It's now directly supported by the Arduino IDE, which means you can make your own [Dash Button](http://www.instructables.com/id/DIY-IoT-ButtonAmazon-Dash-Button/) that triggers IFTTT or Flow with just a few lines of code.

Intel's Edison and Gallileo projects are much more powerful. And of course, there many full-blown stand-alone devices like the Amazon Echo or Fire Tablet which surprisingly cheap and capable.

In between there is a plethora of devices which mimic the Arduino and/or Raspberry Pi form-factor and provide various benefits over those platforms: wireless communication, faster processors, more storage, better graphics, etc.

## Microsoft and the Internet of Things

I don't have enough time to stay general, so let's look specifically at two things that Microsoft has done recently to get companies and hobbyists looking at their platforms and tools.

### Windows IoT

Can you believe Windows 10 runs on a Raspberry Pi?


### Azure IoT

Track and manage, report, and control.


## Conclusion

If you're just trying to learn more, experiment a little, and build some hobbyist projects, you should check out [hackster](https://hackster.io) (they have a [Windows IoT section](https://www.hackster.io/windowsiot), [instructables](https://instructables.com) and of course, [Make](https://makezine.com/projects/).

#### Retailers 

If you're new to this, Buy yourself a starter kit, make sure it includes a prototyping "breadboard" and some interesting sensors...

https://www.adafruit.com/
https://www.makershed.com/
https://www.sparkfun.com
https://www.seeedstudio.com/
https://redbear.cc/
https://www.particle.io/

### Starter project ideas

[The Build Lamp](https://blog.particle.io/2017/01/25/developers-studio-testing-1-2/). You've probably seen one of these on the internet before: a lamp that changes color to indicate problems with automated builds.
[Dash Button](http://www.instructables.com/id/DIY-IoT-ButtonAmazon-Dash-Button/). A button that triggers IFTTT with just an ESP8266.
[Weather log](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-sparkfun-esp8266-thing-dev-get-started) using the [Thing Dev](https://www.sparkfun.com/products/13711) ESP8266 to send temperature and humidity to Azure.
