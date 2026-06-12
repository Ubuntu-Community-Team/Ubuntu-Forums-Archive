---
title: "Ubuntu Interface problem"
date: 2008-11-09
forum: x86 64-bit Users
---

### Post by kyo007 on 2008-11-09
Hi, i have just installed new ubuntu 8.1 and my UI is very bad, there is one bad bug, is there any way to&#305; fix ?

Thanks.

[ATTACH]91822[/ATTACH]

---

### Post by ajgreeny on 2008-11-09
Do you know which application window is this running at full screen, or don't you have any idea?  It looks as if it is nautilus, but I don't know why it is showing like this.  Do you not see any wallpaper or a normal gnome desktop?

---

### Post by bwhite82 on 2008-11-09
I have this same problem. It is not 64bit specific, as I have now installed 32bit edition and still the same. I'm still trying to figure it out. Do you have an Nvidia card as I do?

---

### Post by Toet on 2008-11-09
[https://bugs.launchpad.net/bugs/99508]("https://bugs.launchpad.net/bugs/99508")

---

### Post by bwhite82 on 2008-11-09
> **Toet said:**
> [https://bugs.launchpad.net/bugs/99508]("https://bugs.launchpad.net/bugs/99508")

Nice find. We must just wait until its fixed or use the workaround suggested, change the title bar theme.

---

### Post by kyo007 on 2008-11-09
I have quadro fx card, and is there any patch for this problem ?

Thnaks.

---

### Post by NullHead on 2008-11-09
Looks like it might go away after disabling compiz. I believe the setting for that is under System>Preferences>Appearance>Visual Effects.

---

### Post by kyo007 on 2008-11-09
I don't have any visual effect but still have a problem ..

---

### Post by teddks on 2008-11-09
The fix I prefer is to just use Emerald, which I've always thought was a superior (if slightly less stable) window decorator.

---

### Post by kyo007 on 2008-11-11
> **teddks said:**
> I prefer is to just use Emerald,

What is it ? is it theme for ubuntu ?

Thanks.

---

### Post by teddks on 2008-11-11
> **kyo007 said:**
> What is it ? is it theme for ubuntu ?

Thanks.

No, it's a window decorator. You can install it and emerald-theme-manager from the repositories, and then set compiz to use it by setting the "command" field in the Window Decoration tab of compizconfig-settings-manager (also installable in the repositories) to "/usr/bin/emerald --replace".

Then, you can set up your theme using the Emerald Theme Manager at System>Preferences>Emerald Theme Manager.

---

