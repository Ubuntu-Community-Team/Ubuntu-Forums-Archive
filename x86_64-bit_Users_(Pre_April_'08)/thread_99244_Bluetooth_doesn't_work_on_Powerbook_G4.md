---
title: "Bluetooth doesn't work on Powerbook G4"
date: 2005-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by eduardgrebe on 2005-12-05
I run breezy on a 1.25GHz Powerbook G4 with a built-in bluetooth module. The "Bluetooth manager" software I installed fails with the message "Could not find bluetooth devices on the system. Please make sure that your bluetooth adaptor is correctly plugged into your machine."

I have booted into Mac OS X to ensure that the module is switched on.

Has anyone had this problem? Any idea how to fix it? I have seen reports that bluetooth is working fine on machines like this.

---

### Post by hentaidan on 2005-12-05
I (and others) have had similar problems on my iBook G4, the bluetooth manager reporting "device not found".

```
sudo hid2hci
```
gets it working for me.

---

