---
title: "Emerald --replace does nothing"
date: 2009-08-22
forum: x86 64-bit Users
---

### Post by t0mmy_d on 2009-08-22
I've read a lot on Emerald problems, but not found any solution.  I've just installed the x64 version of 9.04 to replace the old 32-bit (which worked fine, even on this new hardware), but emerald won't change the theme when I run "emerald --replace".

I've also tried running it in Terminal to get an error, but it says nothing, just continues to run.

Can anyone be of any help?  Do you need more info?

---

### Post by Arquis on 2009-08-22
Dumb question: have you installed Emerald?
(Sorry, I had to ask...)

If not, write this on terminal:
sudo apt-get install emerald

---

### Post by oldos2er on 2009-08-22
> **t0mmy_d said:**
> I've read a lot on Emerald problems, but not found any solution.  I've just installed the x64 version of 9.04 to replace the old 32-bit (which worked fine, even on this new hardware), but emerald won't change the theme when I run "emerald --replace".


 Do you have compiz running as your window manager? Emerald requires it.

---

### Post by t0mmy_d on 2009-08-23
I have compiz installed, I'm not sure if it is running though.  I don't see it running in the System monitor, I do see Metacity though (which I understand is the default theme manager)

---

### Post by oldos2er on 2009-08-23
Install the package fusion-icon, it will give you a simple way to control compiz, metacity, and emerald.

 In the meantime, check System, Preferences, Appearance, Visual Effects, and make sure something other than None is checked.

---

### Post by t0mmy_d on 2009-08-23
Thanks oldos2er

Selecting "normal" under system preferences worked a treat!

Always the simple solutions that never get mentioned on the instructions!

---

