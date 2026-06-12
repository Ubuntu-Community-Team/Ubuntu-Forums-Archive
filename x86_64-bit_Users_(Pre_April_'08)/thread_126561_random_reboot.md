---
title: "random reboot"
date: 2006-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by who_cares on 2006-02-06
For some reason my computer reboots at random.
It happens when I'm using it and when the screensaver is up.

Any way for me to stop this?

---

### Post by sredlich on 2006-02-07
Is it possible that you have a heat problem.  I had lockups with a computer that got to hot.  I added fans.
Of course, you should probably look at your log files to see if the system has left you any messages
about why it rebooted.

Steve

---

### Post by who_cares on 2006-02-07
I have 6 fans in there...
How do I get to the logs?

---

### Post by who_cares on 2006-02-14
well, I think I found the logs:
They were completely empty

Any ideas?

---

### Post by RAOF on 2006-02-14
You could try running a memtest - select it from the GRUB bootprompt (if you don't get a grub bootprompt, press "esc" when the computer is just booting).  Also, if you run windows, does that randomly restart too?  Can you think of anything in common with the times it's restarted (graphics use/background tasks, whatever)?

I had a computer that would randomly restart.  Not very often, at first, but it gradually increased in frequency.  Turns out, the motherboard was slowly dying.

---

### Post by dad311 on 2006-02-16
Maybe you have a bad power supply???  Maybe the power supply doesnt have enough power.

---

### Post by trigg on 2006-02-16
Do you need an extra power line to your video card?  I know that ATI cards usually won't let you boot up with it plugged in, but NVIDIA cards might let you boot up, but just act really unstable. . .

---

### Post by who_cares on 2006-02-21
My video card doesn't have a power line

---

### Post by who_cares on 2006-02-21
[QUOTE=RAOF]You could try running a memtest - select it from the GRUB bootprompt (if you don't get a grub bootprompt, press "esc" when the computer is just booting).  Also, if you run windows, does that randomly restart too?  Can you think of anything in common with the times it's restarted (graphics use/background tasks, whatever)?

I had a computer that would randomly restart.  Not very often, at first, but it gradually increased in frequency.  Turns out, the motherboard was slowly dying.[/QUOTE]
well, all the parts are brand new. and I only have Linux for now.
I hope to get dual boot soon...

I'm usually not using it, I come back from getting a snack and it's booting back up for some reason

---

### Post by RAOF on 2006-02-21
[QUOTE=who_cares]well, all the parts are brand new. and I only have Linux for now.
I hope to get dual boot soon...

I'm usually not using it, I come back from getting a snack and it's booting back up for some reason[/QUOTE]
And have you run a memtest?  Sticks of bad memory do exist ;)

---

### Post by who_cares on 2006-02-21
I'll try that. The amount of memory that gnome claims to have matches what I put in.

---

### Post by who_cares on 2006-02-22
I ran memtest.
It said all of it passed but it seemed to loop around. When I got done with test8 it started over at test1.
All my memory passed on all three loops

---

