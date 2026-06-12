---
title: "Ubuntu 6.10 Hangs/Blank screen on Logout,Switch User, etc"
date: 2007-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by xthaparian on 2007-03-08
Hi

I installed AMD64 Edgy on my PC and now I have this wierd problem that my computer gives me blank screen on logout. 

Same is the case if I do Shutdown, Switch User, CTL+BKSPACE, CTL+F1 etc..

I have been googling around..but seems like a bug to me.

How come its not fixed as of yet???

PLEASE HELP ME..

---

### Post by Kilz on 2007-03-08
> **xthaparian said:**
> Hi

I installed AMD64 Edgy on my PC and now I have this wierd problem that my computer gives me blank screen on logout. 

Same is the case if I do Shutdown, Switch User, CTL+BKSPACE, CTL+F1 etc..

I have been googling around..but seems like a bug to me.

How come its not fixed as of yet???

PLEASE HELP ME..

While I do not know 100% what the problem is, or how to fix it. In the past, this is usually because of a bad video driver or its configuration.

---

### Post by joshuapurcell on 2007-03-08
This is most likely related to the video driver. I've had this exact problem with the default vesa driver as well as various versions of the Nvidia driver (although 9742 seems to work... haven't tried the latest one yet).

---

### Post by xthaparian on 2007-03-08
but i recently compiled new drivers from Ati?

may be it has to do with xorg? some experts here????

thanks

---

### Post by Kilz on 2007-03-09
> **xthaparian said:**
> but i recently compiled new drivers from Ati?

may be it has to do with xorg? some experts here????

thanks

If its ATI, I remember that [the 2.25.18 drivers did the exact same thing]("http://www.ubuntuforums.org/showthread.php?t=212697&highlight=ati+black"). The only solution that I remember was to install the previous driver (8.24.8 ). Looking back I even posted that in post 6 of the thread I linked to.

---

### Post by Tim___ on 2007-03-09
This is probably the video driver. I had the same problem using the default nvidia-glx driver in edgy. Upgrading the driver fixed that problem as well as google earth :)

---

### Post by xthaparian on 2007-03-09
hmm,.,,

let me try the previous version and see it works or not?

Thanks for replies..

---

### Post by Mosphet on 2007-03-09
I agree, certainly seems like a bug, but it doesn't appear to be down to a driver. I've had the same problem. I tried different drivers, no solution. It occurred using drivers both the 'ati' and 'fglrx'. 

The solution, for me at least, is to unplug the DVI connector from my ATI X800 card and use the VGA connector instead. It's not ideal but its the only thing I've found that solves this problem and believe me I've tried every piece of advice I could find.

In short, it appears that theres a group of video cards that are failing to switch video mode a second time when connected by DVI. Video output from the DVI connector simply dies, and possibly the kernel crashes if you're unlucky enough to experience this during boot up.

I've an idea this situation started with Edgy and continues in Feisty, but I can't be sure, my evidence is anecdotal as I'd never installed Badger on the machine in question.

So, if you're connecting your screen via DVI, I suggest you try a VGA connector if at all possible until a fix comes. As you can see from the links below, this problem has been going around for a while.

[http://ubuntuforums.org/showthread.php?p=2174927#post2174927](http://ubuntuforums.org/showthread.php?p=2174927#post2174927)

[http://ubuntuforums.org/showthread.php?t=343507](http://ubuntuforums.org/showthread.php?t=343507)

[http://ubuntuforums.org/showthread.php?p=1881681](http://ubuntuforums.org/showthread.php?p=1881681)


Good luck

Mosphet

---

### Post by xthaparian on 2007-03-11
> **Mosphet said:**
> I agree, certainly seems like a bug, but it doesn't appear to be down to a driver. I've had the same problem. I tried different drivers, no solution. It occurred using drivers both the 'ati' and 'fglrx'. 

The solution, for me at least, is to unplug the DVI connector from my ATI X800 card and use the VGA connector instead. It's not ideal but its the only thing I've found that solves this problem and believe me I've tried every piece of advice I could find.

In short, it appears that theres a group of video cards that are failing to switch video mode a second time when connected by DVI. Video output from the DVI connector simply dies, and possibly the kernel crashes if you're unlucky enough to experience this during boot up.

I've an idea this situation started with Edgy and continues in Feisty, but I can't be sure, my evidence is anecdotal as I'd never installed Badger on the machine in question.

So, if you're connecting your screen via DVI, I suggest you try a VGA connector if at all possible until a fix comes. As you can see from the links below, this problem has been going around for a while.

[http://ubuntuforums.org/showthread.php?p=2174927#post2174927](http://ubuntuforums.org/showthread.php?p=2174927#post2174927)

[http://ubuntuforums.org/showthread.php?t=343507](http://ubuntuforums.org/showthread.php?t=343507)

[http://ubuntuforums.org/showthread.php?p=1881681](http://ubuntuforums.org/showthread.php?p=1881681)


Good luck

Mosphet

Totally and absolutely agree...

I tried Demoting Drivers and still no solution !!! So apparently its not driver specific problem.

It has to do with either 64bit Ubuntu or something in Xorg ! 

Well any Administrators can help here????

I dont really want to switch from DVI to VGA as I do dualboot to play games and use CAD softwares....

So I am essentially struck with this problem.!!!

Any EXPERT Advice to listen to peples VOES..here??

Thanks

---

### Post by xthaparian on 2007-03-11
Anybody tried this link??

[http://www.thinkwiki.org/wiki/Problems_with_fglrx#Hardlock_on_X_logout]("http://www.thinkwiki.org/wiki/Problems_with_fglrx#Hardlock_on_X_logout")

---

### Post by Lonthong on 2007-03-13
Don't know if this is related, but I also had log-out issue with both ATI v. 8.33.6 & 8.34.8 (however, in my case, only log-out was the problem. Shutdown & reboot always work properly, I never try switch user though). Whereas v. 8.32.5 did not give any problem.

This solved my log-out issue
 add"AlwaysRestartServer=true" under "Daemon" to  gdm.conf-custom

---

### Post by Sanchopinky on 2007-03-19
Sorry I'm a linux newbie,but how do I get there..?

---

### Post by Lonthong on 2007-03-28
launch terminal & copy+paste the following
sudo gedit /etc/gdm/gdm.conf-custom
type in yr password
scroll to [Daemon]
add: AlwaysRestartServer=True
save

---

### Post by davidblund on 2007-03-29
same problem here.

adding "AlwaysRestartServer=true" in the gdm.conf-custom didn't fix my system.

could any other changes to the gdm.conf-custom fix this issue?

and does the problem only concern ati-users? in that case i'm seriously going to switch to nvidia. 


//david

---

### Post by Lonthong on 2007-04-03
> **davidblund said:**
> same problem here.

adding "AlwaysRestartServer=true" in the gdm.conf-custom didn't fix my system.

could any other changes to the gdm.conf-custom fix this issue?

and does the problem only concern ati-users? in that case i'm seriously going to switch to nvidia. 


//david

You can just downgrade to ati driver 8.32.5

---

### Post by xthaparian on 2007-04-24
its some problem with the Kenel

Today I upgraded to Fiesty and its all fine now..
I ried downgrading the driver too but it did not work..

---

