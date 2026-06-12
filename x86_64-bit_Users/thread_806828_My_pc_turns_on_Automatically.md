---
title: "My pc turns on Automatically"
date: 2008-05-25
forum: x86 64-bit Users
---

### Post by accodata on 2008-05-25
Hi

I have Ubuntu 8.0.4 installed, after I turn it off at night, when I get up in the morning, my tower is already on.

I know I definitely turn off my system, how do I rectify this please?

thanks

:confused::confused:

---

### Post by briandu on 2008-05-25
Could it be that in your bios you have wakeup_on_lan enabled? Some bios are sensitive to this and you router/modem is polling so it wakes up your pc.

Just check this first - hopefully this will remedy your prob - I had something similar.

---

### Post by aaron.d on 2008-05-26
> **accodata said:**
> Hi

I have Ubuntu 8.0.4 installed, after I turn it off at night, when I get up in the morning, my tower is already on.

I know I definitely turn off my system, how do I rectify this please?

thanks

:confused::confused:


Yes, if you are 100% sure you have halted the system entirely (make sure you are not doing some power management/hibernation), then this is most definitely a BIOS issue and not related to OS. Check WOL (Wake-on-LAN) settings, as well as power down settings; make sure pressing power button turns PC OFF, and turn off any options that automatically power on/boot after a power outage situation.

---

### Post by accodata on 2008-05-27
ok, and I find that out how???



> **briandu said:**
> Could it be that in your bios you have wakeup_on_lan enabled? Some bios are sensitive to this and you router/modem is polling so it wakes up your pc.

Sorry I have no idea

Accodata

---

### Post by aaron.d on 2008-05-27
> **accodata said:**
> ok, and I find that out how???





Sorry I have no idea

Accodata

You know what a BIOS is, no?

if not [READ HERE.]("http://en.wikipedia.org/wiki/BIOS")

to enter the bios you will have to restart the computer and press a button while the computer is in the initial POST (power-on self-test), which comes right after a very brief initialization of the graphics card (its around the time your computer will beep, if it does that sort of thing on boot).
The key you need to press should be shown, typically at the bottom of the screen with a message link "press XX to enter setup" or something of that nature.

Common setup entry keys are: delete (most common), F2, F12, F1, Esc ...

BIOS setup vary from vendor to vendor, but the Wake On LAN and power state settings would usually be found under Power Management Settings, or one of the Advanced configuration menus.

Or, if all else fails, unplug the ethernet cable one of these nights when you shut the computer down. 


P.S. 

Have you tried shutting it down and WATCHING it to see how long it takes?

---

### Post by Joeb454 on 2008-05-27
Don't forget to check that some BIOS's allow you to set a time to boot up daily - and it will then boot the PC at that time.

---

