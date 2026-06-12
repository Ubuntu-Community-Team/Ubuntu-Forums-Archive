---
title: "My Ubuntu 7.10 64-bit stability experiences"
date: 2008-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by dominikgeisler on 2008-01-09
Hi, 

I just wanted to share my - sometimes frustrating - expirience with the ubuntu stability. Since I really like Ubuntu, I want to solve the problems, and I thought this might also be the right place to obtain help. 

Three days ago my Ubuntu installation crashed hard, in a way that it often does: The screen turns white, and no ctrl-alt-del, ctrl-alt-backspace, ctrl-alt-1 or anything else but a hard reset helped (I use the fglrx driver that comes with Ubuntu for my Radeon Xpress 200). Rebooted and continued working. 

The next day I got the incredibly annoying "your FS has been mounted 34 times; check forced" warning. I read somewhere I could cancel it with alt-sysrq-k, but the boot process failed because of cancelling the unnecessary check. 

I rebooted and let the 10-minute-check run (250 GB HD). 

Atfer logging in, I got another favourite error: Gnome failed to load its settings (or something like that) and displays the default icons instead of the Ubuntu ones. (error: *Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.*)

I really like using free software and having as OS that doesn't spy on me, but it has almost come to the point where I'd rather boot Windows when I want to do something quickly, especially when the forced FS check is coming close. 

Do others share these problems? Are there solutions for mine?

**Edit: My X-server just rebooted after skipping a bit in a video file with vlc. And that's also happened before... **

---

### Post by wolfen69 on 2008-01-09
if you are asking for help, you are better off picking the right forum in which to ask questions. this forum probably doesnt get as much traffic as support forums. this is basically for posting experiences and testimonials. good luck.

---

### Post by dominikgeisler on 2008-01-10
Could an admin move it, then? Or should I repost it?

---

### Post by RawMustard on 2008-01-10
This is not typical of Ubuntu, but IMHO, it is typical of Gutsy 7.10.  If you can, and your hardware works on Feisty 7.04, go back to that.  Honestly, Gutsy is a huge disappointment, they lost the plot with this latest version, particularly the 64bit version and fixes don't seem to be forthcoming.

---

### Post by Sef on 2008-01-10
Moved to 64-bit forum.

---

### Post by Yellow Pasque on 2008-01-10
I just wanted to note that the fsck is not unnecessary, any more than Scandisk is under Windows. You do like a non-corrupt file system, don't you?

If you don't like the way Ubuntu does this, then run the check at some other time when your computer is sitting idle for 10 minutes.

---

### Post by Kilz on 2008-01-10
> **dominikgeisler said:**
> 
Three days ago my Ubuntu installation crashed hard, in a way that it often does: The screen turns white, and no ctrl-alt-del, ctrl-alt-backspace, ctrl-alt-1 or anything else but a hard reset helped (I use the fglrx driver that comes with Ubuntu for my Radeon Xpress 200). Rebooted and continued working. 


This sounds like the wrong video driver loaded after a crash, or one was not found. It is common if the mesa driver is being used instead of the ATI driver. To check open a terminal and type in ```
fglrxinfo 
```
If it lists mesa as the driver you may need to do some setup to make sure the ATI driver is used.

---

### Post by dominikgeisler on 2008-01-10
> **Temüjin said:**
> I just wanted to note that the fsck is not unnecessary, any more than Scandisk is under Windows. You do like a non-corrupt file system, don't you?

If you don't like the way Ubuntu does this, then run the check at some other time when your computer is sitting idle for 10 minutes.

Yes, I understand that checking a file system is useful. But why not check it after a crash, which is when you may really need it? That's also what Windows does. Why not give an option to do it next time, especially since ext3 is supposed to be so much better than ntfs? What if I need to do a presentation and the laptop is checking the FS for 10 minutes? If Ubuntu wants to be good for end-users, someone will have to explain to them why the file system is more important than their presentation. 

