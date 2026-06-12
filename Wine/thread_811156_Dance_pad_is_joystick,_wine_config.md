---
title: "Dance pad is joystick, wine config?"
date: 2008-05-28
forum: Wine
---

### Post by dlublink on 2008-05-28
Hello,

I am trying to get a dancing game working in Wine. I notice that Linux detects the dance pad ( which is USB ) as a joystick and that wine is detecting the joystick.

I notice that there are messages that appear in the debug when I hit buttons on the dance pad ( running app with WINEDEBUG=+dinput wine appname.exe ).

It would seem that everything in the environment is correct, how do I debug what the application is looking for? Is it possible instead of seeing what wine is receiving from the hardware to see what hardware the program is trying to access?

Is there any special configuration to do to get joysticks working in Wine?

The game is correctly detecting the number of dance pads, it just doesn't seem to accept input from them

Thanks,

David

---

### Post by Kinst on 2008-05-28
Which game?

---

### Post by dlublink on 2008-05-28
Dance praise 2 remix.

Both dance pads work fine using the gtk joystick calibrater I found in apt

---

### Post by dlublink on 2008-05-28
Looks like Linux is detecting them :

crwsrwsrwt 1 root plugdev 13,  0 2008-05-28 20:45 js0
crwsrwsrwt 1 root plugdev 13,  1 2008-05-28 21:54 js1


When I unplug a pad, one of the devices disappear. I am pretty sure the problem is between wine and the software. Is it possible that the software is expecting input in some other form than a joystick?

---

### Post by Kinst on 2008-05-28
> 
I notice that there are messages that appear in the debug when I hit buttons on the dance pad ( running app with WINEDEBUG=+dinput wine appname.exe ) Hm, what do they say?

---

### Post by forestgreen on 2008-07-10
I don't know if my Wine was configuring the dance pad as a joystick. 
But, I did find an answer to making Wine recognize the dance pad here:
[http://news.softpedia.com/news/Wine-1-0-Released-after-15-Years-88218.shtml]("http://news.softpedia.com/news/Wine-1-0-Released-after-15-Years-88218.shtml")
It requires an upgrade to Wine 1.0. 

Thanks and have a great day,
      Christa

---

