---
title: "Warcraft III TFT LAN Issues"
date: 2011-09-03
forum: Wine
---

### Post by Grimmedslug on 2011-09-03
Searched around for a few hours, but on all areas of looking (both WineHQ and Ubuntu Forums) the problem tends to be more of the acceptEx patch, which had already been patched in the updated version.

Cut a long story short, this was the first time I played around with Wine, managed to install TFT, update to latest patch, single player & battle.net (hosting and joining games) worked perfectly. Then on to LAN.


**_Problem_**

I first tried using Garena, which I did manage to install successfully using Wine (Garena Classic), being able to do everything except see games in Warcraft III LAN despite how everyone is on the chat advertising it. So I figured, maybe that's why everyone's complaining online that Garena isn't working. Uninstalled it.

Subsequently, I tried using DotaPod, which uses Java to form an internet connection with the server. It was designed to even work with Linux, and I figured it would work fine. Except when I joined the games that I could see on LAN, it basically just gets stuck and becomes so unresponsive that I have to turn it off using System Monitor.

Clean reinstalled wine (deleted .wine) and the WCIII programs with the same outcome.

Anyone encountered such issues?


**_Full Description_**

System: 
Ubuntu 11.04 64-bit dual boot with wubi
Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz
Nvidia GeForce GT 220M
DDR2 4GB RAM

(Ps this system specs clearly runs more than WCIII, I'm used to playing SCII with it on Windows boot and it is definitely more intensive on the system)


Wine:
v. 1.3.27 (obtained off Ubuntu Software Center)
No use of Winetricks


What I did (on clean install):
1. Ran wine uninstaller
2. Used add/remove program function for both RoC and TFT
3. Used add/remove program function to run 1.26a full patch
4. Enabled Gfx OpenGL on regedit
5. winecfg to run in virtual window (else I cannot even control terminal functions unless I run in windowed mode, essentially both have the same outcome)
6. Downloaded Java file from DotaPod, which connected me to a server.
7. Opened TFT, went to LAN, selected game.
8. ???
9. TFT freezes for the next 30 minutes until I decided to end system process.


> wyz@ubuntu:/media/DATA/Program Files/Warcraft III$ wine "Frozen Throne.exe"
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f300,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5d4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f60c,0x00000000), stub!
wyz@ubuntu:/media/DATA/Program Files/Warcraft III$ fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 8 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x14f3b8,0x148088): stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented TransmitFilePlease help, made this as detailed as I can. Thank you :)

---

