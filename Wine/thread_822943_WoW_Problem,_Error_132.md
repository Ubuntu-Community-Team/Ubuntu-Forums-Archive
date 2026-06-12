---
title: "WoW Problem, Error 132"
date: 2008-06-08
forum: Wine
---

### Post by SuburbanPK on 2008-06-08
Hi everyone,

I'm new to Linux, only starting to use it Jun 5, 2008. I knew that you could play WoW on Linux using different applications (I'm using WINE). I followed the walkthoughs word for word ([http://ubuntuforums.org/showthread.php?t=579378&highlight=WoW+installation](http://ubuntuforums.org/showthread.php?t=579378&highlight=WoW+installation)). And after much forum searching, i got WoW to load (for awhile i had this problem with the Cinematic playing, then the whole program crashed), but now, when i log onto a character i get Error #132.](*,) 

This is the error message:
Error #132 (ox85100084) Fatal Exception
Program:     C:\Program Files\World of Warcraft\Wow.exe
Exception:   0x80000101 (unknown exception) at 0073:b7f7b410

I think it's a graphics problem, seeing that i had a somewhat similar problem when I played WoW on Vista (shocker). I know how to fix windows (because you have to do it so often), but i can't figure out Linux.

I'm running Ubuntu 8.04, with Intel 945GM Graphics and Intel Core Duo CPU T2350 @ 1.86GHz. I know there isn't a problem with memory, and WoW ran decent on the Windows side so I'm really confused. Please, need help.

PS Sorry about the really long post.

---

### Post by xravexheavenx on 2008-06-08
I've had this problem and it seemed to be a graphics issue.  I simply installed nVidia's graphics driver on my Kubuntu box and it went away.  Not sure if the Intel drive for your graphics card will help though.

---

### Post by SuburbanPK on 2008-06-09
Ill try reinstalling the graphics driver, but.. Im not quite sure how to do it on Ubuntu (being the newb i am). Is it as simple as going to the site and downloading the driver from there? :confused:

---

### Post by RaleTheBlade on 2008-06-09
If you go to System > Administration > Hardware Drivers you should get a list of available drivers. If you dont have one available, open your Terminal and type

sudo apt-get install nvidia-glx

And that should download the driver for your particular nVidia based card. Hope this helps! I was a new user about a week ago, but Ive learned quite a bit just by tinkering with everything. Just give it time and youll figure alot of stuff out.

---

### Post by SuburbanPK on 2008-06-09
Well, I updated everything and everything, and it says my Intel 945GM graphics card is up to date. I have been forum searching and I come to three conclusions. Its my graphics drivers, its Ubuntu 8.04, or it's actually a memory problem (which doesn't make sense). Anyone who has solved this problem, i would really like to know the answer.

---

### Post by SuburbanPK on 2008-06-09
Deeply sorry about the double post, but I decided for those who would like to see exactly whats doing on here it is. For those who don't ignore this post. Oh, updates didn't do anything.
==============================================================================
World of WarCraft (build 8278)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     Jun  9, 2008  8:54:34.484 PM
User:     ian
Computer: ian-laptop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\Wow.exe
Exception:	0x80000101 (unknown exception) at 0073:B7FC2410




WoWBuild: 8278
Realm: Azgalor [206.16.23.60:3724]
Local Zone: Irontree Woods, Felwood
Local Player: Unknown, 00000000020AF0F5, (5935.47,-1217.75,383.202)
------------------------------------------------------------------------------

Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x3
Number of Processors:   2
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     3596

Percent memory used:    61
Total physical memory:  1050681344
Free Memory:            406159360
Page file:              2218627072
Total virtual memory:   2147352575

This is the error and the Hardware info. if anyone wants the whole thing (threads, memory dump, etc) just let me know

---

### Post by SuburbanPK on 2008-06-10
I wonder if there is any rule against triple posting... 
Anyway, I'm sick of not being able to play WoW. I'm gonna do back on to my Vista partition (:frown:) but at least WoW works some what on that side. I think its just that 8.04 just has a lot a compatibility issues (is every OS having that problem?) so I'm gonna wait for 8.10 and see if that solves anything... 

I'm still going to be checking this post for any info, I want to switch to Linux so badly, but this little big problem wont let me.

---

### Post by thisismalhotra on 2008-06-11
These links have all the details you will need

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

---

### Post by SuburbanPK on 2008-06-11
Well, i broke down and reinstalled wow, and that fixed my Error 132 problem (probably a corrupt file), but now i have a different problem. When i log into WoW, I CAN SEE THROUGH THE GROUND! Yeah, There is no ground, just trees, ruins, and the occasional mountain that isn't effected by this weird problem. I can see NPCs fine and im getting FPS that im used to (13-25) which sucks, but i think its just my sucky Intel card. If anyone can direct me to a thread that addresses this problem it would be awesome. Im so close to Switching entirely to Ubuntu, but this terrain problem is not cool.

---

### Post by thisismalhotra on 2008-06-12
[http://forums.wow-europe.com/thread.html;jsessionid=2FF94F1530D4180B5A6D8ECF57648B01.app03_02?topicId=3778919002&sid=1](http://forums.wow-europe.com/thread.html;jsessionid=2FF94F1530D4180B5A6D8ECF57648B01.app03_02?topicId=3778919002&sid=1)

[http://forums.wow-europe.com/thread.html?topicId=285139220&sid=1](http://forums.wow-europe.com/thread.html?topicId=285139220&sid=1)

---

### Post by sprockets2000 on 2008-10-30
When I had this issue, I just simple made my own config.wtf and added the opengl part 

SET gxApi "opengl"

before not having a config.wtf from a fresh install it would automatically try and start as a directx application.

---

### Post by Eviljim on 2008-10-31
> **RaleTheBlade said:**
> If you go to System > Administration > Hardware Drivers you should get a list of available drivers. If you dont have one available, open your Terminal and type

sudo apt-get install nvidia-glx

And that should download the driver for your particular nVidia based card. Hope this helps! I was a new user about a week ago, but Ive learned quite a bit just by tinkering with everything. Just give it time and youll figure alot of stuff out.


He is running an Intel card, so the nvidia ones will not help.

Im afraid SuburbanPK that the Intel linux drivers are not as well written/supported/etc than their Windows equivilents.

Whilst some people manage to get their Intel cards working, many do not. I fear that you may fall into the "Do not" category. 

However, the try this Intel driver 

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2301&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go!]("http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2301&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go!")

and FYI the Intel 945GM is the chipset of your motherboard with the Intel GMA 950 being your graphics card.

---

