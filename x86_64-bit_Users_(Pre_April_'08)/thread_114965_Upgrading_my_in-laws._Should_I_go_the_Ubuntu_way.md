---
title: "Upgrading my in-laws. Should I go the Ubuntu way ?"
date: 2006-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Suger on 2006-01-09
My in-laws have a B&W G4 400 with 640 Mo RAM. They were running MacOS 8.5, upgraded to 9 after buying a new printer and completely broke their system.

We have decided that it's time for them to go DSL and to get a real OS, but here is the question : should I have them going to OS X (10.2, as I don't think they have enough processor to run 10.3 or 10.4) or switch them to Ubuntu ?

Whatever I do, they will have a (steep) learning curve (they are over 60). I want to be able to do remote administration and remote maintenance of their system.

In both cases, I can set up sshd and vnc, maybe fink fluxbox to have a little gui when doing remote administration if I go the OS X way.

If everything works OK with the live CD, I think I'd rather go the Ubuntu way, but should I ?

The real question is this : does anyone know if Gnome runs smoothly on such a config, with lots of RAM but a rather old CPU ? Because I can't really think about installing XFCE to older linux beginners coming from OS 9 (no icons, having to right click to get the root menu, etc).

And the other question is : at what point is OpenOffice for Linux PowerPC ? If I switch them, I need a good word processor (don't feel like teaching them LaTeX) and spreadsheet program, but when I last checked, OpenOffice for LinuxPPC was lagging behind, but that was months ago (right now, my own PPCs are running OpenBSD, so there is no OpenOffice at all).

TIA for reading this long monologue and for your help

---

### Post by Ptero-4 on 2006-01-09
I think that gnome is going to go good on that mac specially since it's a G4. And as for Openoffice, I think it's been updated.

---

### Post by sulobanks on 2006-01-10
OS X would be a smaller shock to the system for a mac person, I would think.  As far as installing Linux on someone else's machine, my experience has been that you better be ready to support that installation quite regularly.  It typically takes a non-technical person a long time to learn the Linux desktop.  And the first time they can't play that media file they receive or open that publisher document, they'll be after you to make it work.

But everyone is different. My brother couldn't handle Linux and had no patience to learn.  Thus, he puts up with windows crashes and viruses all the time.  My mom, on the other hand, switched to Linux and is happy with Firefox, Thunderbird, and OpenOffice.  But at first, she required a lot of attention and training.  There were many throwing hands in the air episodes.

I certainly don't mean to discourage an Ubuntu installation. I love the system. But doing it for someone else is a rather large time commitment and it's something to consider carefully.  Of particular frustration to casual web users will be the lack of a usable flash player on ppc arch.

---

### Post by tmeier on 2006-01-10
I have installed on a similar system with less ram and it works well.  However, your in-laws generation is usually a generation of read the book to learn and then try it out while I have the book in front of me.  We are more of a generation to let's try it and see what happens.  I don't want to discourage an ubuntu install either, however considering their skills and comfort level, why not just reinstall OS 9.22.  It should do all the things they need web, media, email and documents.  Otherwise IMHO OS 10.2 maybe best because it is still an Apple OS and lots of things will be similar.  

If your close, to do lots of troubleshooting and training, then it is whatever you feel most comfortable with.

---

### Post by swhit on 2006-01-10
I have an old imac 400 MHz G3 with 320 MB RAM. It currently has OS X 10.4 on it. Runs great, better than 10.2; 10.1 and 10.2 actually seemed more "buggy" than the more current releases of OS X. FYI, 10.3 ran great on the imac G3 too.

The old machine gets quite a bit of use still too. I let my 3 yr old daughter play on it so she doesn't mess up my newer imac G5.

I haven't tried Ubuntu on an imac, although I have installed it on a powerbook. Worked fine other than I couldn't get the airport card running (this was a year ago, might be fixed in breezy).

---

### Post by shawn12345 on 2006-01-10
I like abiword & gnumeric its  tons faster than open office and has enough features for probably 90+% of the users out there i see. Unless of course they need to exchange spreadsheets with people.

---

### Post by trash on 2006-01-10
G4, 466mhz, 512ram - dual boot osx 10.3.9 and Breezy here(gnome is not an issue).
Set them up with mac on linux and you'll have pretty happy in-laws :)

---

### Post by jerrykenny on 2006-01-10
My parent have ubuntu on their system, (dual boot actually),  dont think the learning curve will be a problem,  make sure sound and video is properly configured before you hand over.

Also Create their own user accounts, setup their e-mail on Thunderbird, and put their most likely icons onto the toolbar. . . . 

For the icing on the cake, install   celestia (not the gnome version), kstars, and stellarium, and create shortcuts for them, these are absolutely charming apps.

I wouldnt go for KDE, mind, I reckon its a very "busy" desktop, and it takes me ages to find anything amongst all those add-ons.

---

### Post by jdp on 2006-01-11
With the amount of RAM and the G4 in the B&W it will run 10.3 or 10.4 just fine.  They are actually faster than 10.2 in almost all cases as long as you have 256+MB RAM.  If you are stuck with 128MB, then stay with 10.2 or go back to 9.

---

### Post by christhemonkey on 2006-01-11
yeah, im running ubuntu fine on a 166mhz pentium.

---

### Post by Suger on 2006-01-12
OK. I can't leave them on 9.2 because we want them to go broadband, the computer is not by the phone (they have to pull a line throughout the whole house each time they want to connect, right now), and I don't think the G4 is airport enabled. On the other hand, I've got a spare ral wifi dongle, for which there are drivers both for OS X and Linux. The other problem is that I don't leave very far, but not nearby either, and I already do have to troubleshoot their computer. Thus, with Ubuntu, I'll be able to remotely ssh -Y in their box, with OS X I'll have to set up a VNC over ssh, but in both cases, I'll be able to remotely administrate the box and troubleshoot it.

I have discs for 10.2 and 10.3, but no 10.4, so 10.4 is not a possibility (I don't want to install a pirate version to my in laws).

I'm spending the whole week-end at their place to install whatever I'll be installing, so don't worry, it will be a clean install.

Thanks for your insights, all of you.

@jerrykenny : thanks for the celestial suggestions. Those apps will delight my father in law. And don't worry, I just hate the KDE interface, so I won't install it to them (but I love XFCE, but I won't install them that either, except maybe for my own use).

I'll keep you posted on my choices and results.

---

