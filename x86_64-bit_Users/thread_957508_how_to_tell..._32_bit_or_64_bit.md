---
title: "how to tell... 32 bit or 64 bit"
date: 2008-10-24
forum: x86 64-bit Users
---

### Post by TheSamurai on 2008-10-24
i'm having the hardest time figuring out which version i installed; 32bit or 64bit. i'm trying to figure out in order to install certain programs. i've looked around as much as i could but just can't find an answer. thanks in advance!

command line would be preferred...

Ubuntu 8.04
Fluxbox

---

### Post by Yellow Pasque on 2008-10-24
```
uname -m
```
Command will return x86_64 if you have amd64 Ubuntu installed or soimething like i686 if 32-bit Ubuntu is installed.

---

### Post by revoman3 on 2008-10-24
Well If you have a 32-bit processor then you should use the 32-bit version, If you have a 64-bit processor then you should use the 64-bit version or the slower 32-bit version.

If you have already installed Ubuntu then you should use the code provided above.

Hope this helps :)

---

### Post by TheSamurai on 2008-10-24
thanks very much for that command. i686, not the response i was hoping for. is there a "simple" way to upgrade to 64 bit or should i just completely reinstall? i'm not sure why i installed 32 bit in the first place as i built my box with all 64 bit support about a year ago.

---

### Post by Yellow Pasque on 2008-10-24
Unfortunately, you cannot "upgrade" to 64-bit; it requires a reinstall. Unless your /home folder is on a seperate partition, you will lose personal data if you don't back it up.

---

### Post by TheSamurai on 2008-10-24
i'm thinking it's going to be a fun reinstall... i have too much installed. ugh. thanks again for the help.

---

### Post by subtwo on 2008-10-24
If you have a lot of software installed and want to preserve the selections of packages you could do this:

[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

---

### Post by TheSamurai on 2008-10-25
thanks for the link, i'll be sure to check it out!!

---

### Post by Sef on 2008-10-26
> Unfortunately, you cannot "upgrade" to 64-bit; it requires a reinstall. Unless your /home folder is on a seperate partition, you will lose personal data if you don't back it up.

Wether you have a separate home partition or not, you should always back up your data before an install of any kind.   There are no 100% guarantees that all will go well.

---

### Post by TheSamurai on 2008-10-26
which i do... acronis true home is a fantastic product!!!

---

### Post by senseijose on 2008-10-26
and easy way to detect if you have a 64 bit operating system working is checking your ram.  32 bit system only register 3.5 ram regardless of how much ram you have installed.  i have both 32 and 64 bits install on my hard drive.  there are some programs that wont work properly using 64 bits.  you will have the option to select witch one you want to use when booting.

---

### Post by TheSamurai on 2008-10-27
...

---

