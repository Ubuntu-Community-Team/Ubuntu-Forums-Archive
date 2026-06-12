---
title: "Adding hardware to Dapper 64"
date: 2006-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by j0eb0b on 2006-09-20
I ordered an Audigy soundcard last night that I hope will fix my sound problem using Dapper 64.  Question since Dapper is already installed on my machine, what will I have to do to get the OS to recognize the new hardware and load the appropriate driver.  I know I have to go into the bios and disable the onboard sound but after that what happens next?

---

### Post by kick6 on 2006-09-20
Dapper should recognize the card, and load the proper module.  IIRC the audigy used the EMU10k1 kernel module.  I'd do an lsmod to make sure its loaded.  After that, you're going to have to update your mixer to point at the new hardware.  That should be about it.

---

### Post by fabertawe on 2006-09-20
I'm using an Audigy2 EX (break out box) with no problems whatsoever. Saying that I've not used it with Dapper beyond the basics as I dual boot Windows for my recording. It is the emu10k1. The mappings of mixer names to Audigy controls is a little mixed up but you can play with those to work out which is which. 'Front' in the mixer seems to be another 'Master' so you'll need to push that one up.

As for recognizing the hardware, it was automatic here.

Paul

---

