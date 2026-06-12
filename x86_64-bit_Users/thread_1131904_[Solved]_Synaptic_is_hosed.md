---
title: "[Solved] Synaptic is hosed"
date: 2009-04-21
forum: x86 64-bit Users
---

### Post by AdamantLobster on 2009-04-21
I am haveing a bit of an issue with my synaptic package manager I keep getting the error 

E: The package hot-babe needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I tried installing this fun little system monitor and it failed to install now I cannot uninstall broken package and Synaptic is hosed


Newby instructions please.

---

### Post by Simian Man on 2009-04-21
hot-babe?  You should probably get out more if you are trying to get hot babes through a package manager.

---

### Post by AdamantLobster on 2009-04-21
HaHa a little help would be nice.

---

### Post by Kareeser on 2009-04-21
Try downloading the deb from getdebs.net, since it's not in the repositories.

---

### Post by oldos2er on 2009-04-21
> **AdamantLobster said:**
> I am haveing a bit of an issue with my synaptic package manager I keep getting the error 

E: The package hot-babe needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I tried installing this fun little system monitor and it failed to install now I cannot uninstall broken package and Synaptic is hosed


Newby instructions please.

 Make sure you have the Medibuntu repository enabled (see [http://medibuntu.org](http://medibuntu.org)), then in a terminal, run
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by AdamantLobster on 2009-05-03
Thank you I have fixed the problem. I unfortunately forgot how to mark this as solved.

---

