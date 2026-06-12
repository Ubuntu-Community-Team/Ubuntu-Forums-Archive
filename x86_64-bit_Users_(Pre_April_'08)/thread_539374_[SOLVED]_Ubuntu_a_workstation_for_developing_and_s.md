---
title: "[SOLVED] Ubuntu a workstation for developing and scientific calculations???"
date: 2007-08-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by gnusci on 2007-08-31
Hello guys,

I just installed a new Xubuntu 7.04 x86-64... I am very happy with this, it is fast and lite. but, I just trying to compile some codes that I have compiled before in many other platforms without any inconvenient. I know that Xubuntu it is not the be choice for this kind task, but I choose it because I do no want to waist CPU and RAM with a heavy desktop. 

So does anybody know how to become Xubuntu in a good C/C++ developing workstation?

I am working on scientific calculations so for me CPU and RAM are completely important.

---

### Post by Harpoon on 2007-08-31
I don't have an answer for you, but I have some advice.  Someone with enough experience will ask questions like what are you trying to compile, what problem did you have, what errorss were shown (and then ask you to post the error output).  I offer this as a suggestion to prepare for a more knowledgable individual's questions so help can proceed quickly, and efficient;y.

Good luck with this.

---

### Post by gnusci on 2007-08-31
Sorry, here is output message:

```

oppenheimer:~/src/fltk-1.1.7$ ./configure 
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

BTW: I also will need Mesa GL (or OpenGL) libraries... Sorry for so many question I am new with Ubuntu.

---

### Post by Jouke74 on 2007-08-31
Look for the "build-essential" package under Synaptic and install this one.

Or in terminal: sudo apt-get install build-essential

This will install the compilers and libraries needed.

If you have done this, first check the log file for what it is missing.

---

### Post by gnusci on 2007-08-31
Thanks Jouke74,

It solved the problem with the compiling tools, now I need to install the X11 libraries, this is the output error:

```

checking for X... no
configure: error: Configure could not find required X11 libraries
./configure: line 10022: exit: aborting.: numeric argument required
./configure: line 10022: exit: aborting.: numeric argument required

```

TIA

---

### Post by gnusci on 2007-08-31
I found the solution to the X11 libraries in the thread:

[http://ubuntuforums.org/showthread.php?t=389984](http://ubuntuforums.org/showthread.php?t=389984)

And I have used the following commands to prepare my workstation:

```

sudo apt-get install mc                 (File manager)

sudo apt-get install build-essential (compiling tools)
sudo apt-get install freeglut3-dev   (open gl)
sudo apt-get build-dep xorg-dev     (x11 for developing)


```

---

### Post by Jouke74 on 2007-08-31
Probably, if you start to compile more things, you will going to need more "dev" = development libraries. Anyway, have fun. I compiled load of genetic programs and simulations. Another useful part of installing may be the 32 bit libraries. Some programs that are compiled may not run otherwise. 

That is sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2

Another useful one is "checkinstall"

Instead of installing a program with "sudo make install" you can use "sudo checkinstall -D" instead. This will create a debian file which you can install through the package manager. That way it is easier to remove it afterwards.

---

### Post by gnusci on 2007-09-01
Thanks a lot Jouke74,

That is a great information, now I know better about the appropriate way to make a powerful workstation from Xubuntu....

---

### Post by stmiller on 2007-09-01
And hey you should try Synaptic
```

sudo apt-get install synaptic

```
to search for package libraries. It is good for finding something when you don't quite know the exact package name.

---

### Post by gnusci on 2007-09-02
> **stmiller said:**
> And hey you should try Synaptic
```

sudo apt-get install synaptic

```
to search for package libraries. It is good for finding something when you don't quite know the exact package name.

Yes I did use Synaptic, but after ask for "x11 dev lib" I got a bloated answer that just messed me up... so that why I did not find another option that ask directly in to the forum....

---

