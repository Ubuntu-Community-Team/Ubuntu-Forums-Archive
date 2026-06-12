---
title: "[SOLVED] Trouble with Aspire 5920G"
date: 2008-08-31
forum: x86 64-bit Users
---

### Post by rvm4000 on 2008-08-31
I installed the amd64 version of kubuntu 8.04 (with all the updates) in this laptop. I have some troubles:

The graphic card is an ATI Radeon 3470. After the installation the proprietaries drivers were installed.
The problem is that apparently there's no X-Video:
```

xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present

```

I already run *sudo aticonfig --ovt Xv*, without changes :(

Is there something I have to change in the config files? Or just simply this card doesn't support overlay? (I doubt it, there's overlay in Windows)

Most important problem: if I choose the "Exit" option under the KDE menu, the system freezes. This option supposedly should close the X session and start again, but I've got a black screen, with no mouse cursor or anything. The keyboard doesn't work (tried with Ctrl+Alt+Backspace, Ctrl+Alt+Supr, Alt+F1). Another strange thing, the capslock led on the keyboard blinks during this. What does it mean?

Anyway to fix this?

(After searching a little bit, it might be [this bug](http://ati.cchtml.com/show_bug.cgi?id=239))

---

### Post by rvm4000 on 2008-09-01
Fixed the two problems by updating the ATI drivers using Envy!

---

