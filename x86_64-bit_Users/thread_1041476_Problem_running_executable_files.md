---
title: "Problem running executable files"
date: 2009-01-16
forum: x86 64-bit Users
---

### Post by trexgrec on 2009-01-16
I have switched to Ubuntu 7.10 64bit version, and some executable files ARE NOT running. Example :

me@my_pc:~/MOLARIS/bin$ ./molaris_hpc9.05_temp
bash: ./molaris_hpc9.05_temp: No such file or directory

This file is clearly an exe file, compiled with a FORTRAN compiler, for 32bit
but its not even recognized as a exe file. I have already checked the permissions, it IS an exe file!

What could be the problem?????? In 32bit Ubuntu version, it works and runs instanlty!

A desperate 64b user

---

### Post by gettinoriginal on 2009-01-16
.exe files will run in Ubuntu ??  Without Wine?? please explain as I did not know we could do that.  Please forgive my question to yours, as I am a simple user and not knowledgeable about all this stuff, just learning as I go.

---

### Post by trexgrec on 2009-01-16
Yeah! My mistake. So I rephrase! I have a file, which have been created by a fortran compiler, and it is executable. By the term executable, I DO NOT mean that it is a windows .exe file. Quite the contrary. Its a file which is a 32bit executable, and in theory, it should have run if I type :

[email]me@my_pc:~/molaris/.molari[/email]s_hpc9.05_temp

But instead of Ubuntu 64bit executing this file (as I Said before, I already checked the permissions, it is an executable file) it gives me this message:

bash: ./molaris_hpc9.05_temp: No such file or directory

On the other hand, EXACTLY the same file, on a UBUNTU 32bit 8.04 machine, runs properly!!!!

The info of the file are the following:

me@my_pc:~/molaris/bin$ file molaris_hpc9.05_temp
molaris_hpc9.05_temp: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), not stripped

So what is it that I am missing?

---

### Post by Rog-Mahal on 2009-01-17
At the risk of sounding stupid, are you sure you've typed the right directory? In your info command aren't you in ~/molaris/bin and in your attempt to execute you are in ~/molaris ?

---

### Post by trexgrec on 2009-01-17
No you dont sound stupid. This is so unbelievably buffling I cannot believe it myself! No I am in the correct directory, and I try to run the executable, and it give me the message I wrote before. The worst part is that THE same executable, in a 32Bit version of Ubuntu 8.04 runs perfectly well!!!

So the question is, WHY does the same executable, run fine in the 32Bit version, and cannot run (at least not immediately) into the 64 version????

