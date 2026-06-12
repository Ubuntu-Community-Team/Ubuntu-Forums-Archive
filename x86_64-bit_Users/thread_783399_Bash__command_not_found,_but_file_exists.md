---
title: "Bash : command not found, but file exists"
date: 2008-05-05
forum: x86 64-bit Users
---

### Post by hoornix on 2008-05-05
Hi,

I have the following issue with Kerkythea renderer.
It worked once on feisty 7.10 64 bit. But not on Hardy 64 bit and also not on a new install of 7.10 64bit. 

I get the following when using strace.

execve("./Kerkythea", ["./Kerkythea"], [/* 35 vars */]) = -1 ENOENT (No such file or directory)
dup(2)                                  = 3
fcntl(3, F_GETFL)                       = 0x8002 (flags O_RDWR|O_LARGEFILE)
fstat(3, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fef407e0000
lseek(3, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: No such file or di"..., 40strace: exec: No such file or directory
) = 40
close(3)                                = 0
munmap(0x7fef407e0000, 4096)            = 0
exit_group(1)                           = ?
Process 16135 detached

I am in the correct directoly and the rights are set correctly.

Any ideas what can be the problem. From the Kerkythea forum I know that it should work on Hardy 32 and 64.

Regards,

---

### Post by lesergi on 2008-05-05
Hi!

Can you paste the exit of:

```
ls -l
```

---

### Post by andrewc6l on 2008-05-05
If ./Kerkythea is a shell script, are you sure that the shell it points to in the first line (#!/some/dir/bash) exists on your machine and is in /etc/shells ?

---

### Post by hoornix on 2008-05-06
Hi,
Thanks for your replies,

Kerkythea is a C++ program (renderer), I tried to start it from a script with the most , but with the same results. 
When I tried using . ./Kerkethea I get a 
bash : Elf: File not found. I am not sure about the usefullness of . ./Kerkythea though.
(I am not at my computer so I am not sure about the part after ELF, there was something about no permission)

Concerning ls -l, the program itself and all the directories and files accompagning it are 755, also the containg directory. Owner and user that wants to run it are also the correct ones.
(I can't give the ls -l result right now since I am not near the computer)

Is it possible that a library on which Kerkythea depends has the wrong permissions? 

Regards and thanks!

---

### Post by lesergi on 2008-05-06
Try writing "linux32 ./Kerkethea" instead "./Kerkethea".

Bye!

---

### Post by hoornix on 2008-05-06
Hi,

I am sorry I forgot to tell, I tried the linux32 too.
When using objectdump and the other tools from binutils I get results that you would expect. I get a list with the libs needed, and all of them are available. That looks good to me. It is just a mistery to me that I get the program not found error.
Users of Kerkythea run it on 8.04 32bit as well as on 8.04 64bit so there must be something missing on my installation. I just fail to find the information that leads to the missing library or setting.
On 7.10 64 bit it didn't work, but after a while it suddenly did. I found out when I accidentaly started it so I have no clue what made it work. 

The strace output is very short, it says nothing to me at the moment that might help. Maybe the Seekerror points to something?

Thanks again!

---

### Post by Jouke74 on 2008-05-06
Did you install IA32libs? All of them, plus the development versions, if required?

---

### Post by hoornix on 2008-05-06
I don't think so, I will try when I get home. about 17:00 UTC. ;-)
I think when it worked on 7.10 64 it worked as a 64 application since it easily ate about 7 GB of memory for about 29 hours when doing a giga render. I am no expert on Memory usage..... :-(
I am not sure what it will do when using linux32. Will it hit the 2Gb limit? (I suppose IA32libs belongs to linux32?)

---

### Post by Jouke74 on 2008-05-06
I guess the first thing to know is if the version which you are currently using is fully 64 or 32 bits, or a mixture (part of the binaries 64 bit and part 32 bit). This may also be a bad idea security wise etc, but can you run it under sudo?

---

### Post by hoornix on 2008-05-06
The program is only available in one version for linux. 
I suppose I can check with one of the binutils if there is a mixture of 64 and 32. Maybe somebody at the Kerkythea forum can say something about that.

---

### Post by hoornix on 2008-05-06
Hi,

I installed ia32-libs and ./Kerkythea works and happily eats more than 3GB, which is why I wanted the 64bit......

Thanks for anybody that replied! I am very happy about this working Kerkythingemy.

Kindest Regards!

---

### Post by hoornix on 2008-05-08
It works as stated in my previous posting.

Regards!

---

