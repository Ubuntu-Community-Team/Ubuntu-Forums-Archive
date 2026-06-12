---
title: "Sound driver problems - winsound.dll"
date: 2008-02-03
forum: Wine
---

### Post by Bungo Pony on 2008-02-03
I've been trying to get a piece of my favorite audio mixing software to work with Wine. The software loads and seems to work fine, but there's one problem with it: it's not finding the file winsound.dll.

I tried copying it and putting it in the Wine\system32 directory, but it hasn't helped.

The install also went kind of funny, since the software installed itself under the root of the virtual C drive.

Is there any way I could get this thing to work?

---

### Post by Bungo Pony on 2008-02-03
Nevermind, I got it to work!

I took the directory I had installed in Windows and copied it over to Wine's C drive, and it works flawlessly!

---

