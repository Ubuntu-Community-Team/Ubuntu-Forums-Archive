---
title: "Picasa fatal error"
date: 2007-06-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by fakie_flip on 2007-06-26
Picasa2 installed and worked for about 1 minute :( It was scanning for pictures, and it found many, but then it froze. i had to kill it with the highest signal. I ran Picasa2 again. It worked for about one minute again, and then it said fatal error. :( Help please.

According to the Linux FAQ for Picasa2 from Google, Picasa2 will run on a 64 bit Linux distro. It says you will need to configure your system according to your distro's help information. It says for Debian to install ia32-libs. In Ubuntu 64 Feisty, I have all the 32 lib packages installed.

[http://picasa.google.com/linux/faq.html#2](http://picasa.google.com/linux/faq.html#2)

```
root@ubuntu:~# dpkg -l | grep ia32
ii  ia32-libs                              1.5ubuntu9                             ia32 shared libraries for use on amd64 and i
ii  ia32-libs-gtk                          25                                     gtk+ ia32 shared libraries for with OpenOffi
ii  ia32-libs-kde                          12                                     KDE ia32 shared libraries for with OpenOffic
ii  ia32-libs-sdl                          1.0ubuntu3                             ia32 shared libraries of sdl related package
ii  ia32-sun-java6-bin                     6-00-2ubuntu2                          Sun Java(TM) Runtime Environment (JRE) 6 (32
root@ubuntu:~# dpkg -l | grep "asound\|linux32"
ii  lib32asound2                           1.0.13-1ubuntu5                        ALSA library (32bit)
ii  libasound2                             1.0.13-1ubuntu5                        ALSA library
ii  linux32                                1-3                                    Wrapper to set the execution domain
root@ubuntu:~#
```

---

### Post by sambehera on 2007-06-27
im having the same problem... except mine does not find any pictures before i have to kill it... i dont remember now but i guess i force -installed it as a 32 bit package... any way, its still beta and things might get better when the stable release comes out (hopefully a native x64 version as well)

---

### Post by fakie_flip on 2007-07-05
Mine hasn't gave me anymore problems. I did a pkill wine and pkill exe. That might have fixed it.

---

