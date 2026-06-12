---
title: "not able to install any software .....i am now as a sudo user"
date: 2008-08-21
forum: x86 64-bit Users
---

### Post by mithrandiruk1 on 2008-08-21
[email]root@uday-desktop:/usr/local/etc/WRF/gcc-4.1-4.1.2.orig[/email]/gcc-4.1.2# ./configure 
loading cache ./config.cache
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking build system type... i686-pc-linux-gnulibc1
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.


i need to get this resolved quickly i dont know  why gfortran and any of the applications that i try to install dosent work i am using ubuntu 7.10

thanks for ur support

---

### Post by felker2 on 2008-08-21
1) It's correct that only su / root / superuser can install software.

2) gfortran is in the Ubuntu packages repository (proof: [http://packages.ubuntu.com/hardy/gfortran](http://packages.ubuntu.com/hardy/gfortran)), so I advice you to the install the package via the GUI (= the easy way, sudo-password needed), or via the CLI ("sudo apt-get install gfortran"). This method is much easier and safer than compiling it yourself.

HTH

---

### Post by mithrandiruk1 on 2008-08-21
> **felker2 said:**
> 1) It's correct that only su / root / superuser can install software.

2) gfortran is in the Ubuntu packages repository (proof: [http://packages.ubuntu.com/hardy/gfortran](http://packages.ubuntu.com/hardy/gfortran)), so I advice you to the install the package via the GUI (= the easy way, sudo-password needed), or via the CLI ("sudo apt-get install gfortran"). This method is much easier and safer than compiling it yourself.

HTH

Actually its the first or should i call it the basic step of installation of a application which i need to use ,and i have to compile it ......if i cant sort out the gcc "not work" issue i cannot install my application and i am delayed with 3 weeks of work just because of installations not working.i switch from FC 9 to ubuntu 7.10 and my fc nine crashes and its beyond repair.I have got back to a position where i was 3 weeks ago and have no clue wht should be done with gcc not working .....and i have a presentation on my software at 4 pm (IST) today its allready 3 pm .

---

### Post by Thelasko on 2008-08-21
> i need to get this resolved quickly i dont know why gfortran and any of the applications that i try to install dosent work i am using ubuntu 7.10
To install fortran, open the terminal and type:
```
sudo apt-get install gfortran
```
**You shouldn't install it from source, as you appear to be trying to do.**

To obtain root privileges type "sudo" before the command you are entering.

---

### Post by Yellow Pasque on 2008-08-21
For future reference:
```
sudo apt-get install build-essential
```

---

