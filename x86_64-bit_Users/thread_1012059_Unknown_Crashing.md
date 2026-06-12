---
title: "Unknown Crashing"
date: 2008-12-15
forum: x86 64-bit Users
---

### Post by Goda on 2008-12-15
I'm running 8.04 64-bit. I was having trouble with Amarok, Flash 10 64-bit alpha, and Skype sharing the sound card, so I installed pulse audio. A couple of days later my mouse, keyboard, screen, and sound froze. Also my caps lock and nums lock lights were flashing. I have to hard reboot to get out of it. I'm not sure what to look for in the logs but nothing seemed unusual. This crash may happen several times in a day, or not at all. I also installed 8.10 64-bit on another partition, ran updates, and installed the three programs mentioned above. While I was shutting down it froze like that again.

---

### Post by bford16 on 2008-12-16
I'm no expert, but I would place my bet on Flash 10 64-bit alpha.  When software is released as alpha, that means it is so buggy that a beta cannot be made to work.  Alpha's are for debuggers and people who don't mind having to fix their computers...

---

### Post by Goda on 2008-12-16
Yeah I was thinking it was the alpha, or a combo of the alpha and the pulse audio. The thing is it can happen without Firefox even running.

---

### Post by luke_lukem on 2008-12-16
Hi all,

I'm experiencing the same kind of crashing.

Sometimes it's a hard freezing, not responding to Ctr-Alt-BackSpace nor the ACPI power button, just hard reset.
Today only the gnome bars stopped working, but the window manager still worked: Alt-Tab responded fine, but the applications bar did not.

I've been reading the logs, but i cant find any error or kernel panic that could point out the cause.

My system is Ubuntu 8.10 x64, also with pulseaudio and adobe flash 10-a

¿Does anyone else have this issue as well?

Thanks for your time.

---- edit: 2008-12-17 -------

Maybe i'm closer to find one crashing's cause. Today, i hit restart after a synaptic update, and i was asked to kill gnome-panel because it was not responding. I don't know if it's the only cause, maybe the flash 10-a is still messing with things.
-------------------------------

---

