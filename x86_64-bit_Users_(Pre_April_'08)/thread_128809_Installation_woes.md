---
title: "Installation woes"
date: 2006-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Herring on 2006-02-12
I've done a bit of googling on this problem, but not come up with anything which solves my problem yet. Apologies if I've missed something well known.

Anyhow, the situation is this: I downloaded an ISO of Kubuntu 5.10 for amd64. The new machine I've just got is from a bargain boxbuilder (who knows nothing about Linux) so may have an odd setup. What happens is this:
[LIST]
[*]Boot from created DVD
[*]Select options
[*]Preseed loads
[*]Disc checks out OK
[*]Starts to load modules
[*]Comes up with a CD/DVD read error loading ef2sprogs-udeb
[/LIST]
I have burned a few copies, downloaded a second DVD image and compared with the first and also tried a CD image. There is a slight difference if I play with options where sometimes it comes up with the error loading libc6.

I've tried (in expert mode) limiting the loaded devices to generic IDE and piix. I've also tried disabling SATA from the BIOS. That didn't help.

Once the CD error has come up, nothing will read from the CD anymore so there is some sort of conflict.

The chipset is VIA K8M800 with all the SATA/IDE stuff built in.

I've been on this over a week - so far all I can run is XP64 - which is depressing.

Any help would be appreciated.

---

### Post by jonathan_c on 2006-02-12
Are you burning these to a dvd-rw? I'd try a different medium. My laptop randomly decided to stop reading cd-rws, granted it is a few years old but still. I burned the same downloaded ISO on a cd-r and it worked fine.

---

### Post by Herring on 2006-02-12
I've tried DVD R, CD RW and CD. Always fails in the same place.

---

### Post by obx-jdt on 2006-02-13
odd, I couldn't install it on a simpron64 either...& I have the offical 5.10 64bit CD that was mailed to me. Told me there was no network device, and no hard drive installed.....The real kicker is that win2000 loaded on the system without a hitch. I might be going out on a limb here, but Ubuntu64 does support ATA hard drives dosen't it????:-k

---

### Post by Daggett on 2006-02-21
I don't know if this is your problem, but In order for the kernel to see an SATA CD/DVD drive as a CD/DVD drive, a parameter in libata-core called atapi_enabled has to be set to 1.  It is set to 0 by default.  I don't know of any boot command that can set this to 1.  The boot command libata.atapi_enabled=1 is supposed to work, but it doesn't.  

I encountered this while trying to install Debian AMD64 and the only way I could "solve" it was to install a regular IDE CD/DVD drive and install it from that.  I think the real solution is for the Ubuntu/Kubuntu maintainers to make atapi_enabled=1 the default and recompile the module that way.  There are other solutions that don't require changing the kernel code, but I think that's the easiest and most reliable.

---

### Post by Herring on 2006-02-21
Thanks. I think I have an IDE CD lying around. I'll give it a go.

---

### Post by Herring on 2006-02-21
No, that's not it. Even with no SATA devices on the machine, same thing.

---

### Post by jklasdf on 2006-03-17
[QUOTE=Herring]
[*]Disc checks out OK
[/QUOTE]
When you check the disks does it take a while and show which files it is checking, or does it almost instantly (~less than 5 seconds) say that the disk is ok without showing which files are being checked? For some reason on sufficiently bad/corrupted installation media, the installer just says the disk is good without actually checkingit. 
[QUOTE=Herring]
[*]Starts to load modules
[*]Comes up with a CD/DVD read error loading ef2sprogs-udeb
[/QUOTE]
Interestingly, the first time installing, i kept getting the exact same error (and the md5sums checked and I even tried different cd's). Using the newest media I have (which sadly is almost a year old) I was able to get slightly further. If you can get past loading e2fsprogs-udeb, after it fails, select no when it asks you if you want to retry, hit continue, and repeat the "load components from cd" step. It should ask you what components you want to load. Unselect the base-installer (or whatever it is...should be the first option) and everything else except the download base-installer (or scan hardrive for base-installer, or load base-installer from floppy disk, or etc. depending on how you want to load the installer) and continue with the installation.

---

