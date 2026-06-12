---
title: "Memory limit 64bit Ubuntu and R statistics?"
date: 2008-04-23
forum: x86 64-bit Users
---

### Post by zholden on 2008-04-23
Hi Folks,
I've recently installed Ubuntu 7.10 on a 4-processor 64bit machine with 8 GB of ram. I bought this machine, and hope to use Ubuntu, in order to get run larger statistical analyses in the Software program R. In windows, there is a 3 GB memory limit that doesn't allow for the full potential of this program. 

So I finally run R on fairly large data set, and get an error message telling me that R can't allocate a vector of 2.1 GB. 

Forgive my ignorance here, I've never touched a Linux OS until a few days ago...

Is there any way I can direct Ubuntu to take full advantage of the 8 GB of RAM I've installed in this machine? My understanding is that R compiled for Linux should do this automatically. 

I'll be grateful for any suggestions.

Best,

Zack

---

### Post by chrisdugdale on 2008-04-23
I don't know where I saw it last night. Apparently the new Ubuntu, version 8.04 LTS will let u access your memory. It is scheduled for release tomorrow/this afternoon (depending on your time zone). I'm using the 64bit beta and it runs good on my computer.

---

### Post by Cappy on 2008-04-23
Here are a few possible problems:
1) The 8GB is not viewable in ubuntu. Look using the "free" command and see if it lists all of your memory (in the "Mem:" row). If not then it may be a BIOS setting.

2) You are using a 32-bit R (if you installed it from debs it would say -amd64 on the end if it was the 64-bit version). If you aren't sure you can check if the binary is 32-bit with the "file" command, e.g. file /usr/bin/r or wherever it installed.

---

### Post by zholden on 2008-04-24
Cappy and Chris,
Thanks for the replies. Cappy, that's really helpful. I'm new to the Linux world, those commands will help me figure out what is going on. An R forum post suggested that my model may still just be too large. Maybe I need yet a few more sticks of RAM.

Thanks again for the help,

Zack

---

### Post by kutjara on 2008-04-24
> **zholden said:**
> Cappy and Chris,
Thanks for the replies. Cappy, that's really helpful. I'm new to the Linux world, those commands will help me figure out what is going on. An R forum post suggested that my model may still just be too large. Maybe I need yet a few more sticks of RAM.

Thanks again for the help,

Zack

A little more food for thought: I read that the new 2.6.25 kernel contains a fix for systems with more than 4GB of RAM. Apparently, with earlier kernels (like the one in Hardy - 2.6.24), not all of the memory was being correctly addressed. I'm fuzzy on the specifics, but it's probably worth doing a google on the new kernel to see what improvements it offers.

---

### Post by Slammer64 on 2008-04-24
Both 32 bit Windows and Linux (unless the Linux kernel was compiled with the PAE extensions) will only see approximately 3.25 gig of ram, most Linux 64 bit distributions available today only compile their kernels with support of up to 4 gig of ram, you may need a specialty distro or learn how to roll your own kernel to enable up to 64 gig of ram support.

---

### Post by koshcu on 2008-04-25
Most of the statements made in this thread are VERY wrong. I have been running 64bit ubuntu for a year now with 8G of ram in my box and all of it is addressable and since processes can use all of that memory.

If your program is failing right around the 2GB mark then the odds are very high that the program you are using is a 32bit program. Just about everything except flash is 64bit in the archives but if you installed from another source you might have installed a 32bit version.

Linux has been able to use more then 4GB under 64bit since the alpha port a LONG time ago. x86-64 could use more then 4GB from the beginning.

PAE = Page Address Extensions and it only matters for a 32bit os not a 64bit one

My current machine is a Tyan S-2915 board with dual 2218 opterons and 8G of ram, no problems under ubuntu using all of it.

---

### Post by ASULutzy on 2008-04-25
Since you are probably looking for actual help, click applications, then click accessories, then terminal.

Once that is up type ```
free -m
``` and paste the output here.

We need to see if the problem is localized to just the application you're using, or if it's system wide.

If free -m shows you have more than 3 GB of RAM, you just need to install the 64 bit version of the program you're using.

If it shows 3 GB or less, you've either forgotten to enable memory remapping in your BIOS, or you mistakingly installed the 32 bit version of Ubuntu instead of the 64 bit version.

This is not an Ubuntu limitation, as in Windows you would encounter the same issue if you tried to use more than 3GB of RAM on a 32 bit install. You need to install a 64 bit operating system to address that much RAM.

Welcome to Ubuntu!

---

### Post by Sef on 2008-04-25
> This is not an Ubuntu limitation, as in Windows you would encounter the same issue if you tried to use more than 3GB of RAM on a 32 bit install. You need to install a 64 bit operating system to address that much RAM.

32-bit operating systems are limited to about 3.7 gb ram.  

64-bit operating systems are limited to about [16.8 million tetrabytes]("http://en.wikipedia.org/wiki/64-bit").

---

### Post by zholden on 2008-04-25
What an amazing forum...thank you all for the replies. 

When I use the free command, all 8 GB of RAM are being used. 

When I installed R (following instructions on the Linux/Ubuntu download page) I installed the 32 bit version. 

I read the R install instructions again this morning and I can't really decipher how to specify a 64 bit install rather than the 32 bit. 

I'm guessing this is a simple command statement in a terminal window, but I'm a bit of a computer dummy, so this isn't obvious to me. 

Can anyone tell me how to install (compile binaries??) the 64 bit version? 

Thanks again,

Zack

---

### Post by NiN on 2008-04-25
R is available from the repositories, so if you do not need any special patches, a simple ```
 apt-get install r-base 
``` will do the trick.  There seem to be many additions available in the repositories, so have a look around (best way is to use synaptic and search for "r-" to limit the amount of packages to search trough)

---

### Post by zholden on 2008-04-25
That's actually now in installed it the first time, and assumed it would run the amd64 bit by default. Is there something I need to do after installation, e.g. when I start R in Ubuntu? I've been typing "sudo R" in the terminal window to get start it up.

Thanks again,

Zack

---

### Post by NiN on 2008-04-25
If you already installed that way, you have the 64 bit version installed. It may then be a question of your dataset or a bug in R. I don't know much about the program, so it may be better to read it's release notes, maybe they mention someting.  Btw: why do you start R with sudo? As far as I know, it should work just fine with normal user privileges.

---

### Post by monkeyking on 2008-06-02
Forget the repos for R, I don't think these are 64bit,
I decided to compile from source, use this guide

[http://ubuntuforums.org/showthread.php?t=639710](http://ubuntuforums.org/showthread.php?t=639710)

This one tells you how to install the newest 2.7.0 R on ubuntu using the official sources.

It is about 5 lines of code, but takes around 10 minuttes to do.

I tried this on 7.10 and now on 8.4,

good look.

---

### Post by narcisgarcia on 2009-03-10
You can run this command in a terminal:
```
uname -m
```

If it returns "i686" or similar, you are running a 32-bit environment. If it returns "x86_64" you are running in 64-bit.

---

