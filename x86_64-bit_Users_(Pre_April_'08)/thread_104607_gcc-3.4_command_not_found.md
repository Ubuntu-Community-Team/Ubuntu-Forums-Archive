---
title: "gcc-3.4 command not found"
date: 2005-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by jwhitt on 2005-12-16
ok so im trying to install drivers dor my d-link dwl 122g wireless card andway i downloaded the st2500 drivers apt-get install linux-headers-2.6.12-9-powerpc-2.6.12-9-23 to get the headers everything seems to work fin so then i go into the rt2500 directory to compile then when i ruin make it starts up and ends with verious errors leading to gcc-3.4 command not found lines 11 and 12 in the gcc-version.sh.......ive removed and re installed gcc through apt-get remove and install .... what should i try?

---

### Post by carlosqueso on 2005-12-16
Try ```
sudo apt-get install gcc-3.4
```  Ubuntu ships with 4.0, but if you install this package, they should be able to coexist (they do for me).

---

### Post by MartinG on 2005-12-16
[QUOTE=carlosqueso]Try ```
sudo apt-get install gcc-3.4
```  Ubuntu ships with 4.0, but if you install this package, they should be able to coexist (they do for me).[/QUOTE]

You'll also need to type ```
export CC=gcc-3.4
```
before running ./configure, make, etc.

---

### Post by jwhitt on 2005-12-16
ok i got all that to work now when i insmod the rt2570.ko file i get a -l invalid module format?

---

