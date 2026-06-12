---
title: "Another Orbiter nerd"
date: 2020-03-15
forum: Wine
---

### Post by dan3712 on 2020-03-15
Good day, all. Hope everyone is doing well, especially with current affairs. If you need something to do, hopefully this might keep you entertained.

Current system configuration:
HP 15-dy1023dx laptop
15.6" diagonal HD SVA BrightView micro-edge WLED-backlit touch screen (1366 x 768)
lspci output: VGA compatible controller: Intel Corporation Device 8a56 (rev 07)
Ubuntu 18.04.4 LTS
Wine 3.0-1ubuntu1
No other wine applications in use, including PlayOnLinux

I've tried using both Windows 7 and 10, with similar results.

Terminal output (after about 25 minutes of play)
0009:err:winediag:MIDIMAP_drvOpen No software synthesizer midi port found, Midi sound output probably won't work.
wine: Unhandled page fault on write access to 0xffffffff at address 0x12244f88 (thread 003d), starting debugger...

[1]+  Exit 5                  wine orbiter.exe

The play is actually really good, until it simply stops. I attached screenshots of the moment of crash. I also saved the backtrace file, if that's useful. But I don't know how to interpret the data.

Again, hope everyone and their loved ones are safe.

Dan.

---

### Post by mastablasta on 2020-03-17
perhaps a library is missing or some other thing?!

also maybe time to try out Kerbal space program, though that one costs. i hope they reduce prices so at least people could buy some stuff for the quarantine sessions.

---

### Post by dan3712 on 2020-03-18
Thanks for the reply!

So I discovered PlayOnLinux, and it seems to be working. But I don't understand why. As I understand, it is a front end for Wine. I have to dig in a little more to figure this out.

I'm not really opposed to Kerbal. But I've been using Orbiter for years and am used to it. I really just wanted to ditch Windows. It was starting to get too creepy. &#128556;

- Dan

---

### Post by mastablasta on 2020-03-19
PoL is not the same as Wine. they use Wine and provide a front end to it. not sure it is the same version of wine.

it is very likely a different version if you used a PoL scrip to install it or it provides the stuff that is needed for smooth run.

---

### Post by dan3712 on 2020-04-05
I found an older how-to for running Orbiter using Wine. It seems like win32 is the way to go. So I made a win32 prefix, and installed some libraries through winetricks (as recommended by the how-to)... vcrun2005, vcrun2008, vcrun2010, vcrun2012, vcrun2013, vcrun6, vcrun6sp6, vcrun2015, and corefonts.

It seems like it is perhaps more stable as I'm getting up to over 30 minutes of game time before I get the same error. Below is the error output in Terminal:
                        [FONT=courier new]couldn't load main module (2)
[/FONT]
[FONT=courier new]Process of pid=0008 has terminated[/FONT]
[FONT=courier new]No process loaded, cannot execute 'echo Modules:'[/FONT]
[FONT=courier new]Cannot get info on module while no process is loaded[/FONT]
[FONT=courier new]No process loaded, cannot execute 'echo Threads:'[/FONT]
[FONT=courier new]process  tid      prio (all id:s are in hex)[/FONT]
[FONT=courier new]0000000e services.exe[/FONT]

[FONT=courier new]    00000022    0[/FONT]
[FONT=courier new]    0000001d    0[/FONT]
[FONT=courier new]    00000013    0[/FONT]
[FONT=courier new]    00000010    0[/FONT]
[FONT=courier new]    0000000f    0[/FONT]
[FONT=courier new]00000011 winedevice.exe[/FONT]
[FONT=courier new]    0000001c    0[/FONT]
[FONT=courier new]    00000017    0[/FONT]
[FONT=courier new]    00000016    0[/FONT]
[FONT=courier new]    00000012    0[/FONT]
[FONT=courier new]0000001a plugplay.exe[/FONT]
[FONT=courier new]    0000001f    0[/FONT]
[FONT=courier new]    0000001e    0[/FONT]
[FONT=courier new]    0000001b    0[/FONT]
[FONT=courier new]00000020 winedevice.exe[/FONT]
[FONT=courier new]    00000029    0[/FONT]
[FONT=courier new]    00000024    0
[/FONT]
[FONT=courier new]    00000023    0[/FONT]
[FONT=courier new]    00000021    0[/FONT]
[FONT=courier new]00000027 explorer.exe[/FONT]
[FONT=courier new]    0000002c    0[/FONT]
[FONT=courier new]    0000002b    0[/FONT]
[FONT=courier new]    0000002a    0[/FONT]


Not using PlayOnLinux, as I had tried before. If anybody has any tips, I'd greatly appreciate them. For now, I'm just going through WineHQ FAQs and the documentation to learn as much as possible.

Thanks!
Dan

---

