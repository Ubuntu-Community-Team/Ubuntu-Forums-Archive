---
title: "The Sims 3 - black screen/very poor graphics"
date: 2014-03-26
forum: Wine
---

### Post by maddie2 on 2014-03-26
First thing: I'm a total newbie to Ubuntu.  I very recently installed Ubuntu 12.04 LTS (from ubuntu.com) on a laptop that I found in my basement.  Here are the basic computer specs:

Dell Inspiron E1505
Memory: 992.1 MiB
Processor: Intel® Core™2 CPU T5500 @ 1.66GHz × 2 
Graphics: Intel® 945GM x86/MMX/SSE2 
OS type: 32-bit
Disk: 117.0 GB

I installed The Sims 3 using PlayOnLinux and largely followed the combined instructions from these two posts I found online:

[http://www.maketecheasier.com/play-the-sims3-in-linux/](http://www.maketecheasier.com/play-the-sims3-in-linux/)
[http://zylblog.com/2009/10/run-the-sims-3-under-linux/](http://zylblog.com/2009/10/run-the-sims-3-under-linux/)

I'm able to launch The Sims 3 using PlayOnLinux but my screen goes black immediately and I can only hear the (stuttering) sound of the opening video.  Once the opening video is done, I have visuals again but the graphics are incredibly poor.  The colors are faded and the text is so block-y that I can't read it.  The sound is much better though and doesn't stutter like it does during the opening video.

I've searched the forums and am wondering if it's my graphics driver or card.  I installed driconf and set "Enable S3TC texture compression even if software support is not available" to "Yes" in the Image Quality section, as suggested in some forum posts.  Didn't do anything for me.  

I believe I have an updated graphics driver given that the Graphics section under System Settings says "Standard" for "Experience".

Any thoughts?  Thanks in advance for your help!

---

### Post by Rob Sayer on 2014-03-27
If you're unsure about the video driver go into Additional Drivers.

There seems to be a couple of problems here.  First, it looks like you've installed ubuntu with the Unity desktop.

This will not run satisfactorily on a computer with 1Gb RAM.  I tried it on a laptop with an i3 cpu and 4Gb ram.  I reinstalled another ubuntu desktop version because unity was too slow.  Unity in 2D mode was better but not that much.  This is a common newbie mistake ... they often think ubuntu is just one thing.  It isn't.  Unity needs as much computer power as Windows 7 or 8.

If you *have* installed unity you should be using xubuntu or lubuntu.  In 1Gb I'd recommend lubuntu 13.10 (lubuntu 12.04 isn't a long term release) and then upgrade to 14.04 lubuntu (which will be an lts).  It's possible to just install the lubuntu desktop but I'd recommend a clean total reinstall.  It's more reliable.

The other issue I see is that the minimum memory requirements for the sims 3 in windows xp according to EA is 1Gb ram.  And if you want good performance I generally double minimum requirements.  Plus that was never a particularly high performance video card to begin with.

In other words, you'll get optimum results with lubuntu but I wouldn't expect miracles.

There are other distros besides ubuntu which have smaller system footprints but they're much harder to install and configure than ubuntu.  Ubuntu is the only distro I'd recommend to a novice unless nothing but a really minimal distro will work,

One more thing.  Playonlinux is just a GUI front end for Wine, which is a lot better known.  Another common newbie mistake is to assume that they can run all their old windows apps in linux with it.  Wine is actually not all that reliable.  There's a lot of documentation and program ratings on the web about this.

But according to ...

[https://appdb.winehq.org/objectManager.php?sClass=application&iId=9732](https://appdb.winehq.org/objectManager.php?sClass=application&iId=9732)

... there doesn't seem to be any problem with the sims 3.

---

### Post by maddie2 on 2014-03-29
Doesn't show that I have any additional drivers to download. 

Are you sure that switching to Lubuntu will affect my graphics?  It seems that, although the game runs slower on this computer, it still runs at an OK speed - just not with useable graphics.

---

### Post by Mark Phelps on 2014-03-30
> If you're unsure about the video driver go into Additional Drivers.

You claim to have Intel video -- and that being the case, Additional Drivers is NOT going to do anything for you.

Switching to Lubuntu only will give you a lighter weight desktop; I fail to see HOW it is going to do anything for you in terms of video drivers.

You can try the linked site to see if they have any newer drivers:  [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&lang=eng")

---

### Post by maddie2 on 2014-03-30
I followed the link provided and found that it was for wireless drivers.  Will that affect my graphics?  I ended up doing more searching for graphics drivers and found this website:

[http://www.techlw.com/2012/08/install-latest-intel-gpu-drivers-in.html](http://www.techlw.com/2012/08/install-latest-intel-gpu-drivers-in.html)

I followed the commands and unfortunately, when I try to open The Sims 3, I now get the following error:

> Unable to start game

Device 0 cannot run this title.
No supported video graphics card detected. Please check your system hardware.

Under System Settings->Details->Graphics, there's no longer information for my Driver.  How can I undo what I just did?

Thank you for the help!

---

### Post by oldrocker99 on 2014-03-31
Also, don't feel that you have to reinstall a different Ubuntu version. Try this (for LXDE)

```
sudo apt-get install lubuntu-desktop
```

Then log out, select Lubuntu and log back in again. This is one of the great strengths of the GNU/Linux OS, that we have our choices of user interfaces.

---

### Post by naqash2 on 2014-04-03
same problem with me above solution did'nt helped

---

