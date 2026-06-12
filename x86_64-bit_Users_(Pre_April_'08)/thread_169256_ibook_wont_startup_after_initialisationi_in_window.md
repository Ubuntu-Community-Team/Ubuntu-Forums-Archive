---
title: "ibook wont startup after initialisationi in windows"
date: 2006-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by maxdevis on 2006-05-02
i' have an old ibook with three partitions
1 OSX
2 Ubuntu
3 Storage

i can connect my ibook with firewire to my homepc so he recognize it as an external HDD.
In ubuntu it all works fine,
but i tried it in windows and windows asked me to initialize the disk.
i did
and now
my ibook wont startup
i get a grey screen with in the middle an icon of a folder that change to the finder OSX-symbol and back to the folder image.

is my yaboot deleted?

---

### Post by calum on 2006-05-02
[QUOTE=maxdevis]
i can connect my ibook with firewire to my homepc so he recognize it as an external HDD.
In ubuntu it all works fine,
but i tried it in windows and windows asked me to initialize the disk.
i did
and now
my ibook wont startup
i get a grey screen with in the middle an icon of a folder that change to the finder OSX-symbol and back to the folder image.

is my yaboot deleted?[/QUOTE]

Windows doesn't understand OSX or Linux filesystems, so it sounds like it thought your disk was unformatted, and prompted you to format it with a Windows filesystem (NTFS or FAT32).  If that's what you did, you might well have lost the entire contents of your disk, not just yaboot.  Hope you had a backup...

---

