---
title: "Synaptic Status Button"
date: 2007-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-02-22
It's been over a month since I upgraded from Dapper amd64 to Edgy amd64. I have been having issues with OpenOffice 2.0.4 and tonight I noticed that in Synaptic I have several sections when I hit the Status button -- Residual, Installed - Auto Removable, and Installed -  Local or Obsolete.

None of the Residual ones were marked as installed, but right-clicking on them I had the option to do a complete removal including configuration files. I figured this meant that the application had been installed in Dapper but is no longer installed in Edgy, and there are just some config files left over. I did a complete removal, and it doesn't seem to have changed anything.

The Installed - Auto Removable shows 8 packages installed and , and Installed -  Local or Obsolete sections shows 52 packages. I understand the Local or Obsolete just means the packages are not in the current repositories. But what does Auto Removable mean?

---

### Post by Jussi Kukkonen on 2007-02-22
From *man apt-get*> 
autoremove is used to remove packages that were automatically installed to satisfy dependencies for some package and that are no more needed.
That's the same in Synaptic no doubt.

---

### Post by John Jason Jordan on 2007-02-22
Thanks.

---

