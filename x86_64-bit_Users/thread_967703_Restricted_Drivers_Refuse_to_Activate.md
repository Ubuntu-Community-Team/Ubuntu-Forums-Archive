---
title: "Restricted Drivers Refuse to Activate"
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by Jamstruth on 2008-11-02
Just installed Ubuntu 8.10 and cannot get the restricted drivers for my Nvidia 7900GS to activate. Every time I press activate the window for installing them comes up then disappears. Help?

---

### Post by kdorf on 2008-11-02
Install nvidia-glx-177 and then activate them.

---

### Post by em4r1z on 2008-11-02
```
sudo aptitude install linux-headers-generic
sudo aptitude install nvidia-glx-177
sudo nvidia-xconfig
```
Restart the X session.

---

