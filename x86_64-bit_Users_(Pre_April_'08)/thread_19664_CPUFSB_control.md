---
title: "CPU/FSB control??"
date: 2005-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by blinksilver on 2005-03-13
I don't even know if this is possible, but it would be really cool if it was, seeing as i have been trying to do this for month under windows, have gotten close but not there.

i have a mobile athlon64, with throttling which ubuntu handles well, but, i wish to tweak it some,

when my CPU Hit 800MHz it is running at about .950V, but after extensive test, i have found that my CPU is stable at .825V at 800MHz, which isn't a big deal when its plugged in, but in laptop mode that mean extra minutes which i could use, so part one would be is there a way to get powernowd to do this?

the other half is that again after a fair bit of testing i have found that my CPU will OC to 2100MHz without porblems, so i would like to utilize this, see that it would be a performance boost of almost 15%


so what i would like to do is have my laptop drop it voltage down to .825V when i am it battery mode, and the FSB go up to ~238, which will take moe to 2100MHZ when i am plugged it.

this would al be done automatically of course, anyone have any ideas, or do i have to make a app myself, assuming that i can figure out how,

---

### Post by Bicet on 2005-03-14
[QUOTE=blinksilver]I don't even know if this is possible, but it would be really cool if it was, seeing as i have been trying to do this for month under windows, have gotten close but not there.

i have a mobile athlon64, with throttling which ubuntu handles well, but, i wish to tweak it some,

when my CPU Hit 800MHz it is running at about .950V, but after extensive test, i have found that my CPU is stable at .825V at 800MHz, which isn't a big deal when its plugged in, but in laptop mode that mean extra minutes which i could use, so part one would be is there a way to get powernowd to do this?

the other half is that again after a fair bit of testing i have found that my CPU will OC to 2100MHz without porblems, so i would like to utilize this, see that it would be a performance boost of almost 15%


so what i would like to do is have my laptop drop it voltage down to .825V when i am it battery mode, and the FSB go up to ~238, which will take moe to 2100MHZ when i am plugged it.

this would al be done automatically of course, anyone have any ideas, or do i have to make a app myself, assuming that i can figure out how,[/QUOTE]
 I'm also Interested...

---

### Post by blinksilver on 2005-03-14
well, if know one knows of how to do this, i am going to give coding it a shot, i don't know if i can, but over spring break, (after thurday) i will try, would really perfer not to, might be out of my league

---

### Post by Pse on 2005-03-14
You should look for information on powernowd...which is, as you probably know, the daemon that handles the throttling capabilities of K8s. As far as I can tell (although I probably guessing here), each speed step the CPU makes is programmed by the BIOS, which reads an internal configuration table from the CPU. If you could override that table, you'd be able to get new (and automatical) steps.

---

### Post by blinksilver on 2005-03-14
yeah, it doesn't seem that bad, i am considering using some opensource overclocking  software, and the linux kernels ability to call a command when power states are changed as a starting board, i really don't want to do an overriding myself. 

I was looking at it, and it might go either way, i am still just a basic coder, or at least i still consider myself one, My other option would be to look into the userspace settings the kernel and see what it has to offer.

So anyone know any good overclocking tools for linux?

and yes powernowd is a good spring board, i think i will give its source a good look

---

