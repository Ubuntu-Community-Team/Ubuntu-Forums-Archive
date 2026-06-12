---
title: "[SOLVED] ubuntu fail to install on hard drive"
date: 2007-12-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by brettfromokla on 2007-12-31
help I am trying to install ubuntu on a new pc. clean install hard drive was new. I have the ver 7.10 64 bit install cd from canoical. computer is amd 4400+, msi mainboard, seagate 320 gig 16mb buffer and sata 300. 2 gig pny memory. boots up off live cd and goes into ubunto, seems as if everything works, but when I try to use the install button it goes through the install and gets to the partition portion of the install and hangs at 5%. I left it on all night and it stayed at 5%. bios shows raid and harddrive present and I can seen it in ubuntu but for some reason it freezes in the same place everytime. I think I must be missing something but I dont know what. need help!:confused:

---

### Post by .nedberg on 2007-12-31
I had a similar problem once. Try the alternate installer. You can get it at ubuntu.com. It does not have the fancy graphics, but it is just as easy!

---

### Post by brettfromokla on 2007-12-31
thanks, I'll try that tonight when I get home from work.

---

### Post by jamb on 2007-12-31
I agree with 'nedberg, use the alternate installer, since it gives you a good feeling what is happening during the install.

I had a similar installation experience (xubuntu 7.10) on a newly bought ASUS mb (M2N-E SLI) with three IDE-HD. In my case the partitioner bar graph stopped at ~30% and then completed to fast, and later during the install either dumped me back to the install boot up screen our finish the GRUB install and then failed to reboot. I was puzzled.   

I carefully looked at my homebuilt setup, changed IDE-HD from Cable Select (CS) to what I always used in the past, to master/slave. Look at all the BIOS settings, what to enable/disable. I disabled the parallel port to avoid potential IRQ conflicts, and I also invested in a new DVD reader. I'm not sure why my finally worked - but was happy when it did. 

Is your CD/DVD reader on SATA or is it an IDE device?

My conclusion is, check you hardware. Test an old windows install (if you have) and see what happens - just to verify your build, If you have an IDE-drive around, try that.

Just some ideas, to help.

---

### Post by brettfromokla on 2008-01-02
Ok I downladed the text based installer. I booted up and tried to install the program and it still hangs up on the formatting the partitions portion of the install. I tried another hard drive a 60gig ultra ata I had and it went through the formatting but it hung up on me during the install process at 85%. I still dont have a working install as of yet. the dvdrw drive is a serial connection. This hard drive was working in another machine running windows xp. I'm not sure what I should try now. Help!

---

### Post by jamb on 2008-01-02
If you have the possibility, replace your DVD-RW (Sata) with one CD/DVD R(W) with an IDE interface and set it up in the master/slave mode (keep the IDE HD in this first test configuration). 
If this works, then as follow up you can add back the Sata HD and try again.
In this way you narrow down the cause for your problem. 
Sometimes motherboards have dual Sata controllers, this can also be used to figure out if your problems are indeed located the Sata controller communication. 
Have you Goggled the MSI motherboard P/N or your Sata CD/DVD-RW manufacturer for hints? Is your BIOS up to date?

---

### Post by brettfromokla on 2008-01-03
Ok, I replaced the hard drive with a 60 gig ultra ata I had in another computer and it formatted for me. However it locked up during the install at 25% which showed installing gnome desktop components. I am going to try burning another install cd tonight at 2x speed. I hope it works for me this time. HAs anyone else had problems with freezing during the install and the computer locking up? I tried installing v.6.04 but it shows a kernal panic-not synching and quits working. any help is appreciated.

---

### Post by brettfromokla on 2008-01-04
Ok I burned a new cd at 1x with a new iso I downloaded. The new cd hangs up during the install at the same place and locks the computer up. I tried installing a different cd drive from another of my computers and it still hangs at the same place. It shows installing gnome desktop and the progress bar is at 25% when it stops. checkdisk shows disk is ok. I am starting to get frustrated with it. the hard disk formatsnow, and it runs the live cd perfectly. It just wont install without locking the computer up. I feel it is some type of driver compatability issue, but aI dont know enough yet to figure it out. need help.

---

### Post by brettfromokla on 2008-01-07
Ok I finally got the computer running. seems one of the new pny 1 gig ram sticks was bad and causing the freezing. I ran the memory test but it never picked it up. I fiannly had a ram error show up at the boot screen. removed the defective ram stick and everything went normally. YAY!!!:) thanks for the help I learned a lot.

---

### Post by jamb on 2008-01-09
I'm glad that you solved your problem.
Linux is a learnig experience.:)

---

