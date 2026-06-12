---
title: "how do i install 32 bit programs on a  x64?"
date: 2007-07-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by -=Viper=- on 2007-07-11
I kinda need to know since EVERY program i want/need is 32 bit only -_-  if anyone knows please tell me.  Thanks :D

---

### Post by John.Michael.Kane on 2007-07-11
Would help if you told us what these programs are.

If it's codecs or flash wine ect [Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

---

### Post by bluemech on 2007-07-11
> **-=Viper=- said:**
> I kinda need to know since EVERY program i want/need is 32 bit only -_-  if anyone knows please tell me.  Thanks :D

If you have the deb packages of those programs, just go to the directory where they're at, and type
```
sudo dpkg -i --force-architecture nameofpackagehere.deb
```

That doesn't guarantee that they'll work though. Usually you'll find yourself manually searching for the 32-bit libraries that go with those programs.

---

### Post by Cappy on 2007-07-12
> **bluemech said:**
> 
That doesn't guarantee that they'll work though. Usually you'll find yourself manually searching for the 32-bit libraries that go with those programs.

getlibs:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

