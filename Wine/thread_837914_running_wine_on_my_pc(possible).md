---
title: "running wine on my pc(possible?)"
date: 2008-06-23
forum: Wine
---

### Post by drzanju92 on 2008-06-23
i want to know if i can run wine on my cpmpaq 2002 pc. it has 256 mb of ram :(. using ubuntu hardy heron with lxde.

---

### Post by Victormd on 2008-06-23
There's no reason why you shouldn't be able to. However, the limitation lies on the programs you intend to install under wine considering that you have only 256MB of RAM.

---

### Post by drzanju92 on 2008-06-23
i want to use it for gameboy advance emulation and virtual dj player

---

### Post by drzanju92 on 2008-06-23
forgot to add in xp

---

### Post by Victormd on 2008-06-23
You would have to check what the memory requirements are for gameboy advance emulation and virtual dj play.

What do you mean by "forgot to add in xp"?

---

### Post by drzanju92 on 2008-06-23
that was before i knew you didn't need windows to run files on wine. im having trouble running things on wine i right click on the exe. file and tel it to rune on wine but nothing happens. Its not in my applications so i cant get to it through there.

---

### Post by yatesl on 2008-06-23
Do you have the latest WINE installed?  If so, you should be able to double click the exe's, and they'll load in WINE automatically.

---

### Post by FlyingIsFun1217 on 2008-06-23
> **yatesl said:**
> Do you have the latest WINE installed?  If so, you should be able to double click the exe's, and they'll load in WINE automatically.

And if not, it might be because the library cannot handle the program.

Open a terminal, cd into the program directory, and then type 'wine ./program.exe'. That should output all errors.

FlyingIsFun1217

---

