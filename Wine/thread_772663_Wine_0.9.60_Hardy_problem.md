---
title: "Wine 0.9.60 Hardy problem"
date: 2008-04-28
forum: Wine
---

### Post by MightyMe on 2008-04-28
I have just installed the latest Wine 0.9.60 from scratch on my newly upgraded Hardy Heron and get the following error message:

preloader: Warning failed to reserve range 00000000-00010000

whenever I type a command. And it doesn't appear in my Applications menu like previous versions on Gutsy. 

Anyone have any ideas what this means?

---

### Post by cogadh on 2008-04-28
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

### Post by MightyMe on 2008-04-29
Thanks for the pointer. Guess I have to wait a Wine version or two...

---

### Post by cogadh on 2008-04-29
Its not really a problem with Wine, it is a problem with how they implemented a new security feature in Linux. Wine may be changed to accomodate it in the future, but I think it is more likely that we will see a change in how that security feature is implemented.

---

### Post by ajackson on 2008-05-01
> **MightyMe said:**
> Thanks for the pointer. Guess I have to wait a Wine version or two...
It's just a warning, everything I've ran under wine works despite getting those messages.

---

### Post by cogadh on 2008-05-01
Not true. If you are trying to run anything with Wine that is 16 bit, it will not work at all. Additionally, some 32 bit applications, like MS Office, will crash after a period of usage, as long as that error is still ocurring. Basically any app that needs to legitimately access that 64K of kernel memory will fail to work properly as long as that security fix is in place.

---

