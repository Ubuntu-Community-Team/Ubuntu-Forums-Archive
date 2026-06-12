---
title: "GRUB Problem"
date: 2005-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by vimo on 2005-11-01
So, I have installed Ubuntu Breezy for AMD64. It is wonderful, no doubt!  But... 
I installed Grub for a 2 OS system boot (Win XP Pro  & Ubuntu).

The problem: when I try to boot Windows, I receive the message "unknown filesystem" referred to the NTFS FS of Win.
I tried many times to:
1) restore the MBR using FIXBOOT & FIXMBR from the Windows console.
2) reinstalling GRUB from Ubuntu.

I had the same result: an MBR unusable for Win boot.

What's the matter? Is the AMD64 Grub not safe to use with Win XP (I think it is improbable!)
What error(s) did I do?
Can someone out there help me?

Is there a manner to restore the Win MBR without booting via Windows  Installation CD (it requires too much time).

Thank you.

---

### Post by gandonov on 2005-11-01
Probably XP is installed on NTFS partition. And you get an error: *"Filesystem type unknown, partition type 0x7"*.

Replace **root** with **rootnoverify** in */boot/grub/menu.lst*
```
title Win XP Pro
**rootnoverify (hd#,#)**
makeactive
chainloader +1
```

---

### Post by vimo on 2005-11-01
Your solution works fine!
Thank you very much

---

