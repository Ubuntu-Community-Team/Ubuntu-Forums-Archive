---
title: "Installing 32bit java"
date: 2009-02-04
forum: x86 64-bit Users
---

### Post by jwilley44 on 2009-02-04
Hello,

I am running Ubuntu 8.10 64 bit. I have a 64 bit version of sun's java but I would also like to use GWT which, for host-mode at least, does not work with a 64 bit JVM. I tried several times to install a 32 bit version of sun's java but I keep getting this message:

./jre-6u12-linux-i586.bin: 363: ./install.sfx.11180: not found
Failed to extract the files.

Hope this is clear, thanks in advance.

---

### Post by jwilley44 on 2009-02-04
Ok, so I should have searched around a bit more. The solution was to install ia32-libs as noted on this thread:

[http://ubuntuforums.org/archive/index.php/t-65635.html](http://ubuntuforums.org/archive/index.php/t-65635.html)

The 32bit version of java then installed correctly, easy fix!

---

