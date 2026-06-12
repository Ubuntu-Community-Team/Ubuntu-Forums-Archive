---
title: "How can I boot open suse from CD?"
date: 2008-07-18
forum: openSUSE and SUSE Linux Enterprise
---

### Post by paddy1 on 2008-07-18
Fresh harddrive, but will not boot. Is there a boot disk for this and other distros?:confused:

---

### Post by SunnyRabbiera on 2008-07-18
It should have a live CD, most popular linux distros come with one.

---

### Post by paddy1 on 2008-07-18
This was downloaded form the Linux site as image file, and written to disk

---

### Post by paddy1 on 2008-07-18
What? No answers?

---

### Post by zmjjmz on 2008-07-18
Have you tried the BIOS settings and set it to boot from the CD?

---

### Post by paddy1 on 2008-07-18
Yes, but says missing operating system

---

### Post by zmjjmz on 2008-07-18
> **paddy1 said:**
> Yes, but says missing operating system

Wait hold on, I know this one.
Put the CD in, and check the contents.
If it's just an .iso, you did it wrong.

---

### Post by paddy1 on 2008-07-18
Nope. I looked at cd on my laptop, and open suse tried to boot in windows XP

---

### Post by L815 on 2008-07-18
Go to [http://software.opensuse.org/](http://software.opensuse.org/)
Make sure you check "Live CD" in step 2

Since you have XP, get a free burn program called ImgBurn.
After install, you should be able to right click the downloaded file from Suse's website, and click "Burn with ImgBurn".

Try to boot that copy.

If that doesn't work, then you will have to check your BIOS as someone mentioned above.

In your BIOS, look for BOOT ORDER, or something similar. 

Make sure to set CD Drive or DVD drive as the first Boot option.

Then try booting the cd again.

[B][COLOR="Red"]
Okay, this option should be your last option if everything else fails.[/COLOR][/B]

-Connect your fresh new harddrive to your laptop via a USB adapter, or to another Desktop PC.

-Boot your Suse Live Cd on that machine which you hooked the HDD to.

-Once you get to the step to pick which HDD to partition, Select the one which is your NEW HDD.

-On the next step, make 2 partitions:
1 for Swap (same size as ram, so 1GB ram would be 1000MB)
1 for the root partition (/ as mount point), to the rest of the free space.

[B]-One of the steps is where to install the BOOT LOADER. 
-On this step, make sure to set the installer to install GRUB on the partition of your new HDD.[/B]
[B]
-After completing the rest of the steps, it will require a reboot. Do this reboot on the same machine you are installing from as there are proceeding steps to finish.[/B]

-Once this is done, you can shutdown and put the HDD back in the original PC, and it should boot your fresh installed SuSe.

---

### Post by K.Mandla on 2008-07-20
Moved to OpenSuse subforum.

---

