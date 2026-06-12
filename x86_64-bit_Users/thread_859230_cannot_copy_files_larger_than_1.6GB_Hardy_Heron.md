---
title: "cannot copy files larger than 1.6GB Hardy Heron"
date: 2008-07-14
forum: x86 64-bit Users
---

### Post by veiloctane on 2008-07-14
i cannot copy files larger than 1.6GB when i try to copy a file it runs quick for the first few seconds and once it gets close to 1.6GB the system slows down and hangs i am using hardy heron 8.04 amdx64

i am new to Ubuntu so any help would be great.


thanks

---

### Post by quinnten83 on 2008-07-14
what are you copying to and from?
ifyou are using a hard-disk formatted in FAT32,that moght be your problem right there.

---

### Post by veiloctane on 2008-07-14
> **quinnten83 said:**
> what are you copying to and from?
ifyou are using a hard-disk formatted in FAT32,that moght be your problem right there.

i am copying from a file from a dvd drive to my desktop in ubuntu.


ext3 so i do not have anything formated in fat32.

---

### Post by stchman on 2008-07-14
> **quinnten83 said:**
> what are you copying to and from?
ifyou are using a hard-disk formatted in FAT32,that moght be your problem right there.

FAT32 has a file size limitation of >4GB.  A file of 1.6GB is no problem.

---

### Post by elmoosecapitan on 2008-07-14
If it helps, what I have done in the past is:

cp /media/cdrom0/filename.filetype ~/Desktop/

or if you are trying to copy a folder

cp -r /media/cdrom0/foldername ~/Desktop/


cheers

---

### Post by veiloctane on 2008-07-26
fixed i had to turn off acpi found in this forum...


[http://ubuntuforums.org/showthread.php?t=787573&page=2](http://ubuntuforums.org/showthread.php?t=787573&page=2)

---

