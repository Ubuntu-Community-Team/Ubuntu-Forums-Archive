---
title: "Copying large amounts of data issue"
date: 2009-01-22
forum: x86 64-bit Users
---

### Post by kneewax on 2009-01-22
Hi folks,

I've just started using the 64bit version of Ubuntu on my new desktop having been running solely on Ubuntu (32bit) for just over a year on my now retired laptop.  

I am having problems copying my backed up data onto the new PC, every copy I try in the GUI fails on files with 'I/O error' after the first couple of Gig.   I had this problem in the 32-bit version of Gusty, but not since.  Is it me?  Or does anyone else have this problem.  Is there a workaround?

Cheers

Kneewax

---

### Post by paulisdead on 2009-01-22
Do you see anything in dmesg when that happens?  That's certainly a good place to start.

---

### Post by kneewax on 2009-01-23
OK, Thanks for the reply here is what dmesg gave me:

```

[14599.661943] Buffer I/O error on device sdb5, logical block 19497267
[14599.661959] Buffer I/O error on device sdb5, logical block 19497268
[14599.661965] Buffer I/O error on device sdb5, logical block 19497269
[14599.661971] Buffer I/O error on device sdb5, logical block 19497270
[14599.661977] Buffer I/O error on device sdb5, logical block 19497271
[14599.661983] Buffer I/O error on device sdb5, logical block 19497272
[14599.661989] Buffer I/O error on device sdb5, logical block 19497273
[14599.661995] Buffer I/O error on device sdb5, logical block 19497274
[14599.662001] Buffer I/O error on device sdb5, logical block 19497275
[14599.662006] Buffer I/O error on device sdb5, logical block 19497276

```

Does this suggest a corrupt disk?   The device I am copying from is an Ext USB HDD, an IDE 80GB disk.

Cheers

Ali

---

### Post by Therion on 2009-01-23
Wrong thread.

---

### Post by cubeist on 2009-01-23
This is a known bug that has been around seemingly forever.  It is supposed to have been fixed in the latest updates for intrepid, but I am still affected using USB2 pen drives.

Here is the launchpad page for the bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746")

Have you run the update manager recently? You might be on of the lucky ones with a working fix.

The workaround I use is to use USB1 with the command:
```
sudo modprobe -r ehci_hcd
```
YMMV!

---

### Post by kneewax on 2009-01-24
> **cubeist said:**
> .

The workaround I use is to use USB1 with the command:
```
sudo modprobe -r ehci_hcd
```
YMMV!

Thanks for this.  I tried this code and it still fails.....  Does that suggest a physical disk issue?

---

### Post by dcstar on 2009-01-24
> **kneewax said:**
> Thanks for this.  I tried this code and it still fails.....  Does that suggest a physical disk issue?

Go to the bug report link, it says there are more commands to run than just that one.

---

### Post by kneewax on 2009-01-24
I have done some further testing on the external USB in question and have found that there appears to a physical problem with the drive. 

Does anyone know if there any GUI tools that I can use to scan the disk, and attempt recovery of the bad areas?

Ta.

---

### Post by cubeist on 2009-01-24
if you can mount the drive, you should be able to use the hdparm tools.  I don't have much experience with this tool, so you should first run
```
man hdparm
```
in a terminal to familiarize yourself with the commands.

And remember to double check you are running commands on the external drive, not the internal drive, before you execute!!!

---

### Post by cariboo on 2009-01-24
Gparted has the ability to check the drive fitness and repair some errors. AS in most cases with Linux command line tools are much more powerful than gui tools.

I would also suggest running the diagnostic software from the hard drives manufacturer, these will give you an indication of whether the drive is good or bad.

Jim

---

### Post by dcstar on 2009-01-25
> **kneewax said:**
> I have done some further testing on the external USB in question and have found that there appears to a physical problem with the drive. 

Does anyone know if there any GUI tools that I can use to scan the disk, and attempt recovery of the bad areas?

Ta.

Install the smartmontools package and you can interrogate the drive for problems.

---

