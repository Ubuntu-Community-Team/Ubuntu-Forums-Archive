---
title: "How do I get my system to run at 64bit?"
date: 2007-08-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by chewy86 on 2007-08-19
Hi, I am so confused.  I have been using Ubuntu for about 3 months and really haven't had great success.  But I am sticking with it because I want to step away from windows and really get into LAMP stacks.  But anyway, I am running an AMD Athlon 3200.  In order to run at 64 bits do I need to actually install a 64 bit version of Ubuntu, or has it already done what it needs to so it will run at the right speeds?

Sorry if this is already posted; have looked but cannot find it anywhere!?!?

Thank you so much.

---

### Post by markusf21 on 2007-08-19
If u want to run at 64 bit then u have to use the 64 bit ubuntu

---

### Post by jpkotta on 2007-08-19
You need the amd64 version of Ubuntu rather than the i386 version.  Otherwise you will be running in 32-bit mode.

---

### Post by daveshields on 2007-08-19
You say you haven't had "great success" running Ubuntu, and ask how to move to 64 bit.  You probably won't find much difference in going to 64 bit unless you need to run applications with very large memory requirements. 

Is this why you want to move to 64 bit? If not, please provide some details on your problems, and I'm sure you'll get some useful input  from the community forthwith.

---

### Post by chewy86 on 2007-08-19
Some issues I have had include, my video not running very smoothly, not being able to get some programs to run, but mainly it's the video thing so I was hoping that when if I upgraded to the 64 bit it would run smoother.

---

### Post by Kilz on 2007-08-19
> **chewy86 said:**
> Some issues I have had include, my video not running very smoothly, not being able to get some programs to run, but mainly it's the video thing so I was hoping that when if I upgraded to the 64 bit it would run smoother.

What video card do you have, and have you installed the driver from the company that makes it?

---

### Post by John.Michael.Kane on 2007-08-19
> **chewy86 said:**
> Hi, I am so confused.  I have been using Ubuntu for about 3 months and really haven't had great success.  But I am sticking with it because I want to step away from windows and really get into LAMP stacks.  But anyway, I am running an AMD Athlon 3200.  In order to run at 64 bits do I need to actually install a 64 bit version of Ubuntu, or has it already done what it needs to so it will run at the right speeds?

Sorry if this is already posted; have looked but cannot find it anywhere!?!?

Thank you so much.

To see if the machine is running a 64bit kernel you can run the command below
```
uname -a
```

Example uname -a output 
```
Linux (your machine name here) 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 **x86_64** GNU/Linux
```

If the output does not match this then your running a 32bit kernel.

> **chewy86 said:**
> Some issues I have had include, my video not running very smoothly, not being able to get some programs to run, but mainly it's the video thing so I was hoping that when if I upgraded to the 64 bit it would run smoother.

For us to help with this we are going to need your gpu model/make

Also it would help if you told us what your using the machine for, As you say you want run LAMP,however. LAMP runs are done on server infrastructure, and you state above that video is not running very smoothly which is usually a issue under a desktop install. So are we talking about two machines with two different problems or one machine.

---

### Post by chewy86 on 2007-08-19
> **Kilz said:**
> What video card do you have, and have you installed the driver from the company that makes it?  I am running a ati 9550, I installed the driver glrx driver I think, the open source one not the one from ati.

---

### Post by chewy86 on 2007-08-19
> **SD-Plissken said:**
> 

Also it would help if you told us what your using the machine for, As you say you want run LAMP,however. LAMP runs are done on server infrastructure, and you state above that video is not running very smoothly which is usually a issue under a desktop install. So are we talking about two machines with two different problems or one machine.

I am using my computer for a little bit of everything, I mainly browse the internet.  But I also am using it to edit videos, do some basic web design,  do graphics design, but no 3d graphic design.  I don't play games, and don't really use it to download music.  The whole lampstack thing, I mean that I want to learn all the different aspects of it, so i am trying to use ubuntu so I can understand linux a little better.  I would also like to be able to run MySql on here so I can practice queries and stuff.

