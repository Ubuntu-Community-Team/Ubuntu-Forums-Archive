---
title: "Nothing But Static Kubuntu Gutsy"
date: 2008-02-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by xerobasix on 2008-02-26
This is the second time that I have installed Kubuntu Gutsy and lost all sound when I installed flash. I've tried the automatix2 route and used an excellent swiftweasel install guide by kilz. The video in flash works great however there is no sound. Amarok is broken as well now, but instead of complete lack of sound there is static in its place. All mixer settings appear to be normal and I can't find a similar problem on the forums. Any help or direction would be greatly appreciated.

---

### Post by Yellow Pasque on 2008-02-27
Have you tried?:
```
sudo apt-get install libflashupport
```

You could also try using OSS4 instead of ALSA depending on your sound hardware. BTW, what kind of sound card do you have? (run sudo lshw -C multimedia if you're unsure)

---

### Post by khensucat on 2008-02-28
The use of Automatix is still quite controversial, and while there may be some level of cooperation in the future, much has been written of potential system borkage, etc... I have not used it myself, as it does nothing for me that I don't already know how to do quite easily, but it appears to have wreaked utter havoc on many a system, despite apparently having also helped many a new user, hence the controversy:

[http://www.google.com/search?hl=en&q=automatix%2Bdangerous&btnG=Google+Search](http://www.google.com/search?hl=en&q=automatix%2Bdangerous&btnG=Google+Search)

My first impression would be that any error post-Automatix may be potentially unrecoverable, or at least untraceable :-(

---

