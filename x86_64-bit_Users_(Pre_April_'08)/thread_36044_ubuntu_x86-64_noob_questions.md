---
title: "ubuntu x86-64 noob questions"
date: 2005-05-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by lospheris on 2005-05-21
ok i seem to have this little problem. i successfully used linux mandrake and had no problems everything was good. i got rid of that with my athlon xp and went to this system now that i have the 64. installed fine looks clean runs great but the problem is that i can install ANYTHING from driver for my nforce3 chipset to circlemud it wont install. 
i did what nvidia said to do and it said it need a kernel source file. upon attempting to locate this i discovered.... there doesnt seem to be one i have never had this problem before and i am completely lost as what to do so if anyone could help please dear god feel free to do so

haha that sounds more despirate that it really is but i really do need the help i cant get anything done i also need to know how to or where to find how to use apt-get  

i would also like to note the fact that much of my software says i have no c compiler when i try to use the ./configure  command as root

---

### Post by wvslkr on 2005-05-21
Try this  [http://www.ubuntuguide.org](http://www.ubuntuguide.org) should answer most of your questions. :)

---

### Post by poofyhairguy on 2005-05-21
[QUOTE=lospheris]ok i seem to have this little problem. i successfully used linux mandrake and had no problems everything was good. i got rid of that with my athlon xp and went to this system now that i have the 64. installed fine looks clean runs great but the problem is that i can install ANYTHING from driver for my nforce3 chipset to circlemud it wont install. 
i did what nvidia said to do and it said it need a kernel source file. upon attempting to locate this i discovered.... there doesnt seem to be one i have never had this problem before and i am completely lost as what to do so if anyone could help please dear god feel free to do so

haha that sounds more despirate that it really is but i really do need the help i cant get anything done i also need to know how to or where to find how to use apt-get  

i would also like to note the fact that much of my software says i have no c compiler when i try to use the ./configure  command as root[/QUOTE]


Hmm.....the 64 bit version always causes problems. Lack of pluggins, lack of 32bit programs. As a rule I advise anyone who is not a VERY advanced computer user (much more than myself) should use the 32bit version. The only advantage to the 64 bit version (someone correct me if I'm wrong but I'm pretty sure about this) is if you use programs that need more than 4 gigs of RAM. Otherwise I don;t think there is any other benefit. What you can do, is run the 32bit version then use the Athlon kernel (386 is default) then you will get the best of both worlds.

---

### Post by K6-III on 2005-05-22
Hoary64 does feel a bit faster on the same hardware, even for smaller processes.  Nothing worth suffering over, though, for a new user.

---

### Post by FluffyElmo on 2005-05-24
I think the original problem applies to both 32bit and 64bit. Ubuntu doesn't install the kernel source files or any development tools by default. They are available from Synaptic though...search for and install the *linux-source-2.6.x* version that corresponds to your current kernel. You can also install *gcc*, *g++*, *make*, etc by searching Synaptic. Make sure to get the Nvidia 64bit source and you should be good to go. 

As for the eternal 64bit vs 32bit question, while 64bit still has a handful of problems 32bit doesn't (notably Flash & WMV9/10 codecs), 32bit has a signifigant learning curve as well IMHO. 

My 64bit system is fast (*very* fast for some tasks), stable and really took no more trouble to setup than my 32bit one. While my experience may or may not be the norm, and there is more help available for 32bit (due to more users), I often feel 64bit gets a much poorer reputation than it deserves.

---

### Post by Boggles3 on 2005-07-14
so if we are noobs.. uhem like me.. how do you install gcc... ](*,)

---

### Post by jon_gunnar on 2005-07-14
[QUOTE=Boggles3]so if we are noobs.. uhem like me.. how do you install gcc... ](*,)[/QUOTE]

To get the neccessery tools for compiling and so on:

sudo apt-get install build-essential

---