---

### Post by udayshanbhag on 2007-11-02
Hi

even i have AMD 64bit system and i installed 32bit version of Ubuntu.

isnt it sufficient if i compile and install 64bit version of kernel to get the use of 64bit machine?

Thanks in advance
Uday

---

### Post by Anthrax9 on 2007-11-02
can i in anyway upgrade my 32-bit Ubuntu system to a 64-bit ubuntu???:confused:

---

### Post by cjazz on 2007-11-02
> **Anthrax9 said:**
> can i in anyway upgrade my 32-bit Ubuntu system to a 64-bit ubuntu???:confused:

No. To run 64-bit Ubuntu, you'll have to install the AMD64 version. Of course, that can be a little less painful if you have your /home folder on a separate partition, meaning your personal data and settings would be preserved.

---

### Post by sanderjd on 2007-11-02
I see here that people keep asking whether they can install a 64-bit kernel rather than reinstalling Ubuntu, and that everyone is responding "no." Could someone explain why not? Though I have not done it, I thought it possible to install a 64-bit kernel that is able to emulate 32-bit operation. In fact, I'm nearly positive that this must be the case, since it is possible to create a 32-bit chroot with a 64-bit kernel. This seems to imply to me that the 64-bit kernel can successfully interact with a 32-bit userland. 

Having said all that, I don't know how to do it, and that's why I came to the forums today. I want to install a 64-bit chroot on a 32-bit Ubuntu install. I have an x86-64 processor, but didn't want to deal with the hassle of 64-bit linux when I installed. However, I now have to do some compilation and testing of 64-bit binaries, and it would be nice to not have to reinstall or dual boot.

So my question is: is this possible - to install a 64-bit chroot, which I assume will require a 64-bit kernel - if not, why not? if so, do I need to compile it myself or can I get a binary from the repositories somehow.

Thanks! Sorry for hijacking the thread, but I believe our questions are analogous.

---

### Post by rsambuca on 2007-11-02
> **sanderjd said:**
> I see here that people keep asking whether they can install a 64-bit kernel rather than reinstalling Ubuntu, and that everyone is responding "no." Could someone explain why not? Though I have not done it, I thought it possible to install a 64-bit kernel that is able to emulate 32-bit operation. In fact, I'm nearly positive that this must be the case, since it is possible to create a 32-bit chroot with a 64-bit kernel. This seems to imply to me that the 64-bit kernel can successfully interact with a 32-bit userland. 

Having said all that, I don't know how to do it, and that's why I came to the forums today. I want to install a 64-bit chroot on a 32-bit Ubuntu install. I have an x86-64 processor, but didn't want to deal with the hassle of 64-bit linux when I installed. However, I now have to do some compilation and testing of 64-bit binaries, and it would be nice to not have to reinstall or dual boot.

So my question is: is this possible - to install a 64-bit chroot, which I assume will require a 64-bit kernel - if not, why not? if so, do I need to compile it myself or can I get a binary from the repositories somehow.

Thanks! Sorry for hijacking the thread, but I believe our questions are analogous.

I really don't see how it is possible to do what you are asking, but if you are "almost positive", why not just try it out?  It only takes a few minutes to set it up.  Let us know how it goes :)

Also, what are these so-called "hassles of 64-bit"?

---

### Post by sanderjd on 2007-11-02
Well, as of Feisty, the hassles of 64-bit are two main things - flash plugin and java plugin. Seeing as how I work at a software company and test software that involves both flash and java applets, this is annoying. Yes, it is possible to get both of those to work with 64-bit installations, but like I said, as of Feisty they are hassles (though not impossibilities). Please enlighten me if these things are indeed no longer hassles in Gutsy.

