---
title: "Running Gambas (it is 32 bit) in 64 bit Ubuntu, How ?"
date: 2008-01-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by dptxp on 2008-01-10
Running 32 programs in 64 bit is one thing(never tried yet) but what about running GAMBAS in 64 bit Ubuntu ? They do not have 64 bit package yet.

---

### Post by Kilz on 2008-01-10
> **dptxp said:**
> Running 32 programs in 64 bit is one thing(never tried yet) but what about running GAMBAS in 64 bit Ubuntu ? They do not have 64 bit package yet.

Cappy's fantastic [getlibs script]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") makes installing 32bit applications easy.

---

### Post by dptxp on 2008-01-11
> **Kilz said:**
> Cappy's fantastic [getlibs script]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") makes installing 32bit applications easy.

Thanks Kilz. That is pretty interesting. But will I be able to compile and test run the programs from the 32 bit GAMBAS IDE ? Or do I have to experiment and find it out the hard way ?

---

### Post by Kilz on 2008-01-11
> **dptxp said:**
> Thanks Kilz. That is pretty interesting. But will I be able to compile and test run the programs from the 32 bit GAMBAS IDE ? Or do I have to experiment and find it out the hard way ?

Im not sure, I just know that getlibs will solve install all the needed 32bit libraries, in the correct location fro 32bit programs. If this is a programing application or language you may be better off installing it to a 32bit virtual machine. That can act as a sandbox and make sure that no problems happen to your install from programs you are writing.

---

### Post by jerrylin on 2008-01-11
An easier solution appears to be found here: [http://ubuntuforums.org/showthread.php?p=2559650](http://ubuntuforums.org/showthread.php?p=2559650)

_Quick summary:_
**sudo apt-get install ia32-libs lsb-core**

(include all dependencies of course)

---

### Post by Kilz on 2008-01-11
> **jerrylin said:**
> An easier solution appears to be found here: [http://ubuntuforums.org/showthread.php?p=2559650](http://ubuntuforums.org/showthread.php?p=2559650)

_Quick summary:_
**sudo apt-get install ia32-libs lsb-core**

(include all dependencies of course)

You might want to look at that first post again of that link again. Its a little more than that. Getlibs would make sure everything is installed and the right bit library was in the right location.

---

### Post by dptxp on 2008-01-12
I made separate partition and installed 32-bit Sidux 4.0 LITE to run Gambas. It is not wise to experiment too much with OS when serious work is to be done and in my case I would not know what went wrong. I can experiment in 64 bit Ubuntu later.

This way I learn a bit more too, about KDE (I always find KDE cluttered, pain to navigate) and Debian. I had to configure my network in Sidux for DSL.

Sudux has dynamic CPU frequency control and a monitor. Ubuntu does not use any. Sidux boots fast, runs fast, and seems to be kind on battery. Pretty impressive. And they got nice manual. The forums are not that fast, but I have found help every time.

Thanks to all of you for your help. I shall sure try to run 32 bit GAMBAS in 64 bit Ubuntu in the methods suggested (Getlibs first). After successfully running my test programs in 32 bit.

---

### Post by damvcoool on 2008-03-01
Compile Gambas2 is now working for 64 bit

---

### Post by Pixel_it on 2008-03-04
This is my 64 bit Gambas2 SVN repository 
```
deb http://www.gambas-it.org gutsy gambas
```

---

### Post by dptxp on 2008-03-04
Oh Yes. Finally. I saw on their site a few days back.
But what about the applications we develop in 64-bit Gamabas ?
Can we compile for both 32-bit and 64-bit ?
I will check up anyway in a day or two when I install. 

Thanks.

---

### Post by Pixel_it on 2008-03-04
> **dptxp said:**
> Oh Yes. Finally. I saw on their site a few days back.
But what about the applications we develop in 64-bit Gamabas ?
Can we compile for both 32-bit and 64-bit ?
I will check up anyway in a day or two when I install. 

Thanks.
Not problems..
Project written in Gambas 2.x work in 32 or 64 bit perfectly.

---

