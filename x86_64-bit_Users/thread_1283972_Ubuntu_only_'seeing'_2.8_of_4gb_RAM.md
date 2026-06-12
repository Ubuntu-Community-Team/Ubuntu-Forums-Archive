---
title: "Ubuntu only 'seeing' 2.8 of 4gb RAM"
date: 2009-10-06
forum: x86 64-bit Users
---

### Post by thegutterpoet on 2009-10-06
I recently installed 2 X 2GB corsair SODIMM Ram pieces into my hp compazy nx6235, dual core turion tl=50, 1.6ghz laptop.

The SETUP which I assume is BIOS...the program that can be run before choosing which operating system to boot, recognized the new ram, and counted it. And when I press f10, to enter into that area, it tells me, in system information that I have 4096MB of RAM...

Windows XP, the 32-bit version, when I use it, tells me that I have 3.15GB RAM...which makes sense, given that particular OS's restraints...

However, Ubuntu 9.04 64 bit, sees only 2,8gb RAM.

I have contacted the HP people, who tell me, that yes, my system can take up to 4gb RAM, as long as the 2 X 2GB are of the same speed, which they are. They also tell me, that it is common for XP 32 bit to 'see' only between 2.8 and 3.2GB of RAM as a maximum...and lastly...they tell me, that if my SETUP program 'sees' 4GB then the ram is working fine and dandy.

But still...Ubuntu 64-bit, does NOT see it.

PLEASE HELP...

---

### Post by Lampi on 2009-10-06
check /proc/meminfo and give us the output

It might be kernel related ... debian for example has a **bigmem** kernel configured for >2GB RAM I guess. Does Ubuntu have bigmem kernel images?

---

### Post by thegutterpoet on 2009-10-06
Do you mean, type that code into the terminal???

Sorry, i need more direction!

I have installed the python- meminfo file...but am unsure how to run it. I tried
/proc/meminfo
which gave me :> bash: /proc/meminfo: Permission denied
and also exactly as you wrote:
check /proc/meminfo
which gave me:> bash: check: command not found

but I did manage to run this
**$ cat /proc/meminfo** command
which gave me this:>

MemTotal:        2925860 kB
MemFree:         2002520 kB
Buffers:           35736 kB
Cached:           350980 kB
SwapCached:            0 kB
Active:           595128 kB
Inactive:         216192 kB
Active(anon):     432028 kB
Inactive(anon):        8 kB
Active(file):     163100 kB
Inactive(file):   216184 kB
Unevictable:           8 kB
Mlocked:               8 kB
SwapTotal:        489940 kB
SwapFree:         489940 kB
Dirty:               116 kB
Writeback:             0 kB
AnonPages:        424760 kB
Mapped:            95216 kB
Slab:              41936 kB
SReclaimable:      28488 kB
SUnreclaim:        13448 kB
PageTables:        16936 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1952868 kB
Committed_AS:     748352 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      295864 kB
VmallocChunk:   34359441187 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:        8000 kB
DirectMap2M:     3006464 kB

Now where the devil is my other 1.1GB, if it is only 'seeing' 2.9GB???

even windows 32 bit XP 'sees' more than that...and surely something can be done!!!

---

### Post by cmckdub on 2009-10-06
I am having almost identical issue. Hardware of mine is an ACER TravelMate 4234. I recently upgraded the RAM to 4 GB (2 identical sticks), which meant that 32 bit Hardy recognised a little over 3GB. I increased the RAM because I wanted more RAM for running Windows 7 in VirtualBox. Now the BIOS shows "Extended RAM 4095MB".:)
I then installed 64bit Jaunty, only to find that it now shows only 2.9GB of RAM.:(
I found a similar post in another thread, but still no answers.:confused:
[http://ubuntuforums.org/showthread.php?t=1270401](http://ubuntuforums.org/showthread.php?t=1270401)

---

### Post by thegutterpoet on 2009-10-06
Well...I can't say that it improves my condition to know that I am not alone in this shadowland of darkness. But what the hell...The more the merrier. Perhaps if we combine forces, we can double the exposure of our horrors, and hopefully double the chances of finding a remedy.

---

### Post by Lampi on 2009-10-06
Like I said it's most likely kernel related - to be sure make this final check:

$ cat /boot/config-`uname -r` | grep "CONFIG_HIGHMEM64G"

if you get this output: 

# CONFIG_HIGHMEM64G is not set

then it's clear your kernel is missing the necessary bigmem support

There's two things you can try with ubuntu:

- compile your own kernel with CONFIG_HIGHMEM64G support
- or you can try a different kernel image (64bit, or 32bit server edition)

If you're lucky one of them offers bigmem support. Keep in mind your current kernel does work fine even without using the 4G's, so why bother?

[...]
- last resort: change to debian, they offer precompiled kernel images with bigmem support :-)

---

### Post by NoaHall on 2009-10-06
It might even be your bios settings. You could "flash" it, but it's very risky.

---

### Post by sanderj on 2009-10-06
[http://ubuntuforums.org/showthread.php?t=1270401](http://ubuntuforums.org/showthread.php?t=1270401) is a good thread for your FAQ.

Two important things:

1) Double-check you're using 64-bit OS:
open a terminal and type 'uname -a' and post the output here. It should contain "x86_64"

2) your BIOS:
First thing to do: Update your BIOS to the newest version.

