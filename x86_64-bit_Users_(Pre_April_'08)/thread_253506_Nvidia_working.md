---
title: "Nvidia working?"
date: 2006-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by graylion on 2006-09-08
Hi all

I am working my way towards installing compiz and xgl, but before i do that I want to eb sure that I have correctly installed the nvidia  driver:

- I have installed nvidia-glx
- I have changed the driver xorg.conf to nvidia
- I do not get a nvidia splash screen
- gl-billiards runs nicely and smoothly
- my flying toasters are flying but in low res and quite bumpily

so, any ideas?

cheers

---

### Post by tseliot on 2006-09-08
post the output of
```
dmesg | grep NVIDIA
```

and of
```
glxinfo | grep direct
```

---

### Post by brucevangeorge on 2006-09-13
> **graylion said:**
> Hi all

I am working my way towards installing compiz and xgl, but before i do that I want to eb sure that I have correctly installed the nvidia  driver:

- I have installed nvidia-glx
- I have changed the driver xorg.conf to nvidia
- I do not get a nvidia splash screen
- gl-billiards runs nicely and smoothly
- my flying toasters are flying but in low res and quite bumpily

so, any ideas?

cheers

Did you enable side band adressing and fastwrites?

My card was doing 75fps on glxgears without it and around 4800fps with it enabled. Makes a huge difference.

---

