---
title: "Forcing Architecture"
date: 2008-05-17
forum: x86 64-bit Users
---

### Post by Thunderman on 2008-05-17
Only a few days old in the Linux world, but i am loving it so far :)

One error i keep getting though is "wrong architecture" while trying to run a packaged software that I downloaded.  I read on the forums here that the 

```
 sudo dpkg -i --force-architecture *.deb
```

command may fix this for me, but i am not sure how to use it......I am very new to the terminal.  Thanks for any help on this :) .

---

### Post by macaholic on 2008-05-17
The first thing you want to do is 'cd' (change directory) to the directory the files are in. For example, if they were on your desktop, you would type:```
cd Desktop
```
Then you run ```
sudo dpkg -i --force-architecture <name of file>.deb
```
For long file names, you can type part of it and then ues the '*' to enable the wildcard for the rest of the name.
Also, what packages are you trying to install?

---

### Post by Thunderman on 2008-05-17
Awesome, thanks  mac.

I am trying to get a couple meterology analysis progs to install.  Thanks to you, I got the packages installed and can move on to configuring them :D.

Thanks again.

---

### Post by macaholic on 2008-05-17
Just curious, what are the names of the programs?

---

### Post by Kilz on 2008-05-17
> **Thunderman said:**
> Only a few days old in the Linux world, but i am loving it so far :)

One error i keep getting though is "wrong architecture" while trying to run a packaged software that I downloaded.  I read on the forums here that the 

```
 sudo dpkg -i --force-architecture *.deb
```

command may fix this for me, but i am not sure how to use it......I am very new to the terminal.  Thanks for any help on this :) .

Just remember , never, ever, force in libraries. Instead [use getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") for libraries.

---

### Post by Thunderman on 2008-05-17
> **macaholic said:**
> Just curious, what are the names of the programs?

One was an add on for a program called GEMPAK (which i have yet to get running :confused: ).  Another was a web cam add on for a program called "Free WX".  The last was a web authoring program i downloaded called "NVU" to get a photography website going.

> 
Just remember , never, ever, force in libraries. Instead use getlibs for libraries. 

Note taken.  Thanks, for the tip :D

---

### Post by Grishka on 2008-05-17
NVU is called Kompozer now, and there is an up-to-date 64-bit version in the repos.

---

### Post by Thunderman on 2008-05-17
> **Grishka said:**
> NVU is called Kompozer now, and there is an up-to-date 64-bit version in the repos.

Oh really?  Ill uninstall mine and install from the repos list then.  Thanks for telling me.

---

