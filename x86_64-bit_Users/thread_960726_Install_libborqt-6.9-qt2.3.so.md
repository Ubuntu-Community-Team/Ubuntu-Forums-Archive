---
title: "Install libborqt-6.9-qt2.3.so"
date: 2008-10-27
forum: x86 64-bit Users
---

### Post by Friqenstein on 2008-10-27
Good day all,

I've acquired a program which requires the following library file:
libborqt-6.9-qt2.3.so

I'm having trouble finding a 64bit version of this library for my lappy. I'm running HH-64bit. I've already attempted to go to the site suggested by the original program, but that is a sourceforge site, and it doesn't list anything newer than version 3.2 for that library, and they are all i386 based.

How/where do I obtain this library file?
Can't seem to find anything related to the Synaptic regarding libraries in general, which I find quite annoying actually. Yes I know it's a 'package manager', but still one would think it would be able to sort out issues like missing libraries, or atleast the search would tell you what is what.

At any rate, does anybody know, or had experience with this before?
Any help is greatly appreciated.
Thanks.

---

### Post by Yellow Pasque on 2008-10-27
If the library's only available in 32-bit form, then perhaps you should run the 32-bit version of the program you're trying to run. Getlibs will help you if you go that route. [http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)

---

### Post by Friqenstein on 2008-10-28
> **Temüjin said:**
> If the library's only available in 32-bit form, then perhaps you should run the 32-bit version of the program you're trying to run. Getlibs will help you if you go that route. [http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)
Thanks for the reply,
Well I have **getlibs** installed already. I guess I forgot to mention that. I've run **getlibs** on my program (*which is 32-bit program only*) and it says there are no missing dependencies.
However, when I attempt to run the program, it fails with an error on the command line:```
libborqt-6.9-qt2.3.so: cannot open shared object file: No such file or directory
```
So what I did instead, which took me a moment to remember I could do it this way, was:```
getlibs -l libborqt-6.9-qt2.3.so
```
Once it started, it installed teamspeak-client program. Once it was done, I ran an **ldconfig** and then tried my program once again. It's still telling me it cannot find the library file.

---

### Post by Friqenstein on 2008-10-28
Another update,

Ok, so the program originally said I'd need the libborqt-6.9-qt2.3.so, and it said it would be available from the following link:
[http://kylixlibs.sourceforge.net/down.html](http://kylixlibs.sourceforge.net/down.html)
However, that site doesn't list the correct version of the library file. I downloaded it anyway, and my system will not accept it because I'm running 64-bit ubuntu.

I also tried to download the kylix lib package, and did a forced install with dpkg, which stalls then aborts because it says I don't have xlibs installed.
So I used Synaptic to install xlibs-data. After that I retried the kylix lib package.. it still says I don't have xlibs installed.
This is getting annoying.

Does anybody have a clue to this?
Thanks.

---

### Post by Kilz on 2008-10-28
> **Friqenstein said:**
> 

I also tried to download **the kylix lib package, and did a forced install with dpkg**, which stalls then aborts because it says I don't have xlibs installed.
So I used Synaptic to install xlibs-data. After that I retried the kylix lib package.. it still says I don't have xlibs installed.
This is getting annoying.

Does anybody have a clue to this?
Thanks.

Never, ever, ever, ever force install libraries. The reason is that if you do, 32bit libraries will overwrite any existing 64bit libraries of the same name. This is because of the location that 32bit libraries are stored in in a 64bit install. I hope you have not fubar'd your system.

---

### Post by Friqenstein on 2008-10-28
> **Kilz said:**
> Never, ever, ever, ever force install libraries. The reason is that if you do, 32bit libraries will overwrite any existing 64bit libraries of the same name. This is because of the location that 32bit libraries are stored in in a 64bit install. I hope you have not fubar'd your system.My system is fine.. so how can i overwrite a file that didn't exist in the first place?

Is there any other info you'd like to share?

---

### Post by Kilz on 2008-10-29
> **Friqenstein said:**
> My system is fine.. so how can i overwrite a file that didn't exist in the first place?

Is there any other info you'd like to share?

Then you are lucky. The advice is still important in that someone else may read this thread looking for answers. 

The reason is this. 

In 64bit (AMD64) installs 64bit libraries are in /lib and /usr/lib and 32bit libraries are in /lib32 and /usr/lib32

In 32bit (i386) installs 32bit libraries are in /lib and /usr/lib

When you force install a 32bit library, if the library exists on a 64bit install, it will be overwritten with the 32bit version you force in. The system will not see it or use it.

But getting back to your issue, I do have one question, about the application. Was it compiled and packaged for Ubuntu? What is it and where can I get a copy of it?

There is [one package that contains the file. ]("http://packages.ubuntu.com/hardy/teamspeak-client") You might try installing it and then moving the library to /usr/lib. If you need the 32bit version have getlibs install it for you. Its in the multiverse, make sure its enabled if you cant find the application in synaptic.

---

### Post by Friqenstein on 2008-11-02
> **Kilz said:**
> ... I do have one question, about the application. Was it compiled and packaged for Ubuntu? What is it and where can I get a copy of it?It is a proprietary program. The only way to obtain it is to buy the hardware that it interfaces with.
Having said that, I've spoken with the supplier/manufacturer, and he told me that the application is originally developed on/for Linux and later ported to windows for those that use windows. The program comes in on a CD with the purchase of the hardware.
The program doesn't specify whether it is strictly 32-bit or 64-bit, but it's safe to assume that it was written as a 32-bit app.

> There is [one package that contains the file. ]("http://packages.ubuntu.com/hardy/teamspeak-client") You might try installing it and then moving the library to /usr/lib. If you need the 32bit version have getlibs install it for you. Its in the multiverse, make sure its enabled if you cant find the application in synaptic.I've already installed the Teamspeak client package... as stated above in one of my previous posts. But still, it doesn't work. The Teamspeak program works, but the other program is still complaining it cannot find that stupid library file.
I went as far as copying the library file from the /usr/lib/teamspeak dir and tossed it into the /usr/lib directory. ldconfig... still no joy.

---

### Post by Friqenstein on 2008-11-02
Ok, I got it. I just coppied the library to the /usr/lib32 dir and now the program works... I originally coppied it to the /usr/lib.
So this also proves it was a 32-bit program.

Is there a way to check which version/arch of a library you have installed? Other than navigating to the /usr/lib or /usr/lib32 everytime?

The teamspeak program was installed originally, however it didn't put a symlink to the library file even after ldconfig. Kinda odd I think.

---

