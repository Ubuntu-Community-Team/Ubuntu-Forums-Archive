---
title: "Ubuntu Studio 64 bit - possible problems?"
date: 2009-08-20
forum: x86 64-bit Users
---

### Post by cronholio on 2009-08-20
I've ordered a new PC that will mostly be used for audio production (Ardour), as well as some web surfing and possibly running Quake Wars. I plan to install Ubuntu Studio on it and I would prefer the 64 bit version in  order to be able to address its 6 Gigs of RAM. (I know that you can also get around the limitation by using PAE but apparently there are still issues with that.)

So, my question is: will I run into any problems with Ubuntu Studio 64 bit?

---

### Post by markbuntu on 2009-08-23
None that you wouldn't have with 32 bit.
I find that Ardour/jack is a little faster in 64 bit.

---

### Post by ken78724 on 2009-08-24
> **cronholio said:**
> audio production (Ardour) [+] install Ubuntu Studio on 64 bit 

Cronholio, does this work on 8.04 or 8.10 and/or U Studio for 9.04 Jaunty? And does one do a sudo get in terminal? a snaptic manager update? or are you referring to the The Lasko recommended download? 

Just want a clear path through the jungle  

thanks

---

### Post by ken78724 on 2009-08-24
> **markbuntu said:**
> Ardour/jack ,,, faster.

Markbuntu ,,, point us to a sudo get code or direct download for U 9.04 Jaunty Jack and pls tell us how would one assures Ardour can be used. Help most appreciated   

Kenneth

---

### Post by markbuntu on 2009-08-24
Oh, I forgot. If you have an amd cpu or mobo you may have problems with the rt kernel. It will not boot for some using this hardware. There are bug reports at launchpad...

Anyway, the packages you can find with synaptic package manager. Use the search. It is called jackd. Or you can look in the meta packages for ubuntustudio audio.

---

### Post by ken78724 on 2009-09-03
Markbuntu your words left me unsure then I had to be gone.. Thanks
Ken

---

### Post by acidblue on 2009-09-03
> **markbuntu said:**
> Oh, I forgot. If you have an amd cpu or mobo you may have problems with the rt kernel. It will not boot for some using this hardware. There are bug reports at launchpad...


You are so right, rt kernels do not play well with amd for some reason.
It's a conspiracy I tell ya!

I hope this gets fixed soon, I really need rt support for my home studio.
I guess I could use winbloze, but that would be a giant leap backwards.

---

### Post by ken78724 on 2009-09-04
seeking working U Studio 64 install for 9.04

---

