---
title: "Wine for 7.10"
date: 2008-05-06
forum: Wine
---

### Post by avgazn on 2008-05-06
Yes well i need help. Me being the super noob has a triple boot system right now.XP VISTA and UBUNTU. I am thinking of making a potential switch to all ubuntu or maybe a mac computer later on. I discovered wine so I decided to try it out. I downloaded the .deb in to my share partition and loaded it with my ubuntu partition. It says that it needs binfmt-support that i have mentioned in another post. I downloaded one but i think it was for hardy. Even if it wasn't I wouldn't know. Does anyone have one for 7.10 and can someone help me install it?

---

### Post by cogadh on 2008-05-06
Sticky thread right at the top of this forum:
[http://ubuntuforums.org/showthread.php?t=624644](http://ubuntuforums.org/showthread.php?t=624644)

---

### Post by kostkon on 2008-05-06
> **cogadh said:**
> Sticky thread right at the top of this forum:
[http://ubuntuforums.org/showthread.php?t=624644](http://ubuntuforums.org/showthread.php?t=624644)
I think they have recently killed the repos for the older versions of *Ubuntu*, as you can see [here]("http://www.winehq.org/site/download-deb").
> **avgazn said:**
> Yes well i need help. Me being the super noob has a triple boot system right now.XP VISTA and UBUNTU. I am thinking of making a potential switch to all ubuntu or maybe a mac computer later on. I discovered wine so I decided to try it out. I downloaded the .deb in to my share partition and loaded it with my ubuntu partition. It says that it needs binfmt-support that i have mentioned in another post. I downloaded one but i think it was for hardy. Even if it wasn't I wouldn't know. Does anyone have one for 7.10 and can someone help me install it?
You can download a deb package file for 7.10 from the [*The WineHQ .deb packages archive*]("http://wine.budgetdedicated.com/archive/index.html"). You will not be able to find the latest version there, since they recently started producing debs only for 8.04, but you will be able to download a recent version nevertheless.

If you want the latest version, I believe the only option would be to compile it yourself or find a package that someone else has made.

---

### Post by cogadh on 2008-05-06
The repositories are still there and functioning normally, they just aren't updating them with the latest Wine packages anymore. Even if you download the package manually, you are still going to run into the problem of dependencies that can't be met with a manual install. Using the repository method is just easier in the long run.

---

### Post by avgazn on 2008-05-07
> **cogadh said:**
> Sticky thread right at the top of this forum:
[http://ubuntuforums.org/showthread.php?t=624644](http://ubuntuforums.org/showthread.php?t=624644)

I don't think this will work because I have no internet...

I have the deb but it won't install because I dont have bin-fmts support installed and I do not know how to install that.

---

### Post by cogadh on 2008-05-07
If you have the ability to temporarily connect your Ubuntu PC to the internet, I highly recommend it. You could manually download and install the binfmt-support package as you did with Wine, but then it would also complain about missing dependencies. With a network connection (and the proper configuration as described in the link I posted), installing Wine is as simple as opening a terminal and typing "sudo apt-get install wine". Everything, including any dependencies like binfmt-support, will be installed automatically.

BTW - If your machine is triple boot and you originally downloaded the Wine package using one of your Windows installs, why doesn't Ubuntu have the same network connection?

---

### Post by avgazn on 2008-05-08
> **cogadh said:**
> If you have the ability to temporarily connect your Ubuntu PC to the internet, I highly recommend it. You could manually download and install the binfmt-support package as you did with Wine, but then it would also complain about missing dependencies. With a network connection (and the proper configuration as described in the link I posted), installing Wine is as simple as opening a terminal and typing "sudo apt-get install wine". Everything, including any dependencies like binfmt-support, will be installed automatically.

BTW - If your machine is triple boot and you originally downloaded the Wine package using one of your Windows installs, why doesn't Ubuntu have the same network connection?

The reason my windows have internet and my ubuntu doesnt is because im using wireless. I have a wireless using a linksys driver and i think i would need wine to make the internet work. I have a computer right next to my triple boot computer but i don't think that would help. my computers are upstairs and my internet box is downstairs.

---

### Post by cogadh on 2008-05-08
Wine cannot be used to run hardware drivers, it doesn't work like that. I'm not all that familiar with using wireless networking in Ubuntu (I've heard it can be a pain), but if your wireless device is a Linksys, it really shouldn't be too hard to set up. I believe Linksys products are actually quite well supported in Linux.

---

### Post by YokoZar on 2008-05-09
> **cogadh said:**
> With a network connection (and the proper configuration as described in the link I posted), installing Wine is as simple as opening a terminal and typing "sudo apt-get install wine". Everything, including any dependencies like binfmt-support, will be installed automatically.
Actually it's as simple as [clicking this link](apt://wine) ;)

---

