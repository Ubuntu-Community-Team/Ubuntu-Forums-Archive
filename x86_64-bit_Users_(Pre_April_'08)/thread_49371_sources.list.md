---
title: "sources.list"
date: 2005-07-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by fistfullofroses on 2005-07-16
I uhhh really f--ked up my sources.list file,
trying some things out on the learning process...
and I was hoping someone would copy his/hers
and post it here, so that I can use it for mine,
and uhhh fix my shyte

---

### Post by RastaMahata on 2005-07-16
[QUOTE=fistfullofroses]I uhhh really f--ked up my sources.list file,
trying some things out on the learning process...
and I was hoping someone would copy his/hers
and post it here, so that I can use it for mine,
and uhhh fix my shyte[/QUOTE]
 ```

#Ubuntu Main
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

#Ubuntu Updates
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

#Ubuntu Security
deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

#Ubuntu Universe
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

#Ubuntu Multiverse
deb http://us.archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary multiverse

#Ubuntu Backports Planetmirror
deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-extras main universe multiverse restricted
deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-backports main universe multiverse restricted

```

---

### Post by NeoChaosX on 2005-07-16
Remove the "us" from those addresses. The US archive server has had plenty of MD5 problems with their packages lately.

---

### Post by RastaMahata on 2005-07-16
[QUOTE=NeoChaosX]Remove the "us" from those addresses. The US archive server has had plenty of MD5 problems with their packages lately.[/QUOTE]
 its just that I use cl mirrors... i thought he would use us mirrors since he's from USA :S

---

### Post by fistfullofroses on 2005-07-17
[QUOTE=RastaMahata]```

#Ubuntu Main
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

#Ubuntu Updates
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

#Ubuntu Security
deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

#Ubuntu Universe
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

#Ubuntu Multiverse
deb http://us.archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary multiverse

#Ubuntu Backports Planetmirror
deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-extras main universe multiverse restricted
deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-backports main universe multiverse restricted

```[/QUOTE]
 thank you!!!

---

