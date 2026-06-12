---
title: "Trouble Installing Ubuntu 5.10 on A Mac G3"
date: 2005-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by gconn77 on 2005-12-11
Hey everyone one. I wanted to see if I could get some help here. I am attempting to install Ubuntu 5.10 on a Mac G3. The Mac G3 I have appears to be a 400 Mhz system. I don't know too much more than that. It works fine and had Mac Os 9.2 installed. I ran into trouble installing Ubuntu and then decided to attempt to install Fedora4. Fedora4 had its share of problems as well. So I want to work towards getting Ubuntu installed. I am extremely amazed with the quality of support here in the community. I have Ubuntu installed on my Gateway laptop and it works great!

So here goes... I want to walk you thru my installation set up experience. Hopefully with this detail people will be better able to assist me.

**Welcome To Ubuntu 5.10 (Breezy Badger)!**
[[IMG]http://gconn77.com/images/ubuntu/100_0994_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_0994.JPG")

Ok... don't mind the cc typed next to boot: I accidently typed that... So, my first step was to type:

boot: **install**

So after typing **install** the installer immediately begins the installation process. The screen shows a ton of scrolling information for a few minutes. See image below:

**Screenshot after typing Install**

[[IMG]http://gconn77.com/images/ubuntu/100_0997_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_0997.JPG")

After this is done I am taken to a screen where I need to **Choose Language**. After I **Choose Language**, then I was prompted to **Choose Location**. After I selected my location in **Choose Location** window, I was then prompted to the next window, **Select a Keyboard Layout**.

See images below:

[[IMG]http://gconn77.com/images/ubuntu/100_0998_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_0998.JPG")

[[IMG]http://gconn77.com/images/ubuntu/100_1001_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1001.JPG")

[[IMG]http://gconn77.com/images/ubuntu/100_1002_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1002.JPG")

After I make these selections, a new windows appears which I would guess continues the installation process. See image below:

[[IMG]http://gconn77.com/images/ubuntu/100_1003_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1003.JPG")

Now it will continue to load or install for a few minutes... everything seems to go fine. Next thing that happens for me is the:

**[COLOR="Red"](!!) Configure the network[/COLOR]**
[COLOR="Blue"]Network autoconfiguration failed[/COLOR]
Your network is probably not using the DHCP protocol. ALternatively, the...
See Images below:

[[IMG]http://gconn77.com/images/ubuntu/100_1004_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1004.JPG")

[[IMG]http://gconn77.com/images/ubuntu/100_1005_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1005.JPG")

... Continued on Next Post

---

### Post by gconn77 on 2005-12-11
[[IMG]http://gconn77.com/images/ubuntu/100_1006_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1006.JPG")

Now I am totally fine with this, because I know that I have not connected the computer to my cable modem or home network... later after I install Ubuntu I can do this later when I am ready. For now... I just want to install the program... No big deal... But again, for the purpose of walking you thru my installation experience, I wanted to go ahead and illustrate this step. I selected **Do not configure the network at this time**, and left the host name the default name of **ubuntu**.

Ok after choosing to **Configure the network** later... the installation continues on to the next step which is **Detecting disks and other drives**. See Images Below:

[[IMG]http://gconn77.com/images/ubuntu/100_1007_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1007.JPG")

[[IMG]http://gconn77.com/images/ubuntu/100_1008_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1008.JPG")

After it loads for a few minutes a new windows appears, **Partition disks**.  Now in my setup, the Apple G3 I own has Mac Os 9.2 installed. In my situation, I really could care less about having this operating system. I am not interested in dual Os booting... etc.. So I just want to **Erase entire disk**. You might not want to do this... but again, in my situation I don't need Mac Os 9.2. So for the purpose of walking you thru my installation experience, I did not want to skip documenting this. See images below:

[[IMG]http://gconn77.com/images/ubuntu/100_1009_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1009.JPG")

[[IMG]http://gconn77.com/images/ubuntu/100_1010_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1010.JPG")

... Continued on next post.

---

### Post by gconn77 on 2005-12-11
After this is done... the installation continues to **Installation of the base system**. See image below:

[[IMG]http://gconn77.com/images/ubuntu/100_1011_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1011.JPG")

This takes a few minutes to process... eventually I lead to the same problem, and this is where my installation experience suddenly stops:

[COLOR="Red"]**(!!) Install the base system**[/COLOR]
[COLOR="Blue"]Unable to install initrd-tools[/COLOR]

See Images Below:

[[IMG]http://gconn77.com/images/ubuntu/100_1012_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1012.JPG")

[[IMG]http://gconn77.com/images/ubuntu/100_1013_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1013.JPG")

[[IMG]http://gconn77.com/images/ubuntu/100_1014_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1014.JPG")

---

### Post by gconn77 on 2005-12-11
So at this point... this is where I at stuck at with my installation.

Now... I did notice that there is somekind of log that was illustrated. This is what it reads below:

```
Check /target/var/log/bootstrap.log
```

Now I am very new to Linux... I have it installed on a few other computers... and each computer had their share of work to do to get the installation successful... so, now complaints... I am used to the fact that you need to work a little bit to get a good stable and FREE!!! :) system working... no big deal.

But, I think that log file might have information related to my problem. After walking you thru my installation experience, my first question is this:

How do I access this log file: **/target/var/log/bootstrap.log**

Please be specific with your instructions. I will leave my computer turned ON, and remember I am at this screen:

[[IMG]http://gconn77.com/images/ubuntu/100_1014_small.JPG[/IMG]]("http://gconn77.com/images/ubuntu/100_1014.JPG")

---

### Post by gconn77 on 2005-12-11
I think that the CD was possibly bad. I checked the **CD Integrity** and it turned out to be bad... I will add a screen shot later. 

Instead of downloading the .iso thru the web, I downloaded the bit torrent version. I am installing right now... so hopefully a bad disc was the problem... we'll see!

---

### Post by JoshHendo on 2005-12-11
[QUOTE=gconn77]I think that the CD was possibly bad. I checked the **CD Integrity** and it turned out to be bad... I will add a screen shot later. 

Instead of downloading the .iso thru the web, I downloaded the bit torrent version. I am installing right now... so hopefully a bad disc was the problem... we'll see![/QUOTE]
If you still think it is a bad disk, order it thru shipit.ubuntu.com . Also, if you are using a download manager it can cause it not to work (I know that from experience ;)). Though hopefully the bittorrent works, as shipit can take some time :)

---

### Post by gconn77 on 2005-12-11
Yes... I do know that ordering the CD's can take some time... as I placed an order for the PC install a few months back. It took about a month to get them.... but its worth the wait.

Right now I am at 48% installing the base system... and usually with the other CD that I made my problems would occur around 78%....

So keep fingers crossed! Thanks for the advise.

---

### Post by gconn77 on 2005-12-11
Ok... looks like I made it past the first half! But now I am faced with a new challenge.

First Stage Ubuntu Bootstrap

Press I for GNU/LINUX,
        c for CDROM.

Stage 1 boot:
loading second stage bootstrap...


Nothing happens here? I was instructed to remove the CD ROM which I did do.... and the computer restarted... and I am stuck on this task.... it just keeps refreshing itself?

Does anyone know what I need to do here?

---

### Post by gconn77 on 2005-12-18
Bump, please :)

I have not made any progress past this point. For the past few days I have searched the Internet to find any articles, threads, or pages that have this situation. I haven't given up yet... so I am hoping that the community won't give up on me ;) 

I have ubuntu installed successfully on my laptop... and I had some challenges with that... but after a few challenges... I have an awsome performing older laptop, and still works great now.

So... again, I have my Apple G3 here... and the second stage of the install keeps looping.... loading second stage bootstrap... then a few moments later it loops....  any help would be so much appreciated.

---

### Post by gconn77 on 2005-12-18
This thread branches and here are the links to the two threads:

[Loading second stage bootstrap... ]("http://www.ubuntuforums.org/showthread.php?t=102416")

[Partition Apple G3 B&W 9.1 GB Hard Drive For Single OS Ubuntu]("http://www.ubuntuforums.org/showthread.php?t=102440")

---

### Post by gconn77 on 2006-02-08
I was definately able to get Ubuntu installed on my G3 Apple computer... please follow the links to the other two threads to read on and learn what I did and what the community helped me with.

---

### Post by andre-w on 2006-02-11
Hello gconn77,

I just stopped by to congratulate you for successfully installing Ubuntu in your G3 B&W. I would also like to thank you for helping me when I had a related situation. Good to know you did not give up, so you too are now enjoying Ubuntu on your Mac. Since I installed Ubuntu, I still did not have as much time as I wished to explore its features beyond the trivial applications, but I know Ubuntu has a lot to offer!

Best regards,

Andre W.

---

### Post by aonegodman on 2008-01-04
My son has recently acquired a G3 Blue and wants to attempt to put Ubuntu on it. This post will be most helpful. After skimming over your posts I gather that the main issue was to remove the SCSI HD and replace with an IDE. Is this correct?

Thanks again for this great and informative post.  :D

---

