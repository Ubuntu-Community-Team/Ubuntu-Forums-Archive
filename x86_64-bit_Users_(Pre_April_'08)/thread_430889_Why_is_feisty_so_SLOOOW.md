---
title: "Why is feisty so SLOOOW?"
date: 2007-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by xeocub on 2007-05-02
Since I have updated to feisty from edgy, it is seriously extremely annoying to do anything in Ubuntu. Whenever I open an open office window, switch between it or do anything inside, it has to reload every icon (which takes about 10 seconds). Other windows and programs such as Gimp are slow as balls as well and I don't know why.

I've posted before about my beryl problems, but right now I'm using regular old gnome so that shouldn't be the problem... 

What could this be? And does anyone else have the same issues? I've also went through and taken care of various published "speed ups" such as removing JRE from openoffice etc...

---

### Post by DJiNN on 2007-05-02
Sorry to hear about your computer slowing down with Feisty. I've had nothing but the opposite..... i've found the Feisty install (I've done 386 versions of X/Ubuntu & the 64 bit version of Xubuntu) fantastic..... no real problems & a hell of a lot faster than any of the other releases.

I know that it's not the answer but if you have a seperate /home i would suggest that you do a complete "Re-Install" fresh from CD...... that's almost sure to make a difference. Maybe it's some legacy stuff left over from Edgy or something (Just a guess) that's causing your comp to run slow. 

Good luck......

DjiNN

---

### Post by xeocub on 2007-05-02
> **DJiNN said:**
> Sorry to hear about your computer slowing down with Feisty. I've had nothing but the opposite..... i've found the Feisty install (I've done 386 versions of X/Ubuntu & the 64 bit version of Xubuntu) fantastic..... no real problems & a hell of a lot faster than any of the other releases.

I know that it's not the answer but if you have a seperate /home i would suggest that you do a complete "Re-Install" fresh from CD...... that's almost sure to make a difference. Maybe it's some legacy stuff left over from Edgy or something (Just a guess) that's causing your comp to run slow. 

Good luck......

DjiNN

Yes, that will be my first attempt at fixing things as soon as I have some free time. I'm guessing it somehow is correlated to the nvidia drivers.. but I'm not sure.

---

### Post by blazercist on 2007-05-02
have you looked in the system monitor during these lags perhaps something is eating your cpu?

you mentioned the nvidia driver... did you have that installed in edgy before you upgraded?

---

### Post by xeocub on 2007-05-02
> **blazercist said:**
> have you looked in the system monitor during these lags perhaps something is eating your cpu?

you mentioned the nvidia driver... did you have that installed in edgy before you upgraded?

The CPU is almost in full use when I do ANYTHING. Right now as I am typing this post it spikes to about 60% when I type.. it only says that XGL is using about 29 percent right now though.. nothing else.

The nvidia drivers that were installed when feisty upgraded didn't work for me, it crashed X as soon as it tried to boot it. I had this same issue with edgy because of the default device drivers,  (I need the legacy ones because I have an older GF4 ti4400)
In edgy I downloaded the drivers and it basically took care of it all by itself, and after that my card worked fine. 
So I attempted the same thing here in feisty, I can now start X but the card doesn't seem to work right.

---

### Post by whayong on 2007-05-02
I'm having the same problems with xubuntu Feisty.  System was running like a champ on Edgy.  This is a fresh install.  Boot time has also increase significantly, and it seems like battery time has been cut down as well.  Also have CPU running at 100% at times when doing similar tasks in Edgy didn't have such spikes.

You're not alone buddy.

---

### Post by rriddell on 2007-05-03
I am running a dual system with 64 bit Vista and 64 bit Ubuntu, I have been using both for about 2 weeks now on a new computer. I notice that Ubuntu  takes longer to load programs now than it took originally.

---

### Post by Jouke74 on 2007-05-03
First check if the desktop effects are enabled, if so put them off and compare again.

---

### Post by skibrianski on 2007-05-03
Xgl, at least with an ATI card, eats a non-trivial amount of CPU itself, even before beryl/compiz effecfts. If you're not using desktop effects, you should probably be running plain X11 instead.

---

### Post by Ferrat on 2007-05-03
> **whayong said:**
> I'm having the same problems with xubuntu Feisty.  System was running like a champ on Edgy.  This is a fresh install.  Boot time has also increase significantly, and it seems like battery time has been cut down as well.  Also have CPU running at 100% at times when doing similar tasks in Edgy didn't have such spikes.

You're not alone buddy.

Loading time that increases alot usally means you got a hardware that Ubuntu really can't recognize during bootup because it doesn't have the proper drivers during the booting, I have this problem with my USB Blue-tooth, it adds almoste a minute of Ubuntu checking and rechecking trying to find out what it is, untill Ubuntu settles for a generic "USB what ever I don't know so I just say ok" setting but in Ubuntu when the blue-tooth drivers are loaded it works imidietly, so if I boot without it I boot in like 2/5 of the time and I just plug it in after booting and it works. 

You say your Battery time is cut down noticably, well this could also be a USB or other hardware running full out all the time because it has "two" drivers, the one that makes it work and the one where Ubuntu just acceptes from the boot that there is something there and giving it power, try booting with out the splash screen to see where the boot slows down, try installing all drivers again and try removing all USB devices to see if that helps

---

### Post by Ferrat on 2007-05-03
> **xeocub said:**
> Since I have updated to feisty from edgy, it is seriously extremely annoying to do anything in Ubuntu. Whenever I open an open office window, switch between it or do anything inside, it has to reload every icon (which takes about 10 seconds). Other windows and programs such as Gimp are slow as balls as well and I don't know why.

I've posted before about my beryl problems, but right now I'm using regular old gnome so that shouldn't be the problem... 

What could this be? And does anyone else have the same issues? I've also went through and taken care of various published "speed ups" such as removing JRE from openoffice etc...

As I mentioned in the post above, many of these problem can be due to faulty drivers. 
Like running Beryl using a software rendering 3D instead of hardware, this would make especially grafic apps very slow.

---

### Post by Jouke74 on 2007-05-03
Check also Ipv6 vs Ipv4 related to your internet connection. Some older stuff does not support ipv6 and that causes the internet to timeout. This is related to your program starting, because the loopback device is always started. I don't know anymore how to solve this precisely, but there is a thread about it on the forum for sure.

---

### Post by NickK1066 on 2007-05-03
> **skibrianski said:**
> Xgl, at least with an ATI card, eats a non-trivial amount of CPU itself, even before beryl/compiz effecfts. If you're not using desktop effects, you should probably be running plain X11 instead.

Sounds like it's still using the software emulation (MESA) rather than flgrx.

I've also noted that it's worth recompiling any ATI released drivers into the the restricted driver set; otherwise the old drivers get loaded.

I know there was an issue with the composite flag.

---

### Post by blazercist on 2007-05-03
the OP has an nvidia card... which begs the question why is he using XGL?  Anyway there has to be some command that correlates to fglrxinfo for nvidia cards which will tell you if you are using mesa or the correct driver. Also turn off your Xgl session and see if it still lags.

---

### Post by peterbakker on 2007-05-03
i had the same problem, but i had troubles with beagle eating my CPU. After uninstalling this program this problem was solved..

---

