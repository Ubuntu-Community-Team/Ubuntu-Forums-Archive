---
title: "have questions about 64-bit vs 32-bit"
date: 2009-03-06
forum: x86 64-bit Users
---

### Post by axel_2078 on 2009-03-06
I'm considering ordering a new laptop from System76 soon, which has a 64-bit processor in it. Now, I'm new to this 64-bit stuff. I currently have 4 older computers and none of them have 64-bit processors, so I've never run a 64-bit OS. I have some questions that I'm hoping someone can answer.

1. Can I run 32-bit apps under a 64-bit OS natively, or will it require compiling code to do so?

2. Is Mozilla Thunderbird available in 64-bit? I searched around and I think I found some 64-bit versions for Windows, but not Linux. Maybe I was just looking in the wrong place. If not, can the 32-bit version be used?

3. Are there separate Ubuntu repos for 32-bit and 64-bit?

Thanks in advance.

---

### Post by sanderj on 2009-03-07
> **axel_2078 said:**
> 
1. Can I run 32-bit apps under a 64-bit OS natively, or will it require compiling code to do so?

2. Is Mozilla Thunderbird available in 64-bit? I searched around and I think I found some 64-bit versions for Windows, but not Linux. Maybe I was just looking in the wrong place. If not, can the 32-bit version be used?

3. Are there separate Ubuntu repos for 32-bit and 64-bit?


Yes (except apps very close to the kernel, like video drivers), yes and yes.

HTH

---

### Post by jespdj on 2009-03-07
32-bit binaries run on a 64-bit OS, no recompiling required. You might however need to install 32-bit libraries, because a 32-bit program can't use 64-bit libraries.

Mozilla Thunderbird is in the Ubuntu repository, which means that you can install it the regular way with Synaptic or apt-get. And as almost all software, it's available as a 64-bit native program.

Note that you will rarely have to run 32-bit programs on your 64-bit system. The only two 32-bit programs that I have are Skype and Google Earth - both proprietary programs for which the developers are too lazy to compile a 64-bit version. All the software in the repository for 64-bit Ubuntu, is 64-bit native.

---

### Post by BigSilly on 2009-03-07
Actually I'm in the same position, and not sure what to do. I have an AMD Athlon 64 X2 5200 with 3Gb RAM, and I've been told that a 64 bit OS is only worthwhile with 4Gb RAM and more. Is this true? Would you use a 64 bit Ubuntu with the same hardware as me, or would you stick with 32 bit for now. Thanks all.

---

### Post by sanderj on 2009-03-07
> **BigSilly said:**
> Actually I'm in the same position, and not sure what to do. I have an AMD Athlon 64 X2 5200 with 3Gb RAM, and I've been told that a 64 bit OS is only worthwhile with 4Gb RAM and more. Is this true? 

Yes. Main rational reason is 3.2+ GB of RAM.

> **BigSilly said:**
> 
Would you use a 64 bit Ubuntu with the same hardware as me, or would you stick with 32 bit for now. Thanks all.
I would try out Ubuntu 64-bit as ... it is über-cool, just like Linux itself! ;-)
So, boot the 64-bit Ubuntu live-CD and see if it all works. I've been using 64-bit Ubuntu on my Athlon 64 since 7.04, with no single problem at all.

---

### Post by BigSilly on 2009-03-07
It's a fairly new PC (about two weeks old) so 64 bit is all new to me. I did try out the 64 bit live CD though, and it seemed fine. What made me actually install the 32 bit variant was the claim that it wasn't worth it with "only" 3Gb RAM, and the further claims that certain apps like Flash etc can be a pain on 64 bit. I don't mind configuring and setting up apps to work, but if 3Gb wasn't enough I didn't see the point even trying.

Thanks for your reply though! :)

---

### Post by kelvin spratt on 2009-03-07
You don't need masses of ram to run 64bt this has been taken out of context 64bt uses approx 10% more ram so if Ubuntu 32bt uses 500mb then 64bt will use approx 550mb and you will gain speed with cpu intensive programs like the gimp, or video processing.
You really only need excessive amounts of ram if you run programs like virtual-box as large amounts of ram can then be allocated to run a guest OS at near native speed.

---

### Post by axel_2078 on 2009-03-07
Thanks for all the information guys. I really appreciate it. You've relieved a good deal of my worries. Sounds like I'll be rockin' with 64-bit Ubuntu!

---

### Post by Chibone on 2009-03-07
I would actually run 64 bit even if I didn't have that much RAM as my AMD hardware goes into crippled "legacy mode" (no extra registers) if it is not run at full capability.

---

### Post by 3Miro on 2009-03-07
> **Chibone said:**
> I would actually run 64 bit even if I didn't have that much RAM as my AMD hardware goes into crippled "legacy mode" (no extra registers) if it is not run at full capability.

That explains why my desktop was slower under 32-bit than it is under 64-bit (just a little bit but still slower).

The reasons for updating to 64 bit are: use a lot of ram and/or run apps that benefit from 64-bit (video editing, numerical simulations ... )

I got flash and skype and all other apps running on my desktop with very little trouble (the biggest one was flash, but is it fixed now).

