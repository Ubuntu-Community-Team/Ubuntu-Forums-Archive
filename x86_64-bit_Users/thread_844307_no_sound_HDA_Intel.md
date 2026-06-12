---
title: "no sound HDA Intel"
date: 2008-06-29
forum: x86 64-bit Users
---

### Post by njmbb8 on 2008-06-29
I love ubuntu very much and i am very sad to find out that the sound will not work with my new computers sound card. If there has been a fix for this that google has not shown me could someone please show me?

---

### Post by kuja on 2008-06-29
You'll have more luck if you tell us what chip it is. (both of my computers are HDA Intel and they work quite well) To get this piece of information, try checking in alsamixer.

---

### Post by BryanFRitt on 2008-06-29
I have HDA and KUbuntu 8.04_x64 and didn't have sound until I installed compiled drivers from Alsa (well, I just did the ones that installed easily), and ran a sudo alsaconf, and alsamixer.  I noticed the ones in apt-get were the same version as the one I compiled, so it may have just been the other steps that fixed it, I don't know, and there might have been some extra steps I took that I can't recall at the moment.  .  Oh... almost forgot there was something about having to figure out what chips HDA used on my computer.  You might want/need to know this to compile quicker and smaller, etc...  Hope this helps.

---

### Post by Kevbert on 2008-06-29
Please check out this [community document]("https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28CategoryHardware%29").

---

### Post by stchman on 2008-06-30
> **njmbb8 said:**
> I love ubuntu very much and i am very sad to find out that the sound will not work with my new computers sound card. If there has been a fix for this that google has not shown me could someone please show me?

What version of Ubuntu are you using?

Give us an lspci output in this thread.  My laptop has an HDA Intel card and it works great.

---

