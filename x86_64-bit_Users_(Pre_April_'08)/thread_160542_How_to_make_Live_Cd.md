---
title: "How to make Live Cd"
date: 2006-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by namluc on 2006-04-15
If some of you linux whizzes could help me out I'd much appreciate it. Please help me by giving me a step by step guide to making a live cd

Mac mini PPC
OS:  10.4.6

Thanks as I'm a bit lost!:D

---

### Post by oscar on 2006-04-15
I assume you mean downloading and burning the ubuntu live cd?
To download go to [http://www.ubuntu.com](http://www.ubuntu.com) and click "Download" on the menu on the right.
Under "Ubuntu 5.10" select the mirror closest to you.
If you are on a PPC mac mini, you want the "Mac (PowerPC) live CD". Click the link to download the .iso to your desktop, or somewhere you will remember.
When that is done see [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto) to find out how to burn the iso to a blank cd-r(w). I dont have a mac so havent tested this but it looks like it will work.

---

### Post by namluc on 2006-04-15
Thanks Oscar for toking me through step 1

All that worked but I'm now stuck further along the line.

I now have my live boot cd. :D 

However I have tried to boot in a number of ways and none have worked.

Warm and cold boot with apple command pressed has no effect.

Setting the start up disc to be network startup only manages to confuse the computer for a while. i have booted this way with apple command both pressed and unpressed

Any help on this next step much appreciated.
:D

---

### Post by oscar on 2006-04-15
You don't have to make it use network startup. On a PC you have to change the first boot device to cd in the bios, so it checks the cd before checking the hard drive.
From looking at these forums it looks like you have to hold down or press C when booting to make it boot from the CD. Futher than that I am afraid I cant help.

---

### Post by namluc on 2006-04-15
Thanks for your help iv'e got the cd at least. Hopefully i'll be able to work out how to boot it at some point.

---

### Post by oscar on 2006-04-15
Did you see this bit?
[QUOTE=oscar]From looking at these forums it looks like you have to hold down or press C when booting to make it boot from the CD.[/QUOTE]
Have you tried it?

---

### Post by jdp on 2006-04-15
That is exactly how to do it Oscar.  I've done it many times on my G4 Mini when I was testing the Filght 5 LiveCD.  On a Mac, you almost always hold **C** to boot from a CD.

---

### Post by namluc on 2006-04-15
Is that just button c?

---

### Post by jdp on 2006-04-15
Yes, just hold down the **C** key on the keyboard when you either reboot or power on and it'll boot fromt he CD in the drive if it's bootable.

---

### Post by namluc on 2006-04-15
cheers i'll give it a go now i've been pressing the 'c'ommand button all this time!
:rolleyes:

---

### Post by jdp on 2006-04-15
Ah, that's an understandable mistake.  Generally we'd use Cmd or another abreviatin for Command instead of just C, and also Ctrl for Control.

---

### Post by namluc on 2006-04-15
Thanks for your help guys. Its taken me a while but i've finally got it working!! Writing this from inside ubuntu now!!:KS

---

