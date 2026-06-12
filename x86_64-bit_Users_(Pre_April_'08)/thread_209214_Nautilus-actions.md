---
title: "Nautilus-actions"
date: 2006-07-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by c2483 on 2006-07-04
I can't seem to find a 64 bit version for dapper

---

### Post by atoponce on 2006-07-04
[quote=c2483]I can't seem to find a 64 bit version for dapper[/quote]
A 64-bit version of what?  Do you mean the [AMD64 version of Ubuntu]("http://mirror.cs.umn.edu/ubuntu-releases/6.06/")?  Your title says "Nautilus-actions", so I am really confused about what you are looking for.  Please be more specific.

---

### Post by MetalMusicAddict on 2006-07-04
"Nautilus-actions" is a front-end for "Nautilus-scripts" Its an app he's looking for. I cant help though. I dont run 64-bit.

---

### Post by atoponce on 2006-07-04
[quote=MetalMusicAddict]"Nautilus-actions" is a front-end for "Nautilus-scripts" Its an app he's looking for. I cant help though. I dont run 64-bit.[/quote]
Ah. I see.  It still would've helped if he were a bit more specific.

---

### Post by jkwarras on 2006-07-05
There's a version of nautilus-actions for dapper amd64, I think I get it from the repository.

---

### Post by jkwarras on 2006-07-07
Anyone knows how to add an action that deletes a file/firectory as root? I'll appretiate some help :)

---

### Post by jkwarras on 2006-07-11
> **jkwarras said:**
> Anyone knows how to add an action that deletes a file/firectory as root? I'll appretiate some help :)

Ok, I've finally found how to do this:

gksudo

parameters: "rm -R %M"

It can delete both files and directories as root, and by-pass trash.

Use it at your own risk :)

---

