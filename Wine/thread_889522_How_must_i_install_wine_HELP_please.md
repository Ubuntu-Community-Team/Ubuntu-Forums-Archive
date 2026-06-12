---
title: "How must i install wine HELP please"
date: 2008-08-14
forum: Wine
---

### Post by alperstarr on 2008-08-14
hello all,
i ve just downlaoded the 1.1.2 vs of wine. it's in a package tar.bz2
i extracted it in a folder. then searc it in google and find these

./configure
make depend
make
make install

i wrote these queries in command lines but wine installation had not been completed. at last i gave this error.

 configure: error: no suitable flex found. Please install the 'flex' package.
alperstarr@GadGet:~/Documents/Programmes/Wine/wine-1.1.2$ make depend
make: *** No rule to make target `depend'.  Stop.
alperstarr@GadGet:~/Documents/Programmes/Wine/wine-1.1.2$ make
make: *** No targets specified and no makefile found.  Stop.
alperstarr@GadGet:~/Documents/Programmes/Wine/wine-1.1.2$ make install
make: *** No rule to make target `install'.  Stop.

what must i do now ? i m new at linux, can anyone help me please.

thanx very much all

---

### Post by DJ_Peng on 2008-08-14
Is there a reason you don't want to use the version of WINE that's in the repositories? Or did you know that you can install it with a simple
```
sudo apt-get install wine
```
That may not get you the very latest version of WINE, but it will get you pretty close without the hassle of having to build it.

---

### Post by aoanla on 2008-08-14
You don't want to compile from source.

You want to install a proper pre-compiled Wine, as a .deb (so it's managed by Synaptic, like anything else).

You can do this by following instructions here:

[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)


(Your compiling from source problem, however, could be solved by doing what configure asks you to do. It says you don't have flex, so... try installing flex, in Synaptic.)

---

### Post by YokoZar on 2008-08-14
Applications -> Add/Remove -> Check the box for Wine


This is equivalent to what happens when you [click this link](apt://wine).

---

