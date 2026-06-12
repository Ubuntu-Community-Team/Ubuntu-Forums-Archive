---
title: "Quick Question About Using Wine with E-Sword"
date: 2017-06-23
forum: Wine
---

### Post by cjreynolds on 2017-06-23
Greetings!

I'm a prodigal son - used to use [Linux/Unix/Xenix] years ago, but stopped using it and forgot everything I knew...

I have installed Lubuntu on a friend's Win XP laptop - dual-booted with the existing OS. He already had E-Sword installed in XP - Do I need to install it in Ubuntu in order to use it with Wine?

I know this is an embarrassingly stupid question, but as I said, I've forgotten everything I knew about Linux :/

Thanks for your patience,

joe

---

### Post by Bucky Ball on 2017-06-23
> **cjreynolds said:**
> He already had E-Sword installed in XP - Do I need to install it in Ubuntu in order to use it with Wine?

Welcome. Yes ... ish. You need to install Wine in Ubuntu then install it through Wine as far as I know, but using the version installed in XP will definitely not work. XP is not running when Lubuntu is and vice versa. 

WineHQ is where you check for how well apps work with Wine, and [e-Sword appears to work fine]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=1341").

---

### Post by sccman on 2017-07-08
I mean theoretically you *can* run E-Sword through the XP partition using Wine, as long as you have ntfs-3g installed and the XP partition mounted. I run games in a separate partition that I share with Windows, and they run my games fine given Wine runs them as is. I'm only worried about Lubuntu changing the XP partition and somehow hurting XP, but I haven't heard of that happening.

---