If that does not solve the memory problem, check your BIOS for a setting "memory (hole) hoisting" or "memory (hole) remapping": if you find that setting, you should turn it on.

If the above does not solve it, you could be out of luck. Your laptop is dated 2006 (right?) and in that time full 64-bit and 4GB RAM was not yet common technology. That would mean your BIOS not supoort memory hole hoisting/remapping, and your OS won't see 4GB

---

### Post by cmckdub on 2009-10-06
Thanks for the thoughts.
I tried:
```
cat /boot/config-`uname -r` | grep "CONFIG_HIGHMEM64G"
```
It did not appear to do anything.
I then did 
```
cat /proc/meminfo
MemTotal:        3054272 kB
MemFree:         1610736 kB
Buffers:          162948 kB
Cached:           865488 kB
SwapCached:            0 kB
Active:           754352 kB
Inactive:         540264 kB
Active(anon):     562276 kB
Inactive(anon):        0 kB
Active(file):     192076 kB
Inactive(file):   540264 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       4056404 kB
SwapFree:        4056404 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:        266328 kB
Mapped:            58628 kB
Slab:              97448 kB
SReclaimable:      74836 kB
SUnreclaim:        22612 kB
PageTables:        15624 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     5583540 kB
Committed_AS:     841956 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      271344 kB
VmallocChunk:   34359465203 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:        6656 kB
DirectMap2M:     3137536 kB
```
So it is still the same.
Yes it is 64bit. (Remember I had more memory available in 32 bit anyway).

No the BIOS allows for no other memory settings.

Thanks Sanderj for the suggestion about Flashing the BIOS. Flashing the BIOS is not an easy step as I can only find options for doing this in Windows. Also, I cannot find any references to it improving memory issues. Considering the risk involved, how do you know it will be helpful? The computer was manufactured in 2007.

Regarding the idea of compiling my own Kernel - I am not at that level, and would not even know where to start. I do not even feel comfortable with going with a different distribution (It may be too hard for me to get my mind around, considering that I am required to work in Windows 7 at work.):cry:

---

### Post by thegutterpoet on 2009-10-07
cat /boot/config-`uname -r` | grep "CONFIG_HIGHMEM64G"

did nothing for me either. Not sure if I am simply not pasting it into the terminal correctly, but every time I pressed return, the cursor returned soon after, with no reports of errors or information requested...

---

### Post by Lampi on 2009-10-07
the file might have a different name than I expected, so try to use find:
```
find /boot -name "config*" -exec grep "CONFIG_HIGHMEM64G" {} \;

```

---

### Post by thegutterpoet on 2009-10-08
that command returned nothing but the prompt...any other ideas!!!

---

### Post by sanderj on 2009-10-08
> **thegutterpoet said:**
> that command returned nothing but the prompt...any other ideas!!!

I'm still waiting for your output of "uname -a"...

---

### Post by thegutterpoet on 2009-10-08
> **sanderj said:**
> I'm still waiting for your output of "uname -a"...

My output from that is :

Linux raphael-laptop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux

---

### Post by sanderj on 2009-10-08
> **thegutterpoet said:**
> My output from that is :

Linux raphael-laptop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux

