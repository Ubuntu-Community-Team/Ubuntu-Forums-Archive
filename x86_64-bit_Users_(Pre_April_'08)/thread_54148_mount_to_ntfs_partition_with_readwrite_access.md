---
title: "mount to ntfs partition with read/write access"
date: 2005-08-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by coosa on 2005-08-03
Hi all,

As the title is written, I'd like to mount to a logical ntfs partition (200 GB) with write access support.
I know so far that there are two experimental projects going on and I lake the knowledge about the 64-bit support they might offer.
I assume also that there is no kernel built-in support for that purpose under ubuntu and I would appreciate any help regarding this topic
I'd like also to mention that you should consider me as a newbie under linux to avoid complications.

Best regards

Coosa

---

### Post by Drain on 2005-08-03
There are a couple of threads already discussing this issue. It's relatively easy to read from an NTFS partition (there are straightforward instructions on [www.ubuntuguide.org)](www.ubuntuguide.org)), but writing to an NTFS partition is tricky at best, highly experimental at worst. The bad news is that you'll probably have to end up googling a better solution. 

[http://www.ubuntuforums.org/showthread.php?t=52318](http://www.ubuntuforums.org/showthread.php?t=52318)

---

### Post by coosa on 2005-08-03
I actually neverhad any problems mounting with read access to any ntfs partition so far.
My problem is directly involved with mounting to ntfs paritions with write access.
Before I posted the root message, I had indeed searched in google for this issue and explored the possibilities with linux-ntfs and captive-ntfs.
However, I'm posting here due to a simple fact; namely, i'm also trying to achieve this under ubuntu, so it's a ubuntu forum and there might be kernel specific issues involving ubuntu.

---

### Post by AaronRowe on 2005-08-17
I have encountered the same obstacle. I can easily mount a windows partition with read only access but even when I do either of the following commands, it just mounts the partition as read only. 

I am using the Live CD 

sudo mkdir /media/windows
sudo mount /dev/hda2 /mkdir/windows -t ntfs -o rw 

or 

sudo mkdir /media/windows
sudo mount /dev/hda2 /mkdir/windows -t ntfs nls=utf8,umask=000

How can I get the ntfs partition to be writable?

---

### Post by kao on 2005-08-17
kernel ntfs driver has very limited write support. So it's better to use stuff from captive-ntfs project (i don't know is it available on amd64). But it's extremly slow

---

