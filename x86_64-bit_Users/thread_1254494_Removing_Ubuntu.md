---
title: "Removing Ubuntu"
date: 2009-08-31
forum: x86 64-bit Users
---

### Post by Yowan on 2009-08-31
How can I remove Ubuntu9.04 from my PC?
I've installed it on a 20GB partition
Ubuntu just corrupted my windows vista and is preventing it from booting( i get blue screen error everytime)

Ubuntu does not even run properly on my PC

---

### Post by Bucky Ball on 2009-08-31
How did you install it?

---

### Post by Yowan on 2009-08-31
By using a bootable CD

---

### Post by Bucky Ball on 2009-08-31
I'm talking about when you got to choices for partitioning your disk. Did you do it manually or automatically?

---

### Post by Yowan on 2009-08-31
I did it by using disk management in vista
Then I installed Ubuntu

---

### Post by Bucky Ball on 2009-08-31
Yea, but when you installed Ubuntu, it reaches a part where it asks you how you would like to partition your drives. You have a few options. Which one did you choose?

The partition magic part is not really relevant as I don't think it would make EXT3 or EXT4 partitions and this is what you need to do which is why you need to create the Ubuntu partitions as part of the install (unless they already exist which they didn't).

Are you reaching a grub menu which lets you boot to Windows or Ubuntu when you switch on your machine? Give as much info about what is happening as poss. If you can boot into ubuntu, go to System->Administration->Partition Editor. Is your NTFS Windows partition anywhere to be found?

---

### Post by Yowan on 2009-08-31
I just clicked on 'Advanced' and I used my partition which i created on windows
I did not use Ubuntu setup to partition my hard disk

---

### Post by Bucky Ball on 2009-08-31
Well, I'd be surprised if you can boot into Ubuntu either. If you can:

Are you reaching a grub menu which lets you boot to Windows or Ubuntu when you switch on your machine? Give as much info about what is happening as poss. If you can boot into ubuntu, go to System->Administration->Partition Editor. Is your NTFS Windows partition anywhere to be found?

In the partition editor you should find at least these partitions for Ubuntu:

/
/home
/swap

They have to be EXT3 (or EXT4 for Jaunty I believe). As mentioned, I don't think Partition Magic creates this type (did you attempt to install Ubuntu on NTFS partition? Won't work) and doesn't handle them either. It is primarily for Windows and will only run on that. Totally unsuitable for Linux. I would stick in the live CD if you can't boot to Ubuntu and follow the instructions above.

> Ubuntu just corrupted my windows vista and is preventing it from booting( i get blue screen error everytime). Ubuntu does not even run properly on my PCThere's good reason for this and it probably has nothing to do with Ubuntu. Many of us dual-boot with no problems (I dual-boot three machines faultlessly, two with XP one with Vista). Better to use a guide when new to Linux rather than dive in. Do a bit of research. :)

---

### Post by anujpathania on 2009-08-31
I think you messed up your installation. Infact u should admire ubuntu that it worked.

Put in a clean installation of Vista and next time use Wubi that comes on CD for Dual Boot.

---

### Post by Bucky Ball on 2009-08-31
I would avoid Wubi and just get your dual boot install right. :)

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

That link is a gold mine of info for dual-booting and installation.

---

### Post by anujpathania on 2009-08-31
> **Bucky Ball said:**
> I would avoid Wubi .

Why? Its an awesome piece of software (as open source one always are). It makes installing and uninstalling Ubuntu such a breeze. No easy way of installation for newbie and I always highly recommend it. 

Though I am geek enough to dual boot manually :), I no longer do it any more.

---

### Post by SoftwareExplorer on 2009-08-31
@Bucky Ball:Jaunty uses ext3 by default, but you can set up ext4 by using manual partitioning.

---

### Post by Bucky Ball on 2009-08-31
anujpathania: Glad it works for you, never been anything but trouble for me. Maybe it has improved.

SoftwareExplorer: Noted. Thanks.

---

