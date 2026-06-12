---
title: "Win XP Pro problemstranslates into Ubuntu 9.04 install"
date: 2009-05-20
forum: x86 64-bit Users
---

### Post by neil0mac on 2009-05-20
OK.  No results from a search.

Specs.

AMd 64 3000 CHIP, ASUS (A8V) M/B, 1 Gb Memory, 10GB Hdd (possibly with remnants of WIn XP Pro O/S), DVD CDROM.

I decided to try Ubuntu to get rid of a WIN XP problem where regularly the PC opens dozens/scores of files, changes PC and program settings, and frequently freezes the mouse and keyboard so that the only option left to 'hit the power off button'.

I was expecting that _Ubuntu would _create/delete/overwrite the only partition on the HDD  and clean things  up.

It didn't.

So replacing the HDD with another and checking the 'CHECK foR Disk errors' (negative)
I just let it run from the CD, [B]but the problem is still there.

Does Ubuntu have a 'format disk' utility that can be used?[/B]

Thanks.

---

### Post by Fir3chi3f on 2009-05-21
The 'check for disk errors' option on the live CD checks the CD itself to make sure that it burned correctly.

If you install Ubuntu to the hard drive you will be given some options, 'use entire disk' will wipe out your windows install.

if your looking to just blank the drive of all information than you can go to System->Administration->Partition Editor and just delete the ntfs partition. This is just a quick wipe, to do a full wipe you would need a live CD like [Darik's Boot and Nuke]("http://www.dban.org/")

Hope this helps

---

### Post by neil0mac on 2009-05-21
> **Fir3chi3f said:**
> The 'check for disk errors' option on the live CD checks the CD itself to make sure that it burned correctly.

):PI'm using a CDROM from a download supplier.

[If you install Ubuntu to the hard drive you will be given some options, 'use entire disk' will wipe out your windows install.[/quote]

):PI did 'use entire disk' but the original problem is still there. (See original post.)

[if your looking to just blank the drive of all information than you can go to System->Administration->Partition Editor and just delete the ntfs partition. This is just a quick wipe, to do a full wipe you would need a live CD like [Darik's Boot and Nuke]("http://www.dban.org/")

Hope this helps[/quote]

):P  The spate of windows openings is there even when I run Ubuntu from the cd WITHOUT INSTALLING IT.

Neil.

---

### Post by logos34 on 2009-05-21
> The spate of windows openings is there even when I run Ubuntu from the cd WITHOUT INSTALLING IT.

sure you don't have a failing power supply, or problems with mouse and keyboard?

---

### Post by neil0mac on 2009-05-21
> **logos34 said:**
> sure you don't have a failing power supply, or problems with mouse and keyboard?

Absolutely!  I have one mouse and one keyboard running to two PCs through a data switch.

Added:   I can bypass the data switch, and the problems still appear.  And I can also use a second mouse and second keyboard with or without the switch - with no change.

---

### Post by neopsalmist on 2009-05-21
Try memtest86

---

### Post by neopsalmist on 2009-05-21
You may be experiencing bad RAM, or possibly as logos34 suggested, some form of bad hardware or power.

---

### Post by pbpersson on 2009-05-21
I had a machine here running Ubuntu through a KVM switch and it kept hanging up - the mouse and keyboard were totally dead, could not even move the mouse pointer.  I thought it was KDE because this was a Kubuntu machine.  I did a fresh install of Ubuntu Hardy Heron - same problem.

Then I decided the heck with Ubuntu and I installed Visa.....only to discover the same problem there.

In my case, re-flashing the BIOS fixed my problem.

---

### Post by neil0mac on 2009-05-22
> **neopsalmist said:**
> Try memtest86

This doesn't tell me a thing.  Does it work off the CD?

Will it run on WINXP O/S?  IF so, how?

I can't get started because I don't know anything.

---

### Post by neil0mac on 2009-05-22
> **pbpersson said:**
> 

Then I decided the heck with Ubuntu and I installed Visa.....only to discover the same problem there.

In my case, re-flashing the BIOS fixed my problem.

Do you mean 'Vista'?

OK.  I'll try the BiOS trick as that seems that that is about the level of the problem (machine code almost).

Trouble is, I think it is on both PCs!        Highly improbable?

---

### Post by neil0mac on 2009-05-22
> **pbpersson said:**
> 

Then I decided the heck with Ubuntu and I installed Visa.....only to discover the same problem there.

In my case, re-flashing the BIOS fixed my problem.

Do you mean 'Vista'?

OK.  I'll try the BiOS trick as that seems that that is about the level of the problem (machine code almost).

Trouble is, I think it is one both PCs!        Highly improbable?

---

### Post by logos34 on 2009-05-22
memtest86 is on the ubuntu live cd (first screen)

> **neil0mac said:**
> 
Trouble is, I think it is one both PCs! Highly improbable?

same issue on two different machines? dunno what could be the cause

---

### Post by Kareeser on 2009-05-22
> **neopsalmist said:**
> Try memtest86

Not to be rude, but that in god's name does this accomplish?

If memtest finds anything wrong, then I'll take it back, but this piece of advice is completely random and doesn't seem to be connected to the problem at hand.

---

### Post by JDRagsdale on 2009-06-16
I know this is an older thread, but I didn't see a resolution posted so thought I'd add on. 
 
Are you "running" the CD after you boot windows, or are you booting with the cd?  You need to boot from the cd, not run the cd from inside windows.
 
FWIW, my wifes computer had a similar problem with windows opening all over the place etc. In her case it was simply a key stuck down on the keyboard. Probably not your problem, but I try to check the simple things first. :P
 
> **neil0mac said:**
> ):PI'm using a CDROM from a download supplier.
):P The spate of windows openings is there even when I run Ubuntu from the cd WITHOUT INSTALLING IT.
 
Neil.

---

### Post by neil0mac on 2009-06-16
> **JDRagsdale said:**
> I know this is an older thread, but I didn't see a resolution posted so thought I'd add on. 
 
Are you "running" the CD after you boot windows, or are you booting with the cd?  You need to boot from the cd, not run the cd from inside windows.

I'm trying to run it from the CD on a newly formatted C: Drive.    

Couldn't be more basic.    (Thanks.  At least you replied!.)

---

### Post by pixel :-) on 2009-06-16
in the bios you must set it to boot from the CD

---

### Post by GothRelic on 2009-06-16
What you should have done was use the manual option when it prompts you about your partitions, then select a small space, say about 1gb for swap, and format, and use the ext3 filing system, along with selecting the format option, and selecting to use "/" as your root. Also, when it prompts you to assimilate files and settings from windows, select none. I don't know if you fixed the problem yet. But if you need any assistance with the installation, or partitioning, my e-mail is [email]GothRelic@hotmail.com[/email]

---

### Post by GothRelic on 2009-06-16
Don't do a mem test.. gah.. if you think there is a problem with your harddisk, from the recovery console (running the windows setup disc) type in fixmbr.. this will tell you if there is infact a problem with the actual Filesystem and not your harddisk itself.

---

### Post by neil0mac on 2009-06-17
> **GothRelic said:**
> Don't do a mem test.. gah.. if you think there is a problem with your harddisk, from the recovery console (running the windows setup disc) type in fixmbr.. this will tell you if there is infact a problem with the actual Filesystem and not your harddisk itself.

Another guesser.

No where did I suggest that I had a HDD problem.

---

