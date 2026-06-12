---
title: "another synaptic crash"
date: 2008-05-10
forum: x86 64-bit Users
---

### Post by bridgidpnh on 2008-05-10
When I try to open Synaptic Package Manager in Heron 64, I get this error message:

“E:Type '—21:25:04--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list 
E:The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.”

Unfortunately, closing the error message also closes the manager, precluding the possibility of going to the repository dialog. I am a new user and although I suspect a command line fix is possible, I have had little luck locating terminal syntax documentation so far.

---

### Post by Kevbert on 2008-05-10
In terrminal:
```
sudo gedit /etc/apt/sources.list.d/medibuntu.list

```

You should have something like this:
```
## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ gutsy free non-free
# deb-src http://packages.medibuntu.org/ gutsy free non-free
```

This is my file for Gutsy.

---

### Post by bridgidpnh on 2008-05-10
> **Kevbert said:**
> In terrminal:
```
sudo gedit /etc/apt/sources.list.d/medibuntu.list

```

You should have something like this:
```
## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ gutsy free non-free
# deb-src http://packages.medibuntu.org/ gutsy free non-free
```

This is my file for Gutsy.

Thank you Kevbert!
I typed the code and pressed enter, but the keyboard won't work to type my password!

---

### Post by Kevbert on 2008-05-10
The password is always hidden.  Enter it and press return.
Any probs give me a shout.

---

