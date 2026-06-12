---
title: "Error  Code Following Installation"
date: 2006-12-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by The-Wizard-of-the-Lake on 2006-12-09
I keep getting this error message after every install with synaptic package manager or accessories add/remove utility: E: subprocess post installation script returned error exit status 1.
What does it mean and how do I get rid of it?  Thanks.

---

### Post by John.Michael.Kane on 2006-12-11
Open synaptic package manager click on edit---->fix broken packages 

That error you posted means that a package you tried to install did not install fully.

You can also try running these.

**This should remove all problematic packages automaticaly :**
```
sudo aptitude -f remove
```

**This should configure all packages that are unconfigured :**
```
sudo dpkg --configure -a
```

---

