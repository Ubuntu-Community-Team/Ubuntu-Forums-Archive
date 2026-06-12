---
title: "Nvidia EN7900GT and LiveCD"
date: 2006-05-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Metal03 on 2006-05-23
I'm trying to run the liveCD to see how this Linux would be, but I can an error message when loading the xserver.

I've been browsing the forum for a few hours and to what I understand, looks like the liveCD doesn'T support the most recent Nvidia cards.

Is there a way to correct that...

I've tried these
sudo dpkg-reconfigure xserver-xorg
(I tried "nv' "vesa" etc...  tried a few!!)
/etc/init.d/gdm stop
/etc/init.d/gdm restart

Still nothing...
I have a AMD 3800+ dualcore 64bits (I have the 64bits LiveCD)
Asus A8N-E motherboard
Nvidia EN7900GT

Please help me!!

---

### Post by bikeboy on 2006-05-23
Most likely it will work if you install the proprietary nvidia driver. The wiki has an nvidia binary howto but that gives instructions using synaptic which isn't much good to you if you're not getting a gui.

So, make sure the restricted respository is enabled and install "nvidia-glx", then "sudo nvidia-glx-config enable" once that's done do a sudo dpkg-reconfigure xserver-xorg and the driver should be available there. Then try restarting X.

---

### Post by Metal03 on 2006-05-24
Wow!!  hehehe

Did I mention I'm a Linux virgin...  Make that same description but "for dummy"!

Plus, will all that work with the LiveCD?

---

### Post by bikeboy on 2006-05-24
Ahh sorry, from the other stuff you wrote I presumed you had a bit more experience. Don't worry, it's not that hard but I'll have to explain a bit more. Unfortunately I don't have time right now (it's time for bed in Aus) but yes it will work on the livecd, I've tried it before.

Only downside is you will have to go through the steps each time because it won't save your settings. And you will need a working internet connection from within Ubuntu, hopefully that won't be a problem.

---

### Post by Metal03 on 2006-05-25
Ya, I look all brilliant and stuff with all those commands I tried, but it's only copy/paste for me...!!  hehehe!

The working connexion seems to be ok cause the "autodetect" is detecting my network in the loading of the LiveCD...  but we'll see about that!!

I'm waiting for more details...  ;)

---

### Post by WormWood on 2006-05-26
I am having the same problem and I'm definately a Linux virgin as well.  Can't wait for more information either.

---

### Post by bikeboy on 2006-05-27
Ok, I'm no Linux guru, I've been using it 6 months full time that's all. But I'll try my best to help.

Metal, from your 1st post I presume you are able to get to a command line style prompt where you can type commands in.

The 1st thing to do would be to make sure the Restricted repository is enable (I can't remember if it is by default).

```
sudo nano /etc/apt/sources.list
```

There should be a line similar to this:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
Note the restricted on the end. If it isn't there, type it in and then press Ctrl + X, then Y, then enter.

Then type ```
sudo apt-get update
``` but don't worry if it mentions a lot of packages.

Now type ```
sudo apt-get install nvidia-glx nvidia-settings
```

And hopefully the last scary code is ```
sudo nvidia-glx-config enable
```

If all has gone well and the internet has worked so that you can download the necessary things, type the "sudo dpkg-reconfigure xserver-xorg" like you did before and when selecting the driver there should now be an nvidia one, not just the "nv" you mentioned. Most of the rest can be left to defaults.

Now HOPEFULLY, doing the gdm restart you tried in the 1st post will work and you'll be set. If there are any problems along the way I will try to help resolve them...I must be in a charitable mood :)

I know it seems like a lot of work but I assure you it becomes easy quickly. If you were doing it on a HDD install you would only need to do it once and you'd be set.

If none of that works there are some other alternatives I feel I should mention. Ubuntu 6.06 is in late beta and there is a livecd version of that too, it will have updated hardware support and may work out of the box without any config. The other one I know of is PclinuxOS, it's a livecd also but comes in a version with nvidia's proprietary drivers built in. At the bottom are some mirrors, notice the 7676, that's the nvidia driver version. From what I've read the drivers supports cards and features just like the windows version, so if 7676 is new enough for a 79xx on windows then chances are you will be fine.
I love Ubuntu but if it doesn't do the job for you there's no harm trying something else, Linux is about choice afterall.

[http://www.tlm-project.org/public/distributions/pclinuxos/live-cd/pclinuxos-p92-nvidia7676.torrent](http://www.tlm-project.org/public/distributions/pclinuxos/live-cd/pclinuxos-p92-nvidia7676.torrent)
[http://pclinuxos.ethz.ch/mirror/pclinuxos/live-cd/english/preview/pclinuxos-p92-nvidia7676.iso](http://pclinuxos.ethz.ch/mirror/pclinuxos/live-cd/english/preview/pclinuxos-p92-nvidia7676.iso)

---

### Post by WormWood on 2006-05-27
This sounds like it would work for me, but I cant connect to the internet, in on a wireless lan usb.  Any help for that?  Also another concern I have is that my ubuntu live cd boots up with random problems, not really random, just sometimes it works and sometimes it doesnt, i. e, sometimes i can get to the command line and sometimes it doesn't work, about 50/50 chance.  

Thanx for the help.

---

### Post by bikeboy on 2006-05-27
I really can't explain the 50/50 working but it could well be video related. As for the wireless, it depends a lot on what brand of card you have and more importantly what chipset it has. I have a broadcom 4306 based card which doesn't work out of the box and needed some configuring that wouldn't be worth it on a livecd. Some cards though have drivers already built into linux and might just need a few settings changed to suit your network.

If possible what chipset does you card use and what brand is it? You might be able to find out by looking at the driver details in windows.

If it's Ubuntu Breezy 5.10 you're using it really could be beneficial to download a beta/flight cd of the new version, but that depends on your download quotas etc. Look for a local mirror if you can. If not, pick up the rc-desktop that suits your processor from here:
[http://releases.ubuntu.com/6.06/](http://releases.ubuntu.com/6.06/)

---

### Post by WormWood on 2006-05-28
I've decided to try out Suse10.1 and it works wonderfully, it recognizes my video  card and everything.  I installed on a seperate harddrive and all that good stuff and as for my wireless card im currently trying to get it configured.  I dled and installed suse for 64 bit but my drivers dont work on it so ima try the reg 32 bit version.  I appreciate all the help though and I may check out future versions of Ubuntu when my card is supported without dlin the drivers online, little hard to do since all i have is wireless.  This card im using is some kinda wierd brand im not even sure, its usb dongle (i guess that what its called).  Got it from a friend who works somewhere and he gets them for free..sounds good to me lol.  Will definately be a chalenge getting it to work though.  Wish me luck and if you have any sugestions, its greatly appreciated.

---

