---
title: "Troubles with .wine ( World of Warcraft)"
date: 2008-08-22
forum: Wine
---

### Post by TOAB on 2008-08-22
Complete linux beginner here... and I mean absolutely no idea what I'm doing.

I've tried to follow the step-by-step directions at [https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft"), but I'm pretty sure I messed something up somewhere along the lines.

Install method was done by copying the tome files to a folder on the drive, and running the executable. After install the file Launcher.exe appears to be functioning normally, but when wow.exe opens (pressing play, or running "wine "C:\games\World of Warcraft\WoW.exe"(only place I deviated from the directions was in the installpath I believe) " The program appears to launch, I'm greeted with a black screen, a drop in resolution, as if it were a first launch, audio, and then it crashes. 

The WoW error reporting util to submit info about crashes to Blizzard says I'm missing a few DLL's in my system32 directory. Terminal also tells me ```
toab@toab-laptop:~$ wine "C:\games\World of Warcraft\WoW.exe"
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7cc40000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cc40000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ece0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f328,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6ec,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set


```

The audio for the intro video continues to play until I close the session of Terminal that I launch from.

Using the restricted nvidia drivers, I believe I've correctly configured the audio, and video in winecfg.

---

### Post by Oldsoldier2003 on 2008-08-22
Moved from ABT to wine, where you should get a little more visibility from the folks that can help.

---

### Post by denali on 2008-08-22
Can you show us your config.wtf?  When you post it, make sure your account name and server info are NOT posted.  Security is important.

Also, what type of nVidia card do you have? What version of Wine are you running?

---

### Post by anthony.phipps on 2008-08-22
See here for basic setup
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

See here for links to the DLL files you are missing, and more! =P
[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

---

### Post by TOAB on 2008-08-22
> **denali said:**
> Can you show us your config.wtf?  When you post it, make sure your account name and server info are NOT posted.  Security is important.

Also, what type of nVidia card do you have? What version of Wine are you running?
I actually didn't have a config.wtf as the program had yet to successfully launch. I actually got a friends config.wtf and I got the program to launch :) 

Since the program was crashing and leaving my screen res at the default WoW resolution, it seems to have messed with my display drivers, and I can't seem to get it back to 60hz from the 50hz it's stuck at now. (this is in ubuntu, not WoW)

Video card is a 512mb Nvidia 7900GTX Go. Native screen res is 1920x1200.

edit:Thanks for your help

---

### Post by aer0nz on 2008-08-23
sudo apt-get install nvidia-settings

and then just

sudo nvidia-settings

you'll be able to change all of that, screen res, refresh rate, whatever you feel like changing.

---

### Post by gjoellee on 2008-08-23
> **anthony.phipps said:**
> See here for basic setup
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)


is very important to make WoW work!

---

### Post by khanse on 2008-08-23
FAO and EBRD helping Georgian wine producers protect appellations and capture new markets

A four day wine sector tour in Italy, organized by the European Bank for Reconstruction and Development (EBRD) and FAO, will focus on improving marketing strategies and protecting Georgia’s geographical appellations. The study tour, which takes place from the 16th to the 19th of July 2007, aims to improve Georgian wine producers’ capacity to stimulate demand for their products in the global market.

A team of 11 wine sector stakeholders from Georgia is participating in the study tour, which is fincaned by Canada. The Georgian team, led by Mrs. Lily Begiashvili – the Georgian Deputy Minister of Agriculture – will tour key wineries including Antinori (Orvieto Classico appellation), Ruffino (Chianti Classico appellation) and Masi (Amarone della Valpolicella Classico appellation), where “best practices” in the Italian wine sector will be showcased. In addition to the tour of Italian wineries and associations of wine-makers, the participants will attend a seminar organized by FAO experts and key Italian wine industry players such as - inter alia - the Italian Trade Commission (Istituto nazionale per il Commercio Estero - ICE), the Italian Wine Union (Unione Italiana Vini), Federvini and the National Committee on Wine Appellations (Ministry of Agriculture). The seminar will focus on the importance of collective action and empowerment initiatives such as wine producers associations in capturing new markets and protecting geographical appellations.

FAO has been supporting the development of the Georgian wine sector since 2000 when, at the request of the Government, it provided assistance in drafting Georgiá’s first wine law. The law instituted an appellation of origin labelling system which provides details about where the wine comes from, the grapes used in it and how it was produced. Despite this tracing system, the Georgian wine sector continues to be plagued by counterfeiting. It was affected by the banning of wine exports to Russia - its biggest export market - in 2006.

“Georgia’s wine industry has to broaden its markets” says Emmanuel Hidier of FAO’s Investment Centre. “It has to stimulate demand for its appellations in large wine markets such as the EU and North America.” The seminar will explore ways to do just that and learn from the Italian experience. At the same time it will discuss the geographical appellations issue and learn from the Italian know-how how best to protect and promote such appellations.

For Study tour details, please see Protection of wine appellation

here is a link

---

### Post by aoanla on 2008-08-23
> **TOAB said:**
> 
Since the program was crashing and leaving my screen res at the default WoW resolution, it seems to have messed with my display drivers, and I can't seem to get it back to 60hz from the 50hz it's stuck at now. (this is in ubuntu, not WoW)

Are you sure this isn't the setting it was at, previously? The nVidia drivers don't report the true refresh rate to X, for some reason, so the 50Hz mode reported by Ubuntu is very likely at 60Hz really.

---

