---
title: "Ubuntu with &gt;= 4GB RAM"
date: 2007-07-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by sdennie on 2007-07-20
I've got a friend who would like to switch to Ubuntu.  He's running a dual processor, dual core Xeon (4 processors in total) Dell machine with 4G of RAM.  Dell sells the machine in configurations with a LOT more RAM so I assume the BIOS is perfectly happy with large amounts of RAM.  He's considering upgrading to 8G of RAM before installing Ubuntu so, here are the questions:

1) Assuming the BIOS is Crazy Amounts of RAM Friendly, how much RAM will he see if he installs 7.04 32-bit?  7.04 64-bit?

2) Is there a drawback to installing 7.04 64-bit?  I run a file server with a 64-bit version of Dapper but, I have no experience with 64-bit machines running mainstream apps (VirtualBox would be one of his main apps).

What is his best option?  Install a 64-bit version or compile a custom 32-bit kernel with > 4G of RAM enabled?  Will the 64-bit version automagically recognize the 8G of RAM?

Thanks for your help.

---

### Post by scxtt on 2007-07-20
64-bit is about the only way he'll get all that RAM recognized ... i put a total of 4 in my VMware box and only ~3.2 was seen until i went to 64bit ... it works that same as it did before when it was 32bit, but now i can address all the RAM i paid for ...

---

### Post by firebird84 on 2007-07-20
If he does not go with AMD64 linux, then it will likely only recognize a portion of his 4GB, much less 8.  The reason for this is memory-mapped I/O. He should be experiencing the same problem in Windows unless it is x64 Edition.  So if he ALREADY has 4GB, please for the love of God use a 64-bit OS.

---

### Post by baluchi on 2007-09-07
> **scxtt said:**
> 64-bit is about the only way he'll get all that RAM recognized

Not exactly true, I'm using 32-bit Feisty and managed to detect the whole 4GB RAM on my PC by [[COLOR="Blue"]rebuilding the kernel[/COLOR]]("http://www.howtoforge.com/kernel_compilation_ubuntu") with 64GB RAM support.

```

$ free
             total       used       free     shared    buffers     cached
Mem:       4147488     504104    3643384          0      14752     304516
-/+ buffers/cache:     184836    3962652
Swap:      4192924          0    4192924

```

---

### Post by rabidrabbit on 2007-09-08
that is kind of a hack though, extending the memory space is a less than optimal way to use all your memory. i would switch to 64 bit.

---

### Post by asdfoo on 2007-09-08
> **vor said:**
> I've got a friend who would like to switch to Ubuntu.  He's running a dual processor, dual core Xeon (4 processors in total) Dell machine with 4G of RAM.  Dell sells the machine in configurations with a LOT more RAM so I assume the BIOS is perfectly happy with large amounts of RAM.  He's considering upgrading to 8G of RAM before installing Ubuntu so, here are the questions:

1) Assuming the BIOS is Crazy Amounts of RAM Friendly, how much RAM will he see if he installs 7.04 32-bit?  7.04 64-bit?

2) Is there a drawback to installing 7.04 64-bit?  I run a file server with a 64-bit version of Dapper but, I have no experience with 64-bit machines running mainstream apps (VirtualBox would be one of his main apps).

What is his best option?  Install a 64-bit version or compile a custom 32-bit kernel with > 4G of RAM enabled?  Will the 64-bit version automagically recognize the 8G of RAM?

Thanks for your help.

Just install the 64bit version.

I have an intel core 2 quad (4 cores), with 8GB of ram.  64bit ubuntu works fine.

I also use virtualbox without a problem, they provide a 64bit deb package on their website.  I also use Cedega to play battlefield 1942 and a bunch of other stuff.

The only thing which I don't use is flash.  Adobe don't provide a 64bit version of flash.  If I _really_ need it, I use virtualbox to view a website. like google analytics.

---

### Post by dptxp on 2007-09-10
2 to the power 10 is 1 KB(1024), 2 to the power 20 is 1 MB (1024 X 1024), 2 to the power 30 is 1 GB (1024 X1024 X 1024) , 2 to the power 32 is 2 to the power 30 multiplied by 2 to the power 2, OR 4GB.

So you can not access more than 4 GB with 32 bit OS.

Just imagine how much you can access with 64 bit !!

---