OK: "x86_64". That's good. So the OS is not the problem. Only the BIOS remains. If the BIOS does not provide memory above the 32-bit/4GB barrier, and you can't solve that with a BIOS update and you can't solve that with a (missing) BIOS setting for memory hoisting / hole remapping, you're out of luck. Your laptop (2007, right?) hasn't got the above the 32-bit/4GB barrier feature ...

FYI: the fact that the BIOS (or Windows Vista) reports 4GB RAM is just that: the memory is there. Linux has also a command to show the physcial RAM. See below.
What counts: To make it usable, the BIOS needs to remap everything above 3GB above the 32bit/4GB barrier. If the BIOS does not do that, the OS will only see around 3GB.


Edit: 
if you want Ubuntu to show the physical installed memory chips (just like the BIOS and Vista does), you can use

> sudo lshw | grep -A 200 memory | grep size:

Sample output of my 1GB only laptop (sorry, no access to my 4GB machine right now):

> ubuntu@ubuntu:~$ sudo lshw | grep -A 200 memory | grep size: 
          size: 1GiB      
             ...  size: 512MiB
             ...  size: 512MiB
ubuntu@ubuntu:~$

So: I have 1GB physical RAM, composed by two RAM modules of 512 MB each.


If that does not work: use

> sudo lshw 

for very raw output, and search for your physical memory.

---

### Post by falconindy on 2009-10-08
Laptops are notorious for "stealing" memory. The missing memory is likely shared with the graphics card. The output of `free` should show the missing 1gb under the 'shared' column.

---

### Post by Slim Odds on 2009-10-08
I'm completely baffled as to why some of you would think that the issue would be the kernel (or the kernel configuration).

Do you really think that the kernel that Ubuntu distributes with the 64 bit version would not be configured to allow more then 4G of RAM?

Especially since tons of people use it without issues.

---

### Post by sanderj on 2009-10-08
> **Slim Odds said:**
> I'm completely baffled as to why some of you would think that the issue would be the kernel (or the kernel configuration).


I completely agree!

Lesson to be learned: apparantly this subject is dark magic to a lot of people: both the OP and some of the people answering.

Time to write a wiki about this FAQ "I'm only see around 3GB of my 4+GB RAM".

Or even better: Ubuntu should provide a built-in tool that would check the physical RAM (with the lshw command), and if it's more than 3GB, would check the CPU for 64-bit-ness and check whether the OS was 64-bit. If Yes resp No, it could advice the 64-bit OS.
With a 64-bit OS, and still memory lost, it could advice to upgrade the BIOS.
This tool could even collect & share BIOS-dates/version, and build a list of BIOSes capable of memory memory hole hoisting / remapping

---

### Post by thegutterpoet on 2009-10-10
> **sanderj said:**
> OK: "x86_64". That's good. So the OS is not the problem. Only the BIOS remains. If the BIOS does not provide memory above the 32-bit/4GB barrier, and you can't solve that with a BIOS update and you can't solve that with a (missing) BIOS setting for memory hoisting / hole remapping, you're out of luck. Your laptop (2007, right?) hasn't got the above the 32-bit/4GB barrier feature ...

FYI: the fact that the BIOS (or Windows Vista) reports 4GB RAM is just that: the memory is there. Linux has also a command to show the physcial RAM. See below.
What counts: To make it usable, the BIOS needs to remap everything above 3GB above the 32bit/4GB barrier. If the BIOS does not do that, the OS will only see around 3GB.


Edit: 
if you want Ubuntu to show the physical installed memory chips (just like the BIOS and Vista does), you can use



Sample output of my 1GB only laptop (sorry, no access to my 4GB machine right now):



So: I have 1GB physical RAM, composed by two RAM modules of 512 MB each.


If that does not work: use



for very raw output, and search for your physical memory.

Using that command, the first one, gives me the following:

[B]size: 4GiB      
             size: 2GiB
             size: 2GiB
                size: 55GiB (60GB)
                   size: 43GiB
                   size: 11GiB[/B]

so where can I go from here??? How can I tell BIOS to remap the RAM??? Take out the RAM and then put it back in????

---

### Post by sanderj on 2009-10-11
> **thegutterpoet said:**
> Using that command, the first one, gives me the following:

[B]size: 4GiB      
             size: 2GiB
             size: 2GiB


Good, that shows that you have 2 x 2GB = 4GB physically installed.

> **thegutterpoet said:**
> 
so where can I go from here??? How can I tell BIOS to remap the RAM??? Take out the RAM and then put it back in????

