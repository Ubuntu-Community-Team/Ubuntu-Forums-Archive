---
title: "W: GPG error:"
date: 2008-05-16
forum: Wine
---

### Post by symon1980 on 2008-05-16
Hi guys. I was trying to install the latest version of wine, this is what i done....
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
sudo wget [http://wine.budgetdedicated.com/apt/sou](http://wine.budgetdedicated.com/apt/sou) ... hardy.list -O /etc/apt/sources.list.d/winehq.list

now everytime i reload Synaptic, i get this error...
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

the package wouldn't work, then i realised that it was for hardy, not gutsy. I removed the repo i created to the wine website
from synaptic.... and now i get this error.

anybody know how i can remove this error?
thanx

---

### Post by hermes0710 on 2008-05-16
Go to System>Administration>Software sources and in the third tab i think you have a list of keys. Since you removed the repositories you no longer want the key so remove it from there. After closing, run "sudo apt-get update" inside a terminal to make sure everything is ok

---

### Post by symon1980 on 2008-05-16
ah, that will probably do it. although...
you wouldn't happen to know how to do it in KDE would you?
i can't seem to find anything to get me into system sources?
cheers.

---

### Post by symon1980 on 2008-05-16
ahh, got it sorted now. thanx.

---

### Post by hermes0710 on 2008-05-16
Great :)

---