As for the rest of your much appreciated reply, you are correct to have thrown my "almost positive" back in my face. Obviously if I were confident at all, I wouldn't be posting here. How about this, I think it is *plausible* that a 64-bit kernel can be installed without a full new installation. I'll tell you the reasons I think so. Firstly, it is possible to install a new kernel without fully re-installing the system, because the kernel is updated all the time and the new versions are installed seamlessly. This leads me to believe that a 64-bit kernel could be similarly installed. Now, the question becomes whether doing so will result in a functional system. The reason I believe it to be possible that it will work is that I have seen tutorials such as this one: [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575) that allow you to run a full 32-bit userland on top of a 64-bit kernel using a chroot. Since nowhere in that tutorial do you install a 32-bit kernel I am led to believe that the 64-bit kernel must be able to execute 32-bit applications. I don't see any reason that running those programs in a chrooted environment should be any different than running them in the original environment. Again, I am admittedly not an expert on this and I would really like to know why you believe it to be impossible.

Now, after that mouthful, I'll say that I liked your idea of trying it for myself instead of speculating and I've been trying to do that. The real question I have is where I can acquire a 64-bit kernel. The kernel I have installed is called "generic" and contains "the Linux kernel image for version 2.6.22 on x86/x86_64" according to its description. When I saw that I was excited and thought maybe this whole conversation is moot because it already includes both. Alas, this does not appear to be the case, because after setting up my chroot for amd64 I am unable to execute any of the 64-bit binaries installed and receive the error "Cannot run the command ____: Exec Format Error" - this error being exactly what I would expect were I to run a 64-bit binary on a 32-bit machine. Also, looking in the kernel directory I find an "arch/i386" directory but no "arch/amd64" so I'm pretty convinced that this kernel cannot run 64-bit code. So my question is, how can I get a 64-bit kernel image package (I would prefer not to build it myself) to try out?

---

### Post by rsambuca on 2007-11-02
> **sanderjd said:**
> Well, as of Feisty, the hassles of 64-bit are two main things - flash plugin and java plugin. Seeing as how I work at a software company and test software that involves both flash and java applets, this is annoying. Yes, it is possible to get both of those to work with 64-bit installations, but like I said, as of Feisty they are hassles (though not impossibilities). Please enlighten me if these things are indeed no longer hassles in Gutsy.


Both Flash and Java are installed in Feisty with simple scripts.  Two mouse clicks is hardly what I would call a "hassle".  The same can be done with Gusty.  If all you need is Flash, then it is now included in the repos.

> **sanderjd said:**
> As for the rest of your much appreciated reply, you are correct to have thrown my "almost positive" back in my face. Obviously if I were confident at all, I wouldn't be posting here. How about this, I think it is *plausible* that a 64-bit kernel can be installed without a full new installation. I'll tell you the reasons I think so. Firstly, it is possible to install a new kernel without fully re-installing the system, because the kernel is updated all the time and the new versions are installed seamlessly. Keep in mind that any time a kernel is updated, you do need to do a reboot to get it running.

> **sanderjd said:**
> http://ubuntuforums.org/showthread.php?t=24575[/url] that allow you to run a full 32-bit userland on top of a 64-bit kernel using a chroot. Since nowhere in that tutorial do you install a 32-bit kernel I am led to believe that the 64-bit kernel must be able to execute 32-bit applications. I don't see any reason that running those programs in a chrooted environment should be any different than running them in the original environment. Again, I am admittedly not an expert on this and I would really like to know why you believe it to be impossible.I am not an expert neither, by I do not see how you can possibly run 64bit programs via chroot from a 32bit system.  The kernel you would still be using is 32bit, and thus apps can not possibly use all of the registers that would be coded for in the 64bit.  Just because it works one way doesn't mean it will work in reverse.
> **sanderjd said:**
> Now, after that mouthful, I'll say that I liked your idea of trying it for myself instead of speculating and I've been trying to do that. The real question I have is where I can acquire a 64-bit kernel. The kernel I have installed is called "generic" and contains "the Linux kernel image for version 2.6.22 on x86/x86_64" according to its description. When I saw that I was excited and thought maybe this whole conversation is moot because it already includes both. Alas, this does not appear to be the case, because after setting up my chroot for amd64 I am unable to execute any of the 64-bit binaries installed and receive the error "Cannot run the command ____: Exec Format Error" - this error being exactly what I would expect were I to run a 64-bit binary on a 32-bit machine. Also, looking in the kernel directory I find an "arch/i386" directory but no "arch/amd64" so I'm pretty convinced that this kernel cannot run 64-bit code. So my question is, how can I get a 64-bit kernel image package (I would prefer not to build it myself) to try out?Having said all that, you can get the [64bit kernel here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmain%2Fl%2Flinux-source-2.6.22%2Flinux-image-2.6.22-14-generic_2.6.22-14.46_amd64.deb&md5sum=907ab576506dd6a835c6d3572ba332ba&arch=amd64&type=main").

