---
title: "system not recognizing 8GB RAM"
date: 2009-07-23
forum: x86 64-bit Users
---

### Post by seabiscuit on 2009-07-23
Hi,

I have ubuntu64 installed on my machine and I have purchased 8 GB or RAM, 2X4GB, installed it to replace my previous 2X2GB and it seems that my OS does not recognize the 8GB.

Please see below the results for the command "top":


op - 16:16:51 up 12 min,  2 users,  load average: 0.11, 0.27, 0.20
Tasks: 134 total,   2 running, 132 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.5%us,  3.2%sy,  0.0%ni, 87.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
**Mem:   3998964k total,   627388k used,  3371576k free,    36868k buffers**
Swap: 13799824k total,        0k used, 13799824k free,   219860k cached

I would very much appreciate you advising here about what can i do to "see" the 8GB of RAM.

PS: I am an ubuntu beginner

Thank you very much!

---

### Post by wojox on 2009-07-23
you may not of seated the cards properly.
I'd turn it off and try reseating them again.

---

### Post by meeples on 2009-07-23
my computer cant support any more than 512mb of ram.

maybe your computer has a limit like that or you have bought the wrong type of ram (eg DDR, DDR2 is that right?)

all i can think off, check if your bios recognizes the ram?

---

### Post by seabiscuit on 2009-07-23
> **meeples said:**
> my computer cant support any more than 512mb of ram.

maybe your computer has a limit like that or you have bought the wrong type of ram (eg DDR, DDR2 is that right?)

all i can think off, check if your bios recognizes the ram?

The fact that my system can support only 4GB is an interesting theory.

I have a dell xps laptop m1530 and did find sites on internet claiming that it supports only 4GB. However I have called Dell before I made the purchase and 
explicitly asked if my system supports 8 GB. They said "Yes" and i purchased my memory from Dell after checking if they think it's compatible (I bought from Dell although it is a Corsair Kit as it was cheaper).

right now I took out 1 RAM unit and with one unit my running top shows what is below, which seems to be identical with what i had with both units in.

