---
title: "Help me please"
date: 2008-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by takahiro on 2008-03-11
Ok, I am new to Ubuntu 7.10 64-bit. I have been running it for around 2 months now. Today I just got a big problem just arise.

I was listening to music on my Ubuntu box while working on my family's computer(Windows) and I had set it to at 1 hour to go to sleep. I forgot to move the mouse getting close to the 1 hour mark. Then boom. It goes to sleep. Ok, tried waking it up, moved mouse and hit  couple keys on the keyboard. Nothing happened. I forced shut down and now when I start it up it gives me this:

* Starting anac(h)ronistic cron anacron                   [ OK ]
* Starting deferred execution scheduler atd           [ OK ]
* Starting periodic command scheduler crond          [ OK ]
* Checking batter state...                                        [ OK ]
* Running local boot scripts (/etc/rc.local)               [ OK ]
_

At the end is a blinking cursor, I can type there.
It wouldn't be that big of a problem, execpt that my family only has dail-up internet. I have music on there, mostly MP3s. I just got it updated at my job, Best Buy. I did the updates and installed the codec pack.

Anyone have any ideas?

If this will help at all, right before this happened, my graphics were going a little wonky, when logging in and out the screen would become all minimized like towards the bottom. So I took the graphics card out and ran it on the built-in chipset.

If the specs of my system will come in handy here they are:
Intel P4 LGA 775 w/ HT, 500GB WD HDD, 2GB of PQi DDR2, ATI X1050 card.

It wouldn't a big problem if my family had cable net, but they don't.
Thanks everyone.

---

### Post by kuja on 2008-03-12
Those look like messages from the normal bootup process. ATI cards and Linux have a tendency not to play nice, what is the integrated chipset? Intel? You did remember to reconfigure X after pulling the card right? (ie: sudo dpkg-reconfigure xserver-xorg -phigh) To get to a regular terminal you'll probably need to press ctrl + alt + f2 ... it sounds like the XServer is failing to start at any rate.

---

### Post by felker2 on 2008-03-12
The subject is not so meaningful; that won't attract a lot of people.

Anyway:

Have you tried the second boot option ("Safe Mode" AFAIK)? It will give you the option of repairing the X / GUI settings.

---

### Post by takahiro on 2008-03-12
Well, the mobo is a Biostar unit. I got it from Newegg pretty cheap. I'm checking what on board video chip set it has. It is a VIA S3 UniChrome. 
I tried it, now it works(so far). Now it is giving me like a 800x600 resolution. To me that is really off.

I'm also thinking of picking up a 8800GT, 8600GT, or a 9600GT at work this weekend.

Thanks everyone.

---

