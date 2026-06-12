---
title: "WIne all messed up"
date: 2008-03-29
forum: Wine
---

### Post by lsearcey on 2008-03-29
I started using wine and used it to play return to Castle Wolfenstein which worked great.  I installed Adobe Acrofat 7 Professional and now all of the wines menus are small and unreadable.  Like this:

[IMG]http://img249.imageshack.us/img249/1958/winescreende9.png[/IMG]
By [lsearcey](http://profile.imageshack.us/user/lsearcey) at 2008-03-29



Any ideas on how to fix this?  I tried uninstalling Adobe Acorbat but i can't read the screens.

Thank You very much for your help

---

### Post by happyhamster on 2008-03-29
Is the text gone or just very small? (Can't see on the picture). 

Either way, you could try this:
[http://ubuntuforums.org/showthread.php?t=733352](http://ubuntuforums.org/showthread.php?t=733352)

---

### Post by lsearcey on 2008-03-29
Very small looks like a bunch of small lines where text should be.

---

### Post by happyhamster on 2008-03-29
> **lsearcey said:**
> Very small looks like a bunch of small lines where text should be.
Ok, then I'm pretty sure the above fix should work.

---

### Post by lsearcey on 2008-03-29
I tried what the link said to do and its still the same. Any other ideas?

---

### Post by lsearcey on 2008-03-29
I tried removing wine with the Synaptiv Package manager and that didn't work either.

---

### Post by happyhamster on 2008-03-30
As a last resort, you can always delete (or move) the hidden .wine folder in your home dir. That means you'll have to re-install all applications you had working under wine.

- Go to Places-->Home Folder and press ctrl-h to be able to see hidden folders and files. Delete or move .wine

- Run winecfg to create a fresh .wine folder and configure wine:

winecfg

---

### Post by lsearcey on 2008-04-04
That seemed to fix it by deleting the .wine folder.

thanks

---

