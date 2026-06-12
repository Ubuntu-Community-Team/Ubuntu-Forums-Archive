---
title: "got ubuntu ultimate x32 working perfectly...but"
date: 2008-07-01
forum: x86 64-bit Users
---

### Post by binskipy2u on 2008-07-01
I am missing bout 400mb of ram, ( i have 4 gigs) its a 64bit machine.. its working beautifully.. i'm dual booting with vista(not that i use it much), just got the machine today..
triple core amd 8450 @ 2.1ghz
500gig SATA2 hd
4 gigs pc5300 ram
22" lcd
256mb ATI HD 3200

the ram is "not" a HUGE deal.. but if i were to d/l and burn the x64 edition and boot it up, goto terminal type "top" and if it sees 
ALL the ram, its most likely to see ALL of it when its "installed"
and would i notice a REAL difference from x32 to x64 of UE1.8?
would it be worth "fixing" what isnt "that" broken?
any info would be helpful..
thanks

---

### Post by pixel :-) on 2008-07-01
//I am missing bout 400mb of ram, ( i have 4 gigs)
You mean that the OS can't see the final 400M.In 32bit the limit in memory adressing is around 4G,so it's possible,are you sure you compare Gigas with Gigas and not Gigas with Gibi.In the repositories there is a 32bit kernel that can go well above 4G,install this one,i don't remember it's name,it should be self evident,in synaptic.64 bits limit in adressing memory is in Terabytes,so the 64bit ubuntu should see all of it.

//its working beautifully.. i'm dual booting with vista
if it's not about games,or stuff demanding in resources(like 3D),you can try a virtual machine, like virtualbox,to avoid reboots.You have plenty of hard disk space for experimentation.

//500gig SATA2 hd
an advice,make a dedicated partition for your home partition.

//and would i notice a REAL difference from x32 to x64 of UE1.8?
//would it be worth "fixing" what isnt "that" broken?
//any info would be helpful..
//thanks
There are still some problems,you will face different bugs,and compatibility problems, on the other hand you will have improvements in efficiency, in certain tasks,not all. I would recomend to have both 32 and 64 in duall boot, and your home on a dedicated partition that they share,and keep both. If you find that it doesn't worth it as you primary OS,leave 64 in, in sucesive upgrades,it may become acceptable to you.Sooner or later you will migrate anyway.

---

### Post by soxs on 2008-07-01
> **pixel :-) said:**
> //I am missing bout 400mb of ram, ( i have 4 gigs)
You mean that the OS can't see the final 400M.In 32bit the limit in memory adressing is around 4G,so it's possible,are you sure you compare Gigas with Gigas and not Gigas with Gibi.In the repositories there is a 32bit kernel that can go well above 4G,install this one,i don't remember it's name,it should be self evident,in synaptic.64 bits limit in adressing memory is in Terabytes,so the 64bit ubuntu should see all of it.

The lack of the last 400mb will not vanish with 64 bit (there are allready multiple threads about). It's either bios relate (enable memory remapping, if your bios has sutch an option) and kernel requires some MiB s.

And it's GiB (1024) and GB (1000), whereas for RAM 1024 is "normally" used... 

> **pixel :-) said:**
> 
an advice,make a dedicated partition for your home partition.

Allright, this is really usefull

> **pixel :-) said:**
> 
There are still some problems,you will face different bugs,and compatibility problems, on the other hand you will have improvements in efficiency, in certain tasks,not all. I would recomend to have both 32 and 64 in duall boot, and your home on a dedicated partition that they share,and keep both. If you find that it doesn't worth it as you primary OS,leave 64 in, in sucesive upgrades,it may become acceptable to you.Sooner or later you will migrate anyway.
Wrong, 64bit is ready for usage.. anything it lack,s have a look at the sticky section. Using AMD64 version since almost 2 years now.

---

### Post by pixel :-) on 2008-07-01
**Per above try first,"enable memory remapping" in the bios**

//1024 is "normally"
i have the fealling that this issue is still a mess,depending on programs.To prevent multiple post i was preempting a potential source of the discrepancy.

//Wrong, 64bit is ready for usage.. anything it lack,s have a look at the //sticky section. Using AMD64 version since almost 2 years now.

"ready for usage"!="the same"(vista too is ready for usage :) )

They are proprietary aplications that are 32 bit only, some of them don't like ia32-libs.Even if the source it's open,theres no garanties that is portable, you need to reright parts, for some this hasn't happen yet.Even if it's portable,theres no garantie that the quality will be the samen different bugs.For w64codecs are not equivalent to w32codecs ,they are almost empty, and some times you run on a movie that need w32codecs.So yes they are problems, it boils down too,does your job get done.I'm not scare mongaring,i'm advizezing to install both,depending what he itends to do,he might get very frustrated.

---

### Post by binskipy2u on 2008-07-02
ive read where the win codecs are NOT as plentiful in 64bit ubuntu.. here's my question. what bout the open gstreamer plugins? 
wont they work just as well till the win64codecs catch up?

just wondering..
thanks

---

### Post by soxs on 2008-07-03
> **binskipy2u said:**
> ive read where the win codecs are NOT as plentiful in 64bit ubuntu.. here's my question. what bout the open gstreamer plugins? 
wont they work just as well till the win64codecs catch up?

just wondering..
thanks

I don't know much about, but I did not come about any format I weren't able to play on my 64bit machine wit w64codecs... so, I will stick with what I am on..

---

### Post by cariboo on 2008-07-03
If you install the ubuntu-restricted-extras you get all the codecs you need, except for libdvdcss2 which you can get from Medibuntu. Restricted extras take the place of the w64codecs. 

I've been using a 64bit distribution since 6.04 and had never had a showstopper because there wasn't a program available in 64bit. Most gui programs are frontends for what is already available in most distributions. If you really need something there is alway a way to do it, usually three or four ways. Remember Google is your friend there is more information and howto's available than you know what to do with.

If you are unsure about a command there is always

```
man <command>
```

If you are really bored and have nothing to do you can always go thru /usr/bin and read the manpages for all 1500+ applications found there.

Jim

---

