---
title: "amd64 and chroot 32bit same themes"
date: 2005-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by leonv on 2005-03-08
Hi

I have installed chroot environment on a 64 bit platform. 

One app I like that will only work in a 32bit environment is gphpedit. 

A simple question, what is the best way to keep the same look and feel for apps (borders/themes etc) between launching from the 64bit and chroot environments?

Many thanks
Leon

---

### Post by leonv on 2005-03-08
For those that are interested, what I needed to do is to install the relevant gtk2-engines-X in the chroot environment.

--
Leon

---

### Post by my64 on 2005-03-08
[QUOTE=leonv]Hi

I have installed chroot environment on a 64 bit platform. 

One app I like that will only work in a 32bit environment is gphpedit. 

A simple question, what is the best way to keep the same look and feel for apps (borders/themes etc) between launching from the 64bit and chroot environments?

Many thanks
Leon[/QUOTE]

I have added this to my /etc/fstab, and your entire home with your settings now appears also under the chroot:

```
# for chroot
/home           /var/chroot/home        none    bind            0       0
/tmp            /var/chroot/tmp         none    bind            0       0
/proc           /var/chroot/proc        proc    defaults        0       0
/media/cdrom    /var/chroot/media/cdrom none    bind            0       0
```

---

### Post by andyjeffries on 2005-10-16
[QUOTE=leonv]I have installed chroot environment on a 64 bit platform. 

One app I like that will only work in a 32bit environment is gphpedit.[/QUOTE]

Just to let you know, the current CVS version of gPHPEdit is 64 bit safe.  I'll be doing a release sometime next week so then push your Ubuntu maintainers to put the new version in the distro.

Cheers,


Andy

---

