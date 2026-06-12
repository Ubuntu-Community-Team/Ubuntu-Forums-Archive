---
title: "New Ubuntu User: Installation &amp; Conf. Problems..."
date: 2007-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by navas on 2007-03-31
Hi everybody!

I decided to give Linux a try and had chosen Ubuntu. I installed 6.10, but now i find so many problems that could leave me to definitely leave linux... I hope you could help me.

To begin, these are my PC specs: 
Compaq Presario R3000, AMD Athlon 64, NVIDIA GeForce4 440Go 64M, Ethernet Card Realtek RTL8139/810x, Wi-fi Broadcom 43xxx...

So:

1. When I boot, the screen with the ubuntu logo and the waiting bar is black & white. This is not really important but could indicate some problems recognizing the NVIDIA video card.

2. Most important. When I connect my PC to the net via Ethernet cable... nothing happens! I cant use Internet! Thats why i am writing this in Windows XP... As you will understand, as long as i dont have Internet access, Linux is not useful.

3. Then I tried the Wi-fi; I already know the problems with the Broadcom bcm43xx chips ([http://bcm43xx.berlios.de/)](http://bcm43xx.berlios.de/)), but in order to solve these problems i have to download some packages from repositories, and i don't Internet access! The other possible solution is to use "ndiswrapper" but i don't know how to use it...

4. Si I tried to compile a new kernel, hoping that Ethernet and wi-fi drivers could be included in the new kernel. I followed these instructions ([http://www.howtoforge.com/kernel_compilation_ubuntu)](http://www.howtoforge.com/kernel_compilation_ubuntu)), and when i do "make menuconfig" i have the message shown at the end of this post. I think that reading the firsts lines gives an idea: i don't have basic C libraries! 

As you see, installing linux in my machine is really a pain, and i suppose thats why linux i not used by the "normal" PC user (the one that only use hotmail and word, more than 80% of users), but i will try harder and i hope i will make it.

If you have any useful ideas, please...

Thanks!

------------------------------------------------------------------------------------------------------------------
make menuconfig output:

make menuconfig
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:105:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:106:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:107:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:108:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:109:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:111:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:112:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/x86_64-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.1.2/include/limits.h:11,
                 from scripts/basic/fixdep.c:113:
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:115:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function ‘usage’:
scripts/basic/fixdep.c:129: warning: implicit declaration of function ‘fprintf’
scripts/basic/fixdep.c:129: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:129: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:129: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:129: error: for each function it appears in.)
scripts/basic/fixdep.c:130: warning: implicit declaration of function ‘exit’
scripts/basic/fixdep.c:130: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c: In function ‘print_cmdline’:
scripts/basic/fixdep.c:138: warning: implicit declaration of function ‘printf’
scripts/basic/fixdep.c:138: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:141: error: ‘NULL’ undeclared here (not in a function)
scripts/basic/fixdep.c: In function ‘grow_config’:
scripts/basic/fixdep.c:154: warning: implicit declaration of function ‘realloc’
scripts/basic/fixdep.c:154: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:156: warning: implicit declaration of function ‘perror’
scripts/basic/fixdep.c:156: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c: In function ‘is_defined_config’:
scripts/basic/fixdep.c:172: warning: implicit declaration of function ‘memcmp’
scripts/basic/fixdep.c: In function ‘define_config’:
scripts/basic/fixdep.c:185: warning: implicit declaration of function ‘memcpy’
scripts/basic/fixdep.c:185: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c: In function ‘use_config’:
scripts/basic/fixdep.c:204: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:212: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c:218: warning: implicit declaration of function ‘tolower’
scripts/basic/fixdep.c:220: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c:204: warning: unused variable ‘s’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:223: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_config_file’:
scripts/basic/fixdep.c:225: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:231: warning: implicit declaration of function ‘ntohl’
scripts/basic/fixdep.c:242: warning: implicit declaration of function ‘isalnum’
scripts/basic/fixdep.c: In function ‘strrcmp’:
scripts/basic/fixdep.c:255: warning: implicit declaration of function ‘strlen’
scripts/basic/fixdep.c:255: warning: incompatible implicit declaration of built-in function ‘strlen’
scripts/basic/fixdep.c: In function ‘do_config_file’:
scripts/basic/fixdep.c:266: error: storage size of ‘st’ isn’t known
scripts/basic/fixdep.c:270: warning: implicit declaration of function ‘open’
scripts/basic/fixdep.c:270: error: ‘O_RDONLY’ undeclared (first use in this function)
scripts/basic/fixdep.c:272: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:272: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:274: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:276: warning: implicit declaration of function ‘fstat’
scripts/basic/fixdep.c:278: warning: implicit declaration of function ‘close’
scripts/basic/fixdep.c:281: warning: implicit declaration of function ‘mmap’
scripts/basic/fixdep.c:281: error: ‘PROT_READ’ undeclared (first use in this function)
scripts/basic/fixdep.c:281: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
scripts/basic/fixdep.c:281: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:288: error: too many arguments to function ‘parse_config_file’
scripts/basic/fixdep.c:290: warning: implicit declaration of function ‘munmap’
scripts/basic/fixdep.c:266: warning: unused variable ‘st’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:295: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_dep_file’:
scripts/basic/fixdep.c:298: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:300: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:302: warning: implicit declaration of function ‘strchr’
scripts/basic/fixdep.c:302: warning: incompatible implicit declaration of built-in function ‘strchr’
scripts/basic/fixdep.c:304: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:304: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:305: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:307: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c:308: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c:300: warning: unused variable ‘s’
scripts/basic/fixdep.c: In function ‘print_deps’:
scripts/basic/fixdep.c:337: error: storage size of ‘st’ isn’t known
scripts/basic/fixdep.c:341: error: ‘O_RDONLY’ undeclared (first use in this function)
scripts/basic/fixdep.c:343: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:343: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:345: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:349: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:353: error: ‘PROT_READ’ undeclared (first use in this function)
scripts/basic/fixdep.c:353: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
scripts/basic/fixdep.c:353: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:360: error: too many arguments to function ‘parse_dep_file’
scripts/basic/fixdep.c:337: warning: unused variable ‘st’
scripts/basic/fixdep.c: In function ‘traps’:
scripts/basic/fixdep.c:372: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:372: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:374: warning: incompatible implicit declaration of built-in function ‘exit’
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2

---

### Post by nsteussy on 2007-03-31
navas,

You are posting in a forum designed for folks who install the x86-64 version of ubuntu.  If you don't have specific needs for the 64 bit version, I'd recommend you install the 32 bit production version (6.10).  You will have many fewer headaches.

Regarding your network problem - boot up the 6.10 live CD.  Can you access the network?

The black/white ubuntu splash screen is an artistic choice.

You will need to install the nvidia drivers after you get a working installation.

duke out

---

### Post by Kilz on 2007-03-31
> **nsteussy said:**
> navas,

You are posting in a forum designed for folks who install the x86-64 version of ubuntu.  If you don't have specific needs for the 64 bit version, I'd recommend you install the 32 bit production version (6.10).  You will have many fewer headaches.

Regarding your network problem - boot up the 6.10 live CD.  Can you access the network?

The black/white ubuntu splash screen is an artistic choice.

You will need to install the nvidia drivers after you get a working installation.

duke out

Nothing in his list of problems other than the black and white startup is a 64bit issue that will be solved by going to 32bit. This is easy to fix by installing another graphic. The other problems will most likely face him in 32bit land. Suggesting someone install the 32bit version , while in the 64bit section is not a god idea imho. They made their choice, lets support them on it, not offer them FUD.

---

### Post by Kilz on 2007-03-31
> **navas said:**
> Hi everybody!

I decided to give Linux a try and had chosen Ubuntu. I installed 6.10, but now i find so many problems that could leave me to definitely leave linux... I hope you could help me.

To begin, these are my PC specs: 
Compaq Presario R3000, AMD Athlon 64, NVIDIA GeForce4 440Go 64M, Ethernet Card Realtek RTL8139/810x, Wi-fi Broadcom 43xxx...

So:

1. When I boot, the screen with the ubuntu logo and the waiting bar is black & white. This is not really important but could indicate some problems recognizing the NVIDIA video card.

2. Most important. When I connect my PC to the net via Ethernet cable... nothing happens! I cant use Internet! Thats why i am writing this in Windows XP... As you will understand, as long as i dont have Internet access, Linux is not useful.

3. Then I tried the Wi-fi; I already know the problems with the Broadcom bcm43xx chips ([http://bcm43xx.berlios.de/)](http://bcm43xx.berlios.de/)), but in order to solve these problems i have to download some packages from repositories, and i don't Internet access! The other possible solution is to use "ndiswrapper" but i don't know how to use it...

4. Si I tried to compile a new kernel, hoping that Ethernet and wi-fi drivers could be included in the new kernel. I followed these instructions ([http://www.howtoforge.com/kernel_compilation_ubuntu)](http://www.howtoforge.com/kernel_compilation_ubuntu)), and when i do "make menuconfig" i have the message shown at the end of this post. I think that reading the firsts lines gives an idea: i don't have basic C libraries! 

As you see, installing linux in my machine is really a pain, and i suppose thats why linux i not used by the "normal" PC user (the one that only use hotmail and word, more than 80% of users), but i will try harder and i hope i will make it.

If you have any useful ideas, please...

Thanks!


1. [Take a look here]("http://www.ubuntuforums.org/showthread.php?t=304673") for instructions on how to replace the black and white graphics.
2. What connection is the computer using , look in System > Adminastration > Networking.
3. the ndsiwrapper is a package, you will also need a 64bit windows driver. I recommend getting the wired connection working first then get these things.
4. You are correct , you are missing the header files. You need the a number of [packages listed here]("https://help.ubuntu.com/community/Kernel/Compile?highlight=%28kernel%29"), work on the wired access before starting this. Also you may be doing this for nothing. This is a last resort step as the kernel compile page states.

---

