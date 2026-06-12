---
title: "All I want to do is access a drive off windows?"
date: 2008-05-08
forum: x86 64-bit Users
---

### Post by jcmvp on 2008-05-08
I'm having the most difficult time with this. I've spent a good few days trying to do it but now I'm just lost. I have the newest release of ubuntu... I'm still a n00b coming from going into linux. But this is what I want to do... I have an external hard drive on my vista ultimate machine that is simply plugged in via usb. All I did was set that drive (g:) to be shared and then i enabled the wins support. 

On my ubuntu machine, i've gone through several tutorials and now my brain is just a mess. I think I'm trying to mount that drive to a folder within samba? I'm not sure anymore because in "Networks", I can see "MyFiles" (from another tutorial) under My Windows computer. I'm just so confused its ridiculous.

These are the links to the tutorials I've been using:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html#comment-95826](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html#comment-95826)

[http://ubuntuforums.org/showthread.php?t=511327](http://ubuntuforums.org/showthread.php?t=511327)

[http://linux.die.net/man/8/mount.cifs](http://linux.die.net/man/8/mount.cifs)

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)


Can anybody help me?

---

### Post by prshah on 2008-05-08
> **jcmvp said:**
> 
On my ubuntu machine, i've gone through several tutorials and now my brain is just a mess.

These are the links to the tutorials I've been using:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html#comment-95826](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html#comment-95826)
[http://ubuntuforums.org/showthread.php?t=511327](http://ubuntuforums.org/showthread.php?t=511327)
[http://linux.die.net/man/8/mount.cifs](http://linux.die.net/man/8/mount.cifs)
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)


Can you try one more: [http://ubuntuforums.org/showthread.php?t=785517](http://ubuntuforums.org/showthread.php?t=785517)

It seems to have helped a number of people today; I'm a little surprised myself.

---

### Post by jcmvp on 2008-05-08
I'll let you know in a bit ^_^

---

### Post by jcmvp on 2008-05-08
Tried it and I was really hoping to. But it just tells me it can't mount the drive. I don't know what else to do... it says I have a share called '/home/samba/'.......................... this sucks.

---

### Post by saru411 on 2008-05-08
this has solved all of my hdd mounting issues

[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

it should solve yours

---

### Post by jcmvp on 2008-05-08
From what I get out of that guide is mounting from windows that is dualbooted on your machine already. This is two different boxes... this is probably the most annoying thing I've ever come across. But I'm not giving up!

---

### Post by prshah on 2008-05-09
> **jcmvp said:**
> Tried it and I was really hoping to. But it just tells me it can't mount the drive. 

A more specific error message, please? Perhaps a screenshot?

---

### Post by Em-Buntu on 2008-05-09
What are you actually trying to do?

I have a Windows2000 (NTFS) system on my network that I access with my Ubuntu system using the ubuntu disk mount app. It works great, with no problems.
I can also access USB flash drives plugged into the Win2K system, with no problem which is close to what you are attempting to do.
The difference is, I am not using Apache, but just plain network access. Still, it should work as well, unless you don't have permissions configured correctly.

---

### Post by jcmvp on 2008-05-09
Before I post screenshots... I want to ask Em-Buntu what the name of the 'disk mount app' he uses. Maybe I can give that a shot first. Oh... and I'm not running any apache software either... I am however running cassani on my vista box but I don't see that being a problem...?

---

