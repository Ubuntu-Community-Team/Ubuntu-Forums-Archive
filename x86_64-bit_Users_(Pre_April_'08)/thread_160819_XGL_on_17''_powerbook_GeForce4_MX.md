---
title: "XGL on 17'' powerbook GeForce4 MX"
date: 2006-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by n00bWillingToLearn on 2006-04-15
Has anyone gotten XGL to work on a 17'' powerbook? I have tried many of the instructions in other threads to no avail and since I cant seem to find any accounts of this working I would like to know if it is even possible. I have a fresh dapper install and I don't mind experimenting so if anyone has any crazy ideas but are afraid to try them I will also be a willing gunny pig :)

---

### Post by aimislame15 on 2006-04-16
Yeah, I did it on my G5 and now my computer starts up to a white screen, I'm more than alittle annoyed by this, but hey, thats what I get for going with something expiremental eh? Can anyone help me fix this white screen? What can I do to stop it?

---

### Post by n00bWillingToLearn on 2006-04-18
[QUOTE=aimislame15]Yeah, I did it on my G5 and now my computer starts up to a white screen, I'm more than alittle annoyed by this, but hey, thats what I get for going with something expiremental eh? Can anyone help me fix this white screen? What can I do to stop it?[/QUOTE]
Ok I'll take my first stab at trying to troubleshoot someone elses problem. Is this screen before or after the grub bootloader? Which directions did you follow as most that I have seen back up your previous X configuration so that it can be easily restored.

---

### Post by aimislame15 on 2006-04-18
On a mac, its called yaboot... and its after. The computer starts up with the video startup and the orange ubuntu boot screen. But then when its supposed to load GDM and let me log in, it goes straight to a white screen. I've noticed that once at this screen, the computer is completely seized; not even caps lock or num lock light up after this. I don't know if I can do anything else to fix it other than erase and start over.

---

### Post by aimislame15 on 2006-04-19
After about two days, I came to the conclusion that I really wanted ubuntu back. So I set out to rid myself of the white locked up screen of death. It would boot up normally, attempt to launch gdm, and then stall.

After two tries of dropping myself to console from there, I knew it was futile.
I waited until the computer was in the startup phase after launching the kernel but before starting gdm. Did ctrl+opt+f1 and it dropped me to a console successfully for the first time.

I logged in and set my gdm.conf-custom and xorg.conf files back to their original state, and rebooted. 

Success! I am back in ubuntu without lock up. Now can someone please pull out some instructions that work for getting xgl working with radeon 9800 ppc?

---

