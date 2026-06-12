---
title: "Some help.  1 package broken"
date: 2007-08-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by weverjames on 2007-08-11
Hello everybody.
I installed successfully the ubuntu 64 bit version (moving from pclinuxos).  I saw there was a new nspluginwrapper that would allow me to use firefox 64 bits.  It is working fine after installation, but now my synaptic package manager shows that I have 1 broken package, that results to be the nspluginwrapper.
1.  Is it expected or there is something that I have to fix?
2  I am wondering if this issue wouldn't allow my sytem to get automatic updates through the synaptic manager?

I am going to appreciate your help and patience if this is a silly question.
Thanks

---

### Post by John.Michael.Kane on 2007-08-11
> **weverjames said:**
> Hello everybody.
I installed successfully the ubuntu 64 bit version (moving from pclinuxos).  I saw there was a new nspluginwrapper that would allow me to use firefox 64 bits.  It is working fine after installation, but now my synaptic package manager shows that I have 1 broken package, that results to be the nspluginwrapper.
1.  Is it expected or there is something that I have to fix?
2  I am wondering if this issue wouldn't allow my sytem to get automatic updates through the synaptic manager?

I am going to appreciate your help and patience if this is a silly question.
Thanks

To fix the package issue via synaptic.
1) Open synaptic
2) Click on edit
3) Click Fix broken packages
4) click reload
5) click mark all upgrades

Should the above fail to resolve the issue try the method below.

To try, and fix it via the terminal
This will try to configure all packages that are unconfigured :
```
sudo dpkg --configure -a
```

The other option remove the problematic program
```
sudo aptitude -f remove
```

Then rerun

```
sudo dpkg --configure -a
```

---

