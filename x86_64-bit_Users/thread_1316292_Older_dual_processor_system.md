---
title: "Older dual processor system"
date: 2009-11-05
forum: x86 64-bit Users
---

### Post by reaper666 on 2009-11-05
I have an older sual processor system.
2 intel 1 gig processors and 1.5 gig ram.
It is an all scsi baby server made by dell. About 7 years old.

My question is will the x86 setup use both processors or just one
of them?

Thanks.....

---

### Post by bonestonne on 2009-11-05
x86 is capable of dual, quad and even 8 core systems, it's the RAM that is less flexible, as your computer wont be able to properly address more than 4gb.

---

### Post by Sef on 2009-11-06
> x86 is capable of dual, quad and even 8 core systems, it's the RAM that is less flexible, as your computer wont be able to properly address more than 4gb.

If PAE was installed, then the system could handle more than 4gb of ram.

---

### Post by reaper666 on 2009-11-06
Thanks for the info.
Now to give it a try and see what happens.
Will post the results when it is done.

---

### Post by bonestonne on 2009-11-06
While the PAE is true, having it would allow for more than 4gb of RAM to be accessed, the support is dodgey, and I wouldn't trust it in a high usage system.

---

### Post by cascade9 on 2009-11-06
Try finding 4x1GB PC-133. Fun! Even _more_ fun with the registered/EEC that old server would be using.

---

