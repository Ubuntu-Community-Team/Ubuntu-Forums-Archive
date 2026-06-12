---
title: "wine wont install/download"
date: 2008-01-14
forum: Wine
---

### Post by NoobToast on 2008-01-14
I run all the code in the terminal as suggested by [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) then i go into synaptic package manager and i get this error in a dialog box and i dont know how to install any of that. 

```
wine:
 Depends: binfmt-support (>=1.1.2) but it is not installable
 Depends: libaudio2  but it is not installable

```

---

### Post by sauronsmatrix on 2008-01-18
try these in terminal:

```
sudo apt-get install libaudio2
sudo apt-get install binfmt-support
```

then see what happens

---

