---
title: "Some help needed (WoW/graphics problem) !!"
date: 2008-10-24
forum: Wine
---

### Post by Iron Coney on 2008-10-24
Hello all. Very new to Linux, switched over from windows and overall Ive been extremely impressed, and I love it, but lately Ive been getting major issues playing World of Warcraft. 

Obviously I messed something up...I had WoW working, after quite some time of configuring my ATI card, and adding config to WoW, I got it working quite well a few days back, except for an annoying glitch when I walk indoors, the screen goes crazy, and I have to relog. Not a huge deal, but I wanted to fix it, well this morning I guess I got greedy, lol...

So anyway I read somewhere online that putting the following into the terminal will fix the issue...

sudo /etc/init.d/gdm sto

sudo startx `which wine` wow.exe

Basically it froze at that point and my computer has been royally jacked up ever since. Upon reboot I got a message saying "Low Graphics Mode...Your Screen and Graphic Card could not be detected correctly..." or something to that effect. I tried reconfiguring it, and its still not quite right. Basically it seems like the card + monitor + WoW all got thrown out of whack simultaneously somehow. 

To get anything to work I had to reconfigure some things...

I downloaded the drivers for my card again using these instructions:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
though I never could remove the 'Mesa drivers' highlighted in section 2.9 of that page. - don't know if that matters or not. 

I also went here -----> sudo displayconfig-gtk
and reselected a better option for my monitor and card and that helped...but it's still not quite 100% like it was. Currently on that page I have Dell2007FP 1024x768 (60hz) selected for the "Screen" tab and radeon selected for the "Graphics Card" tab (I had to do this just to get the desktop to load at all)

While the computer is OK now - World of Warcraft no longer functions at all...On the logon screen it just looks like random colorful jargon, nothing is readable. 

Card is ATi Radeon X1300
Im on Ubuntu Hardy


What can I do to fix whatever it is that I did?
What can I do to get WoW working again?


Let me know if I need to post any other info, I'd be glad to.

---

### Post by Eviljim on 2008-10-27
Hi there,

Here are some things to try (based on my own experience).

Am I right in thinking you are using the repository drivers for your ATi card?

If so these are Catalyst 8.3 drivers and I dont think that these now work since patch 3.x was applied in WoW.

I was running 8.4 for months previously, yet when the patch came, my screen became all garbled and I resorted to using Catalyst 8.10 drivers.

This seems to have worked for me, so I would suggest heading over to the AMD/ATi driver site and grabbing a copy of them. The install guide is very helpful and should only take acouple of lines in the terminal to get them installed.

---

