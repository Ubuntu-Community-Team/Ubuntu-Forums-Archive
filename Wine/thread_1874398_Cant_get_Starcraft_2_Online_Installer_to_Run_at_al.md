---
title: "Cant get Starcraft 2 Online Installer to Run at all!!!"
date: 2011-11-03
forum: Wine
---

### Post by kanazky on 2011-11-03
I have isntalled, Wine, winecfg, winetricks, gecko
I did the mmapi disabled trick.

I downloaded the Starcraft 2 Installer from their website.

When I double click the exe I get "The application could not be executed for some reason. Please close all applications and try again."

I am using 64-bit Ubuntu.

I have consulted the wikki.

Heres the output of wine when running:

> [root@myhost jacob]# wine '/home/jacob/StarCraft_2_NA_en-US.exe'
fixme:process:GetLogicalProcessorInformation ((nil),0x32e368): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 60000
err:wincodecs:JpegDecoder_CreateInstance Failed reading JPEG because unable to find libjpeg.so.8
fixme:ole:CoCreateInstance no instance created for interface {9edde9e7-8dee-47ea-99df-e6faf2ed44bf} of class {9456a480-e88b-43ea-9e73-0b2d9b71b1ca}, hres is 0x80004005
err:ole:OleLoadPicture IPersistStream_Load failed

Any idea on how to fix the battle.net online installer?

---

### Post by kanazky on 2011-11-03
Was missing l32-LibJpg <-- or something close to that found it in the arch linux wikki :D thanks tho!

---

### Post by dino99 on 2011-11-03
**** Failed reading JPEG because unable to find libjpeg.so.8 ****

so open synaptic to check if that(these) libjpeg* is(are) installed
(on my system libjpeg8/libjpeg62/libjpeg-progs are installed)

---

### Post by sffvba[e0rt on 2011-11-03
*Thread moved to **Wine**.*

*(Was between here and gaming and leisure so wasn't sure which would be more appropriate.)*


404

---