Recipe:
1) Search your BIOS for a setting called "memory hoisting" or "memory (hole) remapping". If found, it should be on.
2) If you can't find that option, update your BIOS, and search again.
3) If still not found, you're out of luck, and you will only be able to use about 3GB of RAM.

Rule of thumb: the older your BIOS, the lesser your chance on the memory-hoisting-option. A 2009 BIOS should be OK, with a 2006/2007 BIOS chances are much smaller.

---

### Post by falconindy on 2009-10-11
I'm still unconvinced that you're missing any memory at all. Again, it's a laptop. Laptops, very often, share memory with the graphics card. Post the output of `free`.

---

### Post by thegutterpoet on 2009-10-12
> **falconindy said:**
> I'm still unconvinced that you're missing any memory at all. Again, it's a laptop. Laptops, very often, share memory with the graphics card. Post the output of `free`.

output of 'free':>

           [B]  total      used             free        shared    buffers     cached
Mem:       2925860    2835276      90584          0               518576    1304236
-/+ buffers/cache:    1012464    1913396
Swap:       489940       6608     483332[/B]


the total shared memory appears as 0.

---

### Post by cmckdub on 2009-10-12
Unfortunately it seems to be exactly as sanderj and Slim Odds have been saying. I too tried:
```
ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2982       1460       1522          0        127        797
-/+ buffers/cache:        534       2448
Swap:         3961          0       3961
```
and saw that shared was zero. I think you are correct that 1.2GB is too big for losing by either shared memory or faulty RAM (I also checked all my RAM for errors).
I also checked what was being posted here by installing Windows 7 32 bit and then 64 bit, and compared it to what we were getting in Ubuntu. The differences were minor. I also then checked many other forums and sites such as Intel.
So, in turning to the hardware, as mine is ACER, I asked them about updating the BIOS from v3.5 to v3.6, as I was very skeptical of this move. Their reply indicated that despite the advertising when my laptop was purchased, that they do not support 64bit for my model.:( 
I think the confusion for me came from the advertised CPU indicating 64bit support, saying that the Intel core 2 Duo Processor supports Intel EM64T - which I understand to mean that the CPU can address RAM above 4GB. (I may still be speaking dark magic according to sanderj). However, the Intel i945 chipset in my ACER laptop apparently only uses 32 bit addressing and so does not allow for addressing above 4GB. (Again I may be speaking dark magic here).
As I suspected, for me, upgrading the BIOS would therefore do nothing but risk turning my laptop into landfill.
The bottom line for me is that I am stuck, and have no advantage in going 64bit on this machine. Also, I will need to be lots more careful in checking for false advertising claims when I get my next machine.
For thegutterpoet, you could check the same thing for your model, but if there are no BIOS settings (as there wasn't any on mine), then you too may be stuck too with being unable to access that last 1.2GB.:(

---

### Post by falconindy on 2009-10-12
Well, I'll admit that I'm a little baffled by that. You mentioned that the BIOS shows you as having 4gb, but does your **POST** show 4gb?

Have you tried booting off a live CD and seeing the result?

I'm a little skeptical of any company who claims that their 64 bit hardware isn't up to the task of a 64 bit OS. That's just hogwash. In a similar story of what HP tells you not to do, I was told an HP Pavillion dv7 didn't support Windows XP. Anything other than Vista was "unsupported". Sure enough, HP's Vista drivers actively refused to load in XP and there was no sign of a native driverset. A few hours later when I was done finding drivers directly from the hardware manufacturers, everything worked fine.

---

### Post by cmckdub on 2009-10-12
> **falconindy said:**
> Have you tried booting off a live CD and seeing the result?
Yes - many times over.
> **falconindy said:**
> I'm a little skeptical of any company who claims that their 64 bit hardware isn't up to the task of a 64 bit OS. That's just hogwash. In a similar story of what HP tells you not to do, I was told an HP Pavillion dv7 didn't support Windows XP. Anything other than Vista was "unsupported". Sure enough, HP's Vista drivers actively refused to load in XP and there was no sign of a native driverset. A few hours later when I was done finding drivers directly from the hardware manufacturers, everything worked fine.
True. I had to ignore what ACER told me, and install Ubuntu in the first place. However the documentation from Intel seems to back this up (from my small understanding). It is only the CPU which seems to be OK for 64bit, and not the chipset/BIOS.

---

### Post by grege on 2009-10-13
I make no guarantees, but you could try using 32bit Ubuntu with PAE

 [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

To do this install 32bit and then use Synaptic to install a server kernel and restart.

$ sudo sudo apt-get install linux-headers-server linux-image-server linux-server

You may end up with the same issue due to the BIOS limitations. My 64bit desktop shows 3.9gb ram without any mucking about, so you laptop might just be unable to use more than 3gb no matter what.

---

### Post by sanderj on 2009-10-13
> **grege said:**
> I make no guarantees, but you could try using 32bit Ubuntu with PAE


My guess: this won't work either. 

Reason: if the hardware/BIOS is not doing memory hoisting / hole remapping, and thus no memory above 3,x GB barrier is addressable, neither 64-bit OS nor 32-bit PAE can use that memory.

---

### Post by Slim Odds on 2009-10-13
> **sanderj said:**
> My guess: this won't work either. 

Reason: if the hardware/BIOS is not doing memory hoisting / hole remapping, and thus no memory above 3,x GB barrier is addressable, neither 64-bit OS nor 32-bit PAE can use that memory.

I totally agree. If the 64 bit version doesn't see it, there is another problem that won't be solved by PAE.

---

### Post by thegutterpoet on 2009-10-14
This laptop came originally equipped with a 64-bit processor. And the bios tells me I have 4gb ram installed....

So what are my options?

Is it worthy updating my bios???

Also...when I installed the RAM, and rebooted, a question was asked...I cannot remember what it was, but it was bios asking me something...It may have been a Y/N answer, I can't recall...but after this question had been answered, the new memory was counted. Still, Bios already knows I have that amount of RAM installed. it even checks it for errors, and finds none, when asked. There is no option for remapping memory in my current HP bios...

The maximum RAm for this original laptop is 4GB...

BIOS UPDATE?

---

### Post by sanderj on 2009-10-14
> **thegutterpoet said:**
> This laptop came originally equipped with a 64-bit processor. And the bios tells me I have 4gb ram installed....

So what are my options?

Is it worthy updating my bios???

<snip>


BIOS UPDATE?


The answer to that question has been to you three times in the past week:

[http://ubuntuforums.org/showpost.php?p=8062712&postcount=8](http://ubuntuforums.org/showpost.php?p=8062712&postcount=8)

[http://ubuntuforums.org/showpost.php?p=8071843&postcount=15](http://ubuntuforums.org/showpost.php?p=8071843&postcount=15)

[http://ubuntuforums.org/showpost.php?p=8086525&postcount=20](http://ubuntuforums.org/showpost.php?p=8086525&postcount=20)

---

### Post by Portable_Jim on 2009-10-14
> **thegutterpoet said:**
> This laptop came originally equipped with a 64-bit processor. And the bios tells me I have 4gb ram installed....

So what are my options?

Is it worthy updating my bios???

Also...when I installed the RAM, and rebooted, a question was asked...I cannot remember what it was, but it was bios asking me something...It may have been a Y/N answer, I can't recall...but after this question had been answered, the new memory was counted. Still, Bios already knows I have that amount of RAM installed. it even checks it for errors, and finds none, when asked. There is no option for remapping memory in my current HP bios...

The maximum RAm for this original laptop is 4GB...

BIOS UPDATE?
It may be that a bios update will not help. It may be that the chipset (i.e. the motherboard) cannot actually address all your 4GB of ram. 
Bad analogy time...The arm of your 40 CD chooser may be only able to get to 32 CDs. 

Then again, maybe that is not the case.

Could you please post the following information as it will help in solving your problem:

[LIST=1]
[*]The chipset of the computer. This is usually found in the computer handbook. (this will save googleing you computer model for the info). If you cant find it, or you are confused, just say so.
[*]The output of ```
dmesg | grep BIOS
``` specifically the part that look something like this ```
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afef0000 (usable)
[    0.000000]  BIOS-e820: 00000000afef0000 - 00000000afef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afef3000 - 00000000aff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000250000000 (usable)
```
[/LIST]
Some extra reading:
Last post of [http://hera.hardocp.com/showthread.php?p=1034638421](http://hera.hardocp.com/showthread.php?p=1034638421) 
(3rd page of thread) [http://tinyurl.com/ykqwdhr](http://tinyurl.com/ykqwdhr)

---

### Post by cmckdub on 2009-10-14
I can understand your reluctance to update the BIOS as it is a risky operation. To flash the BIOS you will need to know your BIOS version, and look on the HP site. 
I had a quick look for your BIOS information using the information you provided at the start of this thread and couldn't find anything.
Is your model really a Compaq nx6325? If it is, then _[this site]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=3315736&prodSeriesId=1849082&swLang=8&taskId=135&swEnvOID=1093")_ seems to be the place to get the BIOS update. The latest seems to be F.07. What version is your BIOS? There is also specific information about updating your BIOS in Ubuntu _[here]("https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6325#BIOS%20update")_ - which would makes me feel more comfortable about the BIOS update on yours, **if** this is your model. However, check that all the information is correct, as it doesn't match what you originally posted, and if it is incorrect you may turn the laptop into landfill.
I particularly note that on the _[specification for such a laptop]("http://h18000.www1.hp.com/products/quickspecs/12447_na/12447_na.HTML")_ that they even indicate that 
**"Above 3-GB, all memory may not be available due to system resource requirements."** Which really says **No**, it is not likely to do anything for you.

Otherwise, if the Compaq nx6325 is not your model:
Have you contacted HP about updating the BIOS? That is my suggestion. As we have been saying, the BIOS will register the physical amount of RAM that is in the machine, not the amount accessible to the 64bit OS. When HP said that the RAM is fine, that is only saying that it is physically OK, not whether a 64bit OS can use it. So, ask HP. Simply state that you have installed a 64bit OS and that only 2.8GB of RAM is seen. Then ask whether it is worthwhile updating the BIOS - whether they think it will solve the problem? (Also indicate the version of the BIOS you are using and the model of your machine). 

So, if the BIOS update will not help, then we just need to be satisfied with 2.8GB.:(

---

### Post by thegutterpoet on 2009-10-24
I avoided trying to update the BIOS, even though it had been suggested in this thread, because I am aware that ******* the BIOS can completely ruin the laptop, with no chance of repair, just dead...Until I have made the relevant enquiries, which some of you folks seem to have started doing, kindly, on my behalf, I won't update the BIOS. I should speak with the HP technical goons, and see what they say...I have tried them before, and all they told me was that my nx6235 can take up to 4gb RAM. As I tried to delve deeper into the WHY ARENT MY OPErATING SYSTEMS RECOGNiZING MORE RAM>..they told me to ask Linux folks...as it is common for windows XP 32 bit to only use 2.8gb of 4gb. But with linux, they had no idea...

I am very grateful for the help given here, and will report back once I have asked HP about the bios update.
Cheers...D

---

### Post by thegutterpoet on 2009-10-25
dmesg | grep BIOS
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7fd0000 (usable)
[    0.000000]  BIOS-e820: 00000000b7fd0000 - 00000000b7fe5600 (reserved)
[    0.000000]  BIOS-e820: 00000000b7fe5600 - 00000000b7ff8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7ff8000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffbc0000 - 00000000ffcc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.567046] HPET not enabled in BIOS. You might try hpet=force boot option
[    2.892116] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found

---

### Post by thegutterpoet on 2009-10-25
> **cmckdub said:**
> I can understand your reluctance to update the BIOS as it is a risky operation. To flash the BIOS you will need to know your BIOS version, and look on the HP site. 
I had a quick look for your BIOS information using the information you provided at the start of this thread and couldn't find anything.
Is your model really a Compaq nx6325? If it is, then _[this site]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=3315736&prodSeriesId=1849082&swLang=8&taskId=135&swEnvOID=1093")_ seems to be the place to get the BIOS update. The latest seems to be F.07. What version is your BIOS? There is also specific information about updating your BIOS in Ubuntu _[here]("https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6325#BIOS%20update")_ - which would makes me feel more comfortable about the BIOS update on yours, **if** this is your model. However, check that all the information is correct, as it doesn't match what you originally posted, and if it is incorrect you may turn the laptop into landfill.
I particularly note that on the _[specification for such a laptop]("http://h18000.www1.hp.com/products/quickspecs/12447_na/12447_na.HTML")_ that they even indicate that 
**"Above 3-GB, all memory may not be available due to system resource requirements."** Which really says **No**, it is not likely to do anything for you.

Otherwise, if the Compaq nx6325 is not your model:
Have you contacted HP about updating the BIOS? That is my suggestion. As we have been saying, the BIOS will register the physical amount of RAM that is in the machine, not the amount accessible to the 64bit OS. When HP said that the RAM is fine, that is only saying that it is physically OK, not whether a 64bit OS can use it. So, ask HP. Simply state that you have installed a 64bit OS and that only 2.8GB of RAM is seen. Then ask whether it is worthwhile updating the BIOS - whether they think it will solve the problem? (Also indicate the version of the BIOS you are using and the model of your machine). 

So, if the BIOS update will not help, then we just need to be satisfied with 2.8GB.:(

The NX6235 is definitely MY MODEL...And I presently have BIOS f.07 installed...should I update it, and how easy and secure a process will it be?

What are the risks?

My chipset is      ATI Radeon Xpress        1150 Chipset...

---

### Post by Portable_Jim on 2009-10-25
**Dissecting the memory map:**
I will post the figures underneath the quoted line. The numbers together say the same thing, I just have converted the units. For example, after the first quote, it is usable memory, going to 654336 bytes (which equals 639 Kilobytes (or Kbytes for short)).
> **thegutterpoet said:**
> dmesg | grep BIOS
[ 0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)

0 - 654336 bytes
0 - 639 Kbytes

> **thegutterpoet said:**
> [ 0.000000] BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)

654336 - 1048576 bytes = 394240 bytes
639 - 1024 Kbytes = 385 Kbytes

> **thegutterpoet said:**
> [ 0.000000] BIOS-e820: 0000000000100000 - 00000000b7fd0000 (usable)

1048576 - 3086811136 bytes = 3085762560 bytes
1024 - 3014464 Kbytes = 3013440 Kbytes
1 - 2943.8 Mbytes = 2943.8 Mbytes = 2.87 GB

> **thegutterpoet said:**
> [ 0.000000] BIOS-e820: 00000000b7fd0000 - 00000000b7fe5600 (reserved)
[ 0.000000] BIOS-e820: 00000000b7fe5600 - 00000000b7ff8000 (ACPI NVS)
[ 0.000000] BIOS-e820: 00000000b7ff8000 - 00000000c0000000 (reserved)
[ 0.000000] BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)
[ 0.000000] BIOS-e820: 00000000ffbc0000 - 00000000ffcc0000 (reserved)
[ 0.000000] BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)

3086811136 - 4294967296 bytes = 1208156160 bytes
3014464 - 4194304 Kbytes = 1179840 Kbytes
2943.8 - 4096 Mbytes = 1152.2 Mbytes
2.87 - 4 GB

**Summary:**
From this information, it says that your bios sees all the RAM, and passes that information onto Ubuntu, however not all of it is usable. This would support HP's comment
> Above 3-GB, all memory may not be available due to system resource requirementsThe reason for this seems to be that your bios does not support address remapping. The evidence for this is your comment
 > There is no option for remapping memory in my current HP biosand also a comment from [this]("http://74.125.155.132/search?q=cache:fjNSpr1ioq4J:www.******************/debian-laptop/338105-i-want-all-my-4gb-3.html+338105-i-want-all-my-4gb-3.html&cd=1&hl=en&ct=clnk&gl=au") thread, as follows
> So the last address reported by your bios is 4GB (0000000100000000)
at the end of a reserved area.  The last address of usable memory is
00000000bf680000 which is 3211264000 bytes, so your system does not
remap memory and hence anything covered by PCI devices is simply lost
and can not be used at all.  The hardware is either simply not capable of
remapping memory (this is true for many intel chipsets) or the BIOS didn't
make the chipset do remapping (sometimes there is a bios option for it).
...

So unless your bios has an option for memory remapping, there is no way
to make the rest of memory usable, and you will only get about 3.2GB
out of your 4GB.  Of course if the video steals some of that 3.2GB,
you get whatever is left.So I doubt there is anything you can do to increase the memory.
**About the BIOS upgrade:**
> ...I presently have BIOS f.07 installed...You have the most up to date bios then
> What are the risks?You have already mentioned
> I am aware that ******* the BIOS can completely ruin the laptop, with no chance of repair, just deadwhich is the risk. As you seem to have the latest bios version, there would be no advantages that I can see.

Therefore I advise against doing the upgrade, as there is the risk of damaging the computer, no real advantage, since you are using the latest bios, ad no guarantee that any bios upgrade will do anything.

---

