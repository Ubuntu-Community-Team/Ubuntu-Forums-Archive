---
title: "[SOLVED] Installing Lotus Symphony i386 on Ubuntu 8.10 x64"
date: 2008-12-30
forum: x86 64-bit Users
---

### Post by plr4ever on 2008-12-30
I was interested in trying Lotus' symphony, but i downloaded it an realized that the package was i386, and that they offered no amd64 download. I have looked at the tutorials for installing the i386 package on x64, but they all refer to a lotus symphony binary, not the .deb found on their website. 

Anyone know where i can get the regular binary, or how to install an i386 deb on amd64?

---

### Post by Sharker on 2008-12-31
in theory you can execute 32 bits binaries with ia32 package. you can test to install i386 deb and execute this

---

### Post by plr4ever on 2009-01-01
I just used ```
 dpkg --force-architecture -i packagename.deb
```

and voila! it worked.

---

### Post by SyberKowboy on 2009-01-30
> **plr4ever said:**
> I just used ```
 dpkg --force-architecture -i packagename.deb
```

and voila! it worked.

No success with the force architecture. Does anybody know the dependencies required to install this?

---

### Post by yyyc186 on 2009-02-10
We can only hope that one day they will see the light and release an AMD 64-bit DEB package.

While we are hoping, we should also hope they port Lotus Approach.

Symphony has one advantage over OpenOffice.  It can actually open all of those old LWP files many of us have and save them in OpenOffice format.  Sadly, I have to use my sacrificial notebooks Worsta partition since they didn't give us a 64-bit Deb.  I'm simply not willing to goober up my Ubuntu installation by installing a bunch of 32-bit stuff.  I did that once before, and bad things happened all over.

---

### Post by cogitordi on 2009-06-27
The solution for installing IBM Symphony 1.3 on Hardy Heron AMD64 is here:
[http://ubuntuforums.org/showthread.php?t=946756](http://ubuntuforums.org/showthread.php?t=946756)

---

