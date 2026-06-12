---
title: "Re: Install Flash on 64-Bit"
date: 2008-07-13
forum: x86 64-bit Users
---

### Post by intrader on 2008-07-13
I am seeking to install flash on ubuntu. I install used wubi which installed ubuntu as 64 bit. Lots of stuff does not work in 64 bit. How do I tell wubi to install 32 bit?

Thanks

---

### Post by Sef on 2008-07-13
1) Moved to current 64-bit forum.

2) Did you try [Kilz's script]("http://ubuntuforums.org/showthread.php?t=772490")?

---

### Post by stchman on 2008-07-13
> **intrader said:**
> I am seeking to install flash on ubuntu. I install used wubi which installed ubuntu as 64 bit. Lots of stuff does not work in 64 bit. How do I tell wubi to install 32 bit?

Thanks

Flash works fine in 64 bit.  I have Flash working in 64 bit Ubuntu on three separate machines.  To install flash in 64 bit do the following:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by tuxxy on 2008-07-13
Install Flash 

```
sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0/plugins/
```

> Lots of stuff does not work in 64 bit

What in particular is not working?

---

### Post by stchman on 2008-07-14
Yes, what does not work?

The only thing I had problems with was a Java browser plugin.  I installed Icedtea and all works fine.  Everything else works very well.

---

### Post by Kilz on 2008-07-14
> **stchman said:**
> Yes, what does not work?

The only thing I had problems with was a Java browser plugin.  I installed Icedtea and all works fine.  Everything else works very well.

The low post count of the original poster, and the fact that they used wubi may point to the fact they may not have a lot of experience with Ubuntu or Linux. If that is the case, they still may be going through the learning curve.

---

