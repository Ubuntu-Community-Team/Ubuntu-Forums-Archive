---
title: "Ubuntu 9.04 amd64 refuses to see 4gb ram"
date: 2009-08-23
forum: x86 64-bit Users
---

### Post by KyleRaynor on 2009-08-23
I have triple checked.
My OS, MOBO, and BIOS all support 8gb at the minimum.
And yet when I run :
```

luke@luke-ubuntu:~$ uname -a
Linux luke-ubuntu 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux
luke@luke-ubuntu:~$ cat /proc/meminfo | grep MemTotal
MemTotal:        2837252 kB

```and what's wierder is the fact that in 32bit Vista it acknowledges that I have 4GB even though it can only use 2.7GB

This is a fresh install of Ubuntu, the only modification from that is I have run apt-get upgrade.

What am I missing?


***
Kansas:
    Where the men are men and so are the women!

---

### Post by BlueSkyNIS on 2009-08-23
That's not x64 build.

My x64 system:

> Linux bluesky-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 [COLOR="Lime"]x86_64[/COLOR] GNU/Linux

---

### Post by KyleRaynor on 2009-08-23
But THIS is the iso I burned and used to install. Is there something special you have to do to install the 64bit version from a 64bit disk????
```

luke@luke-ubuntu:/media/disk/ISOs$ ls | grep ubuntu
ubuntu-9.04-desktop-amd64.iso

```

***
Those who believe in astrology are living in houses with foundations of
Silly Putty.
        -- Dennis Rawlins

---

### Post by fela on 2009-08-23
Nope, you obviously didn't install from the 64bit disk, by mistake or whatever. Reinstall with the 64bit disk (making sure it's the 64 bit disk :)) and bob's your uncle.

---

### Post by KyleRaynor on 2009-08-23
Nope, this is the Release file from the disk I used.

***
* knghtbrd ponders how to scare the living [crap] out of 87 people at once..
<knghtbrd> AHH!  I can do it in 3 words!:
<knghtbrd> Microsoft Visual COBOL.

---

### Post by Slim Odds on 2009-08-23
> **KyleRaynor said:**
> Nope, this is the Release file from the disk I used.

Ok, so how is it that you're running a 32 bit kernel when you installed a 64 bit system?

---

### Post by KyleRaynor on 2009-08-24
Beats the hell outta me. Why do you think I had to come here for help? If I knew how that came to be, I'd know how to fix the issue.

***
when i die, i'd like to go peacefully.
in my sleep.
like my grandfather.

not screaming,
like the passengers in his car...

---

### Post by sanderj on 2009-08-24
You could live-boot the AMD64 CD, and then run "uname -a" and "free -m" again... and hopefully see the difference...

HTH

---

### Post by KyleRaynor on 2009-08-24
Ok, I'll try that tomorrow after work. I'm not sure why I didn't think of that.
Is there a way to switch to 64bit **easily** without a reinstall, or is that the crow's path I'll have to take?


***
**Drugs may be the road to nowhere, but at least they're the scenic route!**

---

### Post by fela on 2009-08-24
> **KyleRaynor said:**
> Ok, I'll try that tomorrow after work. I'm not sure why I didn't think of that.
Is there a way to switch to 64bit **easily** without a reinstall, or is that the crow's path I'll have to take?


***
**Drugs may be the road to nowhere, but at least they're the scenic route!**

Switching to 64 bit means reinstalling all your programs, aka reinstalling the operating system. You can't just 'switch to 64 bit' like you say, due to every program being compiled for a 64 bit architecture on a 64bit platform. You have obviously installed the 32 bit OS by accident or something, there's no other explanation I don't think. I've never heard of anyone getting the 32 bit kernel to work on a 64 bit system, neither some weird bug where it reports that it's 32 bit but actually it's 64 bit. You have a 32 bit system installed here :P

---

### Post by KyleRaynor on 2009-08-24
Duh, but how could it have happened. There's only 64bit on this disk. I've installed 64bit on here before, but it was windows and a long time ago. The only reason I've sworn it off for so long is that was too buggy, and finding drivers for it was a nightmare.

***
Do not rejoice in his defeat, you men,
For though the world stood up
And stopped the *******,
The bitch that bore him is in heat again.
        -- Bertolt Brecht

---

### Post by fela on 2009-08-24
> **KyleRaynor said:**
> Duh, but how could it have happened. There's only 64bit on this disk. I've installed 64bit on here before, but it was windows and a long time ago. The only reason I've sworn it off for so long is that was too buggy, and finding drivers for it was a nightmare.

Please don't say 'duh' to me, seeing as you're the one who asked the question about switching in the first place.

I know what you're talking about with 64 bit XP - I had that for a while and everything was unsupported. From my experience it's not like this in 64 bit ubuntu any more than 32 bit.

How could it have happened? Either you hacked the entire operating system or you installed the 32 bit version.

---

### Post by Slim Odds on 2009-08-24
> **fela said:**
> How could it have happened? Either you hacked the entire operating system or you installed the 32 bit version.

That's precisely what I was trying to point out.

There is no 32 bit kernel on the 64 bit disk.

---

### Post by KyleRaynor on 2009-08-24
First :: My apologies, I had just gotten home from work.
Second :: I did NOTHING abnormal. I inserted the amd64 disk. I rebooted. I chose the Install Ubuntu option. The only 'special' thing I did was to tell the installer where I wanted the boot manager. Before this fiasco, my only problem with Ubuntu is that it tries to take over the boot manager of my other hard drive. And correct me if I'm wrong, but that has nothing to do with the kernel and what architecture it's compiled for.

***
This is a scsi driver, scares the **** out of me, therefore I tap danced
and wrote a unix clone around it (C) by Linus
        -- Somewhere in the kernel tree

---

### Post by Slim Odds on 2009-08-24
> **KyleRaynor said:**
> Second :: I did NOTHING abnormal. I inserted the amd64 disk. I rebooted. I chose the Install Ubuntu option. The only 'special' thing I did was to tell the installer where I wanted the boot manager. ....

Ok, but there is NO WAY to install a 32 bit kernel from the 64 bit disk. So there is definitely something abnormal here.

---

### Post by fela on 2009-08-24
It's a 32 bit installation. We know that. The cause was down, almost certainly, to human error  (using the 32 bit disk by mistake?). It's nothing to be ashamed about, everyone's subject to human error, I'm not dissing you :)

EDIT: off topic:
@Slim Odds - I hope you have your 640GB of data backed up...I lost my 750GB disk to a head crash, and you have double the chances of losing everything with RAID 0...You probably know all this already though :)

---

### Post by Slim Odds on 2009-08-24
> **fela said:**
> EDIT: off topic:
@Slim Odds - I hope you have your 640GB of data backed up...I lost my 750GB disk to a head crash, and you have double the chances of losing everything with RAID 0...You probably know all this already though :)

That's what the 400GB and 750GB drives are for (backups).

---

### Post by fela on 2009-08-24
> **Slim Odds said:**
> That's what the 400GB and 750GB drives are for (backups).

One 750GB would be enough.

If you have 4 SATA ports you should get another 2 identical 320GB drives and put them all in RAID 1+0. Speed + redundancy. What's not to like? :)

---

