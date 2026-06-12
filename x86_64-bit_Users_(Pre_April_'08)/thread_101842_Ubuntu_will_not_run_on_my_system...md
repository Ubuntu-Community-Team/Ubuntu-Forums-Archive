---
title: "Ubuntu will not run on my system.. ?"
date: 2005-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubunick on 2005-12-10
I've listed several problems already while I was actually running ubuntu but now it just freezes when I open an application, and/or just messes up graphically and leaves it pretty much useless.

Here's my system specs:
AMD Athlon 64(BIT) Processor
512MB Ram
120GB
Double-Layer Drive (Lite-On)

That's pretty much all I know about my computer, but regardless, shoudn't ubuntu work fine? It's really frustrating because I accidentally deleted my Windows XP (lack of partition know-how) and I'm left with a non-working linux.  As far as I *know* it's kernal "386".. maybe I need 686? I can't really get it through my computer regardless (on a different computer right now) and I really need to fix this.  Any help with be appreciated! If you want you can PM me.

---

### Post by matthew on 2005-12-10
I'm afraid there isn't enough information here to give a real diagnosis of the problem. If you have your data backed up elsewhere you may find it easier to reinstall Ubuntu. I'm not sure what you did to cause the problems or how to fix them...sorry.

---

### Post by ubunick on 2005-12-10
I didn't do anything to cause the problems honestly -- I reinstalled it twice and it does the same thing.  It's probably and video card probably, but it's on-board (128mb) and I'm not sure what to do to fix it.

---

### Post by rplantz on 2005-12-10
Do you also have a live CD? If so, can you run from that?

---

### Post by ubunick on 2005-12-10
[QUOTE=rplantz]Do you also have a live CD? If so, can you run from that?[/QUOTE]

It freezes up as well.

---

### Post by Buffalo Soldier on 2005-12-10
at which part of the boot-up that it freezes?

---

### Post by ubunick on 2005-12-10
It freezes when I run an application (ex. firefox, GAIM) and the only thing that'll move is the cursor.

---

### Post by Buffalo Soldier on 2005-12-10
Does it freezes up when you're running non-internet applications such as games, text editor or OpenOffice?

As for the kernel, I think you need the "linux-k7" kernel.

When it freezes, are you able to switch to other terminals? (CTRL-ALT-F1)

---

### Post by ubunick on 2005-12-10
I think it does "okay" when non-internet related programs, although it HAS had some "graphical" issues with the OS.  Sometimes programs will work without graphical problems and somethings they won't.  I would show you some pics of what's going on but I'm not at my computer right now.

---

### Post by rplantz on 2005-12-10
[QUOTE=Buffalo Soldier]As for the kernel, I think you need the "linux-k7" kernel.
[/QUOTE]

Perhaps a generic kernel, e.g., 2.6.12-10-amd64-generic, would be the safest one to try?

---

### Post by ubunick on 2005-12-11
[QUOTE=rplantz]Perhaps a generic kernel, e.g., 2.6.12-10-amd64-generic, would be the safest one to try?[/QUOTE]

Isn't that what I downloaded?

---

### Post by mo_x on 2005-12-11
Look like a video card problem.
Can you execute the following command from a terminal and post the output:
```
lspci
```
Als post your /etc/X11/xorg.conf and /var/log/Xorg.0.log as attachments, you may have to change the extension (to .txt) to do so.

---

### Post by ubunick on 2005-12-11
[QUOTE=rplantz]Perhaps a generic kernel, e.g., 2.6.12-10-amd64-generic, would be the safest one to try?[/QUOTE]

How do I get another kernal, exactly?

---

### Post by ubunick on 2005-12-11
[QUOTE=mo_x]Look like a video card problem.
Can you execute the following command from a terminal and post the output:
```
lspci
```
Als post your /etc/X11/xorg.conf and /var/log/Xorg.0.log as attachments, you may have to change the extension (to .txt) to do so.[/QUOTE]

I'll see what I can dooooo.

---

### Post by rplantz on 2005-12-13
[QUOTE=ubunick]How do I get another kernal, exactly?[/QUOTE]

I got mine using synaptic.

You can determine which one you're currently running with the uname -a command.

---

