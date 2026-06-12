---
title: "Chroot DNS trouble?"
date: 2007-04-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by kidders on 2007-04-06
Hi guys,

I'm having a problem that I just *know* has an obvious cause & solution, but I can't seem to find it.

I've recently installed my first 64-bit Ubuntu (normally I use Gentoo for 64-bit boxes), and I've decided to admit defeat right away, and run certain things out of a 32-bit chroot-ed environment without putting up a fight. The problem I'm having seems to have to do with performing DNS lookups, but it only affects applications with a GUI.

Some of the detail of my setup might be important...

I'm using dchroot. I ran into trouble right away with locales & DNS, but managed to iron things out as best I could by **dpkg-reconfigure**-ing things, and temporarily adding some entries to /etc/hosts to avoid having to use DNS. Now, I seem to be able to be able to successfully **ping something.ive.never.pinged.before.com**, but my web browsers don't seem to like it when I use hostnames, rather than IPs.

This is probably the cleanest way of describing what I've done...
```
kidders@x2:~$ mount |grep chroot
/home on /opt/chroot32/home type none (rw,bind)
/tmp on /opt/chroot32/tmp type none (rw,bind)
/dev on /opt/chroot32/dev type none (rw,bind)
/proc on /opt/chroot32/proc type none (rw,bind)
/etc/passwd on /opt/chroot32/etc/passwd type none (rw,bind)
/etc/shadow on /opt/chroot32/etc/shadow type none (rw,bind)
/etc/group on /opt/chroot32/etc/group type none (rw,bind)
/etc/sudoers on /opt/chroot32/etc/sudoers type none (rw,bind)
/etc/hosts on /opt/chroot32/etc/hosts type none (rw,bind)
/etc/resolv.conf on /opt/chroot32/etc/resolv.conf type none (rw,bind)
/etc/nsswitch.conf on /opt/chroot32/etc/nsswitch.conf type none (rw,bind)
/media/cdrom0 on /opt/chroot32/media/cdrom type none (rw,bind)
```Was that smart?

---

### Post by Kilz on 2007-04-06
> **kidders said:**
> Hi guys,

I'm having a problem that I just *know* has an obvious cause & solution, but I can't seem to find it.

I've recently installed my first 64-bit Ubuntu (normally I use Gentoo for 64-bit boxes), and I've decided to admit defeat right away, and run certain things out of a 32-bit chroot-ed environment without putting up a fight. The problem I'm having seems to have to do with performing DNS lookups, but it only affects applications with a GUI.

Some of the detail of my setup might be important...

I'm using dchroot. I ran into trouble right away with locales & DNS, but managed to iron things out as best I could by **dpkg-reconfigure**-ing things, and temporarily adding some entries to /etc/hosts to avoid having to use DNS. Now, I seem to be able to be able to successfully **ping something.ive.never.pinged.before.com**, but my web browsers don't seem to like it when I use hostnames, rather than IPs.

This is probably the cleanest way of describing what I've done...
```
kidders@x2:~$ mount |grep chroot
/home on /opt/chroot32/home type none (rw,bind)
/tmp on /opt/chroot32/tmp type none (rw,bind)
/dev on /opt/chroot32/dev type none (rw,bind)
/proc on /opt/chroot32/proc type none (rw,bind)
/etc/passwd on /opt/chroot32/etc/passwd type none (rw,bind)
/etc/shadow on /opt/chroot32/etc/shadow type none (rw,bind)
/etc/group on /opt/chroot32/etc/group type none (rw,bind)
/etc/sudoers on /opt/chroot32/etc/sudoers type none (rw,bind)
/etc/hosts on /opt/chroot32/etc/hosts type none (rw,bind)
/etc/resolv.conf on /opt/chroot32/etc/resolv.conf type none (rw,bind)
/etc/nsswitch.conf on /opt/chroot32/etc/nsswitch.conf type none (rw,bind)
/media/cdrom0 on /opt/chroot32/media/cdrom type none (rw,bind)
```Was that smart?

Just curious, why are you using a chroot? What do you need to run in it?

---

### Post by kidders on 2007-04-06
Wine, Flash, RealPlayer, Opera... (to name a few)

Struggling for days to make hacky 64-bit implementations of certain things half work gets tiresome, so for some things, an easily available 32-bit environment is quite handy. Other times, it's just plain essential. By the way, your signature is suggestive! I must take a look.

---

### Post by haggai_e on 2007-04-23
I'm also suffering from this problem, I think. It started after upgrading from edgy to feisty (I upgraded both the chroot and the main system).
The weird thing is that it only affects one of the users in the system. One user doesn't have any trouble using dns in firefox, but the other can't.

Anyone knows how to debug this?

Haggai

---

### Post by kidders on 2007-04-23
Hi there,

I haven't made any progress with this issue. :-( I wonder what's different about the user account that *can* work DNS on your system!

---

### Post by haggai_e on 2007-04-24
It seems its the firefox's profile. I tried creating a new clean profile for firefox with the user that did work, and the new profile showed the same problem. I also tried safe-mode with the original (working) profile, and it still worked, so I guess its not the extesnions.

---

### Post by haggai_e on 2007-04-24
Ok, I got it!
It was the ipv6 dns setting. For some reason it caused dns searches to fail.
In about:config, I set network.dns.disableIPv6 to "true" and now it works fine.

---

### Post by kidders on 2007-04-24
> **haggai_e said:**
> Ok, I got it!
It was the ipv6 dns setting. For some reason it caused dns searches to fail.
In about:config, I set network.dns.disableIPv6 to "true" and now it works fine.Drat. It doesn't look like we have the same problem.

Glad you've got yours working :-)

---

