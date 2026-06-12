---
title: "Cannot start new display when switching users"
date: 2008-12-20
forum: x86 64-bit Users
---

### Post by bford16 on 2008-12-20
On my laptop (hpdv8110us, Xubuntu 8.10 clean install, ATI Radeon Xpress 200M, proprietary fglrx installed), when I try to switch users, I get this error.

"Cannot start new display.  Perhaps the X server is not configured properly."

If I try a second time, I can switch users without any problem.

I have gnome-screensaver installed and running, so I can switch users just like in gnome.

Any ideas to help would be welcome.

---

### Post by diablozx9 on 2009-01-07
BUMP.
I have similar issue but, doesnt always work on second try

---

### Post by Yashiro on 2009-01-07
Driver bug most likely. Just let it go or try the open source driver if you want to test it out.

---

### Post by Arup on 2009-01-08
Turn off compiz desktop effects and enable metacity, your problem would be over.

---

### Post by diablozx9 on 2009-01-10
I didnt know how to turn on Metacity but
when I turned off desktop effects, I could switch users.
However, My firefox window would ope behind
my top Gnome banner making it impossible
to move.

---

### Post by Arup on 2009-01-10
> **diablozx9 said:**
> I didnt know how to turn on Metacity but
when I turned off desktop effects, I could switch users.
However, My firefox window would ope behind
my top Gnome banner making it impossible
to move.

alt+f2 type gconf-editor navigate to apps>general>metacity and turn on composting manager.

---

### Post by diablozx9 on 2009-01-10
interesting.
I have no "general" under Apps.

---

### Post by Yashiro on 2009-01-11
That's bad advice. Don't enable Metacity compositing, it's buggy and slow and wont 'fix' anything.

The missing Firefox border is a common issue. Look for threads about it on the forum.

---

### Post by altruic on 2009-01-21
I found this post because I had a similar issue, except it would not resolve itself.  This started today, but it wasn't until I saw this post that I remembered installing some new drivers that Ubuntu wanted yesterday.  I switched to the proprietary NVidia video driver, rebooted, and now all is well.  I can only assume that something installed yesterday broke this.  Thanks for the suggestion, Yashiro.

---

### Post by Dareajoe on 2009-01-22
my computer wont let me switch users while staying on one user. how can i get multiple users on my computer without signing off?

---

### Post by Arup on 2009-01-23
Metacity is far from buggy, in fact it runs better than Compiz, there are several sites discussing metacity as a viable option for those who lack the video horsepower to run compiz. The switching session bug is common for embedded Intel video chips and the only workaround is turning off compiz and enabling metacity for effects. Sites like Tombuntu, Ubuntu-Geek etc. as well as pyshocats all have tutorials recommending metacity and nowhere have I seen any bugs. I personally run it on my laptop as I have Intel graphics and not only is my system response quick, I have absolutely no bugs.

---

