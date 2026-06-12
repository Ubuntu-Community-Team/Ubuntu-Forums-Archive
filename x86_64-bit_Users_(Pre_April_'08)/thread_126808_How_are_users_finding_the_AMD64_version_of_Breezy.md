---
title: "How are users finding the AMD64 version of Breezy?"
date: 2006-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by gingermark on 2006-02-07
Hi,

I am about to upgrade my computer. I have bought an AMD Athlon 64 3200+ and was planning to just install the x86 version of Kubuntu as I understand there aren't as many packages available for the AMD64 version (especially regarding proprietery codecs etc).

But I was wondering how you folks are finding it? Is there some wonderful separate AMD64 repository somewhere with all these goodies?

Are there any advantages that make it worth running?

Any thoughts (or links to other threads / sites) would be most appreciated, especially from anyone who has run both the x86 and AMD64 versions.

Thanks a lot,
gingermark.

---

### Post by sithia on 2006-02-07
I was a little leary of running the amd64 at first for the very same reason but decided to give it a go. The only things I found I needed that were only 32-bit were proprietary browser plugins (i.e. macromedia flash). I installed a 32-bit chroot and it worked perfectly. This config has the advantage that anything you run in 64-bit mode takes advantage of 64-bit addressing. The downside is that the 32-bit chroot takes a bit of room. But if you, like me, have plenty of spare disk space the chroot was barely a nudge to my free disk space.

---

### Post by gingermark on 2006-02-07
Thanks for your input. I think after reading [this thread](http://ubuntuforums.org/showthread.php?t=119403) I will stay in the 32-bit world for now, and re-evaluate it with each Kubuntu release.

---

### Post by oxpack on 2006-02-27
Not being a professional system administrator, I wish I'd kept it simple and stayed with 32bit. Linux is a challenge and 64bit makes it worse. Not ready for prime time.

---

### Post by enlightenment on 2006-03-01
Hi Gingermark!
Sorry for joining late!
regarding your query this is what i feel!:
1) when almost a year ago i decided to upgrade my computer from a celrone(is this correct spelling) 533 Mhz , i had many options. People would all around suggest  Pentium 4 and nothing else. Bah! 
with amd bringing in new technology all the time, i got interested in a 64 bit pc. so i purchased an Amd Athlon 2800+ with an Nvidia card. 
operating system was the nest issue, Microsoft had not yet released stable windows 64 bit (and who trusts microsoft anyways). I got hold of fedora core 4 x86_64. also as my pc is used ocassionaly by my family, it had to be a dual boot with windows. excellent backward compatibility enabled that. 
2) DIFFERENCE: i use Gimp the most and also open office. just for example, the gimp is a lot more faster (u know when u apply filters) in x86_64 linux than windows 32. Afterall the simple reason to buy a 64 bit processor is speed.
3) had no compatibility issues (leave winmodems printer/scanners) 
4) flash player etc can be installed 32 bit. ie remove 64bit firefox and install a 32 bit one. Jre is there u can install it manually. and flash, just open up a site that uses flash and firefox will ask for it, and they install that automaticaly. 
5) i am myself new to ububtu (but am using rh and fedora since rh 6.0) duno how is the 64 bit as my package of cds have bad image. But i would suggest please dont de grade ur hardware. respect it!!!:mrgreen:  if ubuntu doesnt work that food in x86_64 use fedora/mandariva/suse for time being. fedora and mandriva are just excellent in 64 bit operation. 
6) this is a simple view not biased towards ubuntu!!!
Regards
enlightenment

---

### Post by ytene on 2006-03-27
Hi GingerMark,

late response to your enquiry. I have mixed results to report. Briefly, hardware I'm working with:-

Tyan Thunder K8W, 2 x Opteron 250s, 4Gb RAM
XFX nVidia 7800 GS AGP, Creative Audigy 2 ZS
Adaptec PCI64 + Freecom DDS5 Tape
Pioneer Slot DVD-ROM and NEC DVD-RW

The base GNOME installation [I always install ubuntu and then add KDE...] and patching is smooth. Adding SMP kernel works fine. Adding KDE broke my machine [like kernel hangs on boot]. Did some work with ubuntu support [Fabio] to try and resolve the problem, looked like a binutils issue. Been out of things for appr 1 month so not aware of latest. 

Cannot get the audigy sound card to work - just produces white noise. There were open bugs on bugzilla for both [need to check latest status]. Interestingly, I installed the 386 version on the above hardware and both of the above problems seem solved... 

Tried to install the native nVidia drivers. Under 64-bit nothing b0rks, and although /var/spool/messages indicates the drivers are running, you do not get visible indicators. Under 32-bit you get the nVidia splash screen and things "seem" better. Suspect this is because nVidia only shipping the 32-bit binaries at the moment...

I have one major outstanding issue, which is that I have yet to figure out how to edit my config to let me write to shared FAT32 partitions... [duh]

General impressions are that ubuntu still somewhat "flaky" on the AMD64 platform, but that could be said of other distros too. In all honesty, you need a spare "play" disk or partition and you need to check out your favourite apps before committing to 64-bit. The environment is too inconsistent for any of us to give you a definitive response either way.

Hope this helps.

---

### Post by lupine_nickt on 2006-03-27
nVidia **are** shipping 64-bit versions of their drivers:- [http://www.nvidia.com/object/linux_display_amd64_1.0-8178.html](http://www.nvidia.com/object/linux_display_amd64_1.0-8178.html)

Make sure that you uninstall all the nvidia packages from the repositories beforehand, though... otherwise whenever you restart, it seems to enjoy loading the 7667 kernel module, and 8178 userspace... which breaks your X.

Or, if you don't need the latest drivers, you can just use the amd64 packages already in the repos - they're version 7667 (as I already said). 

Obviously, you also need to make sure that your /etc/xorg.con is using the "nvidia", rather than "nv", driver.

I've had it all working perfectly, with both methods, on breezy and dapper amd64 (although not smp, I'll admit - I'm not that rich ;) ). 

As for writing to fat32 partitions... in your /etc/fstab file, just need to add 'rw' into options column of the appropriate row.  

HTH...

xF,

...Nick

---

