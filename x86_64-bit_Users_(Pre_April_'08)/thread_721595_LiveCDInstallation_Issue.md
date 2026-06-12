---
title: "LiveCD/Installation Issue"
date: 2008-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lateralis on 2008-03-11
Hello all.  Not sure where to put this, as it could go in a couple of locations... 

I started using (X)Ubuntu a few months back.  Installed Xubuntu on my work computer, then at home here.  Worked fine on my old AMD Athlon processor.  Really loved it in fact.  I then upgraded my PC to an Intel E6750 processor, nVidia nForce 680i LT motherboard with the same hard drives I used previously.  I managed to install a fresh copy of XUbuntu using this setup quite happily.  Then, my motherboard went pop (less than 2 weeks after it arriving and the computer being put together... grrrrr...) at which time a friend accidentaly purchased 2 Intel E8400's.  I've purchased one off of him and replaced my motherboard with an Asus P5KC (current BIOS version is 0904).  Now, using the same CD's I have used on previous occassions, and using new CD's I've burned at home and at work, I can't get Ubuntu (nor Xbuntu nor my Mandriva disc) to load up properly on this new setup.

With Xubuntu or Ubuntu CDs in the drive, it brings up the menu asking if I want to install, install in safe graphics mode, intsall using driver CD etc...  With the 64-bit edition of both editions all I get is a black screen after selecting either of the first two options.  The HDD light flashes in bursts periodically a couple of times, the CD drive powers down, the monitor detects no input and goes into sleep mode and then nothing.  With the 32-bit editions of both versions I've done the same thing again, selecting both options in sequence and this time it does pull up the (X)Ubuntu logo with the scrolling bar.  However, after a short time it pulls up a text based command line - something about ASH?  I can't seem to start Gnome and don't know how to install from the command line.

I also tried selecting the "Install with driver CD" and "OEM install" options, but without success.  I'm currently downloading the "Alternate" Ubuntu CD as a last ditch attempt.  

Just wondered if anyone might be able to help me?  It's a proper problem which I don't mind telling you has got me stumped.  Any advice or fixes will be greatly appreciated.

---

### Post by Lateralis on 2008-03-11
Now I'm really confused.  

I'm using the same CD ROM drive I have used the last two times I've installed XUbuntu, but now the installer is having issues accessing it.  Loads up the Kernel fine.  Everything looks good, but during the text-only installation (from the alternate CD) it says something about not being able to load up the correct module for the CD/DVD drive.  I tried manually selecting several different modules but no cigar.  I don't understand why various Linux live CDs worked just a few weeks ago, but then I change the motherboard and suddenly they don't like my choice of optical drive.  What the Dickens is going on?  

I do have another IDE optical drive around the house so I'll try that one.  I maybe able to boot from USB and I do happen to have a USB optical drive (due to a dodgy laptop optical drive) so may try that as well.  In the meantime, does anyone have any clue as to what's happening and can think of any solutions?  

Cheers muchly in advance.

---

### Post by felker2 on 2008-03-11
Have you run the n-th (last) option "check memory" from the live-CD for a few hours?

---

### Post by Lateralis on 2008-03-11
Nee!  

My RAM works fine in Windows (32-bit XP and 64-bit Vista).  Same memory I used in my previous installation of Xubuntu which worked perfectly fine.  

I'll perhaps do that check memory though if you think it might help.  Are you expecting anything in particular?

---

### Post by felker2 on 2008-03-11
> **Lateralis said:**
> Nee!  

I'll perhaps do that check memory though if you think it might help.  Are you expecting anything in particular?

It will help as it will make clear whether your RAM and the RAM settings are 100% OK.

---

### Post by Lateralis on 2008-03-11
Well, as I said, Windows XP, Vista and the BIOS haven't detected any issues just yet - touch wood.  I did start a memory check whilst I was in the shower though.  The RAM itself seemed OK, but the memory checker did say my processor was a Pentium III with an unknown L2 cache.  I'm not 100% about the architecture of the new Wolfdale 45nm processors, but it's unlikely to be labeled as a PIII? :/  But that's probably a BIOS thing anyway, as the Wolfdale cores are brand new.  

Anyway, onto the problem - I'm currently posting this from Ubuntu.  I hooked up my external CD drive and booted first through the USB.  So far, so good.  Currently installing the thing as I type.  Which means the problem appears to be with some internal gubbings.  As the optical drive worked previously, are there any known Linux issues with the P35 chipset, especially on the (south?) bridge (ICH9 chip?) that connects the optical drive to the rest of the machine?  The drive works fine in Windows XP and Vista and is detected in the BIOS, not to mention I used the exact same drive just the other week before my nVidia mobo died to install Ubuntu.  So I'm disinclined to think the drive itself has gone ga-ga.  

Any ideas?

---

### Post by Lateralis on 2008-03-12
Mixed news this morning.  

Ubuntu installed last night and I was able to load it up quite happily this morning.  However, it is still not detecting my internal CD/DVD drive.  Everything else seems to be working perfectly fine.  

It is strange that it was recognised in previous installations, but now it isn't.  It's an IDE (PATA, no SATA) Samsung CD/DVD-writer combo drive.  Had it for a few years.  It is installed in an Asus P5KC P35 motherboard.  

Any ideas?

---

