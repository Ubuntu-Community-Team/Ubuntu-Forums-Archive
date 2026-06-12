---
title: "Cant install on Dual Core G5"
date: 2006-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by imaswitcheryeah on 2006-05-27
Hello all,

New user here.  I installed the 5.10 Intel version successfully on a Intel Mac Mini within a Parallels virtual machine.  Install went without a hitch.  I used bittorrent to download the dvd install disc.

I did the same for the 5.10 PowerPC version to install natively on a Dual Core 2 GHz PowerMac.  I burned the .iso to a dvd, rebooted my PowerMac and chose the install-powerpc64 option.  After loading the kernel, a white screen comes up with a bunch of text and at end it says something about "init" (i didnt write it down), at the beginning of the white screen, it was outputting the confirmation of detecting the video card and display.

When first choosing an option to install, it mentioned that by using the "video=ofonly" variable, it would help if your install was freezing on "a white screen".  Unfortunately, this variable did not help me and got stuck at the same exact point.

If anyone can help me out that would be great.  I don't know what is going wrong and I've seen so many reports of easy installs for PowerPC users.

(I'm re-downloading the iso just to be sure my file wasn't corrupted)

Thanks all, and I look forward to contributing to the community! :)

---

### Post by kellogs on 2006-05-27
I installed breezy 5.10 on a power mac G5 dual 2.3ghz without problems. Now im running recently updated system with dapper. 

If that helps, Ive got a ATI radeon 9600 128 mb. and the only install option that allowed me to install without hangs was install-powerpc64. 

maybe you should try again, I installed the first time with a CDRW with the iso burned on it and no problems. 

hope you get it fixed.

---

### Post by imaswitcheryeah on 2006-05-27
hey kellogs,

thanks for the reply.

I have one of the recent dual-core G5s with pci-express.  I also have a lot of upgraded components, like 2 GB of Crucial Ballistix memory and some upgraded hard drives.  Are there any internal components that are not compatible with Ubuntu?

I re-downloaded the powerpc iso overnight last night, burned it to another dvd and tried "install-powerpc64".  Stuck on the same white screen. So, I tried "install-powerpc64 video=ofonly" STILL, the same thing.

This time I will write out the entire output from this white screen....

```
done
found display   :  /pci@0,f0000000/NVDA,Parent@0/NVDA,Display-B@1, opening ... done
copying OF device tree ...
Building dt strings...
Building dt structure...
Device tree strings 0x00000000022f9000 -> 0x00000000022fa77a
Device tree struct 0x00000000022fb000 -> 0x000000000230b000
Calling quiesce ...
returning from prom_init
_
```

And that's it.  That where it gets stuck no matter what I do.

Thanks in advance!!

EDIT: I think I spelled "Calling **quiesce** ..." wrong.  I don't feel like going back through that again because of the misspelling.  Sorry! :p

---

### Post by darcyb on 2006-05-30
If it turns out to be a video problem with NVD video cards, then that may be why the live cd for DD RC won't boot for me on my dual core G5 PPC 2GHz. I've got an NVD 6600LE.

---

### Post by imaswitcheryeah on 2006-05-31
[QUOTE=darcyb]If it turns out to be a video problem with NVD video cards, then that may be why the live cd for DD RC won't boot for me on my dual core G5 PPC 2GHz. I've got an NVD 6600LE.[/QUOTE]

hey darcyb,

i have also tried the dapper live cd on this machine to see if there were fixes for this in the RC, and the splash screen that lists everything loading was all completely the wrong colors... it looked strange but recognizable.  did you notice this as well? ultimately it did not boot on the dapper live cd.

my machine has the Nvidia 6600 256MB card (the non-LE version).  is it a known issue that the new (specifically pci-express?) video cards on macs are not fully supported?  can anyone point in the direction of where I can find information on supported hardware or known hardware issues?

thanks!

---

### Post by darcyb on 2006-06-01
Splash screen colors were all messed up, yeah. :(

---

