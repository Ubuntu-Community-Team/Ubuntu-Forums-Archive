---
title: "Intel Fortran 10.0 install"
date: 2007-07-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by mohshee on 2007-07-24
Hi

I am getting a strange error message when I try to install the intel fortran 90 compiler (v 10.0). I have an AMD 64 bit CPU. 

I've checked all the nominal problems, as addressed in other threads. All the install files are bash instead of .sh, etc. But as soon as I try to run:

> sudo ./install.sh

I get the immediate error:
 
ERROR: Problem encountered executing CHKLIC_32_64 utility located here:
    /home/mohshee/downloads/l_fc_p_10.0.023_intel64/data/chklic.em64t

The CHKLIC_32_64 program data/chklic.em64t requires these libraries:
        not a dynamic executable

I have tried manually changing the location of my license file and I have tried re-downloading, re-installing, etc. I can't find out what is going on. The file  data/chklic_em64t is, indeed, a binary executable file. Anyone have any hints?

thanks

---

### Post by mohshee on 2007-07-24
P.S. I have Fiesty Fawn (64 bit) installed and never had this problem using the intel fortran 9.1 on FF (32 bit) on my laptop. I tried installing the 9.1 version on this computer, but get this same error message.

---

### Post by j4play on 2007-08-19
installing lib32gcc1 fixed this for me.

---

### Post by belerophonte on 2007-08-23
That solution solved my problem of starting the installation, but further ahead it tells me that:

The installation program was not able to detect the IA-32 version of the following libraries installed   :  
libstdc++
libgcc
glibc

I've tried everything to install these libraries, but somehow I can't get them and I get stuck.

I have a x86_64 2.2Ghz Intel Core2 Duo with Feisty on it.

Any help is appreciated. Thanks in advance.

---

### Post by jand23 on 2007-08-24
Hey, I have the same problem.
It seems as if some shared libraries are missing.


/opt/intel/fce/10.0.026/bin/fortcom: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
ifort: error #10257: Fatal error in /opt/intel/fce/10.0.026/bin/fortcom, terminated by 0x7f
----------------------------------------------------
Problems with Fortran compiler: <file not found>!=< Hello, World!  F90>


On intels Site, they say that I need to get the package compat-libstdc++
[http://www.intel.com/support/performancetools/sb/CS-026141.htm](http://www.intel.com/support/performancetools/sb/CS-026141.htm)

I installed that package with alien but it did not seem to do the trick.
I am on a mac pro with 2 X5365 xeons running the latest ubuntu server for X86_64.
I intend to use ifort with openMPI.

Any help/insight is greatly appreciated.

Cheers, Jan

---

### Post by belerophonte on 2007-08-24
Hey people...Solved the hard way.

   Since no other program is using the libstdc++.o.5, I replaced the libstdc++.o.5.0.7 (64bits) for the libstdc++.o.5.0.7 (32bits) in the /usr/lib/ folder manually and then installed fortran ignoring the missing IA32 packages. Now fortran works great and don't forget to back it up.

Hope it helps.

---

### Post by aleksandross on 2007-08-27
Unfortunately this causes the idb debugger not to work because it needs the 64 bit version of the libstdc++5 library.

Instead try installing the following packages prior to ifort installation:

* lib32gcc1
* ia32-libs
* libstdc++5

Then ifort and idb should install normally using the install.sh script provided.

---

### Post by ifbird on 2007-10-24
I come to this forum today because of this problem.
I have intel dual core 64-bit cpu.
When I installed the lib32gcc1,libstdc++5,the problem was solved.
But I encountered another problem: invalid license file.
I give the absolute path of the lic file,but it says the file is a invalid file.
I don't know why.
Any help is appreciated, thanks.

---

