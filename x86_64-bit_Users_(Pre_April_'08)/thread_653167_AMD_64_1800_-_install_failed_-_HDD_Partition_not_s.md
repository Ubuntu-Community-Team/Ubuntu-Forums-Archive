---
title: "AMD 64 1800 - install failed - HDD Partition not showing"
date: 2007-12-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by hdredor on 2007-12-29
First off, I'm pretty new to Linux o/s, so some I might be a little slow on the uptake of some of the terminology.  I'm not completely computer illiterate, but most of my experience is with windows based O/S.  I've been thinking about trying out a linux o/s for some time, but generally I'm pretty busy and it's easy to procrastinate when the windows system that I've got is functional for what I generally need it for.  

I am looking into building a new system so I decided to try out linux again to see  if perhaps I could use it as a primary o/s on my new build.  

so....

I downloaded Ubuntu and burned an ISO cd and proceeded to boot up the disk.  The first thing I did was verify the integrity of the CD and it was fine.  So I loaded Ubuntu and toyed around with it awhile and was pretty impressed - except for the fact that it was pretty slow running off the cd.  

Let me add,  before running the Ubuntu disk I did actually have an unallocated partition available on my 80 gig Sata Drive.  That partition was approximately 30 gig.  My windows partition was about the same size and I had one other partition on the drive that made up the remainder of the available space. 


So I decided to go ahead an install Ubuntu thinking that I should be able to simply install it to the available partition that wasn't formatted to NTFS.  Well, I got to the partitioning portion of the install and attempted to install Ubuntu manually.  For some reason that wouldn't allow an install because I didn't have a swap file or something along those lines.  So I decided to use the Guided Install and when I got the part where it warns you that once you begin you can't go back I decided to once again try to see if I could do it manually - to no avail.  Well I'd read that Ubuntu won't generally affect your windows installation and that it would use the available hard space that was unallocated.  Perhaps I just thought I'd read that, but at any rate I decided to go ahead with the Guided Install.  

That's where I got the error message telling me that it was basically too 'dicey' to proceed and recommended that I attempt an install with a different distro.  

So I closed it down and attempted to reboot into my windows o/s.  Right about the time windows normally comes up I got an error message saying the 'autocheck' file was missing and then it would simply reboot, and reboot and reboot.  

I attempted to recover by using the repair console through the installation disk, including rewriting the mbr.  That wasn't affective at all.  Did a few other things and eventually used a program called PTEDIT to reset the partition to a bootable partition.  Seems the Ubuntu program marked the windows partition as something other than a bootable drive.  


Okay, now that's all fixed and my windows system is fine.  It boots just fine and nothing appears to be missing.  

But now my system won't recognize anything but the windows partition - 30 gig (approx) and a small 1.4 gig extended partition that only shows on the Disk Management app.  The rest of the HDD is not available.  On the bottom portion of the DM app (windows) it shows that the 30 gig partition is actually 73.1 GB - which would account for most of the missing HDD, but still only 30 gig is accessible. 

I'm not really interested in reformatting and doing a fresh install of windows just to make my HDD fully functional again, so I'm a little leary of attempting to install a linux application again.  Sure, it probably wouldn't hurt, but I don't really want to spend the time to do that right at the moment.

One other thing - it appears that the Bios was changed from the SATA setting to a RAID setting.


Maybe this is a stupid question, and once I figure it out I'll wondering why I didn't think of it earlier, 

But it's not every day I play around with operating systems and such. 


Is there anyway to recover the lost partition one my hard drive without risking wiping out my windows installation????

Is there perhaps a better Linux application that would work with my hardware enviroment?

Any suggestions or information is most appreciated.

Thanks!

---

### Post by Kilz on 2007-12-29
There is a way, if you want to use[ partimage]("http://www.sysresccd.org/Main_Page"), or have norton ghost. They can make backups of the partition. Then wipe the disk and replace the operating system off of that partition backup.
Just a work of advice for the future, always backup important data before partitioning a drive. You at least have the os back, others have made mistakes and reformatted by accident.

---

### Post by hdredor on 2007-12-29
Thanks for the suggestion Kilz.  I don't have either of those programs, but if there's as free version somewhere I might be inclined to give it a whirl.  

So if can manage to successfully install Linux would I be able to use it to get back my lost HDD space?

I've got an external drive that I use to back up my important stuff, but I'm just not really into having to format my drive to reinstall windows.  Maybe, if I had some more time to fool with it.  The ubuntu o/s looked pretty good.  Now if I can just get one to work!

---