I have also tried the advise i got before (2nd posting this thread and i got into something weird: could not pass the Bios screen that got stuck to the "solid bar" filled just about 20%...

any idea what is going on?

$ top

top - 18:22:50 up 1 min,  2 users,  load average: 0.58, 0.19, 0.06
Tasks: 133 total,   2 running, 131 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.5%us,  0.7%sy,  0.0%ni, 96.0%id,  0.8%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3998964k total,   343728k used,  3655236k free,    12956k buffers
Swap: 13799824k total,        0k used, 13799824k free,   120252k cached

---

### Post by jerome1232 on 2009-07-23
What does your computers bios report as total memory? When both sticks are in.

---

### Post by ratcheer on 2009-07-23
> **jerome1232 said:**
> What does your computers bios report as total memory? When both sticks are in.

Precisely. If the computer BIOS cannot "see" it, Linux cannot use it.

Tim

---

### Post by KinKiac on 2009-07-23
> **seabiscuit said:**
> The fact that my system can support only 4GB is an interesting theory.

I have a dell xps laptop m1530 and did find sites on internet claiming that it supports only 4GB. However I have called Dell before I made the purchase and 
explicitly asked if my system supports 8 GB. They said "Yes" and i purchased my memory from Dell after checking if they think it's compatible (I bought from Dell although it is a Corsair Kit as it was cheaper).

right now I took out 1 RAM unit and with one unit my running top shows what is below, which seems to be identical with what i had with both units in.

I have also tried the advise i got before (2nd posting this thread and i got into something weird: could not pass the Bios screen that got stuck to the "solid bar" filled just about 20%...

any idea what is going on?

$ top

top - 18:22:50 up 1 min,  2 users,  load average: 0.58, 0.19, 0.06
Tasks: 133 total,   2 running, 131 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.5%us,  0.7%sy,  0.0%ni, 96.0%id,  0.8%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3998964k total,   343728k used,  3655236k free,    12956k buffers
Swap: 13799824k total,        0k used, 13799824k free,   120252k cached

I wouldnt trust what a phone agent told you.  I used to work in a call centre(not Dell) and from what I undertstand they are all the same.  The people working there in some cases didnt know how to copy and paste before working there, havent been there long(attrition is usually really high for call centres), and know nothing of the products they support except whats written in a script in front of them.  First level support is the worst, if you can manage to get them to send you to second level or advanced support you can usually get someone who actually knows what they are doing, but even then sometimes its hit or miss.  Thats IF you can get second level, in many cases they will say they are sending you to level 2 but then just send you right back to the same dept again.  

If you have found websites that say your model doesnt support any more than 4g, it probably doesnt.

---

### Post by seabiscuit on 2009-07-23
> **jerome1232 said:**
> What does your computers bios report as total memory? When both sticks are in.
 
I have tried to put one of the old 2GB stick and one of the new ggb stick: after it got blocked for a min or so at the Bios screen, it went through. When I used top I got:
 
top - 19:07:57 up 1 min,  2 users,  load average: 0.36, 0.17, 0.06
Tasks: 130 total,   2 running, 128 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.8%us,  3.2%sy,  0.0%ni, 39.1%id, 49.0%wa,  0.5%hi,  0.3%si,  0.0%st
Mem:   6040728k total,  1095684k used,  4945044k free,   716160k buffers
Swap: 13799824k total,        0k used, 13799824k free,   129400k cached
 
SO, it seems that it does work with 6GB.
 

 
jerome1232: I do not know how to check how much the BIOS sees. As it is now stuck at the bios screen, I tried F2 and F12 but no reaction...
 
KinKiac: I agree with you re the first tier  support. However I don't believe what the sites are saying as now I have seen (pls see above the output of "top") that my system can see 6 GB...
 
Any advise?

---

### Post by jocko on 2009-07-24
According to [Dell's documentation]("http://support.euro.dell.com/support/edocs/systems/xpsM1530/en/OM/HTML/specs.htm#wp1102222"), your computer should handle up to 8 Gb of ram, so keep trying. Maybe you need to update the bios? Check Dell's support site if they have any bios upgrades for your computer and try to find the changelogs for those bios versions to see if they mention solving any ram problem.

---

### Post by jerome1232 on 2009-07-24
Do you have a bad stick of ram there? It sounds to me that only the second stick is causing your computer to not pass post.

Try booting with only that second stick in the first slot.

---

### Post by hibliss on 2009-07-24
> **jerome1232 said:**
> 
Try booting with only that second stick in the first slot.

That is your best bet. Test each stick individually. You already know one works, and you get error when the other is installed. Seems you got a bad ram stick.

---

### Post by sanderj on 2009-07-24
> **hibliss said:**
> That is your best bet. Test each stick individually. You already know one works, and you get error when the other is installed. Seems you got a bad ram stick.

Indeed. And after that, combine the functional memory sticks in the two memory bank slot to see what works.

As soon as the BIOS is ready and OK, I myself would run memtest (from the Ubuntu boot menu?) to see if everything is OK.

---

### Post by seabiscuit on 2009-07-24
> **jerome1232 said:**
> Do you have a bad stick of ram there? It sounds to me that only the second stick is causing your computer to not pass post.
 
Try booting with only that second stick in the first slot.
 
I tried booting with each of the new sticks and they each work separately.

---

### Post by seabiscuit on 2009-07-24
> **jocko said:**
> According to [Dell's documentation]("http://support.euro.dell.com/support/edocs/systems/xpsM1530/en/OM/HTML/specs.htm#wp1102222"), your computer should handle up to 8 Gb of ram, so keep trying. Maybe you need to update the bios? Check Dell's support site if they have any bios upgrades for your computer and try to find the changelogs for those bios versions to see if they mention solving any ram problem.

I have trieed to Update the BIOS. I called Dell and they send me to a site, I download an .EXE file, which I do not know how to install... Please see a description of this endeavor in the new thread that I opened:

[http://ubuntuforums.org/showthread.php?p=7670481](http://ubuntuforums.org/showthread.php?p=7670481)

The dell representative (level 2 support) said that he will call Ubuntu to see how can we install, however phone went dead after 15 min of waiting.

I would appreciate help with how can I install this driver, to upgrade the BIOS. The Dell rep said that this is the way to go, however we got stuck due to lack of Ubuntu knowledge.

---

### Post by seabiscuit on 2009-07-24
Thank you everybody for your help!

I finally solved my issue after a 24 hrs ordeal...

It did involve upgrading the BIOS from A09 to A12: if you are interested in the solution, please see the end of the thread below:

[http://ubuntuforums.org/showthread.php?t=1221918](http://ubuntuforums.org/showthread.php?t=1221918)


Now my machine works with 8GB RAM:

top - 11:16:33 up 1 min,  2 users,  load average: 0.73, 0.22, 0.08
Tasks: 133 total,   1 running, 132 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.6%us,  5.3%sy,  0.0%ni, 61.8%id, 22.0%wa,  0.1%hi,  0.2%si,  0.0%st
**Mem:   8088716k total,   556232k used,  7532484k free,   215860k buffers**
Swap: 13799824k total,        0k used, 13799824k free,   120936k cached


PS: I do not need my prev 2 X 2 GB memory that came out with my original Dell System. If anybody is interested in purchasing these from me (at a very reasonable price) please send me a PM.

---

### Post by tad1073 on 2009-07-24
Say's it only supports up to 4gb

[http://www.dell.com/us/en/home/notebooks/xpsnb_m1530/pd.aspx?refid=xpsnb_m1530&cs=19&s=dhs](http://www.dell.com/us/en/home/notebooks/xpsnb_m1530/pd.aspx?refid=xpsnb_m1530&cs=19&s=dhs)

---

### Post by jerome1232 on 2009-07-24
> **tad1073 said:**
> Say's it only supports up to 4gb

[http://www.dell.com/us/en/home/notebooks/xpsnb_m1530/pd.aspx?refid=xpsnb_m1530&cs=19&s=dhs](http://www.dell.com/us/en/home/notebooks/xpsnb_m1530/pd.aspx?refid=xpsnb_m1530&cs=19&s=dhs)

I love it when people just read the topic and not the rest of the thread :p, op solved his issue. He just needed a bios update.

---

### Post by seabiscuit on 2009-07-24
Please see below my system using all 8GB RAM and also swaping:


top - 12:25:59 up  1:10,  3 users,  load average: 1.21, 1.84, 1.59
Tasks: 138 total,   3 running, 135 sleeping,   0 stopped,   0 zombie
Cpu(s): 53.8%us,  1.5%sy,  0.0%ni, 43.0%id,  1.5%wa,  0.2%hi,  0.0%si,  0.0%st
[B]Mem:   8088716k total,  8046052k used,    42664k free,     1900k buffers
Swap: 13799824k total,  6831876k used,  6967948k free,   214828k cached[/B]

wow!

---

### Post by tad1073 on 2009-07-25
> **jerome1232 said:**
> I love it when people just read the topic and not the rest of the thread :p, op solved his issue. He just needed a bios update.

Me too.

I read the first few posts, but not the one where he says he solved it.

I think it was one of those "posting at the same time" moments.

---

### Post by adempewolff on 2009-07-26
> The dell representative (level 2 support) said that he will call Ubuntu to see how can we install, however phone went dead after 15 min of waiting.

:lolflag:  I would be willing to gnaw my leg off if the representative actually called Canonical.  He/she probably fliped a coin over whether to tell you that or promise to personally write a linux compatible version while you were on hold. 	:)

Glad everything worked out though!

---

