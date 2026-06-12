---
title: "Help My computer Restarts Automaticaly"
date: 2007-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by kirtan on 2007-06-27
My computer automatically restart suddenly when i am working on Ubuntu 7.04 feisty x64


my Broadband Connection also disconnect while computer restarts don't know whats the reason behind it 

its not happening in windows Xp
:(:(:(:(:(

---

### Post by praxis22 on 2007-06-27
more details please!

What's your Processor, what's your motherboard, etc.

If you're using a 64bit install on an Intel Conroe (core 2 Duo) chip remove the powernow demon and see what happens:

```
sudo apt-get remove powernowd 
```

That's from memory so you may want to check yourself.

---

### Post by kirtan on 2007-06-27
I  have p-4 3.0 ghz

1 Gb RAM 
Motherboard Intel 915 GLVG
i m running Ubuntu feisty amd64
i don't think its thermal issue

---

