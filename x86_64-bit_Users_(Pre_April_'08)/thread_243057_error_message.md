---
title: "error message"
date: 2006-08-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by gmcm1979 on 2006-08-24
i'm new to this, i get the following error message when opening synaptic package manager

E: Malformed line 77 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.

---

### Post by hajk on 2006-08-24
Well, have you checked the file /etc/apt/sources.list? Just open a terminal and then open this file with the command
"sudo nano -w /etc/apt/sources.list"
and look for things like an extra space that shouldn't be there, etc.

If you can't spot anything, then just copy and paste the contents of that file in a reply message, so that others can have a look at it.

---

### Post by wordsmythe on 2006-08-24
The obvious (probably not really helping) approach:

Yeah, pico (or nano or whatever) that file.  I'd suggest looking at line 77 ;)

---

