---
title: "Password problems."
date: 2009-10-01
forum: x86 64-bit Users
---

### Post by Unholii on 2009-10-01
Hey, i have problems changing password.

I type "passwd mika" (mika is my login account.) And i don't have any password on it and now when i have to enter my password, i dont type anything and only press enter, nothing happens. It doesn't do anything.

I'm going to post SS soon.

EDIT:: Yes it's finnish.

EDIT2:: Can someone tell me how to change unix password?

EDIT3:: And because i don't have password, nothing works.
> 
mika@cens0r-desktop-linux:~/Työpöytä/Lataukset$ sudo apt-get install libgtk1.2
[sudo] password for mika: 
Sorry, try again.
[sudo] password for mika: 
sudo: 1 incorrect password attempt
mika@cens0r-desktop-linux:~/Työpöytä/Lataukset$ sudo apt-get install libgtk1.2
[sudo] password for mika: 


In that, i first tried to put in root pass, but then i tried to only press enter and that happens.

---

### Post by Arndtwe on 2009-10-01
> **Unholii said:**
> Hey, i have problems changing password.

I type "passwd mika" (mika is my login account.) And i don't have any password on it and now when i have to enter my password, i dont type anything and only press enter, nothing happens. It doesn't do anything.

I'm going to post SS soon.

EDIT:: Yes it's finnish.

EDIT2:: Can someone tell me how to change unix password?

EDIT3:: And because i don't have password, nothing works.


In that, i first tried to put in root pass, but then i tried to only press enter and that happens.

Okay, try this. In  a terminal type this
```
sudo passwd
```
If it asks you to enter your current password, then just hit the return key. It should then prompt you to enter new unix password, then to re-enter your new password. See if this works. If not post your output of these commands.

---

