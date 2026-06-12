---
title: "Automatix and Easy Ubuntu"
date: 2006-02-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by YellowHat on 2006-02-26
For AMD 64? Is there a tutorial where I can learn how to use it?

---

### Post by GrammatonCleric on 2006-02-28
Automatix does not support 64bit...yet.  At least that's what it says at the very top of the the Automatix posting.

[http://ubuntuforums.org/showthread.php?t=66563]("http://ubuntuforums.org/showthread.php?t=66563")

---

### Post by seannyob on 2006-03-03
[QUOTE=YellowHat]For AMD 64? Is there a tutorial where I can learn how to use it?[/QUOTE]

I just installed Ubuntu Amd64 and ran EasyUbuntu.  Flash and Java might not work; binary codecs might not work as they're 32 bit, but I installed them anyway because DiVX was listed among them (it works fine) but other than that EasyUbuntu worked like a charm for me.

Steps:

For this you will need python, wget, bunzip2, and tar.
Please make sure you shut down synaptic and that no apt is running when you begin this process.

```

$ cd ~/Desktop
$ mkdir easyubuntu
$ cd easyubuntu
$ wget http://easyubuntu.freecontrib.org/EasyUbuntu-latest.tar.bz2
$ bunzip2 EasyUbuntu-latest.tar.bz2
$ tar xvf EasyUbuntu-latest.tar
$ sudo python easyubuntu.py

```

After that check the boxes of things you'd like to install, be patient, and you're done.

:D

---

### Post by Nubus on 2006-03-22
0o0o Luckly I ran into your post the EasyUbuntu works like a charm (temperarly) as for now I'll use this untill Automatix support my AMD64 ](*,) 


Thanks Seannyob! :KS

---

### Post by ezphilosophy on 2006-03-23
[QUOTE=GrammatonCleric]Automatix does not support 64bit...yet.  At least that's what it says at the very top of the the Automatix posting.

[http://ubuntuforums.org/showthread.php?t=66563]("http://ubuntuforums.org/showthread.php?t=66563")[/QUOTE]


When you say "does not support", specifically, what do you mean?  It will not work at all?  Some things won't work/install?  If so, which parts?  

I will get a 64 bit processor soon.  Just want to be ready in advance.  I love Automatix.

---

### Post by ezphilosophy on 2006-03-23
[QUOTE=GrammatonCleric]Automatix does not support 64bit...yet.  At least that's what it says at the very top of the the Automatix posting.

[http://ubuntuforums.org/showthread.php?t=66563]("http://ubuntuforums.org/showthread.php?t=66563")[/QUOTE]


When you say "does not support", specifically, what do you mean?  It will not work at all?  Some things won't work/install?  If so, which parts?  

I will get a 64 bit processor soon.  Just want to be ready in advance.  I love Automatix.  :)

Edit:  Hmm... seems that got posted twice.

---