---

### Post by sanderjd on 2007-11-02
> **rsambuca said:**
> Both Flash and Java are installed in Feisty with simple scripts.  Two mouse clicks is hardly what I would call a "hassle".  The same can be done with Gusty.  If all you need is Flash, then it is now included in the repos.

I didn't realize such scripts existed, thanks for the info, next time I install freshly I'll probably go back to a pure 64-bit system.

> **rsambuca said:**
> I am not an expert neither, by I do not see how you can possibly run 64bit programs via chroot from a 32bit system.  The kernel you would still be using is 32bit, and thus apps can not possibly use all of the registers that would be coded for in the 64bit.  Just because it works one way doesn't mean it will work in reverse.

I think you've misunderstood what I'm trying to do. I don't want to install a 64-bit kernel in the chroot environment, I want to install a 64-bit kernel *instead* of my current 32-bit kernel. So the kernel I would be using would not still be 32-bit, it would be 64-bit. Everything on the system would use that 64-bit kernel, but the only applications that would use it in 64-bit mode would be those in the chroot.

> **rsambuca said:**
> Having said all that, you can get the [64bit kernel here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmain%2Fl%2Flinux-source-2.6.22%2Flinux-image-2.6.22-14-generic_2.6.22-14.46_amd64.deb&md5sum=907ab576506dd6a835c6d3572ba332ba&arch=amd64&type=main").

Thanks! I have actually followed through with this. Using dpkg --force-architecture, I was able to install the amd64 kernel, and I booted into it, with quite a few graphics-related issues. My guess is that this is due to the fact that I still have a 32-bit version of the binary ati driver. My guess is that if I get the 64-bit version of that as well, this little excursion I've been on will be a success.

---

### Post by rsambuca on 2007-11-02
I still see no way for this to work, since you don't have the proper libraries for the 64bit environment.

---

### Post by sanderjd on 2007-11-02
Yeah that's a really good point. But it does mostly work, because I am using it right now, I haven't found a program that doesn't run properly yet. All the issues seem to be graphics driver related, which makes sense. I think the reason it works is because the 64-bit kernel is perfectly happy with 32-bit libraries (as we've both said before, this must be so because a 32-bit chroot works), so as long as I am only running binaries that link against those 32-bit libraries, everybody will be pleased as puppies. Yes, I did just personify computer programs and then compare them to puppies. In any case, I think as long as I only run 32-bit programs in my main install (which will be the case unless I use dpkg --force-architecture again, which is doubtful), and keep the 64-bit binaries in a chroot environment where the 64-bit libraries are installed, this will work. It's defininitely an odd way to have a system set up, and very interesting.

---

### Post by rsambuca on 2007-11-02
Interesting no doubt!  Keep us updated as to how it works.

---

### Post by jaybombalous on 2007-11-04
> **I have an x86-64 processor**, but didn't want to deal with the hassle of 64-bit linux when I installed. However, I now have to do some compilation and testing of 64-bit binaries, and it would be nice to not have to reinstall or dual boot.


u are using a 64 bit OS kernel because u have a 64 bit processor. Thats why u can run a 64 bit kernel on a 32 bit userland or whatever u call it. The processor work in backwards compatibility mode. 


What doesn't work and what I think rsambuca was trying to point out is 32 bit processors aren't forward compatible to 64 bit OS kernel as u insinuated in your post.

---

