---
title: "help with ./configure"
date: 2007-11-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by LordVeovis on 2007-11-28
Um, this may sound dumb, but I dont understand.... I have seen in alot of places to type ./configure to set up several different things.  I have never gotten this command to work, I always get "bash: configure: command not found" returned to me... why?

Thanks.

---

### Post by rsambuca on 2007-11-28
You need to install the following package first

sudo apt-get install build-essential

---

### Post by sirdilznik on 2007-11-28
> **LordVeovis said:**
> Um, this may sound dumb, but I dont understand.... I have seen in alot of places to type ./configure to set up several different things.  I have never gotten this command to work, I always get "bash: configure: command not found" returned to me... why?

Thanks.
The configure command is generally used for compiling programs from source.  That is something that is generally NOT done on a binary distribution like Ubuntu, but that doesn't mean it can't be done.  The command is preceded by "./" without the quotes to signify to the OS to run the command from within the current working directory (rather than globally).  If successful the ./configure command would generally be followed by
```
make
make install
```
make builds the actual program and make install puts the necessary executables and links in the correct places (you need administrator rights for this step)

If you didn't understand the preceding then you probably shouldn't be compiling programs by hand at this stage.

Note:  I do not mean to sound condescending, but it seemed like you didn't understand what ./configure did and thus probably shouldn't be messing around with it right now.  If I am incorrect I apologize.

---

### Post by LordVeovis on 2007-11-28
haha, not quite, it sounds like I have no idea at all, which is mostly true (new to linux) bnut very knowledgeable on the workings of a pc and the command line type structure.

I am working on installing projectM and am having problems, I am getting an error when trying... durring the process tho i am supposed to run ./configure then yes, like you said, make and then make install... the problem is ./configure command doesnt execute, and I tried to install the package recomended above just to be told it was already installed...

what could the problem be?

---

### Post by Clancy_s on 2007-11-28
If you're trying to install the latest projectM it doesn't use /.configure.  It uses 

cmake

instead.  This started with v 1.0, prior to the it did use /.configure.  You're getting the error because there's no 'configure'  in the directory.

Take a look in the readme file and the install file:

[quote=projectM install]Install FTGL(optional) and GLEW, then:

cmake . -DCMAKE_BUILD_TYPE=RELEASE
make
make install

You may need to type ccmake . and change the PREFIX if your system prefers /usr instead of /usr/local.[/quote]

I don't know if it'll work btw: I tried it on my desktop machine using Xandros but it looks like Xandros' current release is too old to install projectM properly.  There are no ATI drivers for the video card on the laptop I have Ubuntu on so I've not tried it there.

eta: it looks from your other post you know about cmake instead, so maybe you have a different problem.  The above was the source of the error in my case.  There should be a file called 'configure' in the directory you're in, that's what the command /.configure is calling.  If it's not there you'll get the 'command not found' error.  If you *do* have 'configure' in the directory you're trying to run it from I don't know what the problem is. :(

---

### Post by LordVeovis on 2007-11-28
the problem I have with projectM is referenced here, [http://ubuntuforums.org/showthread.php?p=3842568#post3842568](http://ubuntuforums.org/showthread.php?p=3842568#post3842568)

but regardless of that, ./configure still doesn't work for me...

---

### Post by LordVeovis on 2007-11-29
hmm, I never looked to see if there was a config file, I just assumed it to be a universal command or something as several programs i have seen say to extract files... then do ./configure, folowed by make, and make install...so i figured i have to be missing something if everytime i try ./configure i can't do it.

---

### Post by Clancy_s on 2007-11-30
So what version of project M are you trying and do you have a file called 'configure' in it?

/.configure is the most common first step that I've encountered but there are others: cmake, as discussed (seems to be newer) and /.autogen are others.

the 

/. means look in the current directory, so

/.configure tries to call a script or command called 'configure' in the current directory.  If there isn't one you'll get the 'command not found error'.

---

