---
title: "Ut2004 fiesty kubuntu amd64 cant run"
date: 2007-05-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Josiah4jc on 2007-05-15
I'm running Kubuntu fiesty 64 bit an an amd64 machine. My problem is that I want to install and play ut2004, and I can't.

OK ... here's my situation. I install ut2004, installs like a champ. However, There's no ut2004 shortcuts in the K start menu, and the ut2004 script doesn't do anything when double-clicked. also the command "ut2004" comes back with a "command not found" message. Strangely, the unistall script works very well.

---

### Post by tgm4883 on 2007-05-15
Look for the 64 bit patch

---

### Post by Josiah4jc on 2007-05-15
Thanks for the tip.. I did that, and some other things and got it all working. For the poor slob following in my footsteps with the same problem, I'll just put down what I did. It's noobified because we noobs have to look out for each other. :) 

note: 3355 isn't the latest version of the ut2004 linux patch, it's just the only one that I found on a site that allowed download resumes ... dialup is a beast.

How to install ut2004 64 bit on Kubuntu 64 bit :

1 install the patch with these commands:

```
wget http://data.unrealtournament.com/ut2004-lnxpatch3355.tar.bz2     
tar xfvj ut2004-lnxpatch3355.tar.bz2
cd UT2004-Patch
cp -R * /home/your_user_name/ut2004
```

2. Go to ut2004/System and rename ucc-bin-linux-amd64 to ucc-bin and ut2004-bin-linux-amd64 to ut2004-bin

3. install missing libraries
```
sudo aptitude install libstdc++5
```

note: you may also need to install this library:
```
sudo aptitude install libsdl1.2debian-alsa
```

4. make a working link
```
cd /home/userName/ut2004/System/
ln -s /usr/lib/libSDL-1.2.so.0
```

the ut2004 script should now work.

---

### Post by Cappy on 2007-05-16
I use the "ut2004-lnxpatch3369-2" patch, it includes fixed AMD64 support. When I installed it I had to change the path in the ut2004 script to point to ut2004-bin-amd64 instead of ut2004-bin. After applying the patch my i386 (ut2004-bin) exec wouldn't run. I don't know if this gives much performance gain or not =p

---

### Post by j388m on 2007-07-14
Thanks for the noobified version.  It helped me.  =D

---

