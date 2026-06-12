---
title: "How to compile SPECViewperf"
date: 2009-03-14
forum: x86 64-bit Users
---

### Post by zergling on 2009-03-14
Hi my friends penguins :D
I am opening this thread because I would like to help people to compile this wonderful benchmark suite called SPECViewperf.
The steps are very easy to follow and this should work also in Ubuntu. I did this on Debian Lenny.

First of all, if you do not have yet the program go to [http://www.spec.org/gwpg/downloadindex.html](http://www.spec.org/gwpg/downloadindex.html)

open up your terminal

Applications -> accessories -> Terminal

go where you have downloaded the file and type

```
tar -xzf SPECViewperfxx
```  

(where xx is the version)

go in /SPECViewperfxx/viewperf/viewperfxx.x/src


```
sudo apt-get install build-essential libaa1-dev libartsc0-dev libasound2-dev libaudio-dev libaudiofile-dev libcaca-dev libcucul-dev libdirectfb-dev libdirectfb-extra libesd0-dev libglib2.0-dev libjpeg62-dev libmpeg3-dev libncurses5-dev libpng12-dev libsdl-gfx1.2-4 libsdl1.2-dev libslang2-dev libsvga1-dev libsysfs-dev
libasound2-doc libglib2.0-doc libsdl-gfx1.2-dev
```

type 

```
uname -a
```

to know which architecture you are currently running (32-64 bits) 
(you will need this info during compile time)

```
./Configure
```

select your architecture 32 or 64 bits

select the compiler; by default should be GCC

if everything went fine 

```
cd ..
``` 

To run all the benchmarks

```
./Run_All.csh
```

or just for maya for example

```
./Run_maya.csh
```

That is all.

Bye my brothers penguins and take care.

---

