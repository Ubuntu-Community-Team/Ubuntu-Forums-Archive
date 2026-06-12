---
title: "wine 64bit?"
date: 2007-06-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by kzm. on 2007-06-24
is there any replacement for wine under 64bit? or some unofficial 64bit release?

---

### Post by Ocxic on 2007-06-24
I'm not sure, I think there only 32-bit, wine wich I've been using on my 64-bit system, for a while now, only for utorrent, but everything seems to work fine.

---

### Post by Mr_bleu on 2007-06-24
Yes, there is.  This issue was addressed in a previous post.  Have you been to wine hq?  You'll have to add the repository key.  [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
[B][I]For Ubuntu Feisty (7.04):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

64-bit Users:

Packages for the 64 bit version of Ubuntu Feisty (7.04) are now available, however for users of Debian and older Ubuntus the entries above are for i386 users only. Attempting to use these repositories with a different architecture will result in 404 errors as APT will be looking for files not in the repository.

If you are using an older 64 bit distribution and would still like a working Wine package, there is a relatively easy hack that can be used to install the 32-bit package into the 64-bit distribution and have it function normally. See this page on the Wine wiki for more details.[/I][/B]

---

### Post by Kilz on 2007-06-24
Realize, that even if you install the 64bit package, wine is 32bit. It is a Windows application layer, Windows applications are all 32bit. So Wine has to be 32bit. The 64bit package only makes installing that 32bit application easier, it isnt going to give you any performance increase. It does not in any way install a 64bit wine. 64bit wine would be to run 64bit Windows applications on, they dont exist.

---

### Post by kzm. on 2007-06-25
awesome.. it works. but there are no 64bit win apps? but there is xp64 and vista64..??

---

### Post by Kilz on 2007-06-25
> **kzm. said:**
> awesome.. it works. but there are no 64bit win apps? but there is xp64 and vista64..??

Yes, but very few 64bit windows applications. Its kind of like the opposite of 64bit linux, where we have all but a few applications 64bit and a few 32bit. This is the reason some proprietary applications like Flash as still 32bit. There is no need for it on Windows so the company sees no need to port it yet to 64bit for any os. 
Secondly , while the 64bit versions of XP and Vista exist, its hard to find a computer for sale with them installed. Since there is a low install base companies do not see any potential customers to sell to. Linux's strength in this area is that the source is open. So porting the applications is easy, and not bound by a profit motive.

---

