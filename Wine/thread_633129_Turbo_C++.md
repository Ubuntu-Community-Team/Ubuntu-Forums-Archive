---
title: "Turbo C++"
date: 2007-12-06
forum: Wine
---

### Post by subs on 2007-12-06
i have this really old(the era of windows 2.0) version of borland turbo c++ for windows.... i wanted to run it on ubuntu with wine..... when i try it i get this error message.....

> subho@Nebu:/media/sdb1/TC/BIN$ wine TC.EXE 
Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.
err:module:MZ_DoLoadImage insufficient DOS memory
winevdm: can't exec 'E:\TC\BIN\TC.EXE': error=8

this particular app works on the windoze xp i run.....  so i set my wine configuration to WINDOWS XP in the wine configuration window

i have tried all the lower version of windows .... right upto the windows 2.0..... nothing seems to work:(:(

---

### Post by sonofusion82 on 2007-12-06
hmm.. I have not really use dosemu for a long time, but perhaps you can try dosemu, it might emulate DOS better than wine.

---

### Post by subs on 2007-12-06
dosemu isnt working with it either!!!

it gives me a screen saying dosemu was successfully booted and then conks off

---

### Post by ChaiTan on 2007-12-06
I use dosbox for TC++
its runs fine
except that the Ctrl-f9 shortcut in tc is also the shortcut for killing dosbox

---

### Post by subs on 2007-12-07
> **ChaiTan said:**
> I use dosbox for TC++
its runs fine
except that the Ctrl-f9 shortcut in tc is also the shortcut for killing dosbox
when i try to run the TC.EXE file in dosbox.... it just goes to anewline and the cursor blinks.... nothing else happens!!

---

### Post by Sukarn on 2008-01-06
> **ChaiTan said:**
> I use dosbox for TC++
its runs fine
except that the Ctrl-f9 shortcut in tc is also the shortcut for killing dosbox

Press Ctrl+F1 to activate the dosbox keymapper (as it says in the welcome screen), and then delete or change the key for killing dosbox from there.

---

### Post by mail.prabal on 2010-02-08
although turbo c++ works fine with dosemu but it could not run the program....it compiles everything but does not run anything..

---

### Post by x33a on 2010-02-08
> **mail.prabal said:**
> although turbo c++ works fine with dosemu but it could not run the program....it compiles everything but does not run anything..

Try running it under virtualbox.

---

