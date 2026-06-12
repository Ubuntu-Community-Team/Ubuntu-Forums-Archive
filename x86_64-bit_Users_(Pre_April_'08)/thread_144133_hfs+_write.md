---
title: "hfs+ write"
date: 2006-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by maxdevis on 2006-03-13
is it normal that i can't write to a hfs+ hdd?
i have an ibook with 3 partitions
Ubuntu
OSX
storage

storage is hfs+, but i can't write to that from ubuntu?

---

### Post by stuporglue on 2006-03-13
Sounds like it got mounted funny or something. I was able to write to HFS+ on Gentoo two(?) years ago. Never had any problems with it either.

---

### Post by calum on 2006-03-13
[QUOTE=maxdevis]is it normal that i can't write to a hfs+ hdd?
i have an ibook with 3 partitions
Ubuntu
OSX
storage

storage is hfs+, but i can't write to that from ubuntu?[/QUOTE]

Can you write to it as root?  ISTR that's what I have to do, haven't bothered to figure out what might be wrong in my /etc/fstab to change this though.

---

### Post by maxdevis on 2006-03-14
nope, 
i can't write.
maybe i mount it wrong?
[QUOTE=terminal]
sudo mount -t hfsplus -o "ro" /dev/hda14 /media/storage
[/QUOTE]

found that [here](http://www.ubuntuforums.org/showthread.php?t=138558&highlight=mount+hfs)

---

### Post by maxdevis on 2006-03-14
but i can read and write to that partition when i boot in OSX

---

### Post by slux on 2006-03-14
Well, mounting it with "-o ro" is explicitly asking for no write permissions. "ro" there stands for read-only. Leave that out or replace it with rw and you might have more success.

---

### Post by sulobanks on 2006-03-14
I remember having to change my user id in my linux system to match that of my user account in my os x system in order to get the ability to write to that account in the hfsplus partition.  I haven't done that with my system this time around just because I don't feel like it. ;)  But check what your userid is in os x, then type this in linux:

sudo usermod -u <desired UID (from os x)> <your username>

Might have to chown everything in your home directory to this new user id so that you don't have problems, but that should make the os x partition writable to you.

---

