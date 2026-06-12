---
title: "Cpu Temps Core 2 Duo"
date: 2007-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Trippen Out on 2007-02-13
i need a way to moniter my cpu temps from linux ive installed a couple of different things nothing seems to work i need something to moniter my cpu temp for a core 2 duo cpu from intel model e4300 .. this is a crucial thing needed enough so to make me go back to windows and i really dont want to do that.. please help

---

### Post by phiphedog on 2007-02-13
Must have a bad fan or doing some pretty processor intensive stuff to worried about cpu temp.

maybe this will help [http://www.ubuntuforums.org/showthread.php?t=193149](http://www.ubuntuforums.org/showthread.php?t=193149)

---

### Post by Trippen Out on 2007-02-13
yea it doesnt work either.. ive reconfigured my sensors.conf with the proper stuff for my mother board but i cant start any services for it.. in the command if i type sensors i get this reply


trippen@PhasedC2D:~$ sensors
Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!
trippen@PhasedC2D:~$ sudo sensors
Password:
Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!


and i ran the detect program as well.. so i am lost.. and yes i would say that temps are pretty important im running on a phased cooled system on a very high clocked cpu so its good to know how hot things are running

---

### Post by Belboz99 on 2007-02-13
Try xmbmon.

xmbmon doesn't use lmsensors, but you need to have root access to read the temps.

It's a very simple and basic tool, I use it all the time.   Reads same as lmsensors does on my Core 2 Duo. :)

Dan

---

### Post by Trippen Out on 2007-02-13
> **Belboz99 said:**
> Try xmbmon.

xmbmon doesn't use lmsensors, but you need to have root access to read the temps.

It's a very simple and basic tool, I use it all the time.   Reads same as lmsensors does on my Core 2 Duo. :)

Dan
thank you but its certainly not right as its saying my cpu is like 255 degrees and my chipset is 355.. theres no way a cpu would run that hot..any other ideas.. or do you have to configure it somehow to make it work with a core 2 duo chip

---

### Post by laredo7mm on 2007-02-15
> **Trippen Out said:**
> ...

trippen@PhasedC2D:~$ sensors
Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!
...

Did you go through the lmsensors set up prcedure (i.e.: "sudo sensors-detect") and add the correct lines of code to /etc/modules?  Also check out lmsensors website for more information.

I had issues getting my sensors to work on my AMD64 X2 (while usinf 2.6.17-10, but I got them to work after messing around with sensors-detect, /etc/modules, modprobe, and especially compiling my own lmsensors from source.

But now I have upgraded to Feisty and all is well and all sensors show up in Gkrellm (even K8temp).

Search for lmsensors here on the forums and you will find a bunch of information.  I would post my /etc/modules for you but I am not sure it would help since your are running an e4300.

---

### Post by Trippen Out on 2007-02-23
> **laredo7mm said:**
> Did you go through the lmsensors set up prcedure (i.e.: "sudo sensors-detect") and add the correct lines of code to /etc/modules?  Also check out lmsensors website for more information.

I had issues getting my sensors to work on my AMD64 X2 (while usinf 2.6.17-10, but I got them to work after messing around with sensors-detect, /etc/modules, modprobe, and especially compiling my own lmsensors from source.

But now I have upgraded to Feisty and all is well and all sensors show up in Gkrellm (even K8temp).

Search for lmsensors here on the forums and you will find a bunch of information.  I would post my /etc/modules for you but I am not sure it would help since your are running an e4300.

yes i did all that... i tried to do feisty and it died.. i guess for my stuff to be supported correctly i need to wait till it gets closer to release

---

### Post by dannyboy79 on 2007-02-28
you cold always just compile your own custom kernel couldn't you? I have been looking into this myself. I run dapper and I think I am going to compile a 2.6.20 for 1.5gb of ram, also to support the intel core 2 duo and many other things that I am not sure are compiled in by default. I don't want to go to fiesty or edgy hence why I am sticking with dapper but going with a custom kernel.

---

### Post by Trippen Out on 2007-03-02
> **dannyboy79 said:**
> you cold always just compile your own custom kernel couldn't you? I have been looking into this myself. I run dapper and I think I am going to compile a 2.6.20 for 1.5gb of ram, also to support the intel core 2 duo and many other things that I am not sure are compiled in by default. I don't want to go to fiesty or edgy hence why I am sticking with dapper but going with a custom kernel.


no i cant.. im to ignorant at this point in my linux experiance to recompile a kernel .. or i would do so in a heart beat to make sure i have an smp machine with working sensors and proper audio support

---

### Post by ffxr on 2007-03-02
its really not that difficult to compile your own kernel & is easy to undo if it does go wrong.

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

[ although i wouldnt be 100% sure it will fix your sensors issue as it didnt resolve mine : s\ ]

---

### Post by dannyboy79 on 2007-03-03
> **ffxr said:**
> its really not that difficult to compile your own kernel & is easy to undo if it does go wrong.

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

[ although i wouldnt be 100% sure it will fix your sensors issue as it didnt resolve mine : s\ ]

thanks for pointing this out to him, i have been on linux less than a year and the great thing about it is the community is very helpful and I have not preventing myself from trying anything due to this fact. even if you compile it once and it doesn't boot, try again!!! just always leave a backup kernel you can boot to!

---

### Post by Trippen Out on 2007-03-03
no i dont think im going to go that route.. but i have noticed that ubuntu is using out dated versions of lm-sensors and i2c and what not.. maybe the newer versions will support my hardware i noticed also that the newest version supports the core temp stuff as well.. im hoping that in feisty fawn they have included the newest version of the sensors ..

---

### Post by dannyboy79 on 2007-03-04
ok, just because ubuntu doesn't use the latest lmsensors doesn't mean you can't use the latest. you just download the source and install them as a module, i think?

---

### Post by ffxr on 2007-03-04
as an aside, i compiled the latest lmsensors from source today today (painless & u need libfsys-dev; bison, & flex parsers to get it to compile btw ) to try and get some sensor data out of my motherboard/cpu.. still no joy...

i guess newer/my mbs' are not yet supported.????

i have one more thing to try and thats the latest i2c stuff..

---

### Post by ffxr on 2007-03-04
nope no point in compiling latest i2c..

from lmsensors wiki: "* It will not work, and is not needed, on 2.6 kernels."

i guess it must be something with lack of support (as yet, i hope) for my mobo.

---

### Post by Trippen Out on 2007-03-05
ive been in the lm-sensors chat room on freenode and what im getting is i need to use a kernel version 2.6.18 or higher .. i was also told to try the newest version of lm sensors but when i try to do the make user command i get an error something about a rule for stdio.h at first i didnt have that program but i installed the build essentials and now i have but i get the same error.. i guess ill just follow the link about on how to make a new kernel hope i dont screw it to bad

---

### Post by ffxr on 2007-03-05
have you got the extra parsers? [or whatever they are ; ) ]

```
sudo apt-get install flex bison
```

i have kernel 2.6.20 & tried latest lmsensors all the way to the latest svn & still nada.. its really frustrating. i think it might be the bios on my mobo.. but m really shooting in the dark at this stage..


*edit*
you need the libsysfs-dev package as well, in case you missed that.. theres no reason it shouldnt compile..

---

