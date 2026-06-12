---
title: "Ubuntu 7.10 64 bit BLUETOOTH nightmare - please help"
date: 2007-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by havokz on 2007-12-02
I have a fresh install of ubuntu 7.10 with all the updates installed.

bluetooth / bluez-utils / blueman and all required dependencies as well as gnome-vfs-obexftp

lsusb detects my bluetooth dongle fine and hcitool scan finds the phone a W810i

First let me tell you what i can do with bluetooth------

 Using Bluetooth file sharing (gnome-obex-server) i can send any file from the phone to the computer without any problems

Using Blueman i can pair the computer and the phone without any problem

Using Blueman again i can connect rfcomm (serial service) to use the phone as a remote control


Now for the PROBLEMS -----

I cannot browse the phone either from Blueman or Nautilus

In Blueman when I try to browse it says Cannot connect to obex://[       ] Check if the service is running

In Nautilus the phone icon shows up and when i select it the authentication process starts on my phone and then phone is connected for 1 sec and immediately disconnects

When I use send file in Blueman i get an error "Unable to connect to remote device"

From the terminal gnome-obex-send i get the following

Browsing 00:1A:75:4F:32:48 ...
Service Name: OBEX Object Push
Service RecHandle: 0x10006
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 6
  "OBEX" (0x0008)
Service Class ID List:
  "OBEX Object Push" (0x1105)
** Message: device 00:1A:75:4F:32:48 (OBEX Object Push) port 6


** (gnome-obex-send:7949): WARNING **: Unable to make a Bluetooth connection.

** (gnome-obex-send:7949): WARNING **: Unable to initialize OBEX client source


Can anyone help me cause I am slowly getting to the end of my rope :-) with frustration

---

### Post by havokz on 2007-12-02
UPDATE: This problem seems to be specific to w810i phone as I have tested the above configuration with a NOKIA 6300 and everything works!!!!!


Could it be that the OBEX PUSH Channel is 6 on the w810i and on the NOKIA 6300 it is Channel 9???

Waiting, hoping for a solution............

---

### Post by havokz on 2007-12-02
While i was waiting for replies i decided to shutdown my phone w810i

when I restarted it gnome-obex-send and Blueman browsing WORKED


I don't know how??????


Well at least it's working for now....... now on to Wiimote :-)

---

### Post by MichaelSM on 2007-12-02
It's amazing what re-starts can do.

The software in mobiles and PCs can't always adjust during a  session.

So many posts on this Forum relate to this. 

The gadgets, whichever they are, are simply brilliant binary data-processors after all. Once they receive a new input, it depends upon the algorithm running them as to whether or not they can organise the data input in  real time.

Say, for instance, one receives an mpeg file. From wherever. Our previously-installed programs are able to process it because they  recognise the input and are able to run it.

So, a session starts with trillions of known parameters, then along comes an input which doesn't fit the 'known' database. DURING THAT SESSION. What I mean by the 'known ' database is what the PC or mobile had in hand at the time.when it was booted.

Along comes a perfectly acceptable piece of software which is digested up to a point; But it wasn't there at the previous boot, if you catch my drift.

Having digested the new executable package, we re-boot, and there it is.

Any re-boot after a new install takes longer than a normal start-up. We're beginning a new session with extra bits to be attached, which have to be categorised and frameworked.

The framework is always there, as long as the package is acceptable.

Re-boots kill hard drives.

Eventually flash drives will overcome their immense problems.

Cheers,

Mike.

---

### Post by Non Plus Ultra on 2008-01-09
Yep, also for me a restart of the W810i did the trick. Annoying how much time you can spend trying to solve a problem which is resolved by restarting your device....

---

### Post by steveneddy on 2008-01-11
I was wanting to figure out how to browse my phone (MotoRazr V3) and this post helped me identify the correct software to install.

I can now browse my phone whereas before all I could do was share files between PC and phone.

Bluetooth is a wonderful toy and has turned into a very useful tool. In my office, all of the phones and PC laptops have bluetooth enabled and we can share files, pics and other things with each other to help streamline the work flow (whatever, we are sharing jokes and DLed music).

What would we do without Bluetooth?

I have a Bluetooth mouse on my laptop and it works great.

I use Blueman as a Bluetooth interface.

:popcorn:

---

### Post by John Jason Jordan on 2008-01-11
> **steveneddy said:**
> I was wanting to figure out how to browse my phone (MotoRazr V3) and this post helped me identify the correct software to install.

I can now browse my phone whereas before all I could do was share files between PC and phone.

Bluetooth is a wonderful toy and has turned into a very useful tool. In my office, all of the phones and PC laptops have bluetooth enabled and we can share files, pics and other things with each other to help streamline the work flow (whatever, we are sharing jokes and DLed music).

What would we do without Bluetooth?

I have a Bluetooth mouse on my laptop and it works great.

I use Blueman as a Bluetooth interface.
I also have a Razr V3. Using Blueman I can see the phone, but I've never succeeded in transferring files or even browsing it. However, I can browse it and transfer files via USB with moto4lin, so I don't really care about the bluetooth capability. 

I love bluetooth also, but I have another problem. Until the other day I used a Logitech V270 mouse, plus I have Sony DR-BT50 audiophile headphones. Every time I moved the mouse the sound would cut out. I never succeeded in troubleshooting this, although it was discussed at length in another thread.

I also have a problem with the mouse, in that it broke after only two months of normal use. It just quit working. Over the past three years I have had other Logitech USB notebook mice that use the same exact case and probably some other identical components. They don't hold up very well. After googling I discovered that there seems to be a pretty high failure rate with the entire line.

Since I am shopping for a replacement, which bluetooth mouse do you use and have you had any problems with it?

---

