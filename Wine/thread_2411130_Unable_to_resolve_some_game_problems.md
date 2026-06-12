---
title: "Unable to resolve some game problems"
date: 2019-01-25
forum: Wine
---

### Post by victor9212 on 2019-01-25
Greetings to every one. The problem im having is i can not start some .exe files with Wine and Windows games installed thou Steam do not always run. I'm having problems with one game in particular:Fiesta online NA.
It's installed thou Steam with Proton 3.16-beta(if im not wrong) for compability. 
A while back i installed the game just fine with the client from the official site(now the client from gamigo.com starts and crashes without even showing any interface on the desktop).
So i started it throw terminal and here's what i got:
```
wine /home/neef/.steam/steam/steamapps/common/Fiesta_Online/FiestaOnline.exe
000f:err:service:process_send_command receiving command result timed out
000f:fixme:service:scmdatabase_autostart_services Auto-start service L"WineBus" failed to start: 1053
Unknown heap type: CLR


0009:err:ole:CoGetClassObject class {d27cdb6e-ae6d-11cf-96b8-444553540000} not registered
0009:err:ole:CoGetClassObject no class object {d27cdb6e-ae6d-11cf-96b8-444553540000} could be created for context 0x1
0009:fixme:wincodecs:JpegDecoder_Frame_CopyPalette (0x169ee4,0x1623f8): stub
libgluezilla not found. To have webbrowser support, you need libgluezilla installed
```

My computer is with a AMD Athlon 64bit 2.3Ghz dual core, 2Gb RAM, Geforce gt710 2Gb gddr5(althou i dont think it's important), Currently runing with Linux Mint 18 64bit.

Sorry for the typos(i know there are some). Any help is appreciated.

---

### Post by slickymaster on 2019-01-25
Thread moved to **Wine** for a better fit

---

