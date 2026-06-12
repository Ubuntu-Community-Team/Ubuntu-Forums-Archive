---
title: "Ubuntu 64-bit and 32-bit compatibility"
date: 2008-07-16
forum: x86 64-bit Users
---

### Post by dexfos on 2008-07-16
I have a laptop system with an AMD Turion 64 x2 processor currently running Windows Vista 64. Vista works so well that I am replacing it with WinXP Pro 64. Additionally I will be installing Ubuntu in a dual boot configuration. Ideally, I would like to install 64-bit Ububuntu but am concerned that this will end up an application starved installation, so I am leaning toward a 32-bit install.

Quoting the Common Questions from the Ubuntu website: "The drawbacks are that Ubuntu, with APT (the package manager for Ubuntu), currently does not support BiArch, which means you likely won't be able to install and run 32bit packages on your AMD64 install."

After having spent the last couple of weeks digging through the internet resources and wading through linux source code and docs, I'm totally confused as to what 64-bit Ubuntu (Linux) really is. The impression I get is that the 64-bit version supports only the long mode and not 32-bit compatibility mode - that is, the OS is really intended to operate pure 64-bit unless shims or hacks are used to enable 32-bit compatibility. Is this correct?

Thanks

---

### Post by elmoosecapitan on 2008-07-16
Hi,

64-bit Hardy does have 32-bit libraries and is thus partially compatible with 32-bit programs. Coming from someone who runs 64-bit, I haven't really had any problems with being 'application-starved'. Yes, it is true that not all the latest media components, e.g. flash-10, are available in 64-bit linux but that only means that you will have to settle for beta releases and previous releases. I run flash 9.0+ rather than flash 10.0+ and honestly I can't tell a difference. There are also user-friendly instructions for installing codecs and libraries to run dvd/music/media players somewhere on the web.

Most importantly, you can have the security and speed of 64-bit linux and still be able to run vista by partitioning your hard drive. If you install from a live CD, ubuntu gives you the option to partition your harddrive, thus  dedicating a part of your harddrive for vista, or the capability of writing over vista.

---

### Post by Sef on 2008-07-17
> Most importantly, you can have the security and speed of 64-bit linux and still be able to run vista by partitioning your hard drive. If you install from a live CD, ubuntu gives you the option to partition your harddrive, thus dedicating a part of your harddrive for vista, or the capability of writing over vista.

The same is true for the alternate cd too.

---

### Post by Kilz on 2008-07-17
> **elmoosecapitan said:**
> Hi,

64-bit Hardy does have 32-bit libraries and is thus partially compatible with 32-bit programs. Coming from someone who runs 64-bit, I haven't really had any problems with being 'application-starved'. Yes, it is true that not all the latest media components, e.g. flash-10, are available in 64-bit linux but that only means that you will have to settle for beta releases and previous releases. I run flash 9.0+ rather than flash 10.0+ and honestly I can't tell a difference. There are also user-friendly instructions for installing codecs and libraries to run dvd/music/media players somewhere on the web.

Most importantly, you can have the security and speed of 64-bit linux and still be able to run vista by partitioning your hard drive. If you install from a live CD, ubuntu gives you the option to partition your harddrive, thus  dedicating a part of your harddrive for vista, or the capability of writing over vista.

Flash 10 is still in beta testing. Anyone wanting to install it can. For information on that see the flash sticky

dexfos - For the original poster, the Ubuntu repositories for AMD64 and i386 (64 and 32 bit) contain the same number of packages. Can you please provide a link to the page you are referring to in the Ubuntu documentation so we can see about getting it corrected.

---

### Post by dexfos on 2008-07-17
Kilz - 
The source of the documentation quote is Common Questions section 5.5 AMD64 Processors. The direct link is:

[https://help.ubuntu.com/community/CommonQuestions](https://help.ubuntu.com/community/CommonQuestions)

---

### Post by dfreer on 2008-07-18
I believe by "BiArch" they are referring to the ability to use a package manager like synaptic to install both a 32-bit and 64-bit version of a program or library side-by-side from the main repos (I wish :( ). In which case the documentation is correct.

As others have stated though, there are 64-bit packages of those 32-bit programs which should work just fine. And if you must absolutely run a 32-bit program, just install the correct 32-bit libraries and you should be ok.

---

### Post by Kilz on 2008-07-18
> **dexfos said:**
> Kilz - 
The source of the documentation quote is Common Questions section 5.5 AMD64 Processors. The direct link is:

[https://help.ubuntu.com/community/CommonQuestions](https://help.ubuntu.com/community/CommonQuestions)

Thanks for that url, while it is in fact correct that biarch isnt possible, it lists flash and wine as needing hacks to run, this hasnt been the case since Gutsy. I will fix it.

---

### Post by stchman on 2008-07-18
> **dexfos said:**
> I have a laptop system with an AMD Turion 64 x2 processor currently running Windows Vista 64. Vista works so well that I am replacing it with WinXP Pro 64. Additionally I will be installing Ubuntu in a dual boot configuration. Ideally, I would like to install 64-bit Ububuntu but am concerned that this will end up an application starved installation, so I am leaning toward a 32-bit install.

Quoting the Common Questions from the Ubuntu website: "The drawbacks are that Ubuntu, with APT (the package manager for Ubuntu), currently does not support BiArch, which means you likely won't be able to install and run 32bit packages on your AMD64 install."

After having spent the last couple of weeks digging through the internet resources and wading through linux source code and docs, I'm totally confused as to what 64-bit Ubuntu (Linux) really is. The impression I get is that the 64-bit version supports only the long mode and not 32-bit compatibility mode - that is, the OS is really intended to operate pure 64-bit unless shims or hacks are used to enable 32-bit compatibility. Is this correct?

Thanks

I run 64 bit on 3 different machines and they all work very well.  The repos are chocked full of 64 bit DEBs so do not worry.

Also 64 bit Ubuntu supports 32 bit binaries as well.

---

