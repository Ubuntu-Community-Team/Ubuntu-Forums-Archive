---
title: "Install pkgs via sudo dpkg --get-selections?"
date: 2007-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by drs305 on 2007-05-31
I am running 32 bit Feisty on several comptuters but will probably install 64 bit on my home built (AMD). Can I use the results of 
```
sudo dpkg --get-selections >~/Desktop/installed-pkgs
```
from my 32 bit machine to get the list and install the apps on the new 64 bit one?

I realize they may not all be available in 64 bit but assuming I have only the 64 bit repositories in sources.list would running ' dpkg --set-selections' install the correct versions on my machine?  

I guess I also have to know if the 64 bit respositories consist only of 64 bit apps or will they have the 32 bit ones unavailable in 64?

Finally, can I use a single home directory if I install both 32 and 64 Feisty or would it be better to have a separate home for each?

Thanks.

---

### Post by Kilz on 2007-06-01
> **drs305 said:**
> I am running 32 bit Feisty on several comptuters but will probably install 64 bit on my home built (AMD). Can I use the results of 
```
sudo dpkg --get-selections >~/Desktop/installed-pkgs
```
from my 32 bit machine to get the list and install the apps on the new 64 bit one?

I realize they may not all be available in 64 bit but assuming I have only the 64 bit repositories in sources.list would running ' dpkg --set-selections' install the correct versions on my machine?  

I guess I also have to know if the 64 bit respositories consist only of 64 bit apps or will they have the 32 bit ones unavailable in 64?

Finally, can I use a single home directory if I install both 32 and 64 Feisty or would it be better to have a separate home for each?

Thanks.

You should be able to use the package list, most of the applications will have the same names.
The repo's will only have packages designed to be installed on 64bit. Im not aware of any 32bit packages, but there used to be. Open office in Dapper was 32bit , the developers had it setup to install. But there is no way to chose a 32bit package over say a 64bit one.
The home directory is mostly settings, it should be safe to use the same one.

---

