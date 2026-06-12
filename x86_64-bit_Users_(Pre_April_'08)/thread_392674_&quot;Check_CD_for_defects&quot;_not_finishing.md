---
title: "&quot;Check CD for defects&quot; not finishing"
date: 2007-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by DR4545 on 2007-03-24
Hi all,

When I tell Ubuntu (64bit) to "Check CD for defects" after booting from CD it begins running and seems to be OK, but it comes across some strange errors then halts.  I'll post approximately what it says.

[150.030720] udevd-event[1513]: run_program: '/sbin/modprobe' abnormal exit

then, it comes to: Trying to enable the frame buffer ...
Detecting hardware, please wait ... Detecting hardware to find CD-ROM drives (9%)
Loading module 'via82cxxx' for 'IDE chipset support' ...

But, halts.


Anyway, the last two discs would come to messages like these:

ACPI Exception (acpi-processor-0693): AE_NOT FOUND, Processor device is not present [20060707] <--- Three of those
<something that seems like an error>
Getting cpu index for acpiid 0x3
[236.825729] ACPI: Thermal Zone [THRM] (40C)
Starting system log daemon: syslogd,klogd.

Then, it halts


I have downloaded twice (two different mirrors), used two different burners, and two different burning programs (Nero and a freeware)  So, three CDs that couldn't error check.  And, CDs from that spindle never had problems with those burners before.

The file I downloaded was ubuntu-6.10-server-amd64.iso
I'm running a Celeron D 356, with onboard video (it's a 64 bit proc)
Motherboard is ECS 945G-M3, 512MB of RAM
HDD is PATA Seagate

I haven't run an MD5 checker, because I'm not sure what to look for as a correct signature.

I'm leery to install when I'm getting errors like this.  I'm completely new to Linux and Ubuntu, so I won't take any advice as patronizing.

Thanks for your help

---

### Post by cmost on 2007-03-24
Hmmm, not to sound trite, but perhaps your CD has a defect!  Perhaps try downloading again.  :-(

---

### Post by DR4545 on 2007-03-25
> **DR4545 said:**
> I have downloaded twice (two different mirrors), used two different burners, and two different burning programs (Nero and a freeware)  So, three CDs that couldn't error check.  And, CDs from that spindle never had problems with those burners before.

That would be three bad discs, where no others in the spindle were ... highly doubtful.

I may try buying a new 50-pack, I'll need more sooner or later anyway.

I have a hunch there is some sort of compatibility issue, but according to the documentation I read it works with 64-bit Intels.

---

### Post by Kilz on 2007-03-25
> **DR4545 said:**
> That would be three bad discs, where no others in the spindle were ... highly doubtful.

I may try buying a new 50-pack, I'll need more sooner or later anyway.

I have a hunch there is some sort of compatibility issue, but according to the documentation I read it works with 64-bit Intels.

Yes the amd64 version works with most modern 64bit intel chips. Are you sure your chip is 64bit?

---

### Post by DR4545 on 2007-03-26
OK, time for an update!

I ran an MD5 checker, both downloads were fine (same MD5 as listed on the hashes).  It also checked the CD's iso, and said it matched.  So, why would the check for defects feature be unable to finish?  Should I install anyway?

Celeron D 356, with onboard video _(it's a 64 bit proc)_ <-- **I double-checked Intel's site, and Windows reports it as the correct speed for the product specs.**
Motherboard is ECS 945G-M3, 512MB of RAM
HDD is PATA Seagate

Also, I tried opening the files from Windows using the CD-ROM on that computer, and it reads the CD fine.

Any idea why it wouldn't finish checking the disc?

I'm thinking about trying 6.06 instead of 6.10, or just using the 32-bit version.  What's the difference with LTS, just an older release?

EDIT:  Looks like someone was having issues with the Intel 945 chipset (same as mine) using Gnome ... could that be related?

[http://www.ubuntuforums.org/showthread.php?t=384344](http://www.ubuntuforums.org/showthread.php?t=384344)

Oh, and one final question ... where can I download Fiesty?  Perhaps it has solved the 945 chipset issue?

---

### Post by Kilz on 2007-03-26
> **DR4545 said:**
> I'm thinking about trying 6.06 instead of 6.10, or just using the 32-bit version.  What's the difference with LTS, just an older release?

LTS = Long Term Support
Dapper (6.06)was the first long term support release. LTS releases receive more work to make them more polished. They also receive 3 years of updates from the time they release, as opposed to 18 months like Edgy(6.10) got. 
What that means to you, is that if you install Edgy, you will have to replace it in 2008 because its end of life will happen. If you install Dapper, you will not have to upgrade untill 2009, or 2011 if its a server install. Because it will be getting updates.
Edgy was produced in only 4 months , some people feel it was hurried. The version numbers show this, the first numbers are the year, or 2006, the second 2 numbers are the month. To me it shows. I dont run Edgy, Dapper is much more stable.
As for 32bit, you can try it if you want, but you wont get all the performance you would get out of the 64bit version. Also its possible that you may have problems running the 32bit version on 64bit hardware.
Let me also warn you about using the server install disk. The server install disk dose not install a GUI or desktop. If you need one it can be installed, but its just as easy to use a desktop install cd. Secondly on the subject of disks, you might want to try the alternate install cd. IMHO it has a better chance of success.
Edit : I would really think twice about Feisty, it has just enterd Beta testing. As long as you dont mind bugs and things not working, give it a try. But dont expect it to be perfect.

Edit 2: The post you link to , the person has installed Ubuntu and cant adjust the screen resolution , its a graphics driver problem. You cant even boot the install disk.

---

### Post by DR4545 on 2007-03-27
Joyous rapture!

Thanks for the version advice Kilz.

I installed 6.06 LTS server fine.  (The 6.10 CDs were indeed OK, they ran the defect checker fine on another machine.)

I installed the gnome desktop fine with the following command, and everything seems warm and fuzzy ... downloading updates at the moment.

```
sudo apt-get install ubuntu-desktop
```

---

