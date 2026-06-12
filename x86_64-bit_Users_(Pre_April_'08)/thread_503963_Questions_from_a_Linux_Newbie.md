---
title: "Questions from a Linux Newbie"
date: 2007-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by tyrion2323 on 2007-07-18
Hi there,

I have just joined up today, and have been using Ubuntu x64 Feisty Fawn for a little under a month (on-and-off with XP Pro).  I have done several searches for answers to the questions I have, but do not possess the knowledge or confidence to enact any of the solutions that I have found.

I decided to post this in the x64 section because I am running x64, though if I was to install again I'd probably go x86.

So here are my questions, hopefully you guys will be able to help out:

1) Using my Logitech MX310 USB mouse, I am unable to utilize my back/forward buttons.  I have tried to cut and paste some of the "Terminal" codes that people have recommended, but I can't seem to do this.  I am positive that this is my fault, but I have absolutely no terminal or kernel experience, and don't want to blow up my computer.

2) I know this is a common problem, but I would like to get Flash to run in FireFox.  I have tried to download the 32-bit version of FireFox, but again, I'm too inexperienced to know how to install it.

3) I am unable to switch my permissions on my Windows and Storage drives to Read/Write.  How can I take ownership of these drives?

I appreciate any and all help, and I'm sorry to clog up this forum with newb questions.

Thanks!

---

### Post by tyrion2323 on 2007-07-18
Okay, one more stupid question:

I would really like to mess around in Beryl, since it seems to bring a lot of awesome OS-X like features to Ubuntu.  I don't want to mess anything up!

Currently I'm running an nVidia Geforce 7600GT.  I have tried to download the drivers and they are sitting on my desktop, but I am (again) too inexperienced to install.

Any help on the drivers?  Advice on installing Beryl?  I can't even seem to find where to download Beryl.

---

### Post by Kilz on 2007-07-18
> **tyrion2323 said:**
> 
2) I know this is a common problem, but I would like to get Flash to run in FireFox.  I have tried to download the 32-bit version of FireFox, but again, I'm too inexperienced to know how to install it.


Are you 100% positive you have looked at the 64bit section of the forum(the very first , top page), and cant find the answer to this question?

---

### Post by jcronkhite on 2007-07-18
I finally looked into getting Flash working on 64bit Ubuntu.  Go to [http://ubuntuforums.org/showthread.php?t=426921]("http://ubuntuforums.org/showthread.php?t=426921")  and follow the instructions posted by Spike-X.   It's not hard at all and worked great for me.  That's the answer to Flash for you.  Can anyone answer the other questions?  Definitely look around the 64bit threads, they will be very valuable to you.

---

### Post by John.Michael.Kane on 2007-07-18
> **tyrion2323 said:**
> 
1) Using my Logitech MX310 USB mouse, I am unable to utilize my back/forward buttons.  I have tried to cut and paste some of the "Terminal" codes that people have recommended, but I can't seem to do this.  I am positive that this is my fault, but I have absolutely no terminal or kernel experience, and don't want to blow up my computer.

Theres two methods to fixing your mouse issue.

Method one:
[HOWTO: Configuring Logitech mice in Ubuntu 6.10 and 7.04]("http://ubuntuforums.org/showthread.php?t=219894&highlight=Logitech+MX310")

Method two:
[btnx: Send keyboard and mouse combination events with mouse buttons]("http://ubuntuforums.org/showthread.php?t=455656&highlight=Logitech+MX310")

> **tyrion2323 said:**
> 2) I know this is a common problem, but I would like to get Flash to run in FireFox.  I have tried to download the 32-bit version of FireFox, but again, I'm too inexperienced to know how to install it.

Have a read [Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64]("http://ubuntuforums.org/showthread.php?t=202537&highlight=java") **Note: use the Browser Install Script method, and make sure the universe and multiverse are enabled before installing anything.**

Note: For other codecs or dvd play back read the bottom of this thread.
[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

> **tyrion2323 said:**
> 3) I am unable to switch my permissions on my Windows and Storage drives to Read/Write.  How can I take ownership of these drives?

[HOWTO: NTFS with read/write support using the ntfs-3g (easy & safe method)]("http://ubuntuforums.org/showthread.php?t=217009&highlight=read+write+windows")

[Mounting Windows Partitions in Ubuntu]("http://www.psychocats.net/ubuntu/mountwindows")


> **tyrion2323 said:**
> Okay, one more stupid question:

I would really like to mess around in Beryl, since it seems to bring a lot of awesome OS-X like features to Ubuntu.  I don't want to mess anything up!

Currently I'm running an nVidia Geforce 7600GT.  I have tried to download the drivers and they are sitting on my desktop, but I am (again) too inexperienced to install.

Any help on the drivers?  Advice on installing Beryl?  I can't even seem to find where to download Beryl.

Note: Compiz Fuzion, As well as Beryl is NOT for Beginners. It is in development now, and is not stable use at your own risk.

[HOWTO: Beryl with latest nvidia drivers and FEISTY's built in AIGLX (no XGL)]("http://ubuntuforums.org/showthread.php?t=357501")

[BerylOnFeisty]("https://help.ubuntu.com/community/BerylOnFeisty")

[Installing Beryl On An Ubuntu Feisty Fawn Desktop With An ATI Radeon Graphic Card]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

[How To: Compiz Fusion on Ubuntu 7.04]("http://ubuntuforums.org/showthread.php?t=481314")

---

### Post by Kilz on 2007-07-18
Give a man a fish feed him for a day .... teach a man to fish, feed him forever.

---

### Post by tupesadilla on 2007-07-18
for flash... you could always install Wine and install the windows version of firefox.... gaining control of windows drives...install automatix and look through th elist and theres an NTFS read/write.... for nvidia drivers... use Envy

---

### Post by royg on 2007-07-18
Dear Tyrion,

Please make sure you uninstall your "linux restricted drivers" from the synaptics package manager"  before attempting to install the NVIDIA 7600GT Drivers, (if you downloaded the Native drivers supplied by NVIDIA) otherwise both crashes as API errors and you'll resort to command line interface. which i am sure you aren't going to appreciate. 

Installing NVIDIA drivers are walk in the park, just as a windows XP install process if you download full installer instead of just and .rpm or a tarball. (tarz.bz2...etc) if you have the debian package installer in you system all you have to do is simply double click on the downloaded file that contains the extension *.deb 

hope it helps
cheers
royg

> **tyrion2323 said:**
> Okay, one more stupid question:

I would really like to mess around in Beryl, since it seems to bring a lot of awesome OS-X like features to Ubuntu.  I don't want to mess anything up!

Currently I'm running an nVidia Geforce 7600GT.  I have tried to download the drivers and they are sitting on my desktop, but I am (again) too inexperienced to install.

Any help on the drivers?  Advice on installing Beryl?  I can't even seem to find where to download Beryl.

---

### Post by Cappy on 2007-07-18
To install your video drivers:
Here is the home page so you can read it first (for information) : [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

```

sudo apt-get --purge remove nvidia-glx* nvidia-settings linux-restricted-modules*
sudo apt-get install build-essential xserver-xorg-dev
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu1_all.deb
sudo dpkg -i envy*.deb
sudo envy -t
```

As the nvidia script runs, allow it to configure X (xorg.conf).

Once you are in X you can configure (dual monitors, resolution, etc) with ```
gksudo nvidia-settings
```

---

### Post by tyrion2323 on 2007-07-22
Wow,

thank you for the avalanche of responses!  I appreciate all of your patience and links, and I will begin looking into these immediately!

I did use the search function for all of those questions, but I assume that I might not have been using the right keywords.

Again, thanks!

---

