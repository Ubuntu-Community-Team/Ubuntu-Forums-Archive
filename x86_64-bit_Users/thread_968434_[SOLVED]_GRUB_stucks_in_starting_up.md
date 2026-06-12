---
title: "[SOLVED] GRUB stucks in starting up"
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by underground on 2008-11-02
Hello...i can't boot to windows xp...system is dual boot with ubuntu 8.10 and windows xp...when i select windows it stucks in starting up...what can i do???


I solved it..just added the following lines to menu.lst
map (hd1) (hd0)
map (hd0) (hd1)

---

