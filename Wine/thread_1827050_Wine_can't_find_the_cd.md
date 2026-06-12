---
title: "Wine can't find the cd"
date: 2011-08-17
forum: Wine
---

### Post by tomkat3 on 2011-08-17
Lately I've been trying out lots of old windows games (on cd's that I bought legally) I have lying around on wine just for the heck of it. Most are five or six years old and many don't even run properly on Windows 7! Its been hit or miss. 

What's worked most reliably is to install the game on my old windows XP desktop, then do this:

copy the relevant folder in the program files (for example: C:/Program files/Warcraft III) of my windows computer to a USB stick.
paste it in a Linux directory (anywhere)
configure my wine D: drive to point at the D: drive, ex:  /media/Warcraft III/
find a promising .exe file in the folder copied from Windows (like warcraft3.exe) and execute it with wine.

And it works like a charm for most games! However, in ubuntu I think I've only installed (while running Linux, put cd into drive, open installer, install) and run one program in Linux successfully. Usually what happens is this:

The cd automatically mounts, and I configure wine's D: drive to be in /media/Warcraft III/
I'll run the installer.exe with wine
wait for the game to install, it seems to work fine
Next time I try to start the game, it says "Please insert the Warcraft III CD"

 Even programs (like Warcraft III) that get Platinum and Gold ratings at WineHQ do this. When I used PlayOnLinux I think Warcraft III worked, but I later tried to use PlayOnLinux with Diablo II (which I played later using the first method), and it couldn't find the cd's for the installation! Its seems ridiculous that wine can't find the cd that's sitting in my disk drive. 

The only problem I've ever had running games in Linux is with finding the cd like this. I'd at least like to see more interesting error messages than "Can't find the cd you put into the drive :P". What's the problem?


_____
I'm running Xubuntu 11.04 along with Windows 7 in hard drive partitions on a Dell d630 laptop.

---

### Post by stephenhau on 2011-08-17
It looks like you've already configured Wine to access your CD drive, so my guess is that your games use copy-protection methods to access the CD.

How about dual-booting as a last resort, so that you at least can play them on a native Windows installation?

---

### Post by stephenhau on 2011-08-17
And you're not the only one with this problem… 
[http://ubuntuforums.org/showthread.php?t=1824440](http://ubuntuforums.org/showthread.php?t=1824440)

---

### Post by Tekno.Statik on 2011-08-25
Funny, I was just thinking the same thing myself.

We may have to go Dual-boot... but as you can see I also tried half way by using the Virtualbox or whatever...

Dual boot is still last resort, but does anyone have any suggestions of any OLD games that work which were also pirated? I mean, I use Piratebay for everything, but Wine has failed the same way for me in three ways.

I'm not hating WINE, I just want to see it work if possible. if not then I guess we'll have to wait 'till it does.

---

### Post by Tekno.Statik on 2011-09-05
Came back for seconds, I am dissapoint. -_-

---

### Post by Yeeha on 2011-09-05
I dont know if it helps since you already configured D: but autodetect cdrom does not work until you have fstab entry about cd/dvd rom. Dunno why ubuntu does not make fstab entry about cdrom anymore...

---

### Post by jacksaff on 2011-09-06
Probably you're not mounting the cd before you start the program. Wine then doesn't know it's there. Try opening the cd in a file browser first and then run your gaem.

---

### Post by Tekno.Statik on 2011-09-11
> **Yeeha said:**
> I dont know if it helps since you already configured D: but autodetect cdrom does not work until you have fstab entry about cd/dvd rom. Dunno why ubuntu does not make fstab entry about cdrom anymore...

Not sure what you mean by fstab... but I'll research that.

> **jacksaff said:**
> Probably you're not mounting the cd before you start the program. Wine then doesn't know it's there. Try opening the cd in a file browser first and then run your gaem.

I just did another double check, I matched the mounted directory to Wine config for Drives, I even went ahead and CHMOD that directory to allow permission to everything and not just Root.

The CD installed again without a problem, but when I ran the game it still says the same error about inserting the correct CD.

This game only uses 1 CD, so is there maybe a previous version of Wine that perhaps works? Or maybe the mounting program does not work well with Wine and it mounts the files differently... I am lost.

---

### Post by uKEN on 2011-09-13
I'm having diablo II install problems

well wen I try to install d2 I keep geting this error saying to insert the install cd..
but the install cd is all ready in..
if I klick ok the same error keeps poping up..should I try to put it on an iso img ?

I hope some one finds a way around this..

well I'll try the cut/copy/past the file and have wine point to it..should work but i have many games i wuld like to see them install eayser than that..

EDIT: Aww ..no room to make a dull boot :(

---

