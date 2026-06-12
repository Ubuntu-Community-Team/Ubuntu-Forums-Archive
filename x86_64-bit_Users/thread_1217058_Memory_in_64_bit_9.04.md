---
title: "Memory in 64 bit 9.04"
date: 2009-07-19
forum: x86 64-bit Users
---

### Post by theozzlives on 2009-07-19
I know people are tired of hearing the whining, but.... I upgraded to 64 bit because I had 4 GB RAM on the way. Most of my 2 GB was always cached, which was ok cause I was waiting on more RAM.

The 4 GB came. My BOIS reports 4096 RAM with 4086 available??? Free reports 3897 MB (the actual number divided by 1024). I know that's not much of a loss, but I'm just wondering why my system takes 10 MB and Jaunty don't recognize all of what's left. It's not my video cause it has 64 MB RAM by itself.

---

### Post by Jaesin on 2009-07-20
it is most likely ide and adapter irq's being saved in the bios.  My old system had this under windows.  It took like 20 to 30 mb just for system resources.  So your 4gb of ram actually is going to be less then that regardless of what you do.  Even 8gb would still come up to only like 7.75 after booting.  I would not worry about it too much though.

---

### Post by jespdj on 2009-07-21
It could still be your video card, even though it has its own memory.

Part of the address space is used to enable the CPU to talk to the video card. Look in your BIOS if there is a "memory remapping" setting, and make sure it is enabled. This will move the address space for communicating with the video card out of the way of the normal RAM.

---

### Post by jlreich on 2009-07-21
> **Jaesin said:**
>   Even 8gb would still come up to only like 7.75 after booting.  I would not worry about it too much though.
That's what my system reports with 8GB ram.

There is a lot I don't understand about Linux yet but you are not being cheated or the system is not misreading the amount of ram. Don't worry about it. :)

---

### Post by litspliff on 2009-07-21
if you have that much RAM, just let the video hardware use it. especially if you only have 64MB dedicated to video memory. i would look for a bios option to increase the amount of shared RAM. 

i've got a couple gigs, and dropping another 128MB on the video made a huge difference....in a good way.

just out of curiosity, why are you worried about MB's when you have GB's?

---

### Post by theozzlives on 2009-07-22
> **litspliff said:**
> if you have that much RAM, just let the video hardware use it. especially if you only have 64MB dedicated to video memory. i would look for a bios option to increase the amount of shared RAM. 

i've got a couple gigs, and dropping another 128MB on the video made a huge difference....in a good way.

just out of curiosity, why are you worried about MB's when you have GB's?

Not worried, just curious... I've become as knowledgeable as I am because of it. DOS used to report 655360 (640k) base memory. If it was off you had Michaelangelo or Stoned virus or something.

---

