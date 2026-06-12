---
title: "Couple Questions"
date: 2007-10-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by blm126 on 2007-10-01
So, after having played with Ubuntu on my laptop for a while, I finally decided I want to run it on my desktop also. I downloaded 7.04 AMD64, and the installation went great! However, I soon ran into some problems/questions that I was hoping you guys could help me with.

1. I have a Brother MFC 210C printer hooked up to a Windows XP box.  How exactly would I go about installing the drivers for this printer? The drivers I found wouldn't work. I assume it has something to do with 64 Bit vs. 32 Bit.

2. Is there anyway to install Mplayer without using a 32 bit version of Firefox? I can't seem to find anything...:(

3.I have an older Nvidia graphics card that is hooked up to two monitors.  I used the Restricted Drivers Manager to get a driver for it. Then, using some directions  found through google, I managed to open a Nvidia GUI. From there I set up the second monitor. However, for some odd reason, it wouldn't let me set the resolution past 640x480, and I ended up with a zoomed in picture of the center of the screen on the 2nd monitor. Any tips on what to do? My preferable result is the desktop on one monitor with programs opening on the second.

4. Ok, now this question is kind of odd.  This computer is still dual booting with Windows XP.  What I would like to do is some kind of virtualization to the hard drive that contains an already installed Windows XP. Is that possible?

Thanks for anyone who can give me some help. Even if is just to tell me that I'm SOL.

---

### Post by Scunizi on 2007-10-01
1> Printer... 64 bit versions of anything are problemmatic.. even windows.. I suggest reinstalling the 32 bit version and avoid lots of headaches.  If you really want to stick with the 64 bit version you're going to have to get use to compiling some of your own programs.. Actually, if you do decide to go with 32 bit you won't really notice much of a difference.. Most programs that run on 64 bit are actually 32 bit.

2> A case of needing to compile it yourself.

3> You don't mention which card you have but if it's in the FX series the nvidia driver in Synaptic works fine.  After installation go to the terminal and type 
sudo dpkg-reconfigure -phigh xserver-xorg  This will set up the driver.  However, if you still have problems, shutdown, disconnect one monitor and restart then type the command again.  If everything is honky dory then use these forums to get twinnview or xinerama working for dual monitors.. It might take a little tweeking of /etc/X11/xorg.conf

4> VMware server will run inside of windows or Ubuntu allowing you to install another operating system.  If you want a duplicate of what you have on the xp side, installed programs etc, they have a free tool on thier site that will create a VM of your existing install.  The problem you'll run into is "Validation".  You'll have to revalidate in the VM.  Once you do that the XP partition will no longer be validated so if you go back to that you'll have to validate that as well.. Back and forth forever.. (if it's the same copy of xp.

---

### Post by notna01 on 2007-10-01
Get the newest one, 32bit gusty.
64 bit has too many glitches at the moment, so if you want to make stuff on ubuntu, get 32bit

---

### Post by Kilz on 2007-10-01
> **notna01 said:**
> Get the newest one, 32bit gusty.
64 bit has too many glitches at the moment, so if you want to make stuff on ubuntu, get 32bit

That is incorrect. 64bit has no more problems that 32bit does. Looking at your post histroy you had 
1. [Video card driver issues ]("http://ubuntuforums.org/showthread.php?p=3357430#post3357430")- This is common in 32bit, especially if you have no internet connection, like you admitted in the post.
2. [Issues with Beryl - ]("http://ubuntuforums.org/showthread.php?p=3367398#post3367398")This is common as Beryl and desktop effects are under heavy development. They are still considered Alpha code , meaning expect problems. This is true of 32bit as well. The problem is you used incompatible images with beryl.
3. [Your own attempts to mess with things ]("http://ubuntuforums.org/showpost.php?p=3459693&postcount=1")
4.[ A bad update,]("http://ubuntuforums.org/showpost.php?p=3401328&postcount=1") that you posted the problem for but never gave any information to those willing to help.

[After all that it turns out you may never have had the 64bit version installed.]("http://ubuntuforums.org/showpost.php?p=3271978&postcount=9")

---

### Post by John.Michael.Kane on 2007-10-01
> **blm126 said:**
> So, after having played with Ubuntu on my laptop for a while, I finally decided I want to run it on my desktop also. I downloaded 7.04 AMD64, and the installation went great! However, I soon ran into some problems/questions that I was hoping you guys could help me with.
Hope the the answers that follow will help.

> **blm126 said:**
> 1. I have a Brother MFC 210C printer hooked up to a Windows XP box.  How exactly would I go about installing the drivers for this printer? The drivers I found wouldn't work. I assume it has something to do with 64 Bit vs. 32 Bit.

There is a  I386 deb for that printer. You would have to make sure that the dependencies are taken care of. This may be a little troublesome.

The other option which would be cleaner is to you compile the driver from source which is available.

> **blm126 said:**
> 2. Is there anyway to install Mplayer without using a 32 bit version of Firefox? I can't seem to find anything...:(
As far as I know MPlayer-Plugin for Mozilla that is in the ubuntu 64 repo is 64bit, and works with the 64bit firefox browser

> **blm126 said:**
> 3.I have an older Nvidia graphics card that is hooked up to two monitors.  I used the Restricted Drivers Manager to get a driver for it. Then, using some directions  found through google, I managed to open a Nvidia GUI. From there I set up the second monitor. However, for some odd reason, it wouldn't let me set the resolution past 640x480, and I ended up with a zoomed in picture of the center of the screen on the 2nd monitor. Any tips on what to do? My preferable result is the desktop on one monitor with programs opening on the second.
Sounds like you want twin view.For that you can try the link below
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

> **blm126 said:**
> 4. Ok, now this question is kind of odd.  This computer is still dual booting with Windows XP.  What I would like to do is some kind of virtualization to the hard drive that contains an already installed Windows XP. Is that possible?
For visualization you can run one of the programs below.
[64bit ("Feisty Fawn") deb virtualbox]("http://virtualbox.org/wiki/Downloads") 
Theres also VMWare Player,which has a package in the repos,
This may also be of help [http://www.penguin.ch/dokuwiki/doku.php/virtual:vmware:model](http://www.penguin.ch/dokuwiki/doku.php/virtual:vmware:model)

> **blm126 said:**
> Thanks for anyone who can give me some help. Even if is just to tell me that I'm SOL.
No your not out of luck,however. For some of the things you want you will be required to do some work.

---

### Post by blm126 on 2007-10-02
Thanks for all the help. I'll get to reading how to do these things.

---