By the way, I had to downgrade to 8.04 32Bit, JUST for this :( 
But if you guys are seriously interesting in this weird thing, I have another 2 machines, with 64bit Ubuntu 8.04 that produce the same problem, AND...... another one Ubuntu 8.04 64bit tha DOES NOT (How or why, I have no clue). If you can give suggestion in the next few days to come, I would really appreciate it. I can check all configurations and compare libraries or anything else that you may need!

Thanks for the efford

---

### Post by michael37 on 2009-01-17
> **trexgrec said:**
> No you dont sound stupid. This is so unbelievably buffling I cannot believe it myself! No I am in the correct directory, and I try to run the executable, and it give me the message I wrote before. The worst part is that THE same executable, in a 32Bit version of Ubuntu 8.04 runs perfectly well!!!

So the question is, WHY does the same executable, run fine in the 32Bit version, and cannot run (at least not immediately) into the 64 version????

By the way, I had to downgrade to 8.04 32Bit, JUST for this :( 
But if you guys are seriously interesting in this weird thing, I have another 2 machines, with 64bit Ubuntu 8.04 that produce the same problem, AND...... another one Ubuntu 8.04 64bit tha DOES NOT (How or why, I have no clue). If you can give suggestion in the next few days to come, I would really appreciate it. I can check all configurations and compare libraries or anything else that you may need!

Thanks for the efford

Two things to check.

[LIST=1]
[*]Permission flags.  Make sure you can execute the file.  Make sure that owner/group flags are as expected, and the file has executable "x" flag.  Either one of these issues could have occurred when transferring from one machine to another.
```

$ ls -l
-rwxr-xr-x  1 mike mike   23060 2009-01-17 02:06 some_executable_file

```
[*]Make sure you got all the libraries.  Run "ldd <executable>" command on both 32-bit and 64-bit systems.   Check and compare.  If you don't see libraries on the 64-bit machine, try installing ia32-libs package from apt.
[/LIST]

---

### Post by trexgrec on 2009-01-17
I have already checked the flags, many times, including the owner and the group. I have no idea about the libraries! Thanks for the suggestion. I will check it on Tuesday, and update the community for the outcome!

---

### Post by trexgrec on 2009-01-20
OK, here is the weirdest thing! In Ubuntu 32bit, using ldd, I get 4 libraries, which I have. In the 64bit, ldd gives a message :

.....@64bit_pc:~/         not a dynamic executable


!!!
However, in this particular 64bit machine, the file CAN BE EXECUTED!
What is wrong here???

---

### Post by trexgrec on 2009-01-20
I also checked the ia32 libraries and it looks that these are not the problem. The ia32 libraries are properly installed in two 64bit Ubuntu 8.04, where the one can run the executable and the other can not!

so... any other ideas?

---

### Post by roncrump on 2009-01-20
Do you have the fortran code?
If so, have you tried compiling it on the 64bit machine?

It does sound like a problem during the transfer or missing
32bit libraries, but moving the code rather than the binary
would be more reliable.

Or maybe static linking rather than dynamic during compilation.

Ron.

---

### Post by trexgrec on 2009-01-20
SUCCESS!!!!!!!!!!!!!!!!!!!!!!!!!!

Michel37 and Roncrump pointed to the correct solution but it was more complicated than that!

I post here the entire solution. The executable that could not be run/seen was a FORTRAN77 executable, compiled with the Portland and Co. Compiler, as a 32bit application, non static!

First, ldd command was not helpful at all, because for reason unknown to me, it was giving me the error message : not a dynamically executable file.

Second, its true that the trick was between the extra libraries needed if you want to run a 32b Fortran into a 64bit Ubuntu 8.04. You need the libraries ia32-libs which do most of the trick but not all. I was trying to run the executable on a Ubuntu 8.04 64B machine, that HAD ia32-libs installed, BUT STILL IT WAS NOT RUNNING. I checked some other reports of other users and I saw that they were reporting other libraries needed for a 32b application. I Installed them to the computer i mentioned before, and still I was running into weird problems. But here is what I did:

I installed : libc6-i386 , lib32gcc1

Then the messages were different, instead of "command not found" I was getting a message "killed", which means that something was going on. Because the computer was a mess (It was not mine to begin with) I tried a restart, and suddenly..... VOILA!!! The executable was working! When I compiled it as a static, it was showing me that the executable is still "not a dynamic executable". When I compiled it as dynamic it showed me that some libraries were missing! So the weird message is due to the static/dynamic compilation and has nothing to do with the "executability" :)

Now here is the final report. When I switched MY computer this time to Ubuntu 8.04 64bit (not the messy computer of my colleague), I tried to do the necessary installations step by step to find out what was going on. So after I installed the updates and tcsh, I tried to run the fortran executable, nothing happened as expected, same old message! I started to install ia32-libs, and here was the surprise: Synaptic asked to install ADDITIONAL libraries, in order for ia32 to run properly. I marked the suggested ones, and .... VOILA, the executable was running immediately. Apparently in the other PC that I was trying, ia32 was installed WITHOUT the extra supporting libraries! That took me half my day but it was worth it! I post all the "dependent" libraries here, for future reference!

  Installed the following packages:
  ia32-libs (2.2ubuntu11)
  lib32asound2 (1.0.15-3ubuntu4)
  lib32gcc1 (1:4.2.4-1ubuntu3)
  lib32ncurses5 (5.6+20071124-1ubuntu2)
  lib32stdc++6 (4.2.4-1ubuntu3)
  lib32z1 (1:1.2.3.3.dfsg-7ubuntu1)
  libc6-i386 (2.7-10ubuntu4)

As you can see, lib32gcc1 amd lib6-i386 that I installed separately in the other computer, are in the list! The rest of the libraries allowed MY COMPUTER's ldd command to function correctly, when I had a dynamic compilation (NOT A STATIC!)

That was all folks, thanks for the good suggestions!!!!
Cheers

---

