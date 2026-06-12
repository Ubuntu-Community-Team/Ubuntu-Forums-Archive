---
title: "Problem accessing swap"
date: 2007-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by monkeymoo on 2007-09-27
Hi, first post so excuse me if I leave out some vital info. 

I'm running MatLab 7.4.0 (R2007a) Student Version in 32-bit on my 64bit Feisty through the use of debootstrap and chroot. They don't include the 64bit binaries with the Student Version :mad: and this was the only way I could get it to work. Generally everything works fine, although some things (like it remembering the working directory) only work when I call MatLab with sudo. This is no great problem. However, what my MatLab install cannot do is access the swap, so when it fills my RAM (4GB) it crashes my script with an "Out of Memory" error. :confused:

I have no idea what the problem is or what might be the cause. My guess is that it's not a problem with MatLab (which is why I am posting on these forums and not the MatLab forums) because I know that MatLab can use the pagefile on Windows. 

Any ideas/suggestions/help gratefully appreciated :). 

Thanks.

---

### Post by jpkotta on 2007-09-28
32-bit systems can only address 4 GB of memory.  I would guess that is the problem.

You can see how much RAM and swap you have with ```
free
```

---

### Post by monkeymoo on 2007-09-28
Ok. Yes, fair enough. It had not occurred to me that even though I had a 64-bit system because I was running a 32-bit app in a 32-bit chroot that that limit would still apply. Now I remember why I decided to use 64-bit in the first place! 

So basically it's all Mathworks's' fault for not providing a 64-bit Student Version. I suppose it was predictable that it would be the fault of the software you have to pay for! 

Thanks for you help.

---

