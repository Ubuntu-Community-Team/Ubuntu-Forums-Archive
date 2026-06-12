---
title: "dchroot and localhost"
date: 2007-06-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by cequiel on 2007-06-14
hello everybody.

I have Ubuntu Feisty 64bits on my laptop. I needed to install Opera, but there is no release for 64 bits platforms :(, so I installed a chroot with ubuntu 32bits ([http://process-of-elimination.net/wiki/Ubuntu_32bit_CHROOT_for_AMD64](http://process-of-elimination.net/wiki/Ubuntu_32bit_CHROOT_for_AMD64)).

Opera works fine, the problem is I can connect either internet nor localhost. In fact, when I go to the chroot (dchroot -d), and execute the command 'ping localhost' I get the message 'ping: unknown host localhost'.

I don't know what is happening.

(sorry for my english and thank you very much)

---

### Post by Cappy on 2007-06-14
I have no idea but I used this guide:
[http://ubuntuforums.org/showthread.php?t=413040](http://ubuntuforums.org/showthread.php?t=413040)

---

### Post by incubus on 2007-06-14
Hi,

Can you check that 
```

/etc/resolv.conf

```

is the same both in the main installation and in the chroot environment?

incubus

---

### Post by incubus on 2007-06-14
I have a suspicion of what it could be, reading that guide you followed.  Network is being set up after the partitions are mounted.  That could imply that resolv.conf will differ.  You could either manually copy resolv.conf to the chroot environment, or -- I'm not sure if this always works -- delete it from the chroot and don't mount it.

I *think* I did the second thing on my laptop and it worked.

By the way, I love having a chroot environment because you can use it as a sandbox for experimenting with new programs, without interfering with the main installation.  If you screw it up, just make another one.

incubus

---

