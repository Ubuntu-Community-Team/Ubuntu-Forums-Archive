---
title: "SATA hard drives"
date: 2008-11-18
forum: x86 64-bit Users
---

### Post by sambarusty on 2008-11-18
After installation of Ubuntu 8.10, I noticed it doesn't recognize my SATA hard drive, actually I noticed it during the install, but I grabbed an extra ATA hard drive and moved on. I thought it was something with the installer.  I found however that a dmesg shows all sorts of complaints about he the SATA.  Can anyone translate?

[65113.342737] ata4: hard resetting link
[65113.670690] ata4: SATA link down (SStatus 100 SControl 300)
[65113.670727] ata4: hard resetting link
[65113.998696] ata4: SATA link down (SStatus 100 SControl 300)
[65113.998740] ata4: hard resetting link
[65114.326681] ata4: SATA link down (SStatus 100 SControl 300)
[65114.326710] ata4: hard resetting link
[65114.654699] ata4: SATA link down (SStatus 100 SControl 300)
[65114.654729] ata4: EH pending after 5 tries, giving up
[65114.654736] ata4: EH complete
[65114.669421] ata4: hard resetting link

this goes on and on over and over again.  Thanks Craig

PS, the drive works in Mandriva 2007, but not Mandriva 2009 and not ubuntu 8.10.  So I am wondering if it is something that changed in the later kernels.

---

### Post by sambarusty on 2008-11-18
has anyone seen these errors, other than removing the drive, which is just spare space now, not sure what do do.  Are SATA drives not supported?

---

### Post by John Jason Jordan on 2008-11-18
> **sambarusty said:**
> has anyone seen these errors, other than removing the drive, which is just spare space now, not sure what do do.  Are SATA drives not supported?

I know little of the insides of operating systems, but I am certain that SATA drives are fully supported. Just about all new drives these days are SATA drives. I have one in my laptop and two in my desktop and Linux works fine on all of them.

I would start by double checking the connections. A lot of times I have blamed software when the problem was really hardware related. I know that SATA drives are particularly susceptible to bad connections at the cable ends. If you determine that the hardware is fine, then you can go on to other possibilities.

---

### Post by Arup on 2008-11-18
My 1TB SATA are fully recognized by Ubuntu, no issues at all.

---

### Post by Yellow Pasque on 2008-11-18
What kernel version are you using?
```
uname -a
```

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269652)

---

### Post by sambarusty on 2008-11-18
uname -a shows
Linux burgec-desktop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux

I have checked the connections a couple of times. I also flipped to windows and reformatted the drive to make it a spare, so I can access it from one side of the dual boot but not the other.  

What I had noticed is that even the installer was not seeing it, but if I put in the Mandriva 2007 install, it did, which made sense since that is where I had it installed.  But neither Ubuntu or Mandriva 2009 recognize the drive.  I had to add a third drive to do the install.  I don't have a spare SATA to do a swap test, only spare ATA.

---

### Post by dabl on 2008-11-18
Take a look at the SATA bus in your BIOS.  Is there a "mode" option?  On my rig, I have to set it to "AHCI" mode for the SATA drives to work.

---

### Post by sambarusty on 2008-11-18
> **dabl said:**
> Take a look at the SATA bus in your BIOS.  Is there a "mode" option?  On my rig, I have to set it to "AHCI" mode for the SATA drives to work.
I gave the bios a look, I unfortunately don't have anything related to SATA that is relevent.  I coupld of detection options such as large vs auto, things of this nature, but all of the options are auto.  Thanks for the post though.

---

### Post by dcstar on 2008-11-19
> **sambarusty said:**
> I gave the bios a look, I unfortunately don't have anything related to SATA that is relevent.  I coupld of detection options such as large vs auto, things of this nature, but all of the options are auto.  Thanks for the post though.

The point is that "auto" is not working, so change things to see if it makes a difference.

---

### Post by xen-uno on 2008-11-19
Providing that you can find and set the SATA mode in the BIOS, you should pick RAID (over AHCI & IDE).

[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface)

---

### Post by sambarusty on 2008-11-19
So I changed the disk from SATA 4 input to the SATA 1 input.  I changed the sata setting from auto and changed it to the other option SATA 1.  I don't have the errors any more, but I can't see the disk still, not even in /dev, I don't have a new option.  I don't seem to have a SATA mode setting. Like I said though before I can see the drive from older kernels it seems, like 2.6.17 was the last one I had installed on the disk before I tried installing a later version.  So I am hesitent to think it is a bios setting anyway, otherwise wouldn't all the versions have problems.  I went from having it installed on the disk drive to neither of two new distro's recognizing it.  But if I go back to say Mandriva 10.1 I have downloaded, it sees the disk.  But a later version of Mandriva or Ubuntu doesn't recognize it either.  So something is different with the Driver/kernel, I don't think it is in my Bios.  I guess it is going to be a second windows drive for now :(.   Thanks all for your posts.

---

### Post by fjgaude on 2008-11-19
> **xen-uno said:**
> Providing that you can find and set the SATA mode in the BIOS, you should pick RAID (over AHCI & IDE).

[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface)

I use IDE in the BIOS settings for my six SATA drives on a Gigabyte motherboard.

---

### Post by gshockxc on 2008-11-25
> **xen-uno said:**
> Providing that you can find and set the SATA mode in the BIOS, you should pick RAID (over AHCI & IDE).

I'm having the same problem as the author of this post.  I went through all three settings last night: non-RAID, RAID, and AHCI.  Only non-RAID seemed to get me anywhere, but still couldn't complete the install.  Troubleshooting continues.

---

### Post by sambarusty on 2008-12-04
Really with 512 views I have to assume that people are having SATA trouble.  No one has thoughts at all about this issue? (sorry for this but Bump)

---

### Post by sambarusty on 2008-12-04
Not completly true I am supported in windows but not ubuntu or mandriva.  If  it was  supported, it would work, the question really is whether or not a patch has been found.

---

### Post by sambarusty on 2008-12-04
sorry missed a quote there, meant to quote all sata drives are supported.

---

### Post by sambarusty on 2008-12-04
By the way back to my original question, Mandriva 10.1 works with this drive.  Still today.  So something has chaged.  If I install my old disks, they work.  The new ones, not so much so, Ubuntu, Mandriva, doesn't matter, which is why I think it is more of a seagate linux thing than an ubuntu thing. Thanks

---

### Post by dabl on 2008-12-04
The problem is more likely in the domain of your SATA chip on your motherboard, and your BIOS features, than in Linux/Ubuntu. I'd be googling on that chip model and "linux" -- apparently the standard libata driver isn't doing the job on it.

---

