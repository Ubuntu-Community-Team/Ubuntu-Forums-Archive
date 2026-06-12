---
title: "Can't Install WINE"
date: 2008-09-03
forum: Wine
---

### Post by tom_the_drummer on 2008-09-03
Hi guys,

I have tried my best but Linux is sooooo confusing!!


I have Ubuntu Studio and would like to see if my windows prgorams will work.

So I downladed wine, extract it to my desktop. Open the folder, go to tools, click wineinstall, run in terminal (becuase run does nothing). After that it starts up the terminal, starts doing stuff then closes and nothing more happens. Says seeing config.log or something but the terminal closes too quickly for me to read what it says exactly.


PLEASE help - I am getting sooooooooooo cross!!!


Cheers




Tom

---

### Post by pytheas22 on 2008-09-03
Unless you need the very latest stable release of wine, you can install it much more easily by opening a terminal and typing:
```

sudo apt-get install wine
```

(Make sure first that all the repositories are enabled at System>Administration>Software Sources.)  Or you can find it in Synaptic.

What you tried to do is compile from source, which is not recommended unless you have a specific reason to do so (e.g., you know that the version of wine compiled in the repositories will not support a certain Windows application, so you need a later release).

---

### Post by tom_the_drummer on 2008-09-03
> **pytheas22 said:**
> Unless you need the very latest stable release of wine, you can install it much more easily by opening a terminal and typing:
```

sudo apt-get install wine
```

(Make sure first that all the repositories are enabled at System>Administration>Software Sources.)  Or you can find it in Synaptic.

What you tried to do is compile from source, which is not recommended unless you have a specific reason to do so (e.g., you know that the version of wine compiled in the repositories will not support a certain Windows application, so you need a later release).

Thanks for the help!

Just a quickie - why is it no recommended to compile from a source, and how do you do it correctly? (For future reference)

---

### Post by pytheas22 on 2008-09-03
> Just a quickie - why is it no recommended to compile from a source, and how do you do it correctly? (For future reference)

It's better to use the repositories for several reasons, including:

1) it's a lot easier and faster (it can take hours or even days to compile certain big programs from source)
2) it ensures that you're using a standardized version of the software (i.e., you have the same version of wine that everyone else on Hardy uses), which makes support requests simpler
3) the repositories are secure, because they're hosted by a centralized trusted source that requires authentication...if you download source code from random sites on the Internet, it's harder to know that it's not malicious code (you could read the source, but who does that?)
4) most important, if you install through the repositories, you get bug and security fixes pushed out automatically via Ubuntu updates--with one click you can update all of the hundreds of applications on your system.  If you install from source, you would have to update it all manually

Let us know if you have any trouble installing wine; otherwise, enjoy Ubuntu!

---