Unmounting the FS and checking it while the computer is idling is also not a user-friendly solution, as it is way too difficult. I became somewhat apted at linux, but I wouldn't know how to do the check with my encrypted container.

---

### Post by dominikgeisler on 2008-01-10
> This is not typical of Ubuntu, but IMHO, it is typical of Gutsy 7.10. If you can, and your hardware works on Feisty 7.04, go back to that. Honestly, Gutsy is a huge disappointment, they lost the plot with this latest version, particularly the 64bit version and fixes don't seem to be forthcoming. 
> Someone suggested to me, to install and run the 32-bit version of Ubuntu, rather than the 64-bit version. (I was so clueless, I thought I had to use the 64-bit version because I have an AMD64 machine.)

Hmmm... I just spent a lot of time setting everything up right, so I don't really want to try 32-bit or 7.04. Thanks for the suggestions though, the one script looks really cool.

---

### Post by brucewagner on 2008-01-10
I am a brand new user, so take this suggestion with a BIG grain of salt....  but...

Someone suggested to me, to install and run the 32-bit version of Ubuntu, rather than the 64-bit version.   (I was so clueless, I thought I had to use the 64-bit version because I have an AMD64 machine.)

Also, in this thread, I read about a clean and simple way to get all of your video, flash, DVD, stuff installed properly, cleanly, and quickly... with any new install:  [http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

Maybe some of your crashing involves these issues...  (i.e. the thing with VLC hints at that, etc.)...?

(just trying to help..... with my VERY limited experience... :) )

---

### Post by dominikgeisler on 2008-01-10
> **Kilz said:**
> This sounds like the wrong video driver loaded after a crash, or one was not found. It is common if the mesa driver is being used instead of the ATI driver. To check open a terminal and type in ```
fglrxinfo 
```
If it lists mesa as the driver you may need to do some setup to make sure the ATI driver is used.

