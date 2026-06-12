---
title: "dual - boot with windows x64"
date: 2006-09-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by cdavies on 2006-09-24
hi

i currently have a pc with an amd 64 processor and 160 gb hd. it has been partitioned into 2 75gb halves. windows xp x64 is installed on one partition. is it possible to install ubuntu on the other partition and have a dual-boot system?

thanks

---

### Post by bernied on 2006-09-24
Yes it is possible and done regularly. Some things to consider:
- do it slowly, knowing what you are doing at each step
- use the ubuntu live-cd to make a copy of the windows master boot record before you start - the ubuntu install will overwrite this to enable dual booting (generally a good thing but sometimes not)
- consider using more than one partition for the ubuntu install. The installer will want at least one more partition for swap space. You should also consider a partition for sharing between windows and linux. Windows doesn't support linux filesystems well and the same is true for linux support of NTFS. FAT32 works well on both (but only for shared data, not for the the linux OS).
- maintain a way of getting internet access, so you can always get advice, in case things don't go so well (I suggest a bootable grub floppy made from the live-cd is a good tool, combined with the knowledge of how to boot windows from it)
- the 64 bit versions of linux are not quite polished yet. Consider beginning with a 32-bit version (another reason for having multiple partitions)

google any of the above that you don't understand, or (if all else fails) ask for more info here

---

### Post by tymek666 on 2006-09-24
> **bernied said:**
> Windows doesn't support linux filesystems well and the same is true for linux support of NTFS. FAT32 works well on both (but only for shared data, not for the the linux OS).

I haven't any problems with support linux file systems under winxp. I've installed ext plugin for TC, which works very well with linux partitions.

> **bernied said:**
> 
- the 64 bit versions of linux are not quite polished yet. Consider beginning with a 32-bit version (another reason for having multiple partitions)


What do you mean 'not quite polished yet'? I think they are more polished than 64bit winxp...

---

### Post by cdavies on 2006-09-25
i do think there are issuse with windows x64 - until i got a recent update it occasionally refused to shut down!!
i wanted to try ubuntu because i was fairly sure it would run more smoothly, and knew th customer support and help would be better!!
i do need to keep the windows partition, because of school work. having a file sharing partition is a good idea, thanks for that.
i'll let you know how it works out when i get round to it!

---

