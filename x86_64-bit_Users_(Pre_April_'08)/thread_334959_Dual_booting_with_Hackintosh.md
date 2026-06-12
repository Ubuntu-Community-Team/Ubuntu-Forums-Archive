---
title: "Dual booting with Hackintosh"
date: 2007-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by kingleer on 2007-01-09
Okay, this may seem a little unusual. On my desktop machine I want to dual boot ubuntu X86_64 with osx_86. Now, I have dual booted in the past with ubuntu and windows so I know ubuntu can dual boot with windows no problem, Now, I'm replacing windows with osx, since I've pretty much no longer use windows and am interested in playing around with osx86. 
    Now, I've installed osx86 on a separate ATA hard drive from my Ubuntu installation and It works fine by itself. Than I stick in another SATA hard drive, and try to install the 64 bit verision of Ubuntu. 
When the installation finishes, I can enter Ubuntu, but Ubuntu doesn't recognize my os x 86 installation (there is no dual boot menu allowing me to select whether I want to use ubuntu or osx86). When I remove my ubuntu hard drive I am unable to boot into osx86 (It gives me a grub error), so I think the PATA hard drive osx_86 is installed on is the master drive. 

Does anyone know how I would go about getting ubuntu  X64  to dual boot with osx86? Thanks

---

### Post by maxamillion on 2007-01-09
Boot into ubuntu and type this at the command line 

```
sudo update-grub
```

hopefully it will see the other hard drive .... if not you might need to edit the grub menu by hand, if that is the case then post back and we will go from there.

---

### Post by kingleer on 2007-01-13
Sorry for the long delay. My main comp is my laptop, and that already has ubuntu running perfectly . I've been kinda  busy. 

Okay, typed what you said and going for a reboot. 

Nope. OSx86 doesn't come up.

---

### Post by kingleer on 2007-01-14
Again any help anyone can give would be appreciated. I'm trying to follow - 

[http://wiki.osx86project.org/wiki/index.php/Install_On_A_Partition_Simple_And_Accurate#Grub_for_newbies](http://wiki.osx86project.org/wiki/index.php/Install_On_A_Partition_Simple_And_Accurate#Grub_for_newbies)

But without much luck. 

Hmm, found this: 

[http://ubuntuforums.org/showthread.php?t=319721](http://ubuntuforums.org/showthread.php?t=319721) 

Checking it out

---

### Post by aanderse on 2007-01-14
it sounds like grub is not recognizing your osx operating system.  if this is the case you will have to log into ubuntu and manually edit /boot/grub/menu.lst and add the operating system yourself and you will be up and running.

[EDIT] oh wow i should have read those links you posted as they already told you what i did ... sorry :)

---

### Post by kingleer on 2007-01-14
Rofl. ITs okay. Yeah, I tried doing it alone. I tried

sudo gedit /boot/grub/menu.lst

and added 

title OSX_X86
 rootnoverify (hd0,0)
 makeactive
 chainloader +1 

Get an error saying can't load operating system at boot. I figure I'm gonna have to reinstall ubuntu and osx, but I don't have anything important on this comp. 

Figure I should I have stuck with 

title OSX_X86
 rootnoverify (hd0,0)
 chainloader +1

---

### Post by kingleer on 2007-01-17
Nope that didn't work. 

Can anyone tell me what I'm doing wrong?

---

### Post by kingleer on 2007-01-17
[http://www.ubunturunsforums.org/showthread.php?t=275728&highlight=osx86](http://www.ubunturunsforums.org/showthread.php?t=275728&highlight=osx86) 

The solution above is the one I'm going to follow. I have two drives as is in my desktop computer and my laptop only ubuntu...

---

### Post by patrickfromspain on 2007-01-17
have you tried with the same line windows has?

title		Mac OS X
root		(hd0,0)
savedefault
makeactive
chainloader	+1

or

title		Mac OS X
root		(hd0,0)
chainloader	+1

I had it working and I believe it was one of those which did the trick.

---

