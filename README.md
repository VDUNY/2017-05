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

![Nest Thermostat](https://upload.wikimedia.org/wikipedia/commons/thumb/8/87/Nest_Learning_Thermostat_%28cropped%29.JPG/755px-Nest_Learning_Thermostat_%28cropped%29.JPG)

The Nest Thermostat is a programmable thermostat -- that _you_ don't have to program. Rather than expecting the home owner to set up a schedule and pre-determine at which time on which days to change the temperature (with no exceptions), Nest users simply change the temperature by hand for a few weeks, and the Nest learns your schedule automatically. Further, it uses built-in motion and presence sensors, plus location information from your phones, and weather information to shift the house into energy saving modes when no one is at home, and still get the house warm (or cool) before you return.

In a very concrete sense, it saves homeowners money by integrating awareness of your presence and temperature preferences, and eliminates your need to interact with the thermostat...

## A word about hardware

As a developer, if you start considering an IoT project, one of your first choices is going to be about the _physical_ things that you want to build. If, for instance, you wanted to build a Nest thermostat, you'll quickly find there are a bewildering array of temperature and humidity sensor chips, and dozens of choices for core computing capacity.

There are so many different options that there's really no point in my trying to do a survey or overview of them, but let's talk about two major categories, and the "name brand" in each of them that gives us cheap options for prototyping, at least.

### Microcontrollers and System on Chip

A system on a chip (SoC) is a single integrated circuit that integrates all the necessary components of a computer. It may contain digital or analog inputs and outputs, radio-frequency options, and even graphics processing, all on a single substrate. They're extremely cost-efficient at high volume, but expensive to design and produce.

These microcontrollers typically power commercial IoT devices, but with a _programmable_ microcontroller like the ATMega328 chips, we have enough flexibility to create prototypes and single-purpose sensors and devices.


### Single Board Computers

At the other end of the IOT scale are the single-board computers. These are systems with multiple chips for everything from micro-controllers, dedicated sensors, graphics and sound drivers, and more, all integrated onto a single board. Typically they resemble a general purpose computer from years ago but are built around a SoC like the ARM11 or the more modern ARM Cortex-A9 or A53 and have separate GPUs and high speed RAM.


#### SOC 1: Arduino -- an ecosystem

We generally think of Arduino as this little single board computer, but really it's a platform, starting with the cross-platform IDE and software libraries, the open hardware specification and connector layout (a sort-of pre-configured breakout board), and that ATMega microcontroller. The board itself is really just a breakout board for the 14 digital IP pins, and 6 analog, with a built-in USB in-circuit serial programming interface, a power regulator, and a few LEDs.

The major benefit of Arduino is it's popularity: cod modules, with step-by-step instructions for connections, exist for almost every sensor, button, LED, or LCD that you will come across, and there are many options for wireless communication, from add-on modules for WiFi and Bluetooth, to cellular and GPS "hats."

While basic arduinos don't include connectivity options, these low-cost ARM chips are extremely cheap. You can UNO-compatible boards on AliExpress for less than $3/ea shipped from China, or [$8 on Amazon](http://amzn.to/2rfZHE2).

The Arduino was, without question, the first truly mass-produced hobbyist system-on-chip device, and along with the BBC's new microbit, is one of the most commonly used SoC devices in education.

As a side note, the power requirements for the Arduino UNI are barely 10-30 mA!

#### SOC 2: ESP8266

I wanted to make sure to mention the amazing [ESP8266 chip](http://makezine.com/2015/04/01/esp8266-5-microcontroller-wi-fi-now-arduino-compatible/), a tiny (14x15mm?) WiFi chip with an onboard processor that has taken the hobbyist world by storm since the Amazon Dash showed the sort of automation you can do with nothing but a single http request!

The actual ESP8266 chip is extremel cheap, so you can get these for under $2 including the breakout board from AliExpress, or [around $7](https://www.sparkfun.com/products/13678) in the US (or [$16 with a built-in battery charger, power supply, and USB ICSP]). It's now even supported by the Arduino IDE, which means you can make your own [Dash Button](http://www.instructables.com/id/DIY-IoT-ButtonAmazon-Dash-Button/) that triggers IFTTT or Flow with just a few lines of code.

### SBC: The Raspberry Pi

Perhaps even more famous than the Arduino, but certainly at opposite ends of the spectrum, although it's physically similar (and competitively list-priced), the Pi is a completely different beast: with ethernet, USB host, HDMI and stereo, it's more capable than the first computer most of us owned...

Despite being incredibly powerful compared to the Arduino, the Pi is not exactly a heavyweight --even in the IoT world-- and there are [many other options](https://en.wikipedia.org/wiki/Comparison_of_single-board_computers#CPU.2C_GPU.2C_memory) with more of ... whatever you need. The [most well known _competition_](https://learn.adafruit.com/embedded-linux-board-comparison/performance) are probably Intel's Gallileo, the Beaglebone Black, the new Arduino Yun.

However, the Raspberry Pi is by far the most popular (and cheapest) option among the first group of devices Microsoft has targeted for Windows IoT, along with the Arrow Dragonboard, Intel Joule, and Minnowboard Max.

## Microsoft and the Internet of Things

This finally brings us to my main topic. I promised you a presentation on Windows IoT, and so I want to segue here to talking about what Microsoft has been doing lately to try to get companies and hobbyists looking at their platforms and tools.

It's an interesting historical note that most microcontroller systems don't support development except on Windows -- the Arduino IDE was one of the first to be seriously cross-platform.

However, Microsoft isn't happy just providing an operating system for the developers of IoT to use on their laptops, so we have two angles to talk about.

The first is obviously Windows 10 IoT Core: a version of Windows so slimmed down that it can run on the ARM chip on a Raspberry Pi 2 in one gigabyte of RAM.

The second is the latest generation of Azure services for IoT, including Azure Device Management, a collection of projects, dashboards and reporting tools to satisfy whatever kind of IoT project you're planning.

## Windows IoT

Can you believe Windows 10 runs on a Raspberry Pi?

Let's walk through the process of installing Windows on a Raspberry Pi 3, so you can see what you get "out of the box." I have here a Pi 2 and a Pi 3 -- I'm using the 3 because it has WiFi and Bluetooth on board, so there's just a lot less that can go wrong, and honestly, unless you can find them _cheap_ used, there's really just no point in worrying about the difference.

1. We start by visiting the [Windows IoT Core Developer Site](https://developer.microsoft.com/windows/iot) and hitting the [Getting Started](https://developer.microsoft.com/en-us/windows/iot/getstarted) link, but just before we go there I want to point out this line on the home page:

    > Windows 10 IoT Core supports hundreds of devices running on ARM or x86/x64 architectures.

    They're not kidding, but they _are_ cheating. The list of [Windows enabled SoCs](https://developer.microsoft.com/en-us/windows/iot/explore/SoC) is actually very short: 2 Broadcom chips (Raspberry Pi), 3 Qualcomm chips (DragonBoard), and of course, all the Intel chips.

    However, the list is growing. Banana Pi M64 and Pine 64 (using the Allwinner A64 chip) and the Toradex (built on Nvidia's Tegra 3) have already offered support.

2. Find the right instructions.

    On the [Getting Started](https://developer.microsoft.com/en-us/windows/iot/getstarted) page we select our device (Raspberry Pi 3), media (we'll just use a blank SD card, because at this point, I don't need choices), and OS Version (I'm going to use the Insider Preview).

    All of that is just so they can send you to the right docs page...

    [Getting Started with RPi3](https://developer.microsoft.com/en-us/windows/iot/Docs/GetStarted/rpi3/sdcard/insider/GetStartedStep1.htm) has a list of steps for us, starting with installing Windows 10, and then the IoT Core Dashboard.

3. Set up our device.

    To actually install Windows IoT, you just build an image on the SD card the same way you would image media for a regular PC ... except that this handy Windows 10 IoT Core Dashboard app handles it for us:

    ![Set Up Device screenshot](https://az835927.vo.msecnd.net/sites/iot/Resources/images/IoTDashboard/IoTDashboard_InsiderPreview.PNG)

    One thing to note here, the "Device Name" and wireless options don't seem to actually make it into the configuration, so this isn't creating quite as custom an image as I would like.

    In any case, once we've stepped through this wizard, we have an SD card ready to go.

4. Configuring the device...

    When you plug in a Windows IoT box for the first time and it doesn't have wireless, it will boot up with a name like "AJ_SoftAP..." and you can connect directly to it with your laptop wireless in order to finish configuring it remotely.

    You can also just connect the device to a display, and use a mouse and keyboard to negotiate wireless on the device. I've had much better success with that, for some reason. Note that if you're going to hook things up, you're much better off doing so _before_ you plug in the computer.

    For the most part, to configure your Windows IoT box, you're going to use it's management web interface, which is served (by default) on port 8080, and you can get to it by right-clicking the device in our IoT Dashboard app.

    Finally, there's a "Windows IoT Remote Client" app available in the store which allows you to connect to a remote Windows IoT device as if via VNC or Remote Desktop, but at this point, it's terribly laggy to use over wifi.


### What can you do in Windows IoT Core?

It's not an exaggeration to say that it would be better to ask what you cannot do. Almost any Windows Universal App will run on Windows IoT Core, and it shares the new UAP driver model, so you'll find that most of your USB devices already "just work" when you hook them up to the Raspberry Pi, from keyboards and mice, to mics, webcams, etc.

Rather than code up my own sample apps, I've decided for this presentation to use some of the ones that are already available in the community, so let me show off a few of those. I'll start with a few from [ms-iot/samples](https://github.com/ms-iot/samples).

Actually, maybe we should start with [Cortana](https://developer.microsoft.com/en-us/windows/iot/docs/cortanaoniotcore). "Hey Cortana, how are the Yankees doing?" ... "Hey Cortana, is it going to rain tonight?" ... "Hey Cortana, remind me in 10 minutes to show custom Cortana apps."  Of course, Cortana does not really work in "headless" mode, partly because you have to go through some permissions dialogs to turn her on, give Microsoft permission to listen on your mic, and in fact, to sign in with your Microsoft Services Account. You'll find a lot of the actual sample apps are like that too -- designed for the Raspberry Pi as a computer, not for "IoT" itself.

However, let's just look at some as an example.

#### [IoT Walkthrough](https://github.com/ms-iot/iot-walkthrough)

I'm not going to go through this one in detail, because I don't have a weather sensor handy, and the project was done with a Minnowboard anyway, so it would take some extra customizing. The [Windows 10 IoT Core Walkthrough](https://github.com/ms-iot/iot-walkthrough) has a great example of an IoT device: a background app that collects weather sensor data and sends it to the IoT cloud. A foreground application that shows that local weather data, as well as information from the internet (news and weather) or radio streams and photo slideshows...

So instead, let's take a look at the classic "Hello World" of embedded systems: blinking an LED.

#### [Hello Blinky](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)

I've got an LED here with a resistor pre-connected, and we're going to connect it to one of the many GPIO (general purpose IO) pins on the Raspberry Pi, and turn it on and off.

Open ms-iot-samples\HelloBlinky\CS

I'm going to go ahead and start the deployment of this (I've noticed sometimes it takes awhile), but let's look at the code.

A few things to notice:

* A constant for the LED pin = 5 (I have to connect my wires to the that pin, there are pinout diagrams for the Raspberry Pi everywhere).
* We're using a _normal_ Timer class with it's "Tick" handler.
* We get the "default" GPIO Controller -- this is important, because there _is_ an alternative GPIO controller ("Lightning"), which we'll look at later.
* We OpenPin on the pin we want, and set it's pin value by calling .Write(), but we must _also_ set the mode of the pin to _Output_.
* Then in the timer tick, we just swap the LED (and the color of the on-screen circle).

Simple enough? Let's take it to the next level.

#### [Hello Blinky Background](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackground)

For IoT, we always want to do _something_ in the background. Usually that's about talking to sensors, and responding. For now, let's pretend it's about blinking an LED!

Open ms-iot-samples\HelloBlinkyBackground\CS -- note that not only is there a C++ version of this project, there are versions in Python, NodeJS, and VB.Net. This is true of many of the projects, but not all of them are available in so many languages.

The other thing to notice is that this project isn't an "application" anymore, it's just a library with a background task. We registrater that task in the Package manifest. You can see in the "Declarations" that we've got a "Background Tasks" declared with an entry point.

As a result of that, it's now using a ThreadPoolTimer, but other than that, this is basically the same code, with just a little less ceremony.

In any case, you can see that if I deploy this, the LED is  blinking, but the screen has stayed on the default app display ...  "Hey Cortana, what time is it?" ... and we can still run other apps and so on, while the LED just keeps on chugging along in the background.

#### Windows Device Portal

This is probably as good a time as any to go back and spend a little time in the web-based management interface for this device. We can get there from the IoT Dashboard, so let's look around.

* Device Manager - I can rename, change my password, set a pin for remote debugging, change the display, disable Cortana, etc.
* I have a Task Manager in Proces -> Details
* In Debug I can take kernel dumps, remotely start VS Debugger, etc.
* I can even register ETW tracing in Debug -> ETW
* In Devices you can see what's connected
* In Connectivity I can switch wireless networks, etc.
* I can configure the TPM, do windows updates, etc.

But most importantly, right now ... let's go back to the "Apps" that I skipped.  The Apps manager not only lets me upload .appx files to install apps, it also let's me start and stop apps. So in here I can set that "BlinkyHeadlessCS" to run at startup, or I can just start and stop it by hand ...

#### WebCamSample

If we open this project in Visual Studio you'll see it's a very straightforward Windows app, with a MainPage.xaml and some png assets. We can open that xaml up in the designer and take a look, you can see the .appxmanifest packaging file, etc. One thing to point out is that for UAP apps, you have to specify the capabilities you need (remember these are "Store" apps). This one has access to your mic, camera, and the pictures and videos libraries.

Notice our Debug option (in the drop down) includes emulators and the Remote Machine. I'm going to try this, but I'm not totally sure it's going to work on the wifi -- I should be able to bring up the Remote Machine list and see the PiGone device and actually "Deploy" to it, remotely.

So you can see here, on the left side there's a "Preview" window, in the center the last-captured photo, on the right, the last recorded video. We can initialize Audio and record something, or initialize both Audio and Video and take stills or record video ... "This is a test of the emergency broadcast system ... this is only a test."

I can put a breakpoint in the code, and (over wifi, mind-you) break into the running app on the device.

So let's take a look at the source. It's a pretty straight-forward XAML based app, you can see on line 210 where it's setting the "Source" of the previewElement to the actual MediaCapture object, and the use of the `await` keyword on each call to it...we can even tamper with values -- let's change the status text. I'll breakpoint on line 216, and we can set the value and then continue...

Ok. Enough of that.

Actually, one other point, while I'm thinking of it. If we go back to the IoT Device Manager app, there's an option in the right-click for each device to "Launch PowerShell" -- check it out.

I don't actually know why it runs PowerShell elevated locally (I think it's so that it can mess with the trust settings to "trust" the device "host"), but you'll see it prompts me for the credentials to the piGone, and then ... just connects! Anyway, the reason I wanted to do that is because I can actually go in here and look in C:\Data\Users\DefaultAccount\Videos (or Pictures) and we can see the videos we just shot with that app.  If I had an array of these devices mounted around, I could easily poll them all (with PowerShell remoting, no less) and pull down whatever logs or data we have.  Of course, that wouldn't be very ... "IoT" would it?



## Azure IoT

Track and manage, report, and control.

## Beyond Windows

Microsoft is also trying to make sure that it's easy for you to use _any_ devices with your IoT solution, either on their own, or alongside Windows IoT Core. There is a ton of stuff we could talk about here, but let me just leave you with a few links:

[Arduino VirtualShields Universal App](https://github.com/ms-iot/virtual-shields-universal), Windows universal app that lets Arduino use Bluetooth to connect to a Windows device (e.g. phone), and get accesss to any capabilities, including GPS, light sensor, accelerometer, etc. as if they were sensor "shields" for Arduino. This even includes letting Arduino devices use Windows to access the camera, microphone, send email, access the web ... even create screens (for your phone) with buttons that directly affect pins and motors on the Arduino. You'll also need the [Arduino VirtualShields Wiring](https://github.com/ms-iot/virtual-shields-arduino) to provide the virtual shields on Arduino.


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
[Dimmer Switches]() You'll need an Analog-to-Digital chip lke the MCP3008 to use aa potentiometer with a Rasberry Pi, because they only have digital IO. There is a [Potentiometer Sample Project](https://developer.microsoft.com/en-us/windows/iot/samples/potentiometer) from Microsoft.
