---
title: "[SOLVED] 8.10 AMD64 - tvtime , winfast and motherboard audio connector ==&amp;gt; no sound c"
date: 2008-10-31
forum: x86 64-bit Users
---

### Post by nedmar on 2008-10-31
Hi, 
I must say I'm using Ubuntu only from a few weeks now, and I have no previous experience in using any kind of linux, so .. you got the idea.. :) 

**Hardware Description:**

TVTuner: Leadtek WinFast TV 2000 Expert 
Motherboard: [GA-K8NF-9-RH]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2296")

**Problem:**
There is no Audio Connector on the motherboard to insert the audio output/input cable from the tvtuner except the CD In Connector so i used the CD In Connector.

Working fine under Windows OS, but when i switched to Ubuntu and installed tvtime .. the only way to control the sound is from the case volume buttons.. 

The sound bar in tvtime is sliding if I press let/right arrows as well when I press the multimedia keyboard buttons, but nothing else happens.
If I go to the Volume Control and slide up/down the CD track, the sound volume in tvtime increase/decrease as supposed to do.


**Question:**
 How do i bind the sound control in tvtime to the CD Track ( visible in the Volume Control).Is there any other way around to make it work? 

**P.S.** 
The problem is the same no matter what other program I use to watch TV.So I guess is not about the programs I used.

Waiting for a solution. Thank You all.

---

### Post by nedmar on 2008-10-31
SOLVED 

The solution was quite simple..```
~$ sudo gedit ~/.tvtime/tvtime.xml
```
then , in the tvtime.xml change the default value:
```
<option name="MixerDevice" value="/dev/mixer:[COLOR="Red"]line[/COLOR]"/> 
``` to 
```
<option name="MixerDevice" value="/dev/mixer:[COLOR="Red"]cd[/COLOR]"/>
```. Save it and just run tvtime.

Ty all anyway :)

---

