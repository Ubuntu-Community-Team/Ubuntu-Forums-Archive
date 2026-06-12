---
title: "problem installing 5.10 X64"
date: 2005-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by joeav on 2005-12-04
hey everyone

new to linux, managed to install the live cd before with no problem and decided to go for the full installation.

i get stuck (repeatedly)soon after setting my user name and password(should be annoyingly close to the end, right?), 25 % through a screen that says something of the sort of "setting primary repository" (repeatedly, but somehow im still not sure i got it right.,..) . 

i searched the length of the forum and couldnt find any similar enough thread.

the machine is relatively new, i had windows xp on it before.

amd X64 , 512 ram, 160 GB, nvidia nforce4 k8 triton. dont remember other specs, if critical let me know and i'll find out.

please rush to help, i didnt leave any working os on the machine.

thx!

---

### Post by joeav on 2005-12-04
more info - i was stuck before in the base installation step, but after i redownloaded the iso and burnt it again, it was ok untill the mentioned part. i'm going to try and burn it again lower then X32, but for some reason i dont get the choice from nero so far... it just goes auto into 32.

---

### Post by joeav on 2005-12-04
i'm again running from the live cd to post this-

managed to install through the server option, but its not really something i know how to work with. is there any way i can work around the problem using the server interface? solve it from there? get to the gnome platform from there?

---

### Post by joeav on 2005-12-05
managed to fix it. in case anyone runs into the same problem -

i had a hunch that something with the cdrom is causing the problem, so in the setting user name step i tried pulling out the cd but couldnt, so i selected <go back> to get to the main boot menu, and skipped the apt configuration stage into the grub step, and then it asked me to take out the cd and did a 2 step installation like i read it used to be in the 4.10.   btw - when i selected the cd verifying option it told me it isnt a valid cd... any idea what causes that?

now all is well, trying to get the samba to work, to share files with a windows machine on a network, if anyone can explain that process to me i'd appreciate it.

---

### Post by RAOF on 2005-12-05
[QUOTE=joeav]...btw - when i selected the cd verifying option it told me it isnt a valid cd... any idea what causes that?...[/QUOTE]
This means that the MD5 checksum of (some of) the files failed.  That means that the CD you burnt is corrupt, so it's no wonder it didn't install correctly ;)

---

### Post by joeav on 2005-12-06
im not sure about that. i burned that cd about 4 separate times, i even downloaded the file again, and changed the burning speed to a much lower one, each time i got stuck at exactly the same spot.

so hard to imagine they were all screwed exactly in the same way :]

---

### Post by RAOF on 2005-12-06
Maybe your CD writer is deterministicly broken ;)  Or, it's possible that they were all corrupt in different ways, and this only showed at the same step.

---

