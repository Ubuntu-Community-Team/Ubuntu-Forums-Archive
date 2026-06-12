---
title: "32 Bit Compatible?"
date: 2006-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Inhumane on 2006-10-27
Is Ubuntu 64 like Windows 64? Can it natively run 64 bit apps without a performance impact?

---

### Post by John.Michael.Kane on 2006-10-27
Ubuntu 64 bit is not multi arch based. theres howto's for installing some  programs under 64bit ubuntu like flash,and java.

If I'm no mistaken suse does multi arch where you can install 32bit app on 64bit

[http://ubuntuforums.org/showthread.php?t=191205](http://ubuntuforums.org/showthread.php?t=191205)
[http://www.ubuntuforums.org/showthread.php?p=1174435](http://www.ubuntuforums.org/showthread.php?p=1174435)

---

### Post by FedeXX on 2006-10-28
> **SD-Plissken said:**
> Ubuntu 64 bit is not multi arch based. theres howto's for installing some  programs under 64bit ubuntu like flash,and java.

If I'm no mistaken suse does multi arch where you can install 32bit app on 64bit

[http://ubuntuforums.org/showthread.php?t=191205](http://ubuntuforums.org/showthread.php?t=191205)
[http://www.ubuntuforums.org/showthread.php?p=1174435](http://www.ubuntuforums.org/showthread.php?p=1174435)

Ubuntu have a partial multiarch...You can install every .deb 32bit package by forcing architecture:

```

sudo dpkg -i --force-architecture thatnice32bitpackage.deb

```

However you need to manually install its 32bit dependancies too (argh ](*,) )

---

