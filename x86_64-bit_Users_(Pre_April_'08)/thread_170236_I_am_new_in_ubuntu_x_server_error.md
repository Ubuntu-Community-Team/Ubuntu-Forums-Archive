---
title: "I am new in ubuntu x server error"
date: 2006-05-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by ebekir on 2006-05-04
my friends &#305; am new in ubuntu.I have taken ubuntu 5.1 64  bit edition and I tried to install but I get Xserver error and now I am in text screen.Ican't fix the problem because I am NEW in L&#304;nux.I am using amd 64 bit sempron 3400+ and NV&#304;D&#304;A GEFORCE 7600 GS  SLI graphics card.if you help me you encourage me  please help me.thanks alot

---

### Post by kaffeine on 2006-05-04
ebekir, more info would be helpful, but since you have an NVIDIA 7600, i'm guessing it's a driver issue. try this:

```
sudo apt-get install nvidia-kernel-common nvidia-glx
```

if it says nvidia-glx is already installed, go to /etc/X11/xorg.conf and lower the resolution (look for your default depth section and use "800x600" as a first try).

---

### Post by ebekir on 2006-05-04
my friend while I configure X server I can't choose color depth. in text screen I see this error "Xserver-xorg postint warning  overwriting possibly-customised configuration file;backup in /etc/X11/xorg.conf.200605050111

---

