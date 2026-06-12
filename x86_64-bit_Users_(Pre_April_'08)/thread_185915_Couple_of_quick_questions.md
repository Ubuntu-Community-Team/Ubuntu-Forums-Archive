---
title: "Couple of quick questions"
date: 2006-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Princey on 2006-06-01
I've been running linux for quite a while and just got a new machine. Specs are:

AMD 64 X2 3800+
1 GB DDR400 RAM 
250 GB SATA HD (empty for now)
80 GB SATA (came with Windows XP Media Center 2005 SP2)
ATI X600 SLI 250 MB Graphics Card
Realtek Onboard Soundcard (disabled in the bios)
SoundBlaster Audigy 2 
Onboard nVidia Lan chipset
DLink DWL G510 PCI Wireless Card

Well, the rest are the usual. Here are my questions. 
1. I downloaded 6.06 64 bit yesterday but understand Dapper is out today, is that the same versions or it's a bit different and I need to redownload?

2. Which is more beneficial to me? 64bit OS or 32bit? Although presently it will be used for ordinary computing, I plan to move into programming later down this year. I've read the post [http://www.ubuntuforums.org/showthread.php?t=185873]("http://www.ubuntuforums.org/showthread.php?t=185873") through and through but still don't quite get the bit on true 64bit and 64 bit k-8.

3. What issues, if any, with the above hardware will I face? I'm not new to compiling stuff, but I rather know the heads up before doing anything. 

Thanks for the anticipated answer, gents and ladies.

---

### Post by miggl on 2006-06-01
Hi Princey!
Your setup sounds like it would work with K8 which is supposed to be optimized for AMD64 Athlon (and a few other AMD processors). I believe this is the case with your dual-core processor.

Do this: Open Synaptic, go into advanced mode, and search for amd64-k8. Read the description of the packages to make sure they support your processor (I'm not at home at the moment, so I can't check it myself).

Here's what I would do, if you are installing from scratch: try it with k8 kernel, and if it works without any noticable slowness, keep it. If it doesn't work right after that, reinstall from scratch and stick with the amd64-generic kernel.

I've been running the K8 kernel now for the past 2 weeks on my AMD64 Athlon 3500+ with no troubles at all.

Good luck! :)

---

### Post by Princey on 2006-06-01
[QUOTE=miggl]Hi Princey!
Your setup sounds like it would work with K8 which is supposed to be optimized for AMD64 Athlon (and a few other AMD processors). I believe this is the case with your dual-core processor.

Do this: Open Synaptic, go into advanced mode, and search for amd64-k8. Read the description of the packages to make sure they support your processor (I'm not at home at the moment, so I can't check it myself).

Here's what I would do, if you are installing from scratch: try it with k8 kernel, and if it works without any noticable slowness, keep it. If it doesn't work right after that, reinstall from scratch and stick with the amd64-generic kernel.

I've been running the K8 kernel now for the past 2 weeks on my AMD64 Athlon 3500+ with no troubles at all.

Good luck! :)[/QUOTE]

Thanks miggl for your answer. I'm yet to install dapper. I ran kubuntu on my previous machine (amd 750 duron). I'm pretty much headed for a fresh clean install, that's why I'm here asking which is better before I do an install. I'll wait for more feedback from those who've tried it to see what their experiences are like before I install. Maybe over the weekend.

---

### Post by miggl on 2006-06-02
I'm home now, and was able to check the description of the K8 kernel:
> Complete Linux kernel on AMD K8.
This package will always depend on the latest complete Linux kernel available
for AMD Athlon64/Athlon FX/Opteron.

Since you hava an Athlon64 x2 I think you should be good to go. I'll do some more poking around on the subject, too.

---