I do use fglrx, as mesa only gave me 640*480 (see [http://ubuntuforums.org/showthread.php?t=631683](http://ubuntuforums.org/showthread.php?t=631683))

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)

```

My xorg.conf (relevant parts):

```

Section "Device"
        Identifier      "ATI Technologies Inc RS480 [Radeon Xpress 200G Series]"
        Driver          "fglrx"
        Busid           "PCI:1:5:0"
        Option          "VideoOverlay" "on"
        Option          "UseFastTLS" "2"
# TLS=0:fast, TLS=1: faster, TLS=2:compatible
#       Option          "EnablePrivateBackZ" "on"
#("this fixed a problem with running fgl_glxgears (and glxgears) displaying gibberish in the created window"
EndSection

Section "Monitor"
        Identifier      "Belinea10171"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RS480 [Radeon Xpress 200G Series]"
        Monitor         "Belinea10171"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024"     "1024x768"      "832x624"      "800x600"        "720x400"       "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        screen          "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
EndSection

Section "Module"
#       Load            "glx"
EndSection

Section "Extensions"
        Option          "Composite"     "Disable"
        Option          "XVideo"        "Enable"
EndSection


```

---

### Post by tomdkat on 2008-01-10
With regard to the long running fsck, one thing I did with my 160GB HDD was carve it up into different partitions.  Now, when my system runs periodic disk checks (usually after a clean reboot) it will check only the filesystems that are determined to be in need of a check. Not all of my partitions get checked each time the fsck runs.

This might not help in the case of a hard crash but depending on how the filesystems are laid out (and used), it might since not every filesystem would be affected by the system crash.

Peace...

---

### Post by dogson on 2008-01-11
> **dominikgeisler said:**
> Yes, I understand that checking a file system is useful. But why not check it after a crash, which is when you may really need it? That's also what Windows does. Why not give an option to do it next time, especially since ext3 is supposed to be so much better than ntfs? What if I need to do a presentation and the laptop is checking the FS for 10 minutes? If Ubuntu wants to be good for end-users, someone will have to explain to them why the file system is more important than their presentation. 

Unmounting the FS and checking it while the computer is idling is also not a user-friendly solution, as it is way too difficult. I became somewhat apted at linux, but I wouldn't know how to do the check with my encrypted container.

The mount count based fsck:s arent really that neccesarry when using EXT3 in journal or ordered mode (the default), you can disable the checks with tune2fs -c 0 /dev/yourdisk as root, fsck should still run if it detects an unclean shutdown.

---

### Post by kvonb on 2008-01-11
-

---

### Post by dominikgeisler on 2008-01-11
> **dogson said:**
> The mount count based fsck:s arent really that neccesarry when using EXT3 in journal or ordered mode (the default), you can disable the checks with tune2fs -c 0 /dev/yourdisk as root, fsck should still run if it detects an unclean shutdown.

How do I do that when it's in an encrypted volume? To be honest, I don't really understand how my encrypted volume works. Does my HD have one container with different partitions in it, or is each partition encrypted seperately? 
In /etc/crypttab, I see: 
```
sdb5_crypt /dev/disk/by-uuid/83ec8b9b-c115-45f0-89cf-9ba40cc817e4 none luks
```
where uuid 83ec.... is /dev/sdb5
In /etc/fstab, the mounts are: 
```
# /dev/mapper/ubuntu--7.10-root
UUID=3ca7b952-9bf0-4c57-a98d-acc7e7861cd0 /               ext3    defaults,errors=remount-ro,noatime 0       1
# /dev/sdb1
UUID=090ae96a-6d76-43b5-b97b-623a2d7b7e0f /boot           ext3    defaults        0       2
# /dev/mapper/ubuntu--7.10-swap_1
UUID=15d90119-da85-44e6-b2cd-3d24cd0cfc49 none            swap    sw  
```

The UUIDs refer to the location in the comments. When I look in /dev/mapper, I see
```
crw-rw---- 1 root root  10, 63 2008-01-11 18:28 control
brw-rw---- 1 root disk 254,  0 2008-01-11 17:28 sdb5_crypt
brw-rw---- 1 root disk 254,  3 2008-01-11 17:29 truecrypt0
brw-rw---- 1 root disk 254,  1 2008-01-11 17:28 ubuntu--7.10-root
brw-rw---- 1 root disk 254,  2 2008-01-11 17:28 ubuntu--7.10-swap_1
```

And that's where I stop understanding how this encrypted partition stuff works. Using sudo less -f ubuntu--7.10-root i see it's some ugly binary file. Can't figure out what it's supposed to do.

 Would tune2fs -c 0 /dev/mapper/ubuntu--7.10-root disable the checking?

---

### Post by exactopposite on 2008-01-11
> **dominikgeisler said:**
> 

The next day I got the incredibly annoying "your FS has been mounted 34 times; check forced" warning. I read somewhere I could cancel it with alt-sysrq-k, but the boot process failed because of cancelling the unnecessary check. 

I rebooted and let the 10-minute-check run (250 GB HD). 




as for the fsck on startup, u might want to isntall autofsck. it alerts you on shutdown and asks if u want to  run fsck. If you say yes, it'll run before shutdown. If you say no it will jsut remind you the next time you shutdown. This works better for me than having it run on startup.

---

### Post by crjackson on 2008-01-11
> **RawMustard said:**
> This is not typical of Ubuntu, but IMHO, it is typical of Gutsy 7.10.  If you can, and your hardware works on Feisty 7.04, go back to that.  Honestly, Gutsy is a huge disappointment, they lost the plot with this latest version, particularly the 64bit version and fixes don't seem to be forthcoming.

It's NOT typical of Gutsy either.  I'm a Linux newbie myself, but I've done more than 200 installs of Gutsy with minimal problems, and those problems weren't really problems.  They were ME not knowing how to change a few settings on particular systems that needed to be tweaked.  I'm not saying it's perfect but it's no dog either.

---

### Post by dominikgeisler on 2008-01-11
Well, the radeon driver *did* work on 7.04 for me, and not on 7.10. Is there any way to update the open-source-driver?

---

### Post by Kilz on 2008-01-11
> **exactopposite said:**
> as for the fsck on startup, u might want to isntall autofsck. it alerts you on shutdown and asks if u want to  run fsck. If you say yes, it'll run before shutdown. If you say no it will jsut remind you the next time you shutdown. This works better for me than having it run on startup.

Execlent script!!! It isnt in the repositories, [but it is on the wiki. ]("https://wiki.ubuntu.com/AutoFsck") I set fsck to check on shutdown. That way it runs when I am not in a hurry to use the computer.

---

### Post by dogson on 2008-01-12
> **dominikgeisler said:**
> How do I do that when it's in an encrypted volume? To be honest, I don't really understand how my encrypted volume works. Does my HD have one container with different partitions in it, or is each partition encrypted seperately? 
In /etc/crypttab, I see: 
```
sdb5_crypt /dev/disk/by-uuid/83ec8b9b-c115-45f0-89cf-9ba40cc817e4 none luks
```
where uuid 83ec.... is /dev/sdb5
In /etc/fstab, the mounts are: 
```
# /dev/mapper/ubuntu--7.10-root
UUID=3ca7b952-9bf0-4c57-a98d-acc7e7861cd0 /               ext3    defaults,errors=remount-ro,noatime 0       1
# /dev/sdb1
UUID=090ae96a-6d76-43b5-b97b-623a2d7b7e0f /boot           ext3    defaults        0       2
# /dev/mapper/ubuntu--7.10-swap_1
UUID=15d90119-da85-44e6-b2cd-3d24cd0cfc49 none            swap    sw  
```

The UUIDs refer to the location in the comments. When I look in /dev/mapper, I see
```
crw-rw---- 1 root root  10, 63 2008-01-11 18:28 control
brw-rw---- 1 root disk 254,  0 2008-01-11 17:28 sdb5_crypt
brw-rw---- 1 root disk 254,  3 2008-01-11 17:29 truecrypt0
brw-rw---- 1 root disk 254,  1 2008-01-11 17:28 ubuntu--7.10-root
brw-rw---- 1 root disk 254,  2 2008-01-11 17:28 ubuntu--7.10-swap_1
```

And that's where I stop understanding how this encrypted partition stuff works. Using sudo less -f ubuntu--7.10-root i see it's some ugly binary file. Can't figure out what it's supposed to do.

 Would tune2fs -c 0 /dev/mapper/ubuntu--7.10-root disable the checking?

yes, that should do it, fsck would still check the filesystem in an time interval 6 month or so, to disable that use the -i 0 flag

---

### Post by Kilz on 2008-01-12
> **dogson said:**
> yes, that should do it, fsck would still check the filesystem in an time interval 6 month or so, to disable that use the -i 0 flag

But isnt that a bad idea? fsck checks for errors and fixes them. 6 months to me is real risky. Never doing it is even more so. Just like all the Windows users who never run chdisk and defrag. Leaving the settings as they were and using autofsck to make the check happen at shutdown seems like a better idea. That way it would do the check when you are walking away from the computer.

---

### Post by dominikgeisler on 2008-01-12
Hi, 

I used the script now to have the scan is done on shut down. That won't fix my stability issues, though. Any other ideas? Can I update the OSS radeon driver, or is it part of the kernel? I don't really want to try the new ATI driver, since all my experiences with installing ATI drivers have been awful. 

oh, and can anyone explain further how the excrypted FS really works?

---

### Post by Kilz on 2008-01-12
> **dominikgeisler said:**
> Hi, 

I used the script now to have the scan is done on shut down. That won't fix my stability issues, though. Any other ideas? Can I update the OSS radeon driver, or is it part of the kernel? I don't really want to try the new ATI driver, since all my experiences with installing ATI drivers have been awful. 

oh, and can anyone explain further how the excrypted FS really works?

Ubuntu will keep the latest version of the open source driver installed through the update manager. If you did install the ATI driver, I would use the 8.40.4 version. The new 7 series that actually started with 8.41.7 isnt quite right just yet, they are still working out the bugs.

---

### Post by stefcep on 2008-01-13
> **RawMustard said:**
> This is not typical of Ubuntu, but IMHO, it is typical of Gutsy 7.10.  If you can, and your hardware works on Feisty 7.04, go back to that.  Honestly, Gutsy is a huge disappointment, they lost the plot with this latest version, particularly the 64bit version and fixes don't seem to be forthcoming.

 I can't agree that this is the case with all machines.  On my machine I installed with NO hassles at all, all hardware recognized and working, including sound, and all apps work perfectly without a single crash.  .  With Fiesty I had dial-up issues, sound issues.  Interestingly on my AMD 4800+, on asus m2n-mx with 2 gb ram and using built in graphics and sound, 64bit 7.10 installed perfectly but 32bit showed screen corruption and took longer. BUT I am still not convinced that 64-bit has any speed advantages:  I ripped a CD and converted to mp3 and found winxp 32 bit did it just as quickly same compression settings.  I will try ripping a DVD9 to DVD5 next and see which encodes faster: 64-bit Ubuntu with k9copy or winxppro usin dvd-shrink.

---

### Post by Kilz on 2008-01-13
Even slight advantages are better than none. The test of windows vs linux is apples to oranges. Why would anyone want to run virusville?

---

### Post by dominikgeisler on 2008-01-13
> **Kilz said:**
> The test of windows vs linux is apples to oranges. Why would anyone want to run virusville?

In my case: because it's stable.

more on-topic: The comparison is indeed flawed, 32-bit-Ubuntu vs. 64 bit would be better.

---

### Post by Kilz on 2008-01-13
> **dominikgeisler said:**
> In my case: because it's stable.

more on-topic: The comparison is indeed flawed, 32-bit-Ubuntu vs. 64 bit would be better.

While you may have some issues, your experience may not be the norm. 

White screen after a crash - Do you still have a blank screen? If so did you install the ATI driver from ATI?

Fsck - As stated elseware this is a useful tool that should be ran. It looks like you have it now setup to run on shutdown.

So you have 2 issues and you think that Windows is more stable? Ever run Windows ME?

---

### Post by dominikgeisler on 2008-01-13
> **Kilz said:**
> While you may have some issues, your experience may not be the norm.

...which is why I said: "in my case". With Ubuntu 7.04, I had perfect stability. 

> **Kilz said:**
> White screen after a crash - Do you still have a blank screen? If so did you install the ATI driver from ATI?

I don't really understand what you mean. The PC suddenly just shows a white screen, and that's it. After a hard reset, everything is fine again. I didn't download the driver from ATI because of my terrible experiences with installing ATI drivers. 

> **Kilz said:**
> Fsck - As stated elseware this is a useful tool that should be ran. It looks like you have it now setup to run on shutdown.

Yup, no more problems for me. But very confusing and annoying to a novice user. 

> **Kilz said:**
> So you have 2 issues and you think that Windows is more stable? Ever run Windows ME?

No, I never used Windows ME. And I completely fail to see the relevance of its (in)stability. 

Windows XP never crashes on my PC (well, maybe once or twice per year), while Ubuntu crashes every couple of days. Doesn't that make XP more stable *for me*? 

p.s: Comparing Ubuntu 7.10 to an OS that came out 7 years earlier is not a very fair comparison. 

p.p.s: Please don't make this into a "Micro$oft is evil"-thread. I only said that on my PC, ubuntu crashes and XP doesn't. I'm here to get help, not to bash Linux. If I hated it, I wouldn't use it.

---

### Post by Kilz on 2008-01-13
> **dominikgeisler said:**
> I don't really understand what you mean. The PC suddenly just shows a white screen, and that's it. After a hard reset, everything is fine again. I didn't download the driver from ATI because of my terrible experiences with installing ATI drivers. 


You have made a choice not to replace the drivers that are at the root of your problem.  Since you are choosing not to do what is needed to fix the issue, do not complain that something is wrong.

> **dominikgeisler said:**
> Yup, no more problems for me. But very confusing and annoying to a novice user. 
A check of the hard disk is confusing? Thats right, windows users dont usually run maintenance  programs. They just suffer with poor performance and problems because the poor design of the operating system that isnt set up to do maintenance automaticly.

> **dominikgeisler said:**
> p.s: Comparing Ubuntu 7.10 to an OS that came out 7 years earlier is not a very fair comparison. 
[Ok how about Vista.]("http://www.google.com/search?q=vista+crashes")

---

### Post by guren on 2008-01-13
This thread is funny cause Windows Vista is causing my Ubuntu Gutsy 7.10 problem:
[Sound Problem on a Dual Boot Ubuntu/Vista HP Laptop]("http://ubuntuforums.org/showthread.php?t=659833")
I mean, if I didn't dual boot with Vista, I wouldn't have any problems at all. :lolflag:

---

### Post by dominikgeisler on 2008-01-14
> **Kilz said:**
> You have made a choice not to replace the drivers that are at the root of your problem.  Since you are choosing not to do what is needed to fix the issue, do not complain that something is wrong.

Well, is there any way to make a system backup before installing the ATI drivers? I seriously am scared of those things and didn't install the new version because of numerous complaints about them being very slow, eating memory etc.

I would most like to just use the OSS driver; this is the first time I had problems with it. 

> [Ok how about Vista.]("http://www.google.com/search?q=vista+crashes")

I really don't see how basing Microsoft will solve my problems. 

And when I google for 'ubuntu crashes', I have 484,000 hits, for 'vista crashes' I have 562,000. Considering the user-base, the google search result is not really that great.

---

### Post by Kilz on 2008-01-14
> **dominikgeisler said:**
> I really don't see how basing Microsoft will solve my problems. 

And when I google for 'ubuntu crashes', I have 484,000 hits, for 'vista crashes' I have 562,000. Considering the user-base, the google search result is not really that great.

I will point out that a Search for Ubuntu crashes will bring up every version and flavor of Ubuntu. Vista is the latest, and only one version.

---

### Post by OmegaBLK on 2008-01-14
> **dominikgeisler said:**
> 
And when I google for 'ubuntu crashes', I have 484,000 hits, for 'vista crashes' I have 562,000. Considering the user-base, the google search result is not really that great.

Very poor metric to use.  Using the number of google page hits to determine the stability of an OS is just as bad as those who like to point at the number of unpatched/patched security vulnerabilities as proof of how insecure/secure a specific software/OS is.

---

### Post by dominikgeisler on 2008-01-14
> **OmegaBLK said:**
> Very poor metric to use.  Using the number of google page hits to determine the stability of an OS is just as bad as those who like to point at the number of unpatched/patched security vulnerabilities as proof of how insecure/secure a specific software/OS is.

> **Kilz said:**
> I will point out that a Search for Ubuntu crashes will bring up every version and flavor of Ubuntu. Vista is the latest, and only one version.

Both true. I was just a little annoyed with the 'one Google search proves that Vista is crappy'-comment. 

Now can we **PLEASE** get off the 'windows is worse'-topic?

---

### Post by Kilz on 2008-01-14
> **dominikgeisler said:**
> Both true. I was just a little annoyed with the 'one Google search proves that Vista is crappy'-comment. 

Now can we **PLEASE** get off the 'windows is worse'-topic?

Vista is crappy is your choice of words. I merely point out that it has a lot of reports of crashing. Vista is not any more or less crappy than any other version of windows. They are all the products of a convicted predatory monopoly.

---

### Post by dominikgeisler on 2008-01-14
Yes Kilz, you are right, Windows is bad and Evil. Happy? 

Possibly aiding more to my problem: Are there any logfiles that would trace the problem?

---

### Post by K.Mandla on 2008-01-16
Please keep the discussion on-topic and civil. The OPer has asked for assistance with his problems; if you can offer a solution please reply. However, let's try to avoid a discussion of the relative merits of operating systems.

---

### Post by Jzege on 2008-01-16
I'm just guessing (novice here too), but have you ever considered if it might be a hardware problem instead? I.e. try running a live cd version of linux (knoppix?) and see if your computer crashes. 

Of course if all else fails just do a system backup with some disk image backup software. Or you can do it manually. And then reinstall a more stable OS (since you suspect it's your graphics card at fault, just find something that works with it). 

Kilz: I can't help but say that you're an idiot with contradictory and really *weak* posts. Of course, that's only my choice of words.

---

### Post by dominikgeisler on 2008-01-16
> **Jzege said:**
> I'm just guessing (novice here too), but have you ever considered if it might be a hardware problem instead? I.e. try running a live cd version of linux (knoppix?) and see if your computer crashes. 

Of course if all else fails just do a system backup with some disk image backup software. Or you can do it manually. And then reinstall a more stable OS (since you suspect it's your graphics card at fault, just find something that works with it). 

Kilz: I can't help but say that you're an idiot with contradictory and really *weak* posts. Of course, that's only my choice of words.

Hi, 

Thanks for the idea, but my HW is fine. It runs stable under WinXP and it ran fine under Ubuntu 7.04 (with OSS driver). I would most want to use the OSS driver again, but as long as I can't set the resolution right it's notr eally possible. Can I build a newer Radeon driver package myself? I saw that the latest version is 0.0.002 versions ahead of the one in Ubuntu. Or is there any telling when the one from Ubuntu will be updated?

---

### Post by speedkreature on 2008-01-16
Is the ATI graphics card you reference on a daughterboard or onboard?  Also, did you manually configure your graphics card or did it auto-detect during the install?

---

### Post by dominikgeisler on 2008-01-17
The ATI card is onboard (Xpress 200). I installed it automatically, but then chenged xorg.xonf to enable Xvideo (80% CPU usage for playing a video is unacceptable).

---

### Post by speedkreature on 2008-01-17
I had a similar problem with my onboard 6150 in 64-bit Ubuntu 7.10 system, but not in the 32-bit version.  I later discovered the problem was the result of SMART being enabled in BIOS for my hard drives.  Probably a BIOS interrupt bug on my mobo.  I had a similar problem with a BioStar board running Windows 2000 several years ago.  I disabled SMART on my Ubuntu box and I've  been stable since (36 days continuous run time so far).  From what you've posted thus far, I don't think that is your problem, but worth a mention.

Would you, by chance, have a backed up copy of your xorg.conf?  I'll re-browse through this thread to see what's been posted so far.
I'm going to do some experimenting with a 64-bit ATI system I've got in a closet (shelved for instability in all 64-bit OS's I've tried to run on it.).  I'll post or PM you if I find something presuming someone else doesn't beat me to it.

In the mean time, make sure your BIOS is current.

Anyone else with more experience is welcomed to chime in.

---

### Post by speedkreature on 2008-01-17
You may already be familiar with this...
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

To answer one of your questions, yes there are generally logs galore. If you were notified of the crash, you will usually find something it /var/crash.  I believe this is data sent to Lauchpad/Ubuntu for debugging.

Logs are generally stored in /var/log though there are exceptions.  The Xserver will have a log with a path of /var/log/Xorg.*
Unless I am mistaken, Xorg usually keeps only two logs there:  The current one and the previous session.
There's a lot of indecypherable goble-de-gook in there for the average joe.  Most of the useful info for you will be at the top or starting at about half-way through it (past the listing of memory addresses; your mileage may vary).

---

### Post by dominikgeisler on 2008-01-19
Hi Speedkreature, 

I backed up the original xorg.conf; after all my awful ATI experiences it's the first thing I do after any linux installation. 

I never get a crash notifier, but will check the xorg logs next time a crash happens.

I looked at the 8.01 ATI driver, but it wouldn't build a Ubuntu package (sudo sh ./ati-driver-installer-8-01-x86.x86_64.run --buildpkg Ubuntu/7.10 results in driver installer aborting), and the many reports of problems, Xvideo tearing and-so-on don't really encourage me. Maybe I will get a cheap nVidia card when I have the money, this is getting ridiculous with the ATI drivers.

---

### Post by dominikgeisler on 2008-01-20
OK, the PC just crashed (at about 14:27:30)

var/log/syslog says: 
```
Jan 20 13:58:17 ubuntu-7 kernel: [ 4934.527347] APIC error on CPU1: 40(40)
Jan 20 13:58:17 ubuntu-7 kernel: [ 4934.528777] APIC error on CPU0: 40(40)
Jan 20 14:00:29 ubuntu-7 kernel: [ 5066.686603] APIC error on CPU1: 40(40)
Jan 20 14:00:29 ubuntu-7 kernel: [ 5066.688068] APIC error on CPU0: 40(40)
Jan 20 14:03:33 ubuntu-7 kernel: [ 5250.465757] APIC error on CPU0: 40(40)
Jan 20 14:03:33 ubuntu-7 kernel: [ 5250.464243] APIC error on CPU1: 40(40)
Jan 20 14:13:07 ubuntu-7 kernel: [ 5898.897283] APIC error on CPU1: 40(40)
Jan 20 14:13:07 ubuntu-7 kernel: [ 5898.899204] APIC error on CPU0: 40(40)
Jan 20 14:17:01 ubuntu-7 /USR/SBIN/CRON[7296]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 20 14:25:33 ubuntu-7 dhclient: DHCPREQUEST on eth0 to 172.30.22.154 port 67
Jan 20 14:25:33 ubuntu-7 dhclient: DHCPACK from 172.30.22.154
Jan 20 14:25:33 ubuntu-7 NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Jan 20 14:25:33 ubuntu-7 dhclient: bound to 85.216.36.158 -- renewal in 1671 seconds.
Jan 20 14:26:20 ubuntu-7 ntfs-3g[6233]: Skipping unrepresentable filename (inode 4286): Invalid or incomplete multibyte or wide character
Jan 20 14:26:20 ubuntu-7 ntfs-3g[6233]: Skipping unrepresentable filename (inode 4234): Invalid or incomplete multibyte or wide character
Jan 20 14:28:50 ubuntu-7 syslogd 1.4.1#21ubuntu3: restart.
```

xorg.log doesn't have anything about the crash, it was written at boot and then stayed unchanged.

---

### Post by hogman500 on 2008-01-20
i think you should probably  disable the x-server and uninstall it and then change your session to GNOME session and try that it should fix the white screen and if your saticfied enouph with your results reinstall your x-server and re enable it.

*note: the white screen is probabely data curoption on your x-server*
*ps i run the 7.10 version of ubuntu on my AMD64 dell*

---

### Post by dominikgeisler on 2008-01-21
> **hogman500 said:**
> i think you should probably  disable the x-server and uninstall it and then change your session to GNOME session and try that it should fix the white screen and if your saticfied enouph with your results reinstall your x-server and re enable it.


I don't quite follow you. I use GNOME, and I thought that GNOME runs on top of X. Did I get something wrong?

---

