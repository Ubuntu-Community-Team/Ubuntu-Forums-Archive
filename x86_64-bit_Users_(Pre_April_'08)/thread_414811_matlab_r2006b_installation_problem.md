---
title: "matlab r2006b installation problem"
date: 2007-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by dnpkraju on 2007-04-20
Dear friends

I am new to linux 
I tried to install matlab by doing
created license file in /usr/local/matlab
installed matlab
after it is asking to strat license manager

can anay one give me some details about licence manager 
and i didnt installed Flexnet licence manager , is it really needed

when i tried to run matlab from /usr/local/matlab/bin/matlab
I got error licence manager -95

---

### Post by k_the_snake on 2007-04-20
Hello,

Because Matlab is not a GPL program, you need to have a proper license file. There are two majors kind of licenses, the concurrent one and the standalone one. If you've got a standalone one, you don't need anything else than your computer and  your own flexlm manager. But if you've got a concurrent license, you need to be connected to your license computer... Otherwise it will not work...

Hope this can help,

K

---

### Post by sonni_kuba on 2007-04-20
Hi dnpkraju

Two things...

1) Make sure your license is saved as license.dat in /usr/local/matlab

2) Start the license manager manually by typing in the following

/usr/local/matlab/etc/./lmstart

and then matlab

Let me know if this works

---

