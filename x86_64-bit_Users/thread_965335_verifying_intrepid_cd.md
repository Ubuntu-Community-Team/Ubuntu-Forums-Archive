---
title: "verifying intrepid cd"
date: 2008-10-31
forum: x86 64-bit Users
---

### Post by elitenoobboy on 2008-10-31
First, why are there no md5 hashes for 8.10 up yet? [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
Second, when burning the cd, why does brasero not check the cd for burn errors after it finishes?
Third, when trying to boot from the cd, why do I get an error? It happens when either trying to launch the live cd or when selecting the check the cd for errors option. The error was : initramfs: ata4: srst failed [errno:-16]

---

### Post by drs305 on 2008-10-31
You can get the Intrepid hashes from the MD5SUMS file on this page:
[releases/intrepid/]("http://releases.ubuntu.com/releases/intrepid/")

But here they are:
```
ea6d44667ea3fd435954d6e1f0e89122 *ubuntu-8.10-alternate-amd64.iso
f9e0494e91abb2de4929ef6e957f7753 *ubuntu-8.10-alternate-i386.iso
f9cdb7e9ad85263dde17f8fc81a6305b *ubuntu-8.10-desktop-amd64.iso
24ea1163ea6c9f5dae77de8c49ee7c03 *ubuntu-8.10-desktop-i386.iso
e3028a105a083339be8e5af5afbe7444 *ubuntu-8.10-server-amd64.iso
a2ec9975a91e1228c8292ed9799dc302 *ubuntu-8.10-server-i386.iso
2796c696ab368415a30fddc8278e08b0 *wubi.exe

```

Note: The cd I used with the beta version had an option to check the integrity of the disk before installing...

---

### Post by elitenoobboy on 2008-10-31
The option to check the cd doesn't work either. I get the same error.

---

### Post by Sef on 2008-11-01
> The option to check the cd doesn't work either. I get the same error.
You either have a bad download or a bad burn, or a bad CD.   If it is a bad burn, then reburn at 4x or less.  Does the md5sum check out?

---

### Post by Yellow Pasque on 2008-11-01
BTW, the "bug" of not having intrepid md5 hashes in the documentation has been reported in Launchpad.
[https://bugs.launchpad.net/ubuntu-website/+bug/283667](https://bugs.launchpad.net/ubuntu-website/+bug/283667)

---

### Post by elitenoobboy on 2008-11-02
> **Sef said:**
> You either have a bad download or a bad burn, or a bad CD.   If it is a bad burn, then reburn at 4x or less.  Does the md5sum check out?

I just tried the cd on another computer, and it worked. It passed the integrity test. I also did an md5sum on the iso, and it matches the relevant hash listed above. I never had had this problem with any other previous ubuntu version or linux distro.

---

### Post by elitenoobboy on 2008-11-03
So am I to understand that nobody cares/knows what to do about this?

All of the solutions for this that I've tried, such as changing the bios settings haven't worked. Does no one do regression testing anymore?

---

### Post by Sef on 2008-11-04
>  	Quote:
 	 	 		 			 				 					Originally Posted by **Sef** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=6085055#post6085055") 				
 				*You either have a bad download or a bad burn, or a bad CD. If it is a bad burn, then reburn at 4x or less. Does the md5sum check out?*
 			 		 	 	 
I just tried the cd on another computer, and it worked. It passed the integrity test. I also did an md5sum on the iso, and it matches the relevant hash listed above. I never had had this problem with any other previous ubuntu version or linux distro.

What are your system specs?  It would seem that the issue is a hardware one, especially if you got the Live CD to run on another computer.

---

### Post by amgalitz on 2008-11-04
> **elitenoobboy said:**
> First, why are there no md5 hashes for 8.10 up yet? [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
I think this got answered.
> **elitenoobboy said:**
> Second, when burning the cd, why does brasero not check the cd for burn errors after it finishes?
ctrl-f will do it, or option on TOOLS menu. Not everyone wants it done automatically, this allows choice.
> **elitenoobboy said:**
> Third, when trying to boot from the cd, why do I get an error? It happens when either trying to launch the live cd or when selecting the check the cd for errors option. The error was : initramfs: ata4: srst failed [errno:-16]
Failure to run the livecd sounds like a bad CD, or hardware issue.
If you burned the CD on a burner other than the one you are installing from, they may not be able to read each others burns. No point in going further until you can check the cd from the installation menu. Try burning slower as suggested, burn the cd with the cdrom drive that you will install with, check for finger prints on the cd and clean as needed (that happened to me)
If this happens on the first boot after installation, you have my deepest sympathy. I have a similar error on the third machine I've put ubuntu on. see this: [http://ubuntuforums.org/showthread.php?t=968424](http://ubuntuforums.org/showthread.php?t=968424)
and this [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=968968](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=968968) 
You may want to subscribe to these threads and follow for a possible solution.

cheers

---

### Post by elitenoobboy on 2008-11-04
I have an asus m2n-sli deluxe motherboard, with a WD sata HD and a sata cd burner, which means that there are no alternate jumper settings to try for my hard drive, which was a solution in this thread: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706)

It looks like this is a problem with the newer kernel release, as I've seen this same error listed as coming up in other distributions as well.

---

### Post by elitenoobboy on 2008-11-08
bump

---

### Post by elitenoobboy on 2008-11-11
bump

---

### Post by elitenoobboy on 2008-11-20
bump

---

### Post by Hubi5171 on 2009-10-22
No more bumps ? - To be serious, sometimes it is necessary to put a jumper on a SATA drive. HDDs with 3Gbit xfer rate need a jumper when being used on an older controller able to do 1,5Gbit xfer rate only. (SATA II is NOT always 3 Gbit, details on Wikipedia). The other way around: Also as of today, DVD drives are usually 1,5Gbit only, the controller should handle this automatically. The hardware is suspect to me, maybe a combination/level of components/bios/firmware/its configuration. Would strip down the system to absolute minimum, if possible interchanging parts with a working system. Swapping parts preferable first put the "suspect's" part in the good system and test there. You might want to check my other entry in this forum also written today.  ciao  Hubi

---

