---
title: "Getlibs uninstall?"
date: 2007-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dark Aspect on 2007-10-24
How do I uninstall 32-bit programs installed on 64-bit Ubuntu though getlibs?I installed 32-bit ZSNES though getlibs to find out later there is a 32-bit version already compiled for amd64 [here]("http://packages.dfreer.org/").The 32-bit version I already installed does not show up in the synaptic package manager.How do you uninstall programs installed though getlibs?

---

### Post by Cappy on 2007-10-25
Getlibs only downloads libraries to the /usr/lib directory that are required for running the program. It sounds like you are wanting to uninstall your old znes program. How did you install znes? Did you install it from a .deb file or did it come in a zip format of some kind and you extracted in your home directory? Did you install it from synaptic?

---

### Post by Dark Aspect on 2007-10-25
> **Cappy said:**
> Getlibs only downloads libraries to the /usr/lib directory that are required for running the program. It sounds like you are wanting to uninstall your old znes program. How did you install znes? Did you install it from a .deb file or did it come in a zip format of some kind and you extracted in your home directory? Did you install it from synaptic?
I put the deb file in my home folder and typed

> sudo dpkg -i --force-all zsnes_1.420-2.1ubuntu1_i386.deb

um.....that seemed to install the application not just the libraries.I don't think I used getlibs correctly if I am just suppose to get the libraries.I installed Cedega the same way.....

---

### Post by Cappy on 2007-10-25
That would be ```
sudo dpkg -r zsnes
```

The new znes you installed is likely have already overwritten/removed your old znes install and running the code above would probably just remove your new zsnes.

---

### Post by Dark Aspect on 2007-10-26
> **Cappy said:**
> That would be ```
sudo dpkg -r zsnes
```

The new znes you installed is likely have already overwritten/removed your old znes install and running the code above would probably just remove your new zsnes.

Thanks that work and I installed the other 32-bit version that was meant to be installed on 64-bit Ubuntu.

---

