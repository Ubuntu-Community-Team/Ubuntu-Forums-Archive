---
title: "My Puter crashed half way through"
date: 2007-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by ve3rpm on 2007-10-21
As it stands now, it'll still run, however synaptic won't run, and I'm in limbo.  I can reinstall from the 7.10 disk but I'm fairly certain that it's going to want to reformat my drive.  that will certainly suck.  Is there any way that I can fix this?

---

### Post by ve3rpm on 2007-10-23
when I try to use synaptic, I get this message, and don't know what to do with it.

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by ACLerok on 2007-10-23
Can you start update-manager? 
Can you install anything through apt-get?

What happens if you type: sudo apt-get update and then sudo apt-get upgrade?  What happens if you type sudo apt-get install -f?

---

### Post by bonestonne on 2007-10-23
you can install items through "Add/Remove Programs" in the Applications menu.

you can also install via terminal using "sudo apt-get install [packagename]"

Synaptic is just an easier way of doing it, not necessary.

---

### Post by ve3rpm on 2007-10-25
actually, I couldn't add or remove either, and it just didn't occur to me to use the terminal.  In retrospect I'm a little sheepish.  I just reformatted and reloaded.  Everything is ok now.  Thanx I'll have to spend more time with the terminal.

---

