---
title: "Bonobo error...."
date: 2005-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by alfred on 2005-12-16
I will keep looking for why this happened but all was goign well using XFCE on a 400mhz iBook and then Nautilus and other apps that rely on Bonobo no longer could open.  They error out.
For example Epiphany sias
Epiphany cant be used now due to an unexpected error from bonobo when attempting to locate the automation object.
Like i said it was working great before.  What did I do last.
The closest I can remember is 
One.. Setting up and testing gnome-ppp
Two.. install gnumeric
Though sadly i do not know how close these where to when the problem started happening.
Al
ps...thanks for all the great work on this ppc disto

---

### Post by teripittman on 2005-12-24
My bonobo errors have all come from having the wrong system date and time on the computer. Might double check that.

---

### Post by SyL on 2005-12-26
i had the same error with Warty, 
As teripittman, i concluded at this time that after a druty shutting down due to no batterie left, the uncorrect system time made bonobo unwork. 
For fix, just have to fix the system time ...

---

### Post by alfred on 2005-12-27
We'll I had this happen on three machines...
There are four areas of commonality between all of these machines that to me seem to be important.
ppc
xubuntu
gnome-ppp  (this works fine on ppc with ubuntu not xubuntu at one location)
epiphany web browser
So far I could not solve these.  I now have a testing ppc to see if I can reproduce it a fourth time or try a ubuntu in stall with no ephiphany (which seems to rely on bonobo alot)
This is down the line some...
Al

---

### Post by TheOtherShoe on 2006-11-17
I know this is an old thread, but I have just had the same problem so I thought I would weigh in.

I'm running a PowerBook G4 off of the Edgy install CD. It worked on the first boot, but after rebooting once I got the same Bonobo errors. I was shocked - after running an integrity check on the CD, I couldn't think what I could have changed that would have caused problems. But after reading this thread I  remembered that I did set the clock. Unfortunately, I forgot to set the year, so somehow the computer ended up showing the date as 1904. Thus the problems.

Setting the clock to the correct year fixed everything up nicely.

---

### Post by SyL on 2007-01-25
Right, the clock of your system must be correct else you got this error.
Either you fix it after boot and restart or if you have a double boot with OSX you can change the time within osx as well...

---

