---
title: "Blender 2.43"
date: 2007-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by dsegarra on 2007-02-23
Help!. I want to run the latest Blender version 2.43 on my AMD 64 system. It works on a 32Bit system but not on my AMD64. Any leads?.


thanks

Dan

---

### Post by dfreer on 2007-02-23
Blender 2.42a is available through the repositories... but you want Blender 2.43 eh?
First open a terminal and download Blender 2.43:

```
wget -c http://download.blender.org/release/Blender2.43/blender-2.43-linux-glibc232-py24-i386.tar.bz2
```

Extract the file:
```
tar xvf blender-2.43-linux-glibc232-py24-i386.tar.bz2
cd blender-2.43-linux-glibc232-py24-i386
```

Run the program!:
```
./blender
```

Let us know if you have any more problems!

EDIT: It runs fine on AMD64... do you have 32-bit libs installed and all of Blender's Dependencies installed? If you have already downloaded and tried to run Blender 2.43, did you get any errors?

---

### Post by dsegarra on 2007-02-23
dfreer,
Thanks for your help. I did tried everything you wrote. The error I get has to do with libSDL. I have them installed though. The only way it worked was downloading a build from blender forums that was compiled on a 64bit environment. Thanks again.

Probably I just have the 64bit libraries. I tried installing 32bit libraries but it broke a lot of dependencies for other software.

---

### Post by Aldrik on 2007-02-24
dsegarra, you should know that it is currently not recommended to use 64bit versions of blender as they do not save the .blend files correctly and they will not work in newer (fixed) versions of blender.

---

### Post by dsegarra on 2007-02-24
Really?. Good to know. I think I read something about it or I should say, read a post by Ton that they were working on a 64Bit version. Thanks

---

### Post by radopenev on 2007-02-27
Hi ,for all !Help!
Please , dfreer  from what repositories is Blender 2.42a available?
I'm 6.06LTS user  and install Blender by Synaptic .But
ver. is 2.41.
I did tried everything you wrote,dfreer.
The error  with libSDL is too hard for me ...I tried to install lidSDL by Synaptic,but the situation
is the same.
Sorry for my English.Best regards!

---

### Post by Smitje on 2007-02-27
I folowed the instructions but I get the following error:
```
MyHome/install/blender-2.43-linux-glibc232-py24-i386$ ./blender
guessing './blender' == 'MyHome/install/blender-2.43-linux-glibc232-py24-i386/./blender'
Compiled with Python version 2.4.
Checking for installed Python... got it!
Ignoring Xlib error: error code 169 request code 147
Ignoring Xlib error: error code 169 request code 147

```

It all seems to work fine until i run any script, selfmade or included doesn't matter. 
import Whatever # alt p
is enough to give the following error:
```
Traceback (most recent call last):
  File "Text.001", line 1, in ?
ImportError: /usr/lib/python2.4/lib-dynload/math.so: wrong ELF class: ELFCLASS64

```

I'm guessing it wants 32 bit python
can annyone who knows what their doing indicate if that could be right?
  and then tell me how to get 32 bit python without braking everything else on my machine.
please.

Cheers Smitje

---

### Post by dfreer on 2007-02-28
> Hi ,for all !Help!
Please , dfreer from what repositories is Blender 2.42a available?
I'm 6.06LTS user and install Blender by Synaptic .But
ver. is 2.41.
I did tried everything you wrote,dfreer.
The error with libSDL is too hard for me ...I tried to install lidSDL by Synaptic,but the situation
is the same.
Sorry for my English.Best regards!

Blender 2.42a is available from the standard universe repositories for Edgy 6.10. You could try downloading the amd64.deb from [URL="http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Funiverse%2Fb%2Fblender%2Fblender_2.42a-1ubuntu1_amd64.deb&md5sum=e80237d3d78d31bbfc45d884108a76a0&arch=amd64&type=main"]*_packages.ubuntu.com_*
[/URL].

```
sudo aptitude install ia32-libs-sdl
```

Should take care of any libSDL problems you have. If you have any more errors with it you could always post your errors :)

EDIT: Smitje, as I don't use blender myself I didn't bother to test the install. However, I got the same error as you. One solution would be to use --force-architecture to install a 32-bit version of python, but that will surely hose up your 64-bit install. If you can't find a amd64 package that installs a 32-bit version of python, and you REALLY need to use blender on a AMD64 system, you could try manually extracting the files you need and putting them in your /usr/lib32 folder. I wouldn't recommend doing this unless you know what your doing and what the consequences are.

---

### Post by radopenev on 2007-03-01
:) God bless you,dfreer!
1.I downloaded : blender-2.43-linux-glibc232-py24-i386.tar.bz2  from blender.org
2.save and unpack in my home directory
3.according with your advice : 
      sudo aptitude install ia32-libs-sdl
4.     ./blender
5.Everything is OK 
Now I  have installed Blender2.43 and Blender2.41(I'll uninstall ver.2.41 when sure that ver.2.43 is OK )
Thanks,thanks,thanks for your help!
Sorry for my English.Best regards!

---

### Post by dfreer on 2007-03-01
Anytime :D

---

### Post by Unterseeboot_234 on 2007-03-02
I may try your ia32 install. But, I sure wanted to stay 64. But, I really, really like the new plug-in in Blender 2.43 that lets you modify a mesh model with a paintbrush and the dropcloth feature.

So, another forum post has:

```
sudo apt-get build-dep blender
```
that works. works good.

Then, I used the scons method (instead of make). That works. Works good. Makes an executable in fact.

cd to the new blender
```
./blender
64 bits compiles will give incorrectly saved .blend files. Do not use it. For testing purposes please remove this line from creator.c
```

Weirdest build to date for me. Rosegarden build failed. Blender build works but fails. Rosegarden because of hardware design (it wants a synthysizer and nobody tells you that). Blender fails because it's not ready yet for 64 and nobody mentions that little fact.

---

### Post by dfreer on 2007-03-02
> I may try your ia32 install. But, I sure wanted to stay 64.
From what was mentioned earlier it looks like 64-bit versions of Blender cannot make .blend files, so it is probably best to install the 32-bit version in the 64-bit enviroment. Seems that a lot of the programs on my 64-bit system are 32-bit builds.. but since I really don't *need* the performance boost (at most I might transcode some DVD's) I don't care much. I just been enjoying the learning process so far. :D

> Then, I used the scons method (instead of make). That works. Works good.
I haven't heard of this tool... looks very interesting, I might give it a whirl on some of my other packages, thank you.

---

### Post by christoffer on 2007-03-03
> **Aldrik said:**
> dsegarra, you should know that it is currently not recommended to use 64bit versions of blender as they do not save the .blend files correctly and they will not work in newer (fixed) versions of blender.

What version do you refer to as "current"?
What versions are effected and which one is the first one that it's fixed in?

Where have you read this, I've done searches on blender.org and their bug tracker and I have yet to find any information on it. Url, please?

---

