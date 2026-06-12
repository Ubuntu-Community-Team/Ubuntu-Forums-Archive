---
title: "old games run too fast"
date: 2008-05-12
forum: Wine
---

### Post by tribunal on 2008-05-12
Hi all!
Some old games run too fast? 
I have found nothing about it in wine's config :(
What can I do?

---

### Post by tht00 on 2008-05-12
What games are they?

If they are DOS, I'd recommend using DOSBox over Wine.

---

### Post by tribunal on 2008-05-12
No, windows 
no SO old ;)
2000-2001-2002
My PC is just quick (core2Duo, hi-end graphics and so on)

---

### Post by noerrorsfound on 2008-05-12
System > Administration > Services
Disable "CPU Frequency Manager"

This is an issue with old games not being designed for multi-core systems.

---

### Post by tribunal on 2008-05-13
Thank you :)
But may be where is a way to turn off one of "cores" ?
Temporary, of course ;)

---

### Post by happyhamster on 2008-05-13
- You can set cpu affinity for core 1 like this:

taskset -c 1 wine program_name.exe

- For more info, see:
[http://linux.die.net/man/1/taskset](http://linux.die.net/man/1/taskset)

- Another thing you might try is enabling the OpenGL sync-to-vblank setting. In case you're using an nvidia card, run:

nvidia-settings

- Choose "OpenGL Settings" and tick the "Sync to VBlank" option.

---

### Post by tribunal on 2008-05-14
Thank you, it works :guitar:

---

