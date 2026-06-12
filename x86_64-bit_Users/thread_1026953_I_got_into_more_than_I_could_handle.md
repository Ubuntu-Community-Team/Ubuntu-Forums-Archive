---
title: "I got into more than I could handle"
date: 2008-12-31
forum: x86 64-bit Users
---

### Post by BruceBeefcake on 2008-12-31
Hey all,
I messed up real bad, I think. First off, I'm a complete noob at linux. Here's my problem:

I decided to install ubunto 8.04 onto a portable hard drive. My original intentions were to create a linux partition so that this linux distro would only be taking 40 GB of my portable hard drive space; and the rest of it goes to storage. My idea was to boot ubunto from both my PC and laptop. 

As time progressed I decided to see the installation through first using my whole portable drive and then shrink the linux space and use the free space for storage as I wanted to do earlier. I semi-successfully installed ubuntu onto my portable hard drive, using my laptop (vista x64). Now, my vista laptop will not boot vista unless my portable hard drive is connected and I select vista from a menu. 

I have no problems with the menu. My problem is with my laptops dependency on my portable hard drive. And to add to that, my PC(XP) won't boot from my usb drive (portable hard drive), which was one of my original goals. And now my PC can't see my portable hard drive when I connect it. I used PartitionMagic to see if I could shrink it that way, but it says Linux is using all the space on the drive. I didn't want to shrink it because I was worried whether or not I could still operate my laptop if something wrong happened).

What are some recommendations on how to fix these problems and work to my original goals? Thanks very much in advance!

---

### Post by bfinan0 on 2008-12-31
> **BruceBeefcake said:**
> Hey all,
I messed up real bad, I think. First off, I'm a complete noob at linux. Here's my problem:

I decided to install ubunto 8.04 onto a portable hard drive. My original intentions were to create a linux partition so that this linux distro would only be taking 40 GB of my portable hard drive space; and the rest of it goes to storage. My idea was to boot ubunto from both my PC and laptop. 

As time progressed I decided to see the installation through first using my whole portable drive and then shrink the linux space and use the free space for storage as I wanted to do earlier. I semi-successfully installed ubuntu onto my portable hard drive, using my laptop (vista x64). Now, my vista laptop will not boot vista unless my portable hard drive is connected and I select vista from a menu. 

I have no problems with the menu. My problem is with my laptops dependency on my portable hard drive. And to add to that, my PC(XP) won't boot from my usb drive (portable hard drive), which was one of my original goals. And now my PC can't see my portable hard drive when I connect it. I used PartitionMagic to see if I could shrink it that way, but it says Linux is using all the space on the drive. I didn't want to shrink it because I was worried whether or not I could still operate my laptop if something wrong happened).

What are some recommendations on how to fix these problems and work to my original goals? Thanks very much in advance!

You can't boot without the portable HD now because it has GRUB on it.  GRUB is a Linux boot manager that gives you the menu in order to choose between Ubuntu, Vista and any other OS that might be installed.  Since you installed Ubuntu onto that drive, that is also where GRUB went, and the first place your computer looks when it is trying to boot.

One solution: change your boot order so that the primary HD is above the portable one, by going into the BIOS (usually F1 or F9 just after turning computer on); the problem with this is that you would need to change the order back to use Ubuntu again.

Another solution: shrink your Vista partition.  Depending on how much free space you have on your hard disk, you may be able to shrink it (without losing data) in Control Panel -> Administrative Tools -> Create or format partitions.  If you can shrink it by at least 10GB, do that, and install Ubuntu again in the free space created by shrinking your Vista drive.  If you do this, you will be able to use Ubuntu without the portable HD, and will be able to keep the boot menu.

---

### Post by BruceBeefcake on 2008-12-31
I tried solution 1, but it still asked for GRUB. I put the "Notebook Hard Drive" to the top of the boot order and I get this error:
GRUB Loading stage1.5

GRUB Loading, please wait...
Error 21

As for solution 2: Great idea except that I wanted to use this linux on more than 1 computer, thus the reason for the portable drive in the first place. 
But by the looks of it now, it seems like I made my vista laptop dependent on the linux, since you're saying reinstall windows onto the internal hard drive. If I unistalled Linux, after doing solution 2, would it still be able to boot just vista?

---

### Post by Delever on 2009-01-01
Some space at the beginning of disk is called MBR (master boot record), it is used to load boot loader from another disk.

Originally, MBR loaded Windows "boot loader" for you, and it was loaded from notebook drive.

When you installed Ubuntu into removable drive, MBR of your notebook drive was rewritten to load GRUB from removable drive.

