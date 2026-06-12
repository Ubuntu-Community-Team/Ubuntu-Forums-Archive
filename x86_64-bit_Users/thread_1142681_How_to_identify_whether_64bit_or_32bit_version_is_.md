---
title: "How to identify whether 64bit or 32bit version is installed?"
date: 2009-04-29
forum: x86 64-bit Users
---

### Post by pannerrammer on 2009-04-29
Sorry, I've installed (ubuntu gnome desktop) Jaunty on a couple of 386 boxes, and on a 64bit AMD box... but I can't remember if I put the 32bit or 64bit version on the AMD box!

I have probably missed it, but how can I identify which Jaunty is installed on the 64bit AMD box.

:confused:

---

### Post by bobince on 2009-04-29
```
$ uname -m
x86_64
```

(Or -a for more detail.)

---

### Post by slakkie on 2009-04-29
getconf LONG_BIT

For more nifty commands, check out this page: [http://www.unixguide.net/unixguide.shtml](http://www.unixguide.net/unixguide.shtml)

---

### Post by pannerrammer on 2009-04-29
Thanks to both of you. It was the 64bit version.Must remember to lay off the wine!

---

### Post by Robster2 on 2009-05-09
> **pannerrammer said:**
> Thanks to both of you. It was the 64bit version.Must remember to lay off the wine!

I don't think this is right unmame -m tells you what machine you have not if you have a 32 or 64 bit version of Ubuntu.

---

### Post by jespdj on 2009-05-09
> **Robster2 said:**
> I don't think this is right unmame -m tells you what machine you have not if you have a 32 or 64 bit version of Ubuntu.
No, that's wrong, it's the other way around! uname -m tells you if you are running 32-bit or 64-bit Ubuntu. It does not tell you if your processor is 32-bit or 64-bit.

---

### Post by Zer0Nin3r on 2009-05-09
> **pannerrammer said:**
> Thanks to both of you. It was the 64bit version.Must remember to lay off the wine!

What happened to the "Thanks" button?  Thought that was a great way of keeping the forums clean.

---

### Post by jespdj on 2009-05-09
The Thanks button has been removed months ago, when the forums weren't working right and some changes to the forum software had to be made. For some reason it was necessary to remove the Thanks function to keep the forum from getting very slow.

---

### Post by Zer0Nin3r on 2009-05-16
Just saw the [post]("http://ubuntuforums.org/showthread.php?t=1044714").  Next time I'll look harder. :)

---

