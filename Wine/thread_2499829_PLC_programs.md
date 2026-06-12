---
title: "PLC programs"
date: 2024-08-12
forum: Wine
---

### Post by odddsocks on 2024-08-12
I am fairly new to Linux, Tried Zorin, now Umbuntu with Wine. Bottles is a great idea.

really keen to run my PLC program on Linux, 
has Windows lost its way, bloatware, waiting for next blue screen!

Programs I want to run:-
Rockwell Studio 5000. loaded 'dotnet 8.0'
HMS eCtacher runs, certainly can login, but won't run VPN tunnels - eWon hardware fab for remote support.
Yaskawa Speed 7, has issue with Winpcap
Lenze PLC designer looks like it works, won't access CANbus networks PCANview, or PCAN explorer.
Movicom 11
Automation direct Cmore tools.


Linus seams popular with gamers & basic computer apps.
but connection to specific hardware is huge.

thanks Dr Joe.

---

### Post by Holger_Gehrke on 2024-08-12
Running anything that more or less directly controls unusual hardware - meaning devices which aren't sitting on everybody's desktop by the millions - is highly unlikely to work with Wine. Either the functionality available in Windows for controlling that hardware isn't translatable or you need a driver from the manufacturer of said hardware (which would be very different for Linux as opposed to a driver for Windows). Basically Wine is a translation layer: programs make calls to Windows system functions, Wine intercepts those calls and makes it's own calls to Linux system functions and works the results into the form that the program expects and passes those results back to the program. With the number of functions available in the various APIs Windows offers, it's not surprising that a lot of functionality either doesn't (yet ?) exist in Wine or only exists as a stub.

Your best bet in this situation really is to look for a Linux-native application for your needs or to let the makers of the programs you use know that a Linux version of their software would be very welcome.

Holger

---