My 64-bit system76 laptop came with flash preinstalled, so I only had to turn it on, input the password for my wireless network at home and load a youtube video - could not be any easier than that. Skype had a problem with pulseaudio, but it is easily fixed and has nothing to do with 64-bit architecture.

---

### Post by SuperSonic4 on 2009-03-07
> **BigSilly said:**
> It's a fairly new PC (about two weeks old) so 64 bit is all new to me. I did try out the 64 bit live CD though, and it seemed fine. What made me actually install the 32 bit variant was the claim that it wasn't worth it with "only" 3Gb RAM, and the further claims that certain apps like Flash etc can be a pain on 64 bit. I don't mind configuring and setting up apps to work, but if 3Gb wasn't enough I didn't see the point even trying.

Thanks for your reply though! :)

That's changed now, thanks to native 64 bit plugins for flash and java at least

---

### Post by BigSilly on 2009-03-07
So even with just 3Gb RAM, do you think it's worth using 64 bit then with my spec? I will definitely give it a go if you think so. Probably Jaunty 64 bit will be my first stab at it. Let me know...

---

### Post by 3Miro on 2009-03-07
> **BigSilly said:**
> So even with just 3Gb RAM, do you think it's worth using 64 bit then with my spec? I will definitely give it a go if you think so. Probably Jaunty 64 bit will be my first stab at it. Let me know...

Eventually everything will move to 64-bit. Unless you have a good reason to stick to 32 (i.e. some app that you need simply would not run) then go with 64-bit. The little issues there are, are being resolved one by one as we read/write this.

---

### Post by oldos2er on 2009-03-07
"I've been told that a 64 bit OS is only worthwhile with 4Gb RAM and more. Is this true?"

 Define "worthwhile." I ran 64-bit for over a year on 2GB RAM; I simply liked the idea that I was taking full advantage of my processors' capabilities. That may not be a practical reason, but it is a personal one.

---

### Post by tbastian on 2009-03-07
I've been running 64 bit versions of linux since I got my laptop about 2 years ago. The ONLY piece of 32bit software I've ever had to use was mozilla firefox back before there was a good version of flash for 64bit systems.

I've found that 99.9% of the time, if its free-ware, either the developer or someone running a 64bit machine has taken the time to compile a version for the 64bit architecture. That, or I just happen to not need 32bit only programs :D

Also, I had only 1GB of RAM until very recently and didn't notice any slowdowns. Usually when I typed in 'free -m' I wasn't using all my memory unless I was running a lot of programs.

I'd have to say: go for it!

---

### Post by BigSilly on 2009-03-07
> **oldos2er said:**
> Define "worthwhile."

Well, insofar as there's no real practical benefit to moving to 64 bit other than a psychological one. That's kind of the drift of opinion I'm reading around the net. Not my own opinion.

I think I'm really going to have to dual boot with the 64 bit version for a while to see if there is a difference. If 3Gb is enough RAM, and the general performance of my PC is better, then I'll move over to 64 bit with Jaunty. If 3Gb is struggling, then I suppose I'll have to stick with 32 bit. 

It's a knotty one for sure. There's such a diverse range of opinion on the matter that it's impossible to take any as gospel. I'll just have to take the plunge and see for myself!

Thanks all for your help. Sorry for hijacking the thread, but hopefully the OP will have got something from all this too!

---

### Post by axel_2078 on 2009-03-07
> **BigSilly said:**
> 

Thanks all for your help. Sorry for hijacking the thread, but hopefully the OP will have got something from all this too!

Actually, I did learn quite a bit from all the conversations. Thanks a lot for the input guys.

---

### Post by SuperSonic4 on 2009-03-07
> **BigSilly said:**
> So even with just 3Gb RAM, do you think it's worth using 64 bit then with my spec? I will definitely give it a go if you think so. Probably Jaunty 64 bit will be my first stab at it. Let me know...

to be honest I only went to 64 bit because I had 4gb of ram but I think the 64bit will be better for cpu hogging apps. Day to day browsing once you have flash and java done (it's still harder to install them) is much the same, there's no reason to upgrade now, could just use Jaunty 64 bit

---

### Post by movieman on 2009-03-09
> **BigSilly said:**
> Well, insofar as there's no real practical benefit to moving to 64 bit other than a psychological one. That's kind of the drift of opinion I'm reading around the net. Not my own opinion.

Of course you need to remember that most people with an opinion on the subject don't know what they're talking about.

Aside from being able to use >3GB for a single application, 64-bit gives you twice as many registers, which can be a huge benefit for CPU-intensive code; lack of registers has been a perpetual problem with the x86 architecture, requiring lots of extra memory accesses as you save and restore temporary values in RAM. When the Athlon64 first came out I remember some companies claiming they got a 20% performance boost in CPU-intensive C/C++ code just by recompiling.

And that's before you include other benefits that may or may not currently be implemented, such as allowing every single shared library/DLL to be based at a unique memory address so there's no need to relocate them when they're loaded, and allowing you to mmap() multi-gigabyte files into your address space.

The only downside I can think of other than a small increase in memory usage is that prior to Nehalem Intel had extra CPU optimisations for 32-bit code which weren't supported for 64-bit; but in most cases the extra registers will provide more of a benefit than the cost of the missing optimisations.

---

