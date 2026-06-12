---
title: "x86 Dead? Tired and Frustrated"
date: 2009-06-24
forum: x86 64-bit Users
---

### Post by russ.gould1 on 2009-06-24
In advance i want to say im sorry if there are other threads on this topic, im extremely tired and really frustrated as i dont know much about what im doing/what happened to my comp. I had vista 64bit and just got tired of all the access deniles and wanted a useful 64bit os so i decided to try ubuntu. After installing, and deleting my old windows partition, my monitor now shuts off saying "no signal input" and doesnt even show my bios start-up or anything beyond that. After leaving my comp on for a bit my mouse, a razer one with an led, doesnt light up, so i assume it isnt recognized as connected, as well as my keyboard does not light up. Since my monitor never really turns on i cant see if anything really starts up and i have no clue what to do as when i put another bootable cd in (i have a legit copy of windows xp 32bit) i dont get an option to boot from that. Im completely lost as to what to do and i would reformat my drive with another comp but the one i am on currently doesnt use sata or have any sata slots... Again, any info would be useful.
 
 
asus maximus formula mobo
intel c2d 2.6gh
ocz 4gb ram (2x 2gb sticks)
evga 9800gtx
wd 400g hdd

---

### Post by PatrickVogeli on 2009-06-24
so, if you can't even access the BIOS I think you are in front of a clear Hardware fail. You'll have to troubleshoot it: start making sure it's not some bad RAM stick or the graphic card failing.

---

### Post by bedtime_with_the_bear on 2009-06-24
Does your speaker usually work? If so, do you get any beeps when you switch on the computer?

Also, try unplugging the power cable from the computer, wait a couple of minutes and reconnect it - I've seen many power supplies that get upset and display similar symptoms, and need to be powered down for a while to come back.

I agree with Patrick, it's a hardware issue, but that doesn't mean we can't help :)

As above, try reseating your memory and video card if it's not integrated in the motherboard. Maybe try removing the power cable from the monitor at the same time as the computer.

If you have a spare video card, you could also try swapping it out to test for a bad card.

When you try these steps, please try to do one at a time - that will make it easier to identify the problem.

---

### Post by russ.gould1 on 2009-06-24
Ok well i tried replacing things, and removing my memory didnt do anything different, and turning off my power supply for a little bit didnt do anything different, and after removing my video card i dont really think anything happened differently, but i cant tell because i cant see anything... the only thing i noticed was that after leaving the comp on for maybe 3 minutes without a video card in it the system turned off almost instantly when i hit the power button, aside from the others (without ram and after turning off power supply) where i had to hold the button down for a bit before it shut off. I would imagine an evga card wouldnt completely die after only 9 months of un-overclocked use. I dont have another video card to try with it but i will try to get a friends or something, as the last time i had a problem like this i replaced my video card (last september) only to give it to a friend as a joke and have him still using it today.
 
oh and no i dont have any beeps when my comp turns on and i never have.
 
Any other suggestions?

---

### Post by russ.gould1 on 2009-06-24
I am posting a new reply only because i have basically figured out the problem, but not really.  I forgot i have a little lcd display for my mobo that gives me useful information when booting up and i now find that i have a CMOS error.  Thanks to asus they dont have any info on what to do if my lcd thing says this but i do know now thanks to the manual that CMOSerr means CMOS error.  This is way beyond me and if anyone has any clues on what to do that would be useful, but ill take my problems to the asus forum as well.  The only reason i started here was because i just installed ubuntu so i thought that was the problem.

---

### Post by movieman on 2009-06-24
The CMOS RAM stores the BIOS settings, and can be corrupted and cause boot problems. Check the motherboard manual, normally there's a jumper you can set to clear the CMOS and have the BIOS reset everything to default values.

---

### Post by bedtime_with_the_bear on 2009-06-24
Alternatively, look for the battery - usually a silver disc around 15 or 20 mm in diameter - remove it, wait a couple of minutes and replace it.

---

