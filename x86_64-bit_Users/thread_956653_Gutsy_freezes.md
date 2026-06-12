---
title: "Gutsy freezes"
date: 2008-10-23
forum: x86 64-bit Users
---

### Post by babujbf on 2008-10-23
Hi I had this problem with Hardy so I switched back to Gutsy but it is still there.

My computer freezes at startup and randomly freezes all the time when I am surfing the web or what ever. Ive read people have this problem, and some say it might be graphics card, and for graphics I tried all drivers for my NVIDIA I first tried restricted, then ENVY and lastly I built it myself and I still get the same thing. Others post that it might be the wireless card drivers, I have it running on restricted because D-Link does not have linux drivers for it. 

There are also threads like [http://ph.ubuntuforums.com/showthread.php?p=4338552](http://ph.ubuntuforums.com/showthread.php?p=4338552) that say is something about putting the splash screen on quiet or something... I don´t understand I am a newbie lol.

Anyways guys help me out! Thanks

---

### Post by Yellow Pasque on 2008-10-23
Random freezing is often a symptom of bad memory (or an inadequate PSU). Boot into memtest86 through the GRUB menu when you first turn on your PC and let it run for a while. The best time to do this is when you're going to bed or when you're leaving your computer alone for a while

---

### Post by statesec on 2008-10-23
I had a smiliar problem with Hardy 64bit and it would get worse when the CPU utilization went up.  The system would just randomly freeze every so often for 5-10 seconds.  It would go from intermitttent at low CPU utilization to fairly frequent at high cpu utilization.  I tore my hair out trying to figure it out.  Even an absolutely clean install of Hardy with no Nividia drivers being used did it.  I tested my RAM, swapped out sticks from another PC it still happened.  I reinstalled Hardy three times trying different things to no avail.  Finally I tried Debian Lenny 64bit and it worked and works prefectly.  Given the fact that Debian does not cause this issue I can only assume there was some conflict with Hardy and my hardware (AMD x2 and a Asrock Nivida 7050).

---

### Post by babujbf on 2008-10-24
well I didn't finish the test because I needed the computer for school, but I did leave for 17 hours and it did 35 test with no errors, so I don't know... My computer is a Intel Pentium D processor, NVIDIA GEFORCE 8500 GT. 

any ideas?

---

