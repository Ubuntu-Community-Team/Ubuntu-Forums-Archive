---
title: "Wine update"
date: 2008-06-16
forum: Wine
---

### Post by nonmi9 on 2008-06-16
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

I'm new, so what does it mean? It gives me this when I update ubuntu.

---

### Post by cogadh on 2008-06-16
You need to add the WineHQ repository key:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

---

### Post by nonmi9 on 2008-06-16
Thank you thank you!

---

