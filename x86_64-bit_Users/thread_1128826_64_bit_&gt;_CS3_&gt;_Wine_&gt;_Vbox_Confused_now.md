---
title: "64 bit &gt; CS3 &gt; Wine &gt; Vbox Confused now"
date: 2009-04-18
forum: x86 64-bit Users
---

### Post by noelc on 2009-04-18
Hi,  Ive become very confused. I,m currently running Ubuntu 8.10 32 bit. I,m looking to move to 64 bit, I,m yet to load my CS3 apps as I want to become familiar with Ubuntu before I get to far ahead.

I get conflicting info regarding CS3 on 64 bit 32 bit Ubuntu, Wine, or VB. Ideally I,d like to run Unbuntu 64 bit using Wine (have consider Gimp but not yet convinced).

Once and for all can CS3 run under Wine on Ubuntu 64 bit??

---

### Post by Bakon Jarser on 2009-04-18
Photoshop cs3 probably isn't going to work with wine:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584)

Virtualbox would be your best bet.  Wine gets better with every release and cs3 will probably work in the future but it might be a long while.  You could also dual boot.  You might be taking a performance hit with virtualbox.

---

### Post by John Jason Jordan on 2009-04-18
> **Bakon Jarser said:**
> Photoshop cs3 probably isn't going to work with wine:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584)

Virtualbox would be your best bet.  Wine gets better with every release and cs3 will probably work in the future but it might be a long while.  You could also dual boot.  You might be taking a performance hit with virtualbox.

You could also try Crossover office (codeweavers.com). I just looked and discovered that CS and CS2 have bronze ratings, but CS3 is rated as "known not to work." However, Photoshop CS3 has eight advocates and a total of $644 pledged if Codeweavers can get it to work. Meantime, the only option seems to be either dual boot or run it in XP under Virtualbox or Vmware. I used the Virtualbox route and there is no performance hit.

But even though I have the licenses for XP and CS3 I have yet to use them. I try my best to do all projects in Scribus, Inkscape and the Gimp. It might be a bit faster to use CS3, but the payoff for me is that my files are not locked in a proprietary format.

---

### Post by 3Miro on 2009-04-18
32 vs 64-bit makes no difference here. If a program runs under wine it does either way. If a program runs under virtual machine, it does either way. If it doesn't run at all, it doesn't run at all.

---

### Post by Yellow Pasque on 2009-04-18
If the user is running VirtualBox, I would definitely recommend a 64-bit host if possible for the sake of performance.

---

