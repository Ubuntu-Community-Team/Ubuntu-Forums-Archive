---
title: "New kernel is killing me!"
date: 2005-10-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by wmcbrine on 2005-10-12
I got a new kernel from Software Updates the other day, and started getting a kernel panic every time I shut down. Is anyone else seeing this? I'm using the amd64-k8 package.

---

### Post by mlomker on 2005-10-12
> Is anyone else seeing this? I'm using the amd64-k8 package.

Nope.  I run the same kernel.

---

### Post by wmcbrine on 2005-10-15
Perhaps this should be merged with "Oct 12 updates killed my Ubuntu!"?

Anyway, new symptom: Yesterday, I tried logging out without shutting down, and I was taken to a black screen, where I couldn't do anything -- no Ctrl-Alt-F1, no Ctrl-Alt-Backspace, etc. However, I could then ssh in from another machine, issue "sudo shutdown -h now" -- and it actually worked, for the first time since the update. The screen stayed blank under power off. (Previously, I'd tried shutting down without logging in, with the same results as before: kernel panic.)

But I guess I'll just move on to Breezy now...

---

