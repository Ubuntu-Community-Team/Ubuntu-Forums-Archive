---
title: "Cannot install Ubuntu"
date: 2008-03-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by ketzerei on 2008-03-22
```
"The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment."
```

I have Ubuntu 64-bit 7.10, and I have a AMD 64 X2 6400+ processor. I can't for the life of me figure out what is going wrong. Input appreciated, Danke.

---

### Post by Sam Lars on 2008-03-22
That error is pretty self-explanatory.
I haven't had terribly good luck with CDs.  First, check your md5 sum to make sure it matches.
```
md5sum ubuntu-7.10-desktop-amd64.iso
```
Run that on the ISO you downloaded, it should probably say this.
```
61c87943a92bc7bf519da4e2555d6e86 *ubuntu-7.10-desktop-amd64.iso
```
Try installing again.  And again.  And maybe again.  If that fails, burn a new CD at the lowest speed possible.
You could also try the 32-bit version.

---

### Post by ketzerei on 2008-03-23
Okay, now I'm a little ticked off. This kind of thing has NEVER happened before, and I have never had any trouble installing Ubuntu. Ever. I've burned 3 different cd's since then, and have tried the 64-bit and 32-bit 4 times each now, and I STILL get the same error. Ubuntu either cannot run on my machine (which is completely ridiculous seeing as I just uninstalled kubuntu, and I had been running feisty earlier in the year) or something is seriously messed up. My cd drive makes weird noises once in awhile, but I really doubt that thats my problem here. If anyone has ANY suggestions at all, I'm willing to do anything at this point.

---

### Post by ketzerei on 2008-03-24
No one has any suggestions? None at all? This whole thing is strange really. My hard drive and disk drive are perfectly fine. I installed an older version (the initial release of gutsy exactly) of kubuntu, and thats where I'm typing this from right now. I have no problems booting, writing to the hard disk, mounting my ipod, noting. So, I'm almost positive its an Ubuntu specific error. The alternate cd got all the way to "Select and Install Software" and went red, spit out some error, and went to an installer step menu. PLEASE someone give me ideas here, I'm sick of Kubuntu and miss gnome. And no, I don't want to install gnome-desktop over kde.

---

### Post by jhnphm on 2008-03-24
What's wrong w/ just entering aptitude, select all packages for removal, and select ubuntu-desktop for installation?

---

### Post by Drate on 2008-03-24
Have you tried a fresh download of the ISO?  Did you check the MD5?  Even if the MD5 does check out I'd still try a fresh download of the ISO file, and then for safety burn it slow.  Also, the CD has a disk integrity check built in it, make sure the integrity check passes.

Have you tried the CD on another computer or another hard drive (if you have one available to try it on)?

And heck, if all else fails, I know it's not ideal but uninstalling kubuntu-desktop and installing ubuntu-desktop should get the job done.

What specifically was the error message in the alternate install?

---

### Post by GTengineer on 2008-03-24
> **Drate said:**
> Have you tried a fresh download of the ISO?  Did you check the MD5?  Even if the MD5 does check out I'd still try a fresh download of the ISO file, and then for safety burn it slow.  

Second this. I had a similar problem the very first time I installed Ubuntu where my download was corrupted and I essentially burned junk into a CD. Try downloading the ISO again.

---

### Post by ketzerei on 2008-03-25
Well, I don't know. It makes no sense, I only had HP dvds, so I burned the first copy of the64-bit  iso to that using nero (the md5 checked out, and I burned at the slowest speed possible which is 16x) and then I dowloaded the standard 32-bit version and burned that one to a different dvd. Well, then the next day since nothing worked I went out and bought some new CDs (Phillips, so theyre not junk) and downloaded yet again, another iso. This time it was the alternate. I burned that one using nero as well becuase (stupidly) I had dumped Kubuntu off the hard drive the day before, so I had only my window$ boot. But the alternate cd, as you were wondering, stops at "Select and install software" and the screen goes red, and I get a message saying something like it could not install some packages. The base system is there, the kernel, GRUB, all the base componets. But no xserver, nothing. So, there, thats my dilema here. I'm currently back to my old Kubuntu boot, I re-installed it, but i want to go back to Ubuntu because its way more stable and KDE is annoying.

---

### Post by Sam Lars on 2008-03-25
I would suggest adding Gnome and then removing KDE, that should work fine.

---

### Post by cssanyi on 2008-03-26
Somewhere I've read a solution for the problem. It worked perfectly for me. :lolflag:

See the properties of the install icon. Somewhere you will find the command, what it executes. Copy it into the terminal and insert sudo before it. (Than press enter :D)

That's all. I've read it doesn't work for everybody. Give a try.

Good luck!

---

