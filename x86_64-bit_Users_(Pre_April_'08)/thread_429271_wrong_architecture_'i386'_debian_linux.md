---
title: "wrong architecture 'i386' debian linux????"
date: 2007-05-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by cool_mast on 2007-05-01
I got the error when  i tried to install .deb packages.What is this???I am having amd64 processor

---

### Post by cool_mast on 2007-05-01
pls help!!!!!!!!!!

---

### Post by Jouke74 on 2007-05-01
You could start by selecting AMD64 / I686 packages... :mrgreen:

---

### Post by cool_mast on 2007-05-01
thats ok,but How i can download if it is not available????
Or is there is not the other way out or amd 64 bit users will have to sit like a dumb in front of linux machine as they r not able to install anything??

---

### Post by Jouke74 on 2007-05-01
This is the mean reason for this forum, and also why you need to be very specific in what piece of software you are trying to install... I can't look into my crystal ball and give you more help.

Here are some pointers: 

1: Go to synaptic package manager > type the name in search for the software that you want to install > if it's there install the software. To make this work optimally, enable all repositories. If this is still a black box for you, read, read, read all information about how to install software under linux. 

2: If 64 bits software packages are not available see the first two stickied posts on this forum.

3: Install the 32 bit libraries for software : IA32 libs plus dependencies (again more forum and other reading).

4: If there is no way out: download the source code of the software, install the build essential package, compile the software yourself. (that requires more linux knowledge).

I am sorry but there is no other way.

---

### Post by ronocdh on 2007-05-01
Cool_mast, you may find this command useful:
```
dpkg --force-architecture
```

---

### Post by Tanker Bob on 2007-05-01
The following works great for me:

```

dpkg -i --force-architecture mypackage-1.0-i386.deb
```
Where mypackage-1.0-i386.deb is the 32-bit software you wish to install.  As jouke74 said, you'll probably need to install the ia32-libs and its dependencies.  I've gotten the few 32-bit programs that aren't available in 64-bit yet to work this way.

---

