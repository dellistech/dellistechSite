---
title: "Tamagotchi Matrix Pictureframe"
date: 2020-10-17T20:02:15-06:00
draft: false
---

# The Tamagotchi Hive Frame (Part 1: Project Overview)

Ever since I started my first office job, I've wanted a fish tank for my desk. Unfortunately, 
the fine folks who manage the building didn't agree that nothing bad would ever happen with a 
multi-gallon tank of water surrounded by expensive electronics. So I began my search for something a little more office friendly. 

I've always had a love for virtual pets, going back to the Tamagotchi, which were wildly popular in the 90's. I have also always been 
fascinated by projects trying to pick apart the inner workings to see what makes the little guys tick. 

!["Tamagotchi" by Pascal Maramis is licensed under CC BY 2.0](/images/8916250698_d99fe2f598_o.jpg)

<!--
[This old Make article](https://makezine.com/2008/02/29/this-is-what-it-sounds-li/) is really what got me inspired. Just by 
observing the behavior and trying to replay IR sequences, they were 
able to take a peek behind the curtain to de-anthropomorphize the little needy buggers. 
Early in the article, the author mentions his plans to make a *"virtual" virtual pet to live on [his] cell phone or other devices, including an iPod...*
-->

As with all great things in life, there is a relevant XKCD:


![Tamagotchi Hive](https://imgs.xkcd.com/comics/tamagotchi_hive.png)

While trillions of Tamagotchi seemed a little excessive to me, I think having a few of these things patched together in a shadow box 
or emulated in a digital picture frame might be just the ticket. Of course, I'd also have to include the logic to keep them all fed 
and happy without any input from me. 

## Project goals

The goals for this project are as follows:
I needed a display that would show somewhere between 6-12 Tamagotchi. The important thing is that it needs to be very low maintenance.
(I can't imagine anyone would look too kindly on me skipping meetings to feed or care for children's toys from 20 years ago.) 
It would also be really cool if they interacted as a system. Tamagotchi have been social since the IR communication editions, so if I 
can capture that same feeling in a piece of office art, that would be the goal. 

The "fish tank" also needs to be:
- Low maintenance
- Self-contained (Hopefully able to hang on a wall with no wires.)
- Visually appealing
- Power efficient

Think digital picture frame + low power embedded system + battery = Tamagotchi fish tank. 

## Planning the Project Components

I'm breaking the project down into the following categories:
- The Software
- The Platform
- The Display
- The Power

I'll talk a little about some of the choices I've made for the project now, and kick some of the less important or ambiguous parts
down the road for future me to deal with. 

## The Software
This is the simple part for me, but only because I am about to build off the work of giants. All this is only possible because of 
[Natalie Silvanovich's](http://natashenka.ca/about/) work on reliable code execution on Tamagotchi. You can read the paper in 
[PoC||GTFO 0x02](https://www.alchemistowl.org/pocorgtfo/pocorgtfo02.pdf), but the part that matters to us is that her vulnerability 
discovery allowed her to dump the ROM of the Tamagotchi, which will allow us to emulate the bad boys instead of having to figure out 
how to wire up some kind of harness to interact with the pets directly. 

Fortunately, I don't even have to write the emulator myself either, thanks to the work of Jeroen Domburg, AKA 
[Sprite](https://spritesmods.com/?art=about). He took the same inspiration from XKCD to take the ROMs dumped by Natalie Silvanovich 
to write his own [Tamagotchi Hive](http://tamahive.spritesserver.nl/). He designed and wrote a "Benevolent AI" state-machine to 
keep the pets fed and happy. Not only that, but he also re-created the IR communication protocol and has the Tamagotchi randomly visit
other Tamagotchi in the hive. 

![The Tama-Hive](/images/Screenshot_2020-10-18_182015.png)

Mercifully, Sprite released all his work on [his Git server](http://git.spritesserver.nl/tamatrix.git/). So all I have to do is
port his work over to whatever low-power platform I choose for the picture frame, maybe sprucing up the web page a little. Getting 
this to run on a standard Linux desktop is pretty simple too. I'll write more about that in the next post. Until then, it's time to 
start picking out...

## The Platform
Power efficiency is pretty much the most important factor in choosing a platform. If this is supposed to fit into a digital picture 
frame, I need it to be small, light, power efficient, and fairly easy to develop for. I'll list off a few of the platforms I explored
before deciding.

### Raspberry Pi Zero

The go-to these days for hobby projects is the [Raspberry Pi](https://www.raspberrypi.org/).

!["Raspberry Pi Zero GPIO Soldering Project" by ghalfacree is licensed under CC BY-SA 2.0](/images/22690970523_e8aa40049e_o.png)

The Pi Zero was an early contender. At just $5 from [Adafruit](https://www.adafruit.com/category/934?src=raspberrypi), the Zero is 
about as powerful as a first generation Pi and is about the size of a stick of gum. The problem is that they are typically powered 
by 5v cell phone chargers, and I was hoping to be able to hang this on a wall. (Batteries may be an option too, but I'd want weeks 
between charges, and most setups I've seen for the Pi are either giant, or only last a few hours.)

### ESP8266 

The other option is an [ESP8266](https://www.espressif.com/en/products/socs/esp8266). These low-power "WiFi-on-a-chip" devices have 
taken off in popularity, particularly among the DIY IoT crowd. It's even smaller than a Pi Zero, and With a sleep mode using as little 
as 20µA, this could be a solid candidate for the brains of the operation. They even sell ESP8266's mounted to Arduino flashers with 
plenty of GPIO pins to simplify development. These NodeMCU developement boards are what I've chosen for setup, but once I'm familiar 
with programming them, I may go with a more stripped down ESP8266 board for size and potential power consumption reasons. 
I'll write more about setting up and programming the NodeMCU boards in a future post. 

!["ESP8266 WiFi Module" by adafruit is licensed under CC BY-NC-SA 2.0](/images/15860222927_f1ef4005e9_o.jpg)

## The Display

### TFT Displays
These are pretty popular for small gadget projects as well. A small color display could be found for a few dollars. The main issue I have with these is that:
1. Back lit color displays seem a little distracting for what is supposed to be a background installation, 
2. They also tend to be a little power hungry. 

That being said, I picked one up for initial development. The visual feedback will be a massive time saver, and there are dozens of 
libraries for this type of display available. For the final product, I was hoping to go with something a little more exotic. Something like...

### E-Paper Displays
Ever since I picked up a Kindle Paperwhite, I've been thoroughly impressed by the e-paper displays available. Sure, the refresh rate
is abysmal, and anything more than black-and-white is a recipe for empty wallets, but they only use power when they refresh, and the battery on my Kindle lasts for weeks, which is perfect for my use case. 

!["Raspberry pi and a WaveShare E-paper screen" by Espen Klem is licensed under CC BY 2.0](/images/49347606687_6552cb87ab_o.jpg)

[Waveshare](https://www.waveshare.com/7.5inch-e-paper-hat.htm) makes a few of these kits that interface with Raspberry Pi. They also
 make an [esp8266 driver board](https://www.waveshare.com/wiki/E-Paper_ESP8266_Driver_Board) for their e-paper displays for about $20. 
So it looks like the display and platform can be found for around $80-$90. 

I've seen some videos that showed a complete refresh taking nearly 30 seconds, which is concerning. But I think there are ways of 
doing partial refreshes. Ghosting also wouldn't be much of an issue for my use case, I think. Very few of the pixels should move 
each second, so maybe that will be fine. I'll write more about my adventures in E-paper development in a later post.

## The Power

While I initially considered solar panels to get the setup as self-contained as possible, it feels like a lot more complexity and 
surface area to get it running. Not to mention that this will likely be hanging on a wall in a potentially dark office. So I think
trying to instead pursue low power consumption and a long-enough battery life is the way to go. (After all, very few people complain 
about changing the batteries in their wall clocks, right?) 

This might be one part of the design process that I put off until later. It could be that I come up with an attractive enough way to 
hide a cable that I might not bother trying to make it run off a battery. Besides, part of the goal of this project is to actually 
finish a project, and getting too down in the weeds about how to perfect the design has kept me from just getting started in the past. 
As with every other part of this project, I'll write more about this in a future post.


## Conclusion

Now that the initial platform is planned out, it's time to get to work on the software while I wait on the ESP8266 and displays to 
arrive. Check back again soon for part 2 of this on going project build.