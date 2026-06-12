---
title: "processor vs. memory performance"
date: 2009-08-08
forum: x86 64-bit Users
---

### Post by def_mornahan on 2009-08-08
I thought this would be easier to figure out, but I'm having much trouble getting any information off the web, so I'm asking here.  I've had a lot of spare time this week (recovering from having my wisdom teeth out) and got around to a few  things like installing ubuntu on my laptop and starting to rip my old CD collection.  I've got conky installed and was watching my system's performance and I was puzzled by something...

I have an Acer Aspire 5102WLMi, dual processor (1.4 GHz) with 875 Mb memory.  While I'm ripping and encoding CDs with grip+lame and/or playing Space Empires IV on Wine, I notice that the processors will often both be running full tilt, but the memory won't be used above 35 percent, 40 percent at the absolute most.  Why is that?  I thought Linux spread itself across as much memory as possible to try to optimize speed.

I also noticed that the memory test included on the install CD kept flashing an error on test 2 and then quitting completely by about test 5...does that have anything to do with it?  I went ahead and ordered 2 Gb of memory from newegg, but I wonder if it will make any difference.

I know it's got to be a question answered elsewhere, feel free to direct me there and thanks for your patience.

---

### Post by Stunts on 2009-08-08
Hi there!
First a question: How aree you measuring your ram usage?
If you use "free" from the console you can check that most of your memory will be cached.
Then agian, if Memtest86 shows up errors, it's likely that you have some bad memory. You are luck you're not experiencing random crashes...
Sorry, but I guess this is all the help I can offer. I know it doesn't answer your question right away, but I hope it al least points you somewhere. =-)
And, hey, welcome to the forums!

---

### Post by snowpine on 2009-08-08
Processor and ram are two different resources. Tasks like encoding CDs are processor-intensive regardless of how much ram you have.

---

### Post by doas777 on 2009-08-08
ok, first, get some replacement ram. nothing will work reliably until you do.  you could try reseating it (take it out, dust it off, and put it back i) just to be sure, but likely it is corrupt. 

ram usuage should never ever reach 100% if you can help it, so that is a good thing. your CPU is fast enough to do the job without haveing to buffer both sides of the stream. besides, loading a 3.54MB file isn't going to take up more than 3.54MB, so there is no reason that ripping a 12MB wav to a 4MB mp3 would take much ram.

more Ram is only useful if your already running out of it. it's like the ocean; if your swimming in it, it doesn't matter how deep it is, because your just using the top part of it. it does matter if your standing in a kiddy pool though, since it'll take a lot of work to get yourself all wet.

---

