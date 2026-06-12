---
title: "Getting Rift to work on Ubuntu 12.04"
date: 2012-06-02
forum: Wine
---

### Post by Talann on 2012-06-02
I've been trying to get Rift to work on Ubuntu 12.04 all day today, and I  can't get it to work. 

I can get to the launcher using Crossover, but it says the login  request was invalid. :(

Any ideas?

---

### Post by skalrynd on 2012-06-08
I did this to successfully get the installer to update.  I'm waiting for a complete update before attempting to log into the game as it failed on me after getting past this point.


Close all instances of any patcher.

Run this command:

sudo echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope

Try running patcher again. Ths should do the trick. 

Original thread:
[http://forums.riftgame.com/rift-general-discussions/tech-support/317275-2016-login-error-riftpatch-cfg-verifysslcert-false-didnt-fix.html](http://forums.riftgame.com/rift-general-discussions/tech-support/317275-2016-login-error-riftpatch-cfg-verifysslcert-false-didnt-fix.html)

---