### Post by miggl on 2006-06-02
You might want to check into this thread, it deals specifically with your issue:
[http://www.ubuntuforums.org/showthread.php?t=182258&highlight=amd64-k8](http://www.ubuntuforums.org/showthread.php?t=182258&highlight=amd64-k8)

---

### Post by Princey on 2006-06-02
Thanks for the feedback. I'm still doing some reading. I think I might download a few live CD's to test it out before I do any actual hard drive installation. Thanks again for your input.

---

### Post by Princey on 2006-06-02
One more question, I see reference to the k-7, k-8, i686 kernels. From what I can remember (correct me if I'm wrong) when I installed breezy, these options were available when you chose an iso image to download. I don't see that this time around. Does that mean the options are available during install only?

---

### Post by henriquemaia on 2006-06-02
[quote=Princey]One more question, I see reference to the k-7, k-8, i686 kernels. From what I can remember (correct me if I'm wrong) when I installed breezy, these options were available when you chose an iso image to download. I don't see that this time around. Does that mean the options are available during install only?[/quote]

You adjust that after installation. The different kernels will be available through synaptic.

---

### Post by Princey on 2006-06-02
Thanks for the answers so far but I've got one more. Somehow, Dapper seems to have changed how we got used to some things. There's a Desktop version and an Alternate Version. What are the differences? If I go with the Desktop version, do I still have the options to configure my partitions, i.e. split my partitions separately into /root /usr /home /swap or is that available with the Alternate version? I've read the differences on the main page but that doesn't give much as to what you can or can't do with one over the other. I understand the Desktop version is also a Live version which is neat, but will I have total control over my installation as text based installs affords me?

---

### Post by henriquemaia on 2006-06-02
[quote=Princey]Thanks for the answers so far but I've got one more. Somehow, Dapper seems to have changed how we got used to some things. There's a Desktop version and an Alternate Version. What are the differences? If I go with the Desktop version, do I still have the options to configure my partitions, i.e. split my partitions separately into /root /usr /home /swap or is that available with the Alternate version? I've read the differences on the main page but that doesn't give much as to what you can or can't do with one over the other. I understand the Desktop version is also a Live version which is neat, but will I have total control over my installation as text based installs affords me?[/quote]

I have only used the alternate version, but I suppose live will give the same options as alternate. Read this thread for more info:

[http://www.ubuntuforums.org/showthread.php?t=154569](http://www.ubuntuforums.org/showthread.php?t=154569)

---

### Post by miggl on 2006-06-02
[QUOTE=Princey]Thanks for the answers so far but I've got one more. Somehow, Dapper seems to have changed how we got used to some things. There's a Desktop version and an Alternate Version. What are the differences? If I go with the Desktop version, do I still have the options to configure my partitions, i.e. split my partitions separately into /root /usr /home /swap or is that available with the Alternate version? I've read the differences on the main page but that doesn't give much as to what you can or can't do with one over the other. I understand the Desktop version is also a Live version which is neat, but will I have total control over my installation as text based installs affords me?[/QUOTE]
I've always only went with the text install version, because it affords the cleanest install possible. The live CD will write things to your hard-drive and not necessarily give you all the options you need. I remember having some significant problems getting things to work for my setup using the Live/Desktop installation.
Also, don't be afraid of the text install, it might sound a bit scary and infer that you have to do some command-line magic, but that's not the case. It is very simple, straightforward, no-frill, no-thrill typ of setup where you get exactly what you expect.
The Live/Desktop setup does allow you to set partitions, but I think it is limited in certain ways that the text install isn't (not 100% on this). I equate the Live/Desktop install to installing Windows XP from the CD when already running windows, rather than booting from the CD.
Keep us posted on your progress. :)

---

### Post by Princey on 2006-06-02
[QUOTE=miggl]I've always only went with the text install version, because it affords the cleanest install possible. The live CD will write things to your hard-drive and not necessarily give you all the options you need. I remember having some significant problems getting things to work for my setup using the Live/Desktop installation.
Also, don't be afraid of the text install, it might sound a bit scary and infer that you have to do some command-line magic, but that's not the case. It is very simple, straightforward, no-frill, no-thrill typ of setup where you get exactly what you expect.
The Live/Desktop setup does allow you to set partitions, but I think it is limited in certain ways that the text install isn't (not 100% on this). I equate the Live/Desktop install to installing Windows XP from the CD when already running windows, rather than booting from the CD.
Keep us posted on your progress. :)[/QUOTE]

Thanks miggl. I am by no means afraid of the text install. I've used it back in the days when I installed Red Hat 6, Mandrake, Suse and even Hoary and Breezy. I've downloaded both versions via bittorrent and currently seeding to help out those who want to download. I'm going to use the alternate version as from what I've exhaustively read, it seems to be my better bet at having as much control over my installation as possible. I will keep the forum posted of my experience when I take that plunge later in the evening as I got some stuff to do so I'm 'loaning' my machine via bittorrent in the meanwhile to ease the pressure of those seeding via torrents. Thanks to all who assisted. :)

---

### Post by Princey on 2006-06-02
_Update_

I thought I was done asking questions, doesn't seem so. I'm currently posting using the Live/Install CD although I'll be using the Alternative CD to install. I succeeded in booting up after a few glitches and I've got one question more to ask. When I booted using the 1st option, the comp ran fair enough until it was time to load the desktop manager. I was returned after a pretty quick text display to a blank screen with the Kubuntu logo and a progress bar at the maximum. Stayed 5 minutes waiting, nothing. I pressed CTRL + ALT + DEL and the system rebooted. Tested the CD using the boot method mentioned (checksum passed while burning anyhow), that passed. Rebooted and tried again. Same as the above. After pressing ALT + F2, I got to a text based screen with: > ubuntu@ubuntu: $ I typed > startx and got a string of messages with a bug report and crash report. Nothing worked so I rebooted, this time, I chose "limited graphics" as my option and it worked. Here I am now. So, my question is, has anyone encountered that error message and what are the odds with me hitting that block with the text install?

---

### Post by miggl on 2006-06-07
To boot into the graphical desktop don't use **startx**, use **gdm** instead.
If you're still getting errors, try my suggestions here: [http://ubuntuforums.org/showthread.php?t=186546](http://ubuntuforums.org/showthread.php?t=186546).
I had that problem when my video drivers weren't installed correctly, or when I messed up the xserver settings.

---

### Post by Princey on 2006-06-09
[QUOTE=miggl]To boot into the graphical desktop don't use **startx**, use **gdm** instead.
If you're still getting errors, try my suggestions here: [http://ubuntuforums.org/showthread.php?t=186546](http://ubuntuforums.org/showthread.php?t=186546).
I had that problem when my video drivers weren't installed correctly, or when I messed up the xserver settings.[/QUOTE]

Thanks for the input, miggl. This is a fresh install on my new comp. I run Kubuntu, not Ubuntu so I just changed the gdm to kdm however, when I type ```
kdm
``` I get > kdm owned by root. Only root can start kdm Obviously, I then type ```
sudo kdm
``` with the result > username: ******* password: ******* When I type my username and password, all I get is the prompt with my username again. I've read the post you described but I don't have an nVidia Card. I have an ATI X600 SLI Graphics card (graphics card and tv tuner card). How can I possibly get around this?

---

### Post by miggl on 2006-06-09
[QUOTE=Princey]I've read the post you described but I don't have an nVidia Card. I have an ATI X600 SLI Graphics card (graphics card and tv tuner card). How can I possibly get around this?[/QUOTE]

I'm not sure if KDE uses XServer or not for its display? If it does, go ahead and edit your xorg.conf file as described in the other post, changing the appropriate entry to "vesa" (in your ATI section). A good idea would be to just copy the line, comment out the original, and change the copy to "vesa" (vesa should work for ATI as well). Then, once you're back in KDE, reinstall your ATI drivers, and change the line in xorg.conf back to its original.

I think this should work, unless ATI and/or KDE do things drastically different.

---

### Post by Princey on 2006-06-09
[QUOTE=miggl]I'm not sure if KDE uses XServer or not for its display? If it does, go ahead and edit your xorg.conf file as described in the other post, changing the appropriate entry to "vesa" (in your ATI section). A good idea would be to just copy the line, comment out the original, and change the copy to "vesa" (vesa should work for ATI as well). Then, once you're back in KDE, reinstall your ATI drivers, and change the line in xorg.conf back to its original.

I think this should work, unless ATI and/or KDE do things drastically different.[/QUOTE]
Thanks miggl. Apparently, it doesn't. Please see a new thread [http://www.ubuntuforums.org/showthread.php?t=192936]("http://www.ubuntuforums.org/showthread.php?t=192936") I've started with detailed info as to what's happening.

---

