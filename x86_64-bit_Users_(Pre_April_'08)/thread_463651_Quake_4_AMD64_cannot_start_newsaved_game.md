---
title: "Quake 4 AMD64 cannot start new/saved game"
date: 2007-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by zanophol on 2007-06-03
I was running Edgy 32 bit Ubuntu with Quake 4 with success. After an upgrade to Feisty AMD64 Kubuntu, Quake 4 (1.3 and 1.41 beta tried) will load, but when I try to start a new/saved game, the program starts to load, and then exits back to the main program screen. I have checked permissions (755 owned by user running the program), I have tried a new ~/.quake4 directory, I have tried reloading the Quake 4 program installer, and I have copied over the .pak4 files again. Nothing seems to work, and no errors are being reported via the terminal.

Anyone have any suggestions?

---

### Post by kuja on 2007-06-04
Same problem here. It worked fine in edgy x86_64 ... I've spent a few hours looking for a way to work around it, bu t I've not had any luck so far.

---

### Post by jamesford on 2007-06-04
rtcw keeps quitting on me in feisty too, worked fine in edgy

---

### Post by fago on 2007-07-20
hm, my quake4 segfaults when I try to start a game. (feisty, amd64)

according to this it should be a problem with libSDL, however I've installed the suggested package :/
[http://fatooh.org/q4howto/](http://fatooh.org/q4howto/)

---

### Post by fago on 2007-07-20
update: I got it running by intalling ia32-libs-sdl
now quake4 is working, but quake4-smp still segfaults

---

