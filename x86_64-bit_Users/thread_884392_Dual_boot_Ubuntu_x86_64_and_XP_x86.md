---
title: "Dual boot Ubuntu x86_64 and XP x86"
date: 2008-08-08
forum: x86 64-bit Users
---

### Post by rfdeshon on 2008-08-08
Hey all, I have a quandry for those of you who feel so inclined to ponder this with me. I used to dual boot XP x86 and Ubuntu x86_64. When in Ubuntu, I had my Windows disk mounted as /windows in case I needed to get any data from it, though I rarely, if ever, used it from Ubuntu. A lot of the time, when I would boot into XP after running Ubuntu, there would be problems requiring me to run a chkdsk or, sometimes, create a new user profile (very annoying). 

What I was wondering was, do any of you think there is any reason that mounting an NTFS partition from a 32-bit XP install in a 64-bit Ubuntu install would cause problems like these? I really fail to see why it would cause these issues but since wiping out Ubuntu x86_64 and installing regular old x86 edition, I've not had any more problems with it. 

Has anyone else seen issues like this?

---

### Post by sandysandy on 2008-08-09
i have used XP with 64 bit and 32 bit ubuntu.

i have not faced any problem.

regards

---

### Post by dcstar on 2008-08-09
> **rfdeshon said:**
> 
.......
Has anyone else seen issues like this?

Yes, my Win XP goes into chkdisk on boot after 8.04 64 bit has mounted the partition (but I don't seem to have any file loss).

There is probably some minor bug that doesn't unmount cleanly in the 64 bit version - take the partition out of your /etc/fstab file and only mount it as required from the Places menu.

I don't notice this problem much as I hardly ever boot into XP directly - I have a VMware server XP VM that I start up if I need that O/S.

---

### Post by rfdeshon on 2008-08-09
> **dcstar said:**
> Yes, my Win XP goes into chkdisk on boot after 8.04 64 bit has mounted the partition (but I don't seem to have any file loss).

There is probably some minor bug that doesn't unmount cleanly in the 64 bit version - take the partition out of your /etc/fstab file and only mount it as required from the Places menu.

Yeah, I never had any real  file loss per say, but the user registry came up as being corrupted a couple times. That honestly probably has nothing to do with the other problem. Either way, I'm not going to be using my NTFS partition in 64 bit Ubuntu anymore, I'm actually in the process of building a Gentoo install.... just to see if I can do it. Last time I tried, back in college, I gave up after 2 days. I've already gotten farther... Gnome is compiling and everything seems to be running well at this point.

Not that I'm abandoning Ubuntu, that will be running on my laptop for the foreseeable future as I need something solid and stable on my laptop. My desktop is just my playpen if you will.

---

