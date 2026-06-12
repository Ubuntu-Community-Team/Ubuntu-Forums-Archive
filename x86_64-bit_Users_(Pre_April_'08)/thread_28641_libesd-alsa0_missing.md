---
title: "libesd-alsa0 missing"
date: 2005-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Grue on 2005-04-21
I've been wanting to fix the sound as described in the 'Ubuntu starter guide', but then I found out there is no libesd-alsa0 in the AMD64 repositories. I've searched the forums and the net for an alternative way to do this, but I haven't found any.

Does any of you have a way to get full ALSA support in hoary without too much trouble, or do I have to wait for the 64 bit version of the lib to hit Ubuntu repositories?

Is it possible to run with a 32 bit lib and use it in a 64 bit app?

This is my first post here, so be gentle.

---

### Post by squallbsr on 2005-04-21
What repositories are you trying to pull libesd-alsa0 from?

i.e. universe, multiverse...

I don't know exactly what repository you need to be pulling from, but just something simple to check.  Sorry to bother you if you have already checked all the repositories...

---

### Post by Grue on 2005-04-21
All repositories are checked, sorry for not mentioning it in my previous post. As you can see [here](http://ubuntuforums.org/archive/index.php/t-16284.html), it's been brought up before, but there wasn't really any solution :).

---

### Post by Grue on 2005-05-04
Sorry for this, but... ^Bump^

I would really like to know if there is any info on getting ALSA working properly in Ubuntu 64 bit.

---

### Post by St-Ex on 2005-05-04
Same thing here; no way to find the libesd-alsa package on apt... :???:

---

### Post by rsw on 2005-05-05
would it be possible to just download the alsa-lib source and compile it for x86_64 using the march mcpu CFLAGS?

---

### Post by reuben on 2005-05-06
Ah, this explains a lot. I was wondering what was wrong with the sound...

---

