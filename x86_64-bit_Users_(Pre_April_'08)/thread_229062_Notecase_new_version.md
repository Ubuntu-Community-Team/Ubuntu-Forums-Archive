---
title: "Notecase new version"
date: 2006-08-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by code-breaker on 2006-08-03
I am new to linux/ubuntu. 

I'm trying to compile a program from source, but I'm having trouble. The author was kind enough to reply to my email stating that I need the following installed to compile:

- gtk2-devel
- gnome-vfs2 (optional, can be switched off in the config file)

I don't find either of these in synaptic. Any suggestions?

---

### Post by Kilz on 2006-08-04
> **code-breaker said:**
> I am new to linux/ubuntu. 

I'm trying to compile a program from source, but I'm having trouble. The author was kind enough to reply to my email stating that I need the following installed to compile:

- gtk2-devel
- gnome-vfs2 (optional, can be switched off in the config file)

I don't find either of these in synaptic. Any suggestions?

Try 
libgtk2.0-dev
libgnomevfs2-0 
There is also a dev file for libgnomevfs2-0. Most of the time in compiling you need dev files. You might want to just add it.
When you search the file names may not be exactly like someone gives you. Better to widen the search. Instead of searching for "gtk2-devel" wich looks like one word to search use "gtk2 devel".

---

