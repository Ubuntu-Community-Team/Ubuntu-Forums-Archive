---
title: "Problems Installing WINE"
date: 2007-12-23
forum: Wine
---

### Post by TolTime on 2007-12-23
New to ubuntu, 

while trying to install wine to get itunes to work,
i get this message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

i have no idea what to do at this point, i also get the same message when i try and install flash, so clearly its human error.

Any help would be greatly appreciated
thanks

---

### Post by cogadh on 2007-12-23
Did you run "sudo dpkg --configure -a"? As the error says, that should correct the problem.

However, you might not want to waste your time with iTunes in Wine, it doesn't really work. None of the store functions will work and any DRM music that you have already purchased through iTunes will be unplayable. Just about the only thing you might be able to do with it (assuming that you can get iTunes to work at all) is manage any non-DRM music you might have, but you can do that much easier with any number of native apps like Amarok.

---

### Post by TolTime on 2007-12-23
i just need Itunes to activate my iphone and thats it

---

### Post by TolTime on 2007-12-23
i got past the step but now when i try to install it i get this message

terence@ternce-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-03-0ubuntu2) but it is not going to be installed
  wine: Depends: binfmt-support (>= 1.1.2) but it is not going to be installed
Depends: libaudio2 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

sorry if some of this is commen since this is all very new to me

---

### Post by TolTime on 2007-12-23
Thanks to everyone who has helped me to get it working, now i just need to figure out how to use it 

thanks,

---

### Post by TolTime on 2007-12-23
i got WINE installed, but am unsure how to work the software, all i want to use it for is for Itunes to activate my Iphone and for WOW.

can anyone help me?

---

### Post by TolTime on 2007-12-23
I got Itunes to install using WINE but once i try to run Itunes it just says that it is starting up and then nothing happens 

has anyone else had this problem, or does itunes not work
i just need it to activate my iphone, im not going to use it for my music

---

### Post by hikaricore on 2007-12-23
I have moved your last two posts from other threads here.
You've already been told that itunes doesn't work well under WINE in this very thread.

Please refrain from "thread jacking" other users threads.  If your posts are not on topic they are out of place there.

Thank you for your understanding.

--Aaron

---

### Post by cogadh on 2007-12-24
Just to confirm, the current version of iTunes that would allow you to activate your iPhone will definitely not work in Wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9692](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9692)

---

### Post by TolTime on 2007-12-25
lol yeah i figured that out, im just going to use my work computer for my phone.  Now comes the daunting task of trying to get world of warcraft to work, but thats for another thread

---

### Post by cogadh on 2007-12-25
Do yourself a favor and use the Ubuntu how-to for WoW:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by hey_ram on 2008-06-30
hi!

i have been trying to install wine by reading and following the steps listed in the sticky...everything works out just fine except the last step which gives me the following error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
E: Broken packages

i do not know if these errors are pretty common or anything..
but instead of starting up a new thread, it might be better to use an existing one,,,

thanx,,

---

