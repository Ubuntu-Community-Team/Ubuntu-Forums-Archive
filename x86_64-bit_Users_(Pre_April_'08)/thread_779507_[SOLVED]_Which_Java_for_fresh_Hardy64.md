---
title: "[SOLVED] Which Java for fresh Hardy64?"
date: 2008-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by nowhere@cox.net on 2008-05-02
Hey all,

I'm running Hardy LiveCD and everything seems flawless so far. I even got wvdial working with my Sprint EVDO out of the box (only needed a conf file edit). 

I can't think of any way to test the nvidia resistricted drivers and Compiz tho. Need to reboot after installing the drivers which isn't a persistent deal, yes?

Anyway, my question is I want to try out Eclipse and I need Java. I know Java's plug-in is still 32 bit so which package do I install? My Gutsy install is all messed up from installing and uninstalling 32bit libs

In return, here's a quick list of what works on my hardware:
The System:
> Lenovo T61 T7500 2.2GHz Core 2 Duo
nvidia NVS140 discrete graphics
4GB RAM
no bluetooth 
Intel 4965 WiFi
80GB hard drive

What works (absolutely no tweaking, except where noted)
> Wifi 
Sound
Volume Function Keys
Screen Brightness function keys (all the way to full brightness)
Power Info function key
Multimedia function keys (next, prev, play/pause, stop)
iPod support in Rhythmbox
Sprint EVDO using USB Novatel U727 EVDO modem (modified /etc/wvdial.conf with connection details only)
Touchpad
Thinkpad eraser mouse
Firefox 3 no issues
flash-plugin via Synaptic installed 32bit libs and plug-in flawlessly
sleep and hiberate


So far very nice!

Concerns:
> nvidia proprietary drivers may break screen brightness function keys
nvidia proprietary drivers may break sleep
nvidia proprietary drivers WILL break hibernate (from what I have read)
Some add-on haven't been updated for Firefox 3 yet

Will take the plunge, backup Gutsy, format my ext3 partition and fresh install Hardy this weekend!

---

### Post by Sef on 2008-05-02
Download OpenJava through Add/Remove, Synaptic, or the terminal.  You may want to read [my sticky]("http://ubuntuforums.org/showthread.php?t=774956") about it too.

Moved to 64-bit forum.

---

### Post by nowhere@cox.net on 2008-05-06
I installed the openjdk package and dependencies via synaptic and it seems to work fine. Had some troubles with Eclipse but mostly my inexperience with the tool and how it works.

It all seems to be working fine so far with java-6-openjdk.

Thanks Sef!

---

