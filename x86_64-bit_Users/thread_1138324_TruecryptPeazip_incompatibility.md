---
title: "Truecrypt/Peazip incompatibility"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by diw on 2009-04-26
Until a few minutes ago I was the proud operator of a pristine 64 bit jaunty system with all the bells and whistles ringing and blowing.  True crypt (64bit) was working wonderfully ....... until I did a forced install of 32bit peazip using the command

[COLOR="Red"]sudo dpkg -i --force-architecture peazip_2.5.1.LINUX.GTK2-2_i386.deb[/COLOR]

Peazip works great but when I try to open a truecrypt file my system freezes totally.  I have reinstalled truecrypt but it still freezes.  I then tried to uninstall peazip using the following command

[COLOR="Red"]sudo dpkg --remove peazip_2.5.1.LINUX.GTK2-2_i386.deb[/COLOR]

but I get the error message:

[COLOR="Red"]dpkg: you must specify packages by their own names, not by quoting the names of the files they come in[/COLOR]

Its a pity I didn't take notice of a web post warning against the dangers of forcing a 32 bit install on a 64 bit system but there you go!

Ant advice would be welcome

---

### Post by diw on 2009-04-26
Just realised the error of my ways.  It should have been just

sudo dpkg --remove peazip

and it has now uninstalled.

---

### Post by diw on 2009-04-26
This is getting embarrassing.  I was wrong by saying that there was an incompatability.  The problem was nothing to do with peazip, but was due to compiz.  Truecrypt and compiz don't mix on my machine

---

### Post by ebug on 2009-06-26
damn! thanks for the hint! removing compiz fusion solved my problem. i upgraded to jaunty 32bit and 64bit, but when i try to mount truecrypt file, the whole system just freezes until i tried ur tip. now im trying to reinstall compiz now........................ hohohohohohohohohohoohohooooooooooo........it worked!!!!!! no more freezing!!!!!!!thanks a lot!!!!!

---

### Post by ebug on 2009-06-26
damn! i restarted my pc to find out once and for all if it really solve the problem......NO! it freezes the pc when i try to mount a trucrypt. But one thing is for sure, trucrypt and compiz conflicts on jaunty. anyway thanks to wid for the hint. at least now i know whats going on. I just dont know how to fix this permanently.

---

