---
title: "Breezy boots to brown blank screen then nothing?"
date: 2005-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by tommyr on 2005-10-16
I tried loading 5.10 today on a G3 ibook 500 USB with 320m of RAM and I get as far as the brown screen but no logo and nothing else happens. 

I tried the "live" and "live powerpc" option with no joy so far. 

Anyone have ideas? Any help appreciated. 

Tom

---

### Post by wrtpeeps on 2005-10-16
this may be completely useless to you, but i had this problem with 5.04, but it was a driver problem. Not sure if this will help.

---

### Post by tommyr on 2005-10-16
[QUOTE=wrtpeeps]this may be completely useless to you, but i had this problem with 5.04, but it was a driver problem. Not sure if this will help.[/QUOTE]


5.04 worked fine for me, for some reason I just can't get past this brown blank screen. I've tried 6 times now. 

Thank you for replying though!

Tom

---

### Post by thalavoy on 2005-10-17
[QUOTE=tommyr]I tried loading 5.10 today on a G3 ibook 500 USB with 320m of RAM and I get as far as the brown screen but no logo and nothing else happens. 

I tried the "live" and "live powerpc" option with no joy so far. 

Anyone have ideas? Any help appreciated. 

Tom[/QUOTE]

When I had a similar problem, I found that the problem was either with network (DHCP was running) or the date had been reset to Jan 1, 1900 (or something like that)

Siva

---

### Post by tommyr on 2005-10-17
[QUOTE=thalavoy]When I had a similar problem, I found that the problem was either with network (DHCP was running) or the date had been reset to Jan 1, 1900 (or something like that)

Siva[/QUOTE]


No network is hooked up, time/date is o.k., strange problem unless it's a known bug. Thanks for the reply.

Tom

---

### Post by jlapier on 2005-10-17
Same problem here - Live CD on a Power Mac G5. Booting with live-powerpc64 - I tried setting it for various resolutions, but as soon as X loads, I get a blank screen. I can hit CTRL-ALT-F1 and get a console prompt and jump around, but blank screen on X. 

Since I can get a console, can anyone think of any tests I can do from there to try to figure out the problem? I tried the video=ofonly switch on boot-up too, but that one just locked me up when X started.

---

### Post by jlapier on 2005-10-17
Ah - I made it work. I went into the console and checked /var/log/Xorg.0.log and found lots of lines complaining about hsync and vsync being out of range. Did:
sudo nano /etc/X11/xorg.conf

and changed HorizSync to 30-85
and VertRefresh to 75
and made the default resolution 1280x1024 (for the last mode, where DefaultDepth 24)

Then I killed the xserver (switch to X with ctrl-alt-F7 and hit ctrl-alt-backspace to kill it) and restarted with 'startx'.

It took me a few (meaning 15) tries to get HorizSync and VertRefresh to something that made X happy. I'm using an Apple Studio 17" CRT.

---

### Post by ceharon on 2005-10-27
I'm having the same problem, but I can't get the console to appear. :( 

Is there a way to boot straight to runlevel 1 (or 3)?

Thanks,
Charles

---

### Post by ceharon on 2005-11-03
Ok...Here's how I got it to work.

Boot to sigle user mode using the following boot parameters: 
**live capser-udeb/runlevel=S**

Then edit /etc/X11/xorg.conf, setting **HorizSync** to **70-73** and **VertRefresh** to **70-140**. (I'm using an eMac).

---

### Post by Phrostay on 2005-11-03
I have exactly the same problem. I'm using the v5.10 Ubuntu LiveCD! for PowerPC on my iMac G5 20". It works fine until it comes to X / Gnome (I think thats the one;)) and all I get is a brown screen & I cannot move my mouse or use my keyboard:(

---

### Post by elmerhomero on 2005-11-08
I have the same problem as Phrostay, after my 2GHz G5 tries to start live ubuntu I get the brown screen and the mouse cursor. The keyboard and mouse are frozen. CTRL-ALT-F1 does not work with this brown screen.   Can you give details on when to use this command or when and how give the command

capser-udeb/runlevel=S

and how to edit the etc/X11/xorg.conf? 

Thanks

---

### Post by ctt1wbw on 2005-12-27
I'm joining this club right now!  I have a 17" G5 iMac and I'm having the same problems too.  Brown screen, not able to move the mouse, yada yada yada.  I tried the Live cd several times using live-powerpc and live-powerpc64 to no avail.  I'm downloading the Kubuntu live ppc version now.  Let's see how that goes.

---

### Post by josue on 2006-02-17
Arg, i have the same problem on a rev 2 iMac G5.

---

### Post by linear on 2006-02-17
Have a look at this thread:
 
[http://ubuntuforums.org/showthread.php?t=130040](http://ubuntuforums.org/showthread.php?t=130040)

---

