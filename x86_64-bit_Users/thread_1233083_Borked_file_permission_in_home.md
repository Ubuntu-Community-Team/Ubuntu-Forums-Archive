---
title: "Borked file permission in home"
date: 2009-08-06
forum: x86 64-bit Users
---

### Post by niw_uk1964 on 2009-08-06
I have completely borked the file permissions in my Home directory by playing around with chmod (idiot). But I shall learn!

I can't boot properly as a result.

I can boot using a livecd and get into the directory. I assume I will be able to reset the permissions to default there by using:


sudo chmod "parameter" /dev/sdd5/home/niw

Where dev/sdd5 is the partition holding home for my installation

What parameters do I use and what is the correct syntax please?

](*,)

---

### Post by ajgreeny on 2009-08-06
No need to use the live CD; boot to recovery mode from the grub menu (the second item usually) and simply issue the command ```
chmod -R 755 /home/username
```.  Next time you boot there may be an error message about some particular file which I can't remember in detail, but generally it will be sorted without problem.

I assume you didn't change ownership of anything as well as the mode. otherwise you may need to do the same but with chown.

---

### Post by niw_uk1964 on 2009-08-06
You superstar! Thanks very much. I love the OSS community :D

---

