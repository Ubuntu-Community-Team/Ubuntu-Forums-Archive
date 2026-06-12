---
title: "Mixup"
date: 2005-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by tranceConscious on 2005-03-13
How do I set up a dial up connection to a win2k ras server that calls me back???

Why does everything have to be so f#$%@^ complicated???

Why do I have to spend whole days just to make my dial-up connection and my display driver work???

In system -> administration -> networking I see my eth0 and a modem connection which I configure but activating it does nothing (picks up the line but does not dial, cause probably it does not recognise the dial tone which I can't disable from anywhere), same with that modem lights applet, how can I use it????
Gnomeppp which looks nice and simple, sucks cause it won't solve my problems and for some weird reason in the log window it waits for a password that I can't input.

What is that ppp0 that all the programs refer to???

I'm really pissed off.
I have only managed to dial out by using pppconfig to create a connection and pon/poff.

But my bigest problem is that I can't figure out how to configure call-back.

HELP!!!

---

### Post by wmcbrine on 2005-03-13
pppd *can* do it. Unforunately, AFAICT, you'll have to approach this at a lower level than the graphic front-ends, because it's a "fringe" feature.

Google on "pppd callback" and see what turns up. Here's one page that may help:

[http://www.mppmu.mpg.de/callback/linuxanalog.html](http://www.mppmu.mpg.de/callback/linuxanalog.html)

If all else fails, you could try mentioning to your sysadmin that callback is really quite silly. Talk about overkill!

---

