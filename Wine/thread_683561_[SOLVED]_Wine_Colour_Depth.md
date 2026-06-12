---
title: "[SOLVED] Wine Colour Depth"
date: 2008-01-31
forum: Wine
---

### Post by stooshbunutu on 2008-01-31
Hi Guys,

I'm new to the forum so I am just wondering if anyone can help me.

I installed wine and wine-dev and it is working well but some older games tell me they need to run on a 256-bit colour resolution and so don't work properly if at all. Is there any way I can change the wine settings so that it will run things in this colour resolution.

I will welcome any help people can offer, Thanks

:)

---

### Post by Ferrat on 2008-01-31
AFAIK wine runs on the same depth as linux does, ergo change linux depth should make it work in wine, not sure if this applies to 256 color but seen a few fixes that way with 16bit instead of 24/32bit

---

### Post by lha on 2008-02-01
> **Ferrat said:**
> change linux depth should make it work in wine, not sure if this applies to 256 color but seen a few fixes that way with 16bit instead of 24/32bit

An alternative option is described in 
[http://wiki.winehq.org/256ColorsWorkarounds]("http://wiki.winehq.org/256ColorsWorkarounds").

---

### Post by stooshbunutu on 2008-02-04
> **Ferrat said:**
> AFAIK wine runs on the same depth as linux does, ergo change linux depth should make it work in wine, not sure if this applies to 256 color but seen a few fixes that way with 16bit instead of 24/32bit
ok thanks so how do I change the depth in ubuntu, I can only find how to change the screen resolution and refresh-rate. Soz to sound a bit noobie, but im just stuck:confused:

---

### Post by lha on 2008-02-04
> **stooshbunutu said:**
> ok thanks so how do I change the depth in ubuntu, I can only find how to change the screen resolution and refresh-rate. Soz to sound a bit noobie, but im just stuck

Change "DefaultDepth 24" to "DefaultDepth 16" in /etc/X11/xorg.conf. In terminal, type
```
sudo nano /etc/X11/xorg.conf
``` to open the file for editing.

---

### Post by stooshbunutu on 2008-02-07
Ok so I spent the best part part of an evening trying out the work around on the wine website and noe of it worked. Quite annoyed me, does anyone now how I can tell them it didn't work?

I will try the other solution posted shortly

Cheerz again

---

### Post by stooshbunutu on 2008-02-18
Here is the message I get when trying to run the game in WINE

---

### Post by lha on 2008-02-18
> **stooshbunutu said:**
> Here is the message I get when trying to run the game in WINE

Are you trying to install DirectX? Maybe you should check what [WIneHQ FAQ]("http://wiki.winehq.org/FAQ") says about DirectX. (In short, don't try to install Microsoft's DirectX.)

---

### Post by stooshbunutu on 2008-02-18
Yeah it was a direct x problem.

I didn't quite understand the stuff on the wine website, does it mean that direct x is already incorporated, 'cause if so then it is saying tere is a missing component and tis means i wont b able to play the game unless there is going to be some kind of development with direct x 10

Thanks for the ongoing support

---

### Post by lha on 2008-02-19
> **stooshbunutu said:**
> Yeah it was a direct x problem.

I didn't quite understand the stuff on the wine website, does it mean that direct x is already incorporated, 'cause if so then it is saying tere is a missing component and tis means i wont b able to play the game unless there is going to be some kind of development with direct x 10

Wine does not provide DirectX10, so if your game requires the newest DirectX, you're out of luck. There are plans for implementing DX10, though. (At the moment, Wine provides DirectX9.)

---

### Post by stooshbunutu on 2008-02-19
this games is really quite old, it only requires directx6, could it be a backwards compatability problem?

---

### Post by lha on 2008-02-19
> **stooshbunutu said:**
> this games is really quite old, it only requires directx6, could it be a backwards compatability problem?

Take a look at [http://appdb.winehq.org/]("http://appdb.winehq.org/") to find out if someone else has succesfully played it under Wine. Remember that you should not install Microsoft's DirectX; it wont work. Did you install DX6, for example, while installing your game?

---

### Post by stooshbunutu on 2008-02-19
thanks again will try it out ang get back

---

### Post by stooshbunutu on 2008-02-20
well on the site it only has worked with alot of workaround in feisty but then without propper controls. There was a bug listed with the same properties as mine. :(

---

### Post by stooshbunutu on 2008-02-21
I guess i will give up for now and try again on a newer version of wine:(

---

