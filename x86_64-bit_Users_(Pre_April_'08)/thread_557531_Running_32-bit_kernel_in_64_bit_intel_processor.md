---
title: "Running 32-bit kernel in 64 bit intel processor"
date: 2007-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by asundaresan on 2007-09-22
Hi, 

My problem is slightly different from most people's. I have a spanking new dell machine with 64 bit Intel Xeon processor. The current ubuntu install is x86_64. I need to run several 32 bit programs and I wish to do it painlessly. I would like to know if there is anyway I can just pretend that my machine is 32 bit (by running it in legacy mode, compatibility mode or similar) so that the i686 version of the OS is installed with all 32 bit libraries and so on. I really don't mind the performance hit at all. How would I go about accomplishing this?

My processor information is as follows. 

```
[aravind@coriander ~]$ lshw -C cpu 
WARNING: you should run this program as super-user.
  *-cpu:0                 
       product: Intel(R) Xeon(R) CPU            5130  @ 2.00GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx x86-64 constant_tsc pni monitor ds_cpl vmx tm2 cx16 xtpr lahf_lm
  *-cpu:1
       product: Intel(R) Xeon(R) CPU            5130  @ 2.00GHz
       vendor: Intel Corp.
       physical id: 2
       bus info: cpu@1
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx x86-64 constant_tsc pni monitor ds_cpl vmx tm2 cx16 xtpr lahf_lm

```

```

[aravind@coriander ~]$ uname -a 
Linux coriander 2.6.17-12-generic #2 SMP Wed Aug 29 18:53:01 UTC 2007 x86_64 GNU/Linux

```

Thanks in advance.
Aravind.

---

### Post by dcstar on 2007-09-22
> **asundaresan said:**
> Hi, 

My problem is slightly different from most people's. I have a spanking new dell machine with 64 bit Intel Xeon processor. The current ubuntu install is x86_64. I need to run several 32 bit programs and I wish to do it painlessly. I would like to know if there is anyway I can just pretend that my machine is 32 bit (by running it in legacy mode, compatibility mode or similar) so that the i686 version of the OS is installed with all 32 bit libraries and so on. I really don't mind the performance hit at all. How would I go about accomplishing this?
..........
Thanks in advance.
Aravind.

Just find ~5GB of spare disk space and install the "standard" i386 version of Ubuntu, then boot whatever version you feel like using.

I have a separate /home partition that is used by either the 64bit or 32bit Ubuntu systems that I choose to boot on my system.

---

### Post by Kilz on 2007-09-22
> **asundaresan said:**
> Hi, 

My problem is slightly different from most people's. I have a spanking new dell machine with 64 bit Intel Xeon processor. The current ubuntu install is x86_64. I need to run several 32 bit programs and I wish to do it painlessly. I would like to know if there is anyway I can just pretend that my machine is 32 bit (by running it in legacy mode, compatibility mode or similar) so that the i686 version of the OS is installed with all 32 bit libraries and so on. I really don't mind the performance hit at all. How would I go about accomplishing this?


Can you give us an idea of what 32bit applications you need to run?

---

### Post by asundaresan on 2007-09-23
Thanks for the responses. To answer the question about what applications I need to run, there are two parts. First, there are some custom 32-bit libraries which I need to use. Second there are some 32 bit flags in the compiler of the code that I am working with. 

I would also like to install the intel compiler for 32 bit applications for some of the code if possible. This is possible if the processor can run in some compatibility mode. 

Does anybody know if there is a 32 bit compatibility mode for the intel core 2 duo processor. 

I also have a question regarding if I have a choice in installing the i386 version of Ubuntu. The person says he just popped in the Ubuntu (I believe the i386 CD) and the 64 bit version got installed. I think he said that at no point was there a choice. My question is how do I ensure that the 32 bit version of everything is installed. Will the choice of the i386 CD do it?

Thanks,
Aravind.

PS. I have been using Linux for a long time and am not exactly a newbie, but I am not very clear on the 32bit-64bit thing especially since it appears the 64bit  processor is backward compatible with 32bit. I am also not able to find much information regarding this.

---

### Post by Kilz on 2007-09-23
> **asundaresan said:**
> Thanks for the responses. To answer the question about what applications I need to run, there are two parts. First, there are some custom 32-bit libraries which I need to use. Second there are some 32 bit flags in the compiler of the code that I am working with. 

I would also like to install the intel compiler for 32 bit applications for some of the code if possible. This is possible if the processor can run in some compatibility mode. 

Does anybody know if there is a 32 bit compatibility mode for the intel core 2 duo processor. 

I also have a question regarding if I have a choice in installing the i386 version of Ubuntu. The person says he just popped in the Ubuntu (I believe the i386 CD) and the 64 bit version got installed. I think he said that at no point was there a choice. My question is how do I ensure that the 32 bit version of everything is installed. Will the choice of the i386 CD do it?

Thanks,
Aravind.

PS. I have been using Linux for a long time and am not exactly a newbie, but I am not very clear on the 32bit-64bit thing especially since it appears the 64bit  processor is backward compatible with 32bit. I am also not able to find much information regarding this.

Sure you can install the 32bit version, but since you are developing and 64bit is the future, dont you want to develop on 64bit as well as 32? If you install 32bit you only have a 32bit install. 64bit will do both. You could set up a chroot to do development work on. [This script may help.]("http://ubuntuforums.org/showthread.php?t=157412&highlight=chroot") You could also install a 32bit virtual machine and do development work there. Keeping your work separate from your install. Virtualbox and vmware are good choices if you want to go that way.

---

### Post by asundaresan on 2007-09-24
Thanks for the replies. I have one important question: 

How can I force Ubuntu to install the 32-bit OS rather than x86_64 - It also seems that the kernel is named linux-image-generic rather than linux-image-386?

Thanks,
Aravind.

---

### Post by dabl on 2007-09-24
If you use the so-called "PC (Intel x86) desktop CD" or "PC (Intel x86) Alternate CD", the only OS on there is 32-bit, so I'm pretty sure that's what you'll get.  :)

---

### Post by stmiller on 2007-09-24
You could use [Virtualbox]("http://www.virtualbox.org/") to make a 32bit dev install, as another option. Speeds are native to your hardware with Virtualbox.

---

### Post by Yellow Pasque on 2007-09-24
If you're just looking to compile software in a 32-bit environment, I would go the chroot route. It's fairly easy and takes the least amount of resources.

---

### Post by jocko on 2007-09-24
32 bit and 64 bit are on separate cd's.
To install 32 bit ubuntu, you just need to download the 32 bit cd.

---

### Post by picopir8 on 2007-09-26
Just install virtualbox and run the 32 bit OS on a virtual machine.  Its the simplest solution IMO.

---

### Post by asundaresan on 2007-09-28
Thanks very much for all the ideas. I have installed 32 bit dapper from the alternate install cd and that worked fine. I will also try virtualbox some time. 

Aravind.

---

### Post by Kilz on 2007-09-28
32bit Dapper? If you were going to install an operating system not designed for your computer that cuts your performance up to 30% on some tasks. You should have at least tried Feisty.

---

### Post by asundaresan on 2007-10-01
> **Kilz said:**
> 32bit Dapper? If you were going to install an operating system not designed for your computer that cuts your performance up to 30% on some tasks. You should have at least tried Feisty.

Hi Kilz: 

I realise that the solution is non-optimal in most situations. My situation is quite different, I work in an environment where 

- My machine is a production machine administered by someone else
- I have sudo root privilege, but I cannot make drastic changes
- Home directories are automounted making chroot configuration non-standard (and painful)
- The machine is quite powerful and I don't care about the cut in performance
- I need to work with a bunch of other machines running dapper and it helps to have the same programs/versions as they do. The LTS is handy as we do not wish to upgrade very frequently.

Thanks for your comments and tips.

Aravind.

---

### Post by Kilz on 2007-10-01
> **asundaresan said:**
> Hi Kilz: 

I realise that the solution is non-optimal in most situations. My situation is quite different, I work in an environment where 

- My machine is a production machine administered by someone else
- I have sudo root privilege, but I cannot make drastic changes
- Home directories are automounted making chroot configuration non-standard (and painful)
- The machine is quite powerful and I don't care about the cut in performance
- I need to work with a bunch of other machines running dapper and it helps to have the same programs/versions as they do. The LTS is handy as we do not wish to upgrade very frequently.

Thanks for your comments and tips.

Aravind.

ok
I understand, not your toy to break, but there really isnt that much difference in the lifespan of Dapper and Feisty. It may also be a smoother transition to the next LTS from Feisty, that will be the release after Gutsy.

---

