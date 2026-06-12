---
title: "Unknown application installation errors?"
date: 2008-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by AciD-X on 2008-04-12
could anyone help me?

I've recently installed Ubuntu 7.10 with KDE desktop, installed a few applications, applied all updates and generally prepared the operating system for me to start to learn how to use the linux platform. However, on booting this morning, i encounter several errors trying to install applications using either Synaptic or the Adept Manager, they are as follows:
[I]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I]

An image of this error is available below:

[http://i69.photobucket.com/albums/i43/yournumbersup/error1.jpg](http://i69.photobucket.com/albums/i43/yournumbersup/error1.jpg)

Any help or advice would be much obliged. Thanking you in advance.

Ie.

---

### Post by stoodleysnow on 2008-04-12
I suggest you do what the error message says. Go to K Menu - ?(I don't use KDE much) - Terminal (or Konsole) and type ```
sudo dpkg --configure -a
```
and press enter, and type in your password if it asks you to, followed by enter again.
if this doesn't solve the problem, let us know.

---

### Post by AciD-X on 2008-04-12
Sorry if I come across as a complete newbie, I've been an IT Manager in windows based networks for 3 years and recently switched to Ubuntu myself to get a feel for the much talked about open-source O/S.

However, I believe that has solved the problem, i will attempt to install more packages of my choice now and see if the same errors occur.

Thanks for your help :)

---

### Post by AciD-X on 2008-04-12
Working smoothly once more.

Many thanks, enjoying using this Operating System very much so at the moment, help like that and so quickly too, only makes me experience more worth while :)

---

