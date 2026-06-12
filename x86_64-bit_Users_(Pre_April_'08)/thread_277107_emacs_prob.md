---
title: "emacs prob"
date: 2006-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Snodgrass on 2006-10-14
I need Emacs with LaTeX but can't install tetex-base. Should I go back to 32 bit, or is there a workaround? Here is the error message I get from Synaptic:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tetex-base/tetex-base_3.0-15ubuntu1_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tetex-base/tetex-base_3.0-15ubuntu1_all.deb)
  Connection timed out

](*,)

---

### Post by pay on 2006-10-14
Try```
wget http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tetex-base/tetex-base_3.0-15ubuntu1_all.deb
sudo dpkg -i tetex-base_3.0-15ubuntu1_all.deb 
```

---

