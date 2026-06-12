---
title: "counter-strike 1.6"
date: 2008-01-27
forum: Wine
---

### Post by phoenix5002 on 2008-01-27
I am completely new to linux and I need help getting counter-strike 1.6 working.  I found a tutorial here:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

however I run into problems when I get to the part about compiling Wine from CVS.  I just don't understand what it wants me to do exactly it's slightly confusing to me, when I type:
sudo apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev

in the console I get the error:
E: Couldn't find package x-window-system-dev

please help.  Also if anyone knows if there happens to be a different/better method please share.

---

### Post by CCNA_student on 2008-01-27
I have no idea as how to help you. This is also not a good place to post this. You should go to the Ubuntu Gamers Arena or the Wine part of the forum for help. The people there can help you more. This is not a support area.

---

### Post by p_quarles on 2008-01-27
Moved to Gaming & Leisure.

EDIT: On second thought, this belongs in the Wine forum. You'll get the best advice here.

---

### Post by apparle on 2008-01-27
I am also a new user on linux.
I installed wine directly from repositories.
And now I have installed both counter strike 1.6 and condition zero 1.2
Everything works fine. Except not a sigle letter of text is  displayed. No text is visible

---

### Post by bigb_thedestroyer on 2008-01-28
You probably need the Tahoma.ttf font.  you can find that anywhere, just google it

---

### Post by Sockerdrickan on 2008-01-28
Tahoma.ttf replacement is already there with the WINE 0.9.46 (I think it was) and up

---

### Post by macogw on 2008-01-28
I think the package you need is xserver-xorg-dev since Ubuntu doesn't have x-window-system-dev.  Just take x-window-system-dev out of the apt-get install line, and replace it with xserver-xorg-dev   It's probably just a matter of different distros giving different names to the same package.  xserver-xorg-dev is the main development package for X, though.

---

### Post by phoenix5002 on 2008-01-28
ok, so I did what macogw said and it worked.
However, the next step on that website is to run the WineCVS.sh script using "sh WineCVS.sh".  However, I then get a syntax error:

test: 43: ==: unexpected operator
WineCVS.sh: 48: Syntax error: "(" unexpected

Is there something wrong with the script?

---

### Post by andreykyz on 2010-03-23
I'm make video tutor of [Install Counter strike 1.6 in Linux]("http://frit.su/index.php/%D0%A3%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0_Counter_strike_1.6_Linux")

---

