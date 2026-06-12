---
title: "Forcing architecture for .bin files???"
date: 2008-10-22
forum: x86 64-bit Users
---

### Post by MasterNetra on 2008-10-22
I was wondering how would i force the installation of a 32-bit program set to install from a .bin file? would it be " sudo dpkg -i --force-architecture /Something.bin " or what?

---

### Post by jespdj on 2008-10-22
A .bin file is not a standard Debian package file that you can install with dpkg.

You can let programs fool into thinking that they run on 32-bit Linux by starting them with linux32. For example:
```
linux32 uname -m
```
will show "i686" if you run it on 64-bit Linux. If you have an installation program that checks if it's on 32-bit Linux, you can try:
```
linux32 somefile.bin
```
Beware, however, that this might not install the program correctly. You might need to use [getlibs](http://ubuntuforums.org/showthread.php?t=474790) to install the necessary 32-bit libraries.

Is there a specific program that you are trying to install? Are you sure that there is no 64-bit native version of the program available?

---

### Post by MasterNetra on 2008-10-22
I tried to intially get adobe air in... but the result

```
agent7662@NexCore3200:~/Downloads$ linux32 ./adobeair*.bin
Error loading the runtime (libnss3.so: wrong ELF class: ELFCLASS64)
```

How would i use getlibs to get the basic set of 32bit libraies?

---

### Post by jespdj on 2008-10-22
That error message means that the 32-bit program is trying to load a 64-bit library, which doesn't work.

I don't use getlibs everyday, so I don't know. Did you click the link to the information about getlibs? How about trying this:
```
getlibs adobeairblahblah.bin
```
Or:
```
getlibs -l libnss3.so
```

---

### Post by MasterNetra on 2008-10-22
Well i tried using getlibs with the adobe bin files itself as you suggested and it claims its not missing anything, as for using getlibs for libnss3.so it just hangs there and does nothing.

---

### Post by RaveJunkie on 2008-11-23
I am having the same issue and the fix above didnt work for me either......    other forums listed that im just SOL until adobe supports 64bit..... this true?

---

### Post by Yellow Pasque on 2008-11-23
I was at least able to get the program to install:
```
sudo apt-get install ia32-libs
sudo getlibs -p libxslt1.1 libnss3-1d
```
Download the installer (.bin file). The installer uses dpkg, so make sure you don't have any Synaptic, Update-Manager, or any other program installer apps open.
```
cd <wherever you downloaded the file>
chmod +x adobeair_linux_b1_091508.bin 
./adobeair_linux_b1_091508.bin
```

---

