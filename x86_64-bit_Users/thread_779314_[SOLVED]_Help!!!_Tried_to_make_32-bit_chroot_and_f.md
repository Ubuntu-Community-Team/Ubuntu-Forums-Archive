---
title: "[SOLVED] Help!!! Tried to make 32-bit chroot and failed!"
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by ZabiGG on 2008-05-02
Hi all and thank you for this forum.

Newbie here made a big boo-boo. I tried to set up a 32-bit chroot, but I failed over and over again. So now I'm stuck with a number of them, and in various directories. I would love to be able to erase everything and start again, but I'm scared I'll scrap the original chroot (is it required?) if I do. All this simply because I need to install some 32-bit software :O(

Running Hardy 64 bit on an AMD 64.

I could always leave the unnecessary files and duplicates there, but I try to keep a streamlined computer.... (lol) 

Thanks in advance

ZabiGG

---

### Post by Grishka on 2008-05-02
you don't have to install 32-bit software under chroot in Hardy. all 32-bit software will work, provided you have proper libraries in /usr/lib32/ folder. I don't think removing your chroot dirs will do any harm.

---

### Post by ZabiGG on 2008-05-02
Thanks very much. 

But is there an easy way for me to get rid of everything I just installed for nothing then?

Cheers,

ZabiGG

---

### Post by Grishka on 2008-05-02
> **ZabiGG said:**
> Thanks very much. 

But is there an easy way for me to get rid of everything I just installed for nothing then?

Cheers,

ZabiGG

that depends on how exactly you set it up, but I'd say removing them by hand may be your best bet.

---

### Post by ZabiGG on 2008-05-11
Yup, it worked.

Thanks!

---

