---
title: "ubuntu live cd error (xserver failed)"
date: 2006-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by linuxepoch on 2006-05-02
i dont really understand the error. it shows xserver error and asks for a diagonosis but nothing seems to work after that.

---

### Post by gondilon on 2006-05-02
I had the same problem with my laptop. What is probably happening is that it is trying to accelerate the praphics and your card does not support  it. If you made the cd yourself, your could  reburn it onto a CD-RW and add option noaccel in the section of xorg.conf that names your graphics card.

---

