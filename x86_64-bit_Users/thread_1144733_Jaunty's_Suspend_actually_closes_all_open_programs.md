---
title: "Jaunty's Suspend actually closes all open programs"
date: 2009-05-01
forum: x86 64-bit Users
---

### Post by Shrikaant on 2009-05-01
When i Suspend my ubuntu 9.04, it does standby and the power light also indicates the same by blinking.

But when i resume from standby, after entering my username and password i find that all the programs i left open have been closed. Its as if ubuntu logs me out before continuing the standby...

Is this the expected behaviour? How can i solve this? :confused:

---

### Post by bford16 on 2009-05-01
It sure sounds like your computer is shutting down, not suspending. When I suspend my laptop by closing the lid, the screen goes blank, then dark, then the computer powers down (mostly), and the power light blinks. When I open the lid, the system resumes with a password prompt.  After I enter the password, all my programs are right where I left them.

Go to System>Administration>Log File Viewer, and take a look at 'kern.log.'  You should see messages about suspending and waking.  If you don't, then your computer is not really suspending.  It might be hibernating instead, or just shutting down.

---

### Post by Shrikaant on 2009-05-01
Hello bford16,

i just checked the kern log data and i can see suspend and wakeup events taking place. [See attachment where the suspend starts at 15:34]

And as i mentioned earlier, the power led blinks, it shows that the OS is actually doing some kind of standby but unfortunately, it is unable to restore back the running processes...

Hibernate just hangs my machine... i had standby atleast, but now thats also gone... :(

---

