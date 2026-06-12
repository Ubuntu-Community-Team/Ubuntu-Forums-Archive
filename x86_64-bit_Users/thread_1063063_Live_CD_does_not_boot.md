---
title: "Live CD does not boot"
date: 2009-02-07
forum: x86 64-bit Users
---

### Post by gsub on 2009-02-07
Hi all.

I recently got a Compaq Presario CQ60Z with an AMD Turion X2 processor.

I downloaded a copy of the 64-bit live CD and tried to boot with it. Upon choosing "Try Ubuntu without making changes to your PC", the progress bar reaches about 20%, the caps lock light starts blinking, and nothing else happens.

The checksums on the live CD check out. I downloaded the live CD again, just to be sure, and I get the same problem.

I don't know if this is a common problem, and was wondering if anyone knows of any solutions, or have any ideas on some things I could try out.

Cheers.

---

### Post by 2hot6ft2 on 2009-02-07
Have you tried hitting the F6 key after selecting your language and adding "noacpi" to the end without the""'s and hitting Enter?

---

### Post by gsub on 2009-02-07
Just tried it:

There are two dashes at the end of the line when I press F6. Tried the following:

--noacpi
--<space>noacpi
pci=noacpi

Same problem as before.

---

### Post by 2hot6ft2 on 2009-02-07
If you're installing anyway you could try the OEM Install option. My laptop is the HP G60-125NR, it's a lot like the CQ60 and I installed the Ubuntu Ultimate Edition 2.0 32 bit (basically it's Intrepid Ibex with more apps and a newer kernel) with no problem at all.

I went with the 32 bit for the lightscribe drive and it's related applications.

---

### Post by gsub on 2009-02-07
Well, I tried doing the OEM installation (with and without the noacpi).

Same thing - the progress bar goes upto 20%, and the system hangs, no activity at all.

---

### Post by gsub on 2009-02-07
Update:

I got the alternate install, and installed Ubuntu.

Now, when I try to boot, the same thing happens.

If I try booting into recovery mode, It starts to boot normally, and then a bunch of error messages come up, and the system hangs.

Help, anyone?

---

### Post by ssulliv8 on 2009-03-01
I have a similar problem. running an hp/compaq presario cq50, athlon 64x2.

When I boot the live cd it hangs on the splash screen, at about 20% like you said.

I downloaded the 8.10-alternate-amd64 cd and was able to install kubuntu successfully; but it still hangs when trying to boot the kernel from the disk.

If you boot without the "splash" option you might see where its hanging up. For me, it hangs (system panic) on the initialization of the ath_pci driver for the integrated wireless chip.

Would like to try to get it booted so I can maybe remove the ath_pci kernel module like this guy did:
[http://www.linuxquestions.org/questions/ubuntu-63/upgrade-to-8.10-ath59k-not-working-cannot-reinstall-madwifi-681043/#post3460988](http://www.linuxquestions.org/questions/ubuntu-63/upgrade-to-8.10-ath59k-not-working-cannot-reinstall-madwifi-681043/#post3460988)

Otherwise, its back to i386. :(

---

### Post by manisa4583 on 2009-03-03
i have an sis671/968 chipset, phoenizbios v:1.04c and core 2 duo T8100 i have the same problem. live cd does not starts. can any one help?

---

