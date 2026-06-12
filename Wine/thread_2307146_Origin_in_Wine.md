---
title: "Origin in Wine"
date: 2015-12-22
forum: Wine
---

### Post by eagerlinuxlearner on 2015-12-22
Hey, new Ubuntu convert here.

I was trying to run Origin in Wine without asking for help for as long as I can, but every time I open the program, it shows the loading for the login then crashes. I have the crash log from Origin itself as well as the terminal output.

Specs:
Xubuntu 15.04
Wine version 1.7.50
Nvidia GeForce Go 7950 GTX
4 GB ram

Both terminal output and Origin itself's crash report are in attached zip file because they are so long and I do not want to clog the forum with the text. They're too long for me to even attach here!

Winecfg (as much as I can find that I've configured, since I am very new to wine)
Default Windows Version: Windows 7

Library DLL Overrides (holds breath, there's a long list...)
devenum (native)
dxdiag.exe (native)
dxdiagn (native)
iexplore.exe (native, builtin)
itircl (native, builtin)
itss (native, builtin)
jscript (native, builtin)
msctf (native, builtin)
mshtml (native, builtin)
quartz (native)
shdoclc (native, builtin)
shdocvw (native, builtin)
shlwapi (native, builtin)
updspapi (builtin)
urlmon (native, builtin)
wininet (native, builtin)
xmllite (native, builtin)

Graphics (from Winecfg):
Screen Resolution: 96 dpi
Window Settings (only listing ones that are turned on):
Allow the window manager to decorate the windows
Allow the window manager to control the windows

Desktop Integration: No themes, completely default

Audio: Totally default

Drives:
C: (my C drive in wine)
Y: (winetricks cache)
Z: (main Ubuntu drive)


Other Wine Programs Installed:
Notepad
MS Paint
IE 8 (I read it would help make Google Drive work in Wine or else I wouldn't have bothered. SPOILER ALERT: It didn't.)

-------------
Whew, that's a mouthful. If there's anything I forgot let me know and I will do my best to find it. I hate having to ask for help but at the same time it's how I learn so maybe I can one day help fellow Ubuntu newbies out.

Thank you all!

---

### Post by sweldon001 on 2016-01-04
1st install wine Tricks then install all plugin / features available from it .. then try again if you haven't already installed all *.dll and or directx components as well as font sets, and or Ethernet patch files from winetricks

---

