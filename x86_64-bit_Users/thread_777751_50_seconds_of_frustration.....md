---
title: "50 seconds of frustration...."
date: 2008-05-01
forum: x86 64-bit Users
---

### Post by Skweek on 2008-05-01
Hi all,

I've recently install Hardy 64 on my Dell 1720 lappy and I'm  extremely pleased with the result. Except for one thing... when I select "Quit" from the System menu, I have a wait of 50 seconds before the options box (logout, restart etc.) displays.

Anyone else have this problem?

B

---

### Post by agim on 2008-05-01
that is a strange one. Here are some workaround commands. It might be quicker from the command line.

logout
Crtl-Alt-Backspace

shutdown
sudo shutdown -h now

reboot
sudo reboot

I know this isn't what you are looking for, but until you find a solution, at least you won't have a 50 second wait.

---

### Post by Skweek on 2008-05-01
Hi Agim,

Yeah, I do all of those things, and in the grand scheme of things this problem isn't really a problem.  It's just a little iritating when I forget (due to the fact that if I do click Quit, the the desktop is totally unresponsive), which means I end having up going to TTY1 and doing it from there instead. Grrrr...

---

### Post by agim on 2008-05-01
Yeah, I can imagine its pretty frustrating. What version of Ubuntu do you use?

---

### Post by Skweek on 2008-05-01
I'm using Hardy 64 - (and lovin' it!)

---

### Post by phoenix_abhi on 2008-05-01
> **Skweek said:**
> I'm using Hardy 64 - (and lovin' it!)

Man I will suggest u to switch off the CCSM or compiz fusion manager, GL desktop etc. Keep u r visual effect to minimum and try again

---

### Post by Skweek on 2008-05-01
Pheonix, you're a star.  Disable CCSM and the problem goes way!
However I can't give up compiz, so it's terminal reboot/shutdown for me.

Many thanks

B

---