There are two solutions:
You can restore original MBR, by using Vista DVD and following this procedure: [http://support.microsoft.com/kb/919529](http://support.microsoft.com/kb/919529)
Note, if you do this, your removable drive will no longer load. You can fix this by changing MBR of removable drive from Live CD.

Or, you can install GRUB into your notebook. The problem is, GRUB partition should not be NTFS. It may be possible to shrink notebook drive (from live CD) and make room for additional disk (~100-150MB), and rewrite boot loader to point to that disk, so it would be able to load GRUB even when removable drive is disconnected. This GRUB should only launch one OS - Vista. 

Tell us the route you want to follow.

---

### Post by bfinan0 on 2009-01-01
> **BruceBeefcake said:**
> since you're saying reinstall windows onto the internal hard drive. 

If I unistalled Linux, after doing solution 2, would it still be able to boot just vista?

First, did you mean reinstall Linux onto the internal hard drive?  That's what I thought I said...

Second, I'm not quite sure what happens when you completely uninstall Ubuntu, I've never done that yet.

---

### Post by DeMus on 2009-01-01
> **BruceBeefcake said:**
> Hey all,
I messed up real bad, I think. First off, I'm a complete noob at linux. Here's my problem:

I decided to install ubunto 8.04 onto a portable hard drive. My original intentions were to create a linux partition so that this linux distro would only be taking 40 GB of my portable hard drive space; and the rest of it goes to storage. My idea was to boot ubunto from both my PC and laptop. 

As time progressed I decided to see the installation through first using my whole portable drive and then shrink the linux space and use the free space for storage as I wanted to do earlier. I semi-successfully installed ubuntu onto my portable hard drive, using my laptop (vista x64). Now, my vista laptop will not boot vista unless my portable hard drive is connected and I select vista from a menu. 

I have no problems with the menu. My problem is with my laptops dependency on my portable hard drive. And to add to that, my PC(XP) won't boot from my usb drive (portable hard drive), which was one of my original goals. And now my PC can't see my portable hard drive when I connect it. I used PartitionMagic to see if I could shrink it that way, but it says Linux is using all the space on the drive. I didn't want to shrink it because I was worried whether or not I could still operate my laptop if something wrong happened).

What are some recommendations on how to fix these problems and work to my original goals? Thanks very much in advance!



The way I see it is to re-install Ubuntu on your portable harddrive and to make sure GRUB (the bootloader) is stored on the MBR of the fixed drive of your laptop. That way when you boot the laptop it sees the GRUB menu where you can choose Ubuntu or Windows.
In one of the 7 screens you see when you install Ubuntu there is a button with (I think) Advanced on it. Press it and choose the option to store Grub on the fixed disk (HDA or SDA probably).

Then you still have the problem with the other PC. On the MBR of that boot drive should also be GRUB so you also can choose here.
I have no other solution than to connect the portable drive to that computer and to install Ubuntu on the portable disk again, also with the option to place GRUB on the fixed disk.
I'm sure there is a way to copy GRUB but I don't know that.

Good luck and Happy New Year.

DeMus

---

### Post by BruceBeefcake on 2009-01-01
> **bfinan0 said:**
> First, did you mean reinstall Linux onto the internal hard drive?  That's what I thought I said...

Second, I'm not quite sure what happens when you completely uninstall Ubuntu, I've never done that yet.

Yea I meant linux. There were both going through my mind at the same time.

My laptop isn't with me at the moment so I'm unable to try out some solutions. But I'm totally excited about it. Thanks for the quick responses guys.
I'll let you know if the solutions work.
Thanks again and have a happy new year!

---

### Post by Sef on 2009-01-01
>  I'm sure there is a way to copy GRUB but I don't know that.

There is [Super GRUB Disk]("http://supergrubdisk.org").  It will install grub.

---

### Post by BruceBeefcake on 2009-01-01
> In one of the 7 screens you see when you install Ubuntu there is a button with (I think) Advanced on it. Press it and choose the option to store Grub on the fixed disk (HDA or SDA probably).

It's on the 7th page right before the install. I tried to install GRUB onto the internal hard drive (sda), but vista was still unable to boot without my external hard drive. 

If I used Super GRUB Disk, would i be able to manually install it on my laptop's hard drive without having any conflict with the GRUB on my portable hard drive (I think I know the answer but I just want to make sure)

---

### Post by euclidsbrother on 2009-01-02
I'm kinda new to ubuntu, but I had done a dual boot between XP and Vista and used VistaBootPro as the boot manager.  It should also work here and it's free.. (VistaBootPro.org)

Install that from your vista OS and it will rewrite the MBR and you should be able to tell it to boot either Vista or your ubuntu from the external drive.

-EB

---

### Post by -kg- on 2009-01-02
> **euclidsbrother said:**
> I'm kinda new to ubuntu, but I had done a dual boot between XP and Vista and used VistaBootPro as the boot manager.  It should also work here and it's free.. (VistaBootPro.org)

Install that from your vista OS and it will rewrite the MBR and you should be able to tell it to boot either Vista or your ubuntu from the external drive.

-EB

Sorry, but [VistaBootPro]("http://www.vistabootpro.org/") is not free.  It costs $8.95 for Home/Personal (the site says *that's* 50% off) and $24.99 for Business use.

Not much, but not free.

---

### Post by BruceBeefcake on 2009-01-02
I tried installing Super GRUB but the menu doesn't even come up. It goes straight into ubunto. How can I fix this? Or better yet, how can I restore my computer without reinstalling vista?

EDIT: Nevermind. I was able to get Vista to boot by itself again. Thanks for the help with ubuntu, though. Classes start soon and I can't give more time to deal with it. Thanks again.

---

### Post by euclidsbrother on 2009-01-03
ah well.. it used to be free a couple of years ago..  too bad..

---

