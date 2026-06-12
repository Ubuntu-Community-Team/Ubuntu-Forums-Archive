---
title: "64bit Ubuntu on Dell Vostro 1320 (wireless wont enable)"
date: 2009-11-07
forum: x86 64-bit Users
---

### Post by eakron on 2009-11-07
Title says it all. 32-bit works, althought installing it can be messy (LiveCD defaults to command line, gotta startx. Also it wont reboot after install, has to be forcibly shut down). Once you get all the drivers enabled (takes two restarts), it works perfectly.

However, after messsing some stuff up (Ubuntu One wouldn't start anymore, but it's not worth doing a bug report over, probably self-inflicted) I decided to try out 64-bit. LiveCD worked perfectly, didn't even need to manually startx. Wireless worked in LiveCD as well.

But after installing I was unable to activate the drivers. Clicking activate prompted me for password, then just returned to the Hardware Drivers window. No more action. I've tried several times, reinstalled the broadcom driver package, plugged it in and updated, rebooted a bunch of times.

Anyone got an idea?

Dell Vostro 1320
Core 2 Duo 2.2GHz
4GB 800MHz memory

and the BIOS is rev A04.

---

### Post by HappyFeet on 2009-11-08
In the hardware drivers window, you have to highlight the choice before clicking activate. It has happened to me before.

And I suspect the problems you had with 32bit were from a bad disc. Both discs should be essentially the same.

---

### Post by eakron on 2009-11-08
The 32bit install was exactly the same with 2 USB discs and one CD. Worked fine on my other laptop. So I'd say it's a Dell Vostro 1320 specific problem.

And how do I choose wireless drivers without clicking them? They were below graphics drivers. Of course I highlighted them. This is an issue with gtk-jockey, I was hoping someone had a fix or any idea.

---

