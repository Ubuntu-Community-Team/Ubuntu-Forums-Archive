---
title: "howto mount HFS+ volumes as writable on kernel 2.6.15 and later"
date: 2006-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by tomislavmedak on 2006-05-10
although i've tried everything that was suggested in the extensive post on mounting HFS+ volumes as writable:

[http://www.ubuntuforums.org/showthread.php?t=123785&highlight=hfs](http://www.ubuntuforums.org/showthread.php?t=123785&highlight=hfs)

my HFS+ partition would nonetheless mount as read-only. 

but yesterday i've discovered over at the gentoo PPC forum the reason why this it didn't work:

[http://forums.gentoo.org/viewtopic-t-460239.html](http://forums.gentoo.org/viewtopic-t-460239.html)

in brief, rw support for journaled HFS+ was removed from kernel 2.6.15 and later, as it wasn't checking if journal was clean before writing, and in consequence journaled HFS+ volumes cannot mount as writable.

now, there are two solutions.

1) there's a patch that can be applied against the kernel that allows clean journaling and can be found here: [http://dev.gentoo.org/~josejx/hfsplus-rw-journal.patch](http://dev.gentoo.org/~josejx/hfsplus-rw-journal.patch)

2) turn off journaling on the HFS+ volume. i did that by going in my OS X terminal and typing:

```
diskutils disableJournal /dev/your_disk_or_partition
```

after that i could finally touch my HFS+ partition :D

---

### Post by tomislavmedak on 2006-05-14
i figured out that this howto is incomplete. it works only after you have applied read and write permissions to all the enclosed folders of your HFS+ volume. 

to do that you have to either right-click your HFS+ volume and chose information in the drop down menu or just simply go to information widget by pressing the key combination apple+i. there under ownership and permissions you should give read and write permissions to all users and apply it to all enclosed folders.

now, upon rebooting into linux everything should work fine.

---

