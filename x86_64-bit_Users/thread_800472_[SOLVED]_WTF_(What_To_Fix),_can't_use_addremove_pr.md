---
title: "[SOLVED] WTF (What To Fix), can't use add/remove programs anymore, nor package manage"
date: 2008-05-19
forum: x86 64-bit Users
---

### Post by DJSchmidty on 2008-05-19
Grrr...

K, i'm trying to learn here guys, gimme a break.

So i'm installing a wine program (one that helps with the dvd copy process), and I goto go back to the add.remove programs to look for a dvd authoring tool or something.  I find one, but when I goto install it through the add/remove programs, it hangs up and just sits there doesn't do anything...  I don't know what I did, but i'd hate to have to re-install the os AGAIN... (Although, I know that i'm just learning here, i mean i already installed it about 8 times on this machine cause of errors that I couldn't figure out how to recover from)

But this time I wanna fix it, not just re-install the OS..

So how can I diagnose this problem>

(BTW, i'm using ubuntu 64-bit)

thanx

(Also, BTW, i notice a window appear on the bottom, like the minimized bar, and it says: "starting administration...." something, I can't read all of it, then it goes away but the add/remove application window is still dead, just get an hour glass.)

---

### Post by tamoneya on 2008-05-19
go into terminal (applications -> accessories -> terminal) and type```
sudo apt-get update
sudo apt-get check
```Post any errors you get and then if you are error free try the add/remove program again.

---

### Post by DJSchmidty on 2008-05-20
wow, don't know how that fixed it, but it did!!!

Thanx dude!

So why did this happen so I know for next time
(Recently converted, and utterly sick of, windows dude)

---

### Post by tamoneya on 2008-05-20
no real reason to it.  This first makes sure your repositories are up to date by checing the servers (update) and then it checks to see if there are any broken dependencies(check).

---

### Post by ASULutzy on 2008-05-20
I know this is set to solved, but I noticed you said you were using wine to install a DVDcopy program, and there's no need to do that.

There are several applications that facilitate this in Linux, check out mencoder (command line), and maybe acid rip? 

I use mencoder for everything, but I imagine there are others who could suggest good ripping/transcoding apps, I'd certainly be open to a suggestion as anytime I can save keystrokes from mencoder is good news to me:)

---

### Post by DJSchmidty on 2008-05-21
Damn it, it happened again, and this time the two commands aren't clearing it out!!!!

---

