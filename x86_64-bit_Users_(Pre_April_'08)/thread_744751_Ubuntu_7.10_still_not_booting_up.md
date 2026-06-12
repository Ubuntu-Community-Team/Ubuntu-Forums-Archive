---
title: "Ubuntu 7.10 still not booting up"
date: 2008-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sidereus on 2008-04-03
Hello everyone,

Now I have just installed ubuntu 7.10 on my laptop. It is a Win Xp/Ubuntu dual boot.

The installation worked fine and np loading up the first time.

I think installed the required files for my modem, wifi card and ATI vid card.

Now i have read on the forums that there have been problems related to the splash/nosplash option in the grub menu file.

I have changed the 2 locations in the file from splash to nosplash, however it still does not boot.  Everything seems to load fine ( I get [ok] with everything) but when it gets to loading boot info, it just hangs and never loads up.

I would like to get this fixed, anyone run into this before?

---

### Post by NullHead on 2008-04-05
You should explain to us exactly whats not happening. Like an error message or something like that.

---

### Post by Sidereus on 2008-04-07
Thanks for the reply.  

I was able to get this resolved by removing the slash and quiet options from menu.lst

Since they have been removed, I boot up very quickly and everything works (just no splash screen) but that really doesn't bother me.

---

