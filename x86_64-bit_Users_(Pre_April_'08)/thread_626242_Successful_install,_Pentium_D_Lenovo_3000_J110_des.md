---
title: "Successful install, Pentium D Lenovo 3000 J110 desktop"
date: 2007-11-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by BobHur on 2007-11-28
Not much else to tell, I installed it on my "test"partition, seemed to work fine but I munged my 32-bit Grub in the process. Instead of hacking through fixing Grub, I just wiped the disk and installed (only) Ubuntu 64bit.

This box has onboard Intel GMA 950 video, which works fine except for Compiz. I don't need Compiz, so that's not an issue for me. The onboard sound is wonky, I've got a Soundblaster card ordered to fix that. I imagine the proper soundcard drivers will appear soon, but the Soundblaster will likely be better quality anyway. I didn't expect that much of the onboard auxiliaries would work anyway when I bought it.

When I did the test install on Tuesday morning (I think) there wasn't a lot of software on the 64-bit repositories, particularly Geany and Lisp. A few hours later it was there, so I made the jump.

I'm pleased. I don't know that I'll do a lot of things that can take advantage of the 64 bit system, but it seems a shame to have the hardware and not make at least an attempt to utilize it.

---

### Post by Yellow Pasque on 2007-11-29
> **BobHur said:**
> I don't know that I'll do a lot of things that can take advantage of the 64 bit system, but it seems a shame to have the hardware and not make at least an attempt to utilize it.

Do you ever boot your PC? (because that runs faster in 64-bit) How about software compilation or media encoding/decoding? Do you ever compress or uncompress large files?

BTW, I recommend using OSSv4 for your sound architecture as that's what Creative officially supports. You should try installing it now and you'll probably get your integrated sound working too.

---

### Post by BobHur on 2007-11-30
Sound - I get the right channel working, the left channel a shrill feedback kind of noise, as if it were plugged into an overamplified source without sound. I have OSS, ALSA, and a couple more systems that show in the Sound section, they all work about the same ... poorly. I strongly suspect a bad onboard sound system. We'll see in a week or so when the sound card gets here.

Based on blind optimism I went ahead and ripped a bunch of my CDs onto the hard drive. It was much faster, and a couple that had previously shown "bad tracks" ripped entirely without complaint. That may be that my new hardware is better, or it may be due to the new OS. Who knows. 

I seem to be getting true multitasking instead of that task-switching crap that MS calls multitasking. I'm enjoying the huge improvement.

---

### Post by bpazolli on 2007-11-30
I succesfully installed it on a HP Pavillion Notebook dv6140us for information, just a night or two ago. One question, out of interest, why did you supposedly install 7.04?

---

### Post by BobHur on 2007-11-30
I didn't, it's 7.10. Oops, need to update my profile, thanks!

---

### Post by dixiebuyer on 2007-12-01
I have the same system and the same problem with a squealing channel. The channel that squeals on mine is marked as the left channel for system sounds. CDs won't play at all, just the high pitched squeal.

Curious if there is a fix. Or did the add on sound card work? Thanks in advance.

---

### Post by dixiebuyer on 2007-12-01
Well if you look long enough I guess you find your answer. 

[http://ubuntuforums.org/showthread.php?t=221875]("http://ubuntuforums.org/showthread.php?t=221875")

---

### Post by BobHur on 2007-12-01
> **dixiebuyer said:**
> Well if you look long enough I guess you find your answer. 

[http://ubuntuforums.org/showthread.php?t=221875]("http://ubuntuforums.org/showthread.php?t=221875")

Yes. Some of us are lucky with search engines, others are lucky at love. :)

I bought a Soundblaster Audigy SE and slapped in in. Problem solved; perhaps not the most elegant solution, but a solution nevertheless.

---

