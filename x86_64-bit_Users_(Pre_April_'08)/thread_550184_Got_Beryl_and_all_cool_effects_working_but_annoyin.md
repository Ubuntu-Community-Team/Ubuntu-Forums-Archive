---
title: "Got Beryl and all cool effects working but annoying flicker"
date: 2007-09-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by alvarez1900 on 2007-09-13
I have everything working perfectly.. I have ripple effects, cube, wobbly, etc. 

 However I keep getting this flicker that comes across the screen randomly.. sometimes a lot and sometimes not for a bit. I think it might in some way be connected to the touchpad. I am on a G53-AV660 Toshiba Qosmio and its at 1920x1200 and looks beautiful but the flicker is peaving me off pretty good heh.

 The whole time it took to write this it hasn't done it further backing my touchpad theory. argh.

 Any Ideas?

---

### Post by alvarez1900 on 2007-09-13
its a nvidia go 7600 card btw

---

### Post by alvarez1900 on 2007-09-13
maybe not on the touchpad I was reading something and it just did it randomly. argh!

---

### Post by sicknessjb on 2007-09-13
any chance why you didnt end up using compiz fusion?

---

### Post by alvarez1900 on 2007-09-13
I am very new to all of this and have been soaking up all I can learn... I was told to install beryl after envy and got all the visuals running. Why would I want compiz over Beryl?

 This is pretty barebones but I am making a transition from windows if I can... here is what it looks like currently

[http://www.ramzmusic.com/pics/Screenshot.png](http://www.ramzmusic.com/pics/Screenshot.png)

and 

[http://www.ramzmusic.com/pics/Screenshot2.png](http://www.ramzmusic.com/pics/Screenshot2.png)

---

### Post by alvarez1900 on 2007-09-13
I have heard you can get animated backgrounds etc running but I haven't gotten that far... right now I just wanna stop this stupid flicker that keeps happening...

 I have selected Gnome window manager and  GTK window decorator essentially stopping beryl completely and its still flickering :(

---

### Post by Jouke74 on 2007-09-14
Check what is your refresh rate under the monitor settings. You might need to adjust that in your configuration files.

---

### Post by alvarez1900 on 2007-09-14
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

 Its a high def Toshiba monitor 1920x1200 laptop display. Under screen resolution it is at 50

 Haven't messed with the HD-DVD player yet but hopefully I can find drivers for that eventually too. 

 You think that refresh rate needs tweaking?  a bunch of peeps over at another forum I post at think I should ditch the 64 bit ubuntu as it offers no major difference if you don't have 4gig ram they said. except an encoding boost. I will say on all my other computers ubuntu 32 runs flawlessly but they aren't near as high powered as this laptop or have 1920x1200 display heh.

---

### Post by miggols99 on 2007-09-14
You should try Compiz Fusion, which is much better and more stable than Beryl. There's a repo you can use to get it. I've got it here and I love it :)

---

### Post by alvarez1900 on 2007-09-15
I have compiz runnin I like it and like the plugins better but I liked how easily tweakable beryl was in the manager. 

 Nonetheless the flicker is gone now so ultimately I am happier :)

 Does WINE work more stable in the 32 bit ubuntu? I have been having trouble installing quicktime plugin into firefox. I can't even get the slim installer to work I open with wine and nothing happens.

---

### Post by alvarez1900 on 2007-09-15
The flicker is back with compiz and I have found the problem... this time in the terminal window that runs my compiz and emerald the errors are showing. it flickers everytime it has the unhandled error.




Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:6074): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6074): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6074): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

(emerald:6078): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6078): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6078): Wnck-WARNING **: Unhandled action type (nil)

(emerald:6078): Wnck-WARNING **: Unhandled action type (nil)

---

### Post by alvarez1900 on 2007-09-17
noone knows?

---

### Post by alvarez1900 on 2007-09-19
bump

---

### Post by alvarez1900 on 2007-09-19
rebump

---

