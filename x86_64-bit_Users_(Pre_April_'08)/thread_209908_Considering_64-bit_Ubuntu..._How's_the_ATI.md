---
title: "Considering 64-bit Ubuntu... How's the ATI?"
date: 2006-07-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Zifnab on 2006-07-05
I've got an Athlon 64 3200+, and I'd to make full use of it. :D 

I installed the amd64 Gentoo yesterday, and the base install went w/o a hitch, but getting ATI's flgrx drivers working with X11 is a bitch. (Hey that rhymes!) I like the level of control over your system you have (and is sort of required of you) in Gentoo, but I need a working GUI.

I've had good experiences with 32-bit Ubuntu in the past... So I must ask, is 64-bit Ubuntu easy to get working with ATI cards (mine is a 9800 Pro)? What sorts of experiences, good or bad, have you had using ATI cards?

---

### Post by Kilz on 2006-07-05
[QUOTE=Zifnab]I've got an Athlon 64 3200+, and I'd to make full use of it. :D 

I installed the amd64 Gentoo yesterday, and the base install went w/o a hitch, but getting ATI's flgrx drivers working with X11 is a bitch. (Hey that rhymes!) I like the level of control over your system you have (and is sort of required of you) in Gentoo, but I need a working GUI.

I've had good experiences with 32-bit Ubuntu in the past... So I must ask, is 64-bit Ubuntu easy to get working with ATI cards (mine is a 9800 Pro)? What sorts of experiences, good or bad, have you had using ATI cards?[/QUOTE]
I would avoid the 8.25.18 drivers now in the repositories like the plauge. They are in my opinion one of the worst drivers ATI has ever made. After installing them some people cant shut down correctly and the computer hangs. Others get no acceleration. You can get 8.26.18 drivers from ATI and [use this install method.]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2") But one thing the howto doesnt say is you may need the headers.  ```
sudo apt-get install linux-headers-`uname -r`

```

---

### Post by clumsychild on 2006-07-13
It's like hell, I really think it is. This is probably the one reason I'll never buy another ATI card is because they are the least flexible things when it comes to Linux. I have a 9800 pro as well and it took me a while to get open gl support, i now do have it using fglrx, but it was an interesting task. If you have any questions feel free, I think I've been through everything.

---

