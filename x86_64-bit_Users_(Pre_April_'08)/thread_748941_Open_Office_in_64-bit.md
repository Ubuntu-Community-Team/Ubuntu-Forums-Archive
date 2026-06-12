---
title: "Open Office in 64-bit?"
date: 2008-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hapahauli on 2008-04-07
Hello =)

I'm new to **Ubuntu Studio v 7.10**, and everything's been running smoothly until today.  The platform came standard with a version of **Open Office Word**, which today I uninstalled in the hopes of installing the complete Open Office applications package.  Unfortunately... I can't figure out how to install it on a 64 bit (amd).  The only files I have found on the internet so far are the i386, 32-bit files, which I cannot install due to **"Architecture Error"**. 


_So the grand question:_
**How do I get Open Office running on my computer again?  **

Is there a 64-bit version of Open Office out there (usable for someone illiterate with linux as I), or is there a way to run the 32-bit version on my computer?  I've heard some snippets about **32-bit emulators**, but I have no idea what they are nor how they work nor where I'm supposed to get them.

Any help, large or small, appreciated.

Thanks in advance!

---

### Post by tempest on 2008-04-07
You could try re-installing Openoffice from the repositories. Can you elaborate on the reason why you removed the default Openoffice installation?

---

### Post by Hapahauli on 2008-04-07
Alright, I"ll try to figure that one out tomorrow morning ;)

The only Open Office program I had installed was Open Office Writer, and on openoffice.org, I remember reading that it was impossible to install other openoffice software separately, and that one would have to de-install all the old software to install the complete new package.  Or that's what I understood anyway =P

Re-installing through the repositories might be a good idea for now, but I do eventually want to have other openoffice software on my computer.

---

### Post by jocko on 2008-04-08
> **Hapahauli said:**
> Alright, I"ll try to figure that one out tomorrow morning ;)

The only Open Office program I had installed was Open Office Writer, and on openoffice.org, I remember reading that it was impossible to install other openoffice software separately, and that one would have to de-install all the old software to install the complete new package.  Or that's what I understood anyway =P

Re-installing through the repositories might be a good idea for now, but I do eventually want to have other openoffice software on my computer.

To install the complete openoffice, all you need to do is install the package 'openoffice.org'.
Find it in synaptic or paste this in a terminal:
```
sudo apt-get install openoffice.org
```

---

### Post by Hapahauli on 2008-04-08
Ah, thank you... that was a lot easier than I made it out to be :lolflag:

---

### Post by jocko on 2008-04-09
> **Hapahauli said:**
> Ah, thank you... that was a lot easier than I made it out to be :lolflag:

You're welcome! And yes, things in ubuntu is very easy once you realize most things you need are available through the repos...

---

### Post by Princey on 2008-04-09
If you're running the 64bit version of Ubuntu and it's derivatives, the openoffice that comes in the repositories will be 64bit as well.

---

