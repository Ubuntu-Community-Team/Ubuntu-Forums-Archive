---
title: "Swap size advice"
date: 2008-07-29
forum: x86 64-bit Users
---

### Post by mad_max0204 on 2008-07-29
Hey guys

I have 8gigs of ram and a C2Q processor. I think I made a mistake by making swap partition too large. Its sitting at 4gb at the moment. I made it twice as my previous amount of ram (2gb) (used to do it like that on older comps). Would I get any performance boost by setting my swap to 1gb or less since I have enough ram ?? Or maybe more than 4gb ?? How about making swap on other hard drives ?? How is it done in linux and is that a better solution ??

Any advice/link/howto would be appreciated.

Cheers

---

### Post by John.Michael.Kane on 2008-07-29
> **mad_max0204 said:**
> Hey guys

I have 8gigs of ram and a C2Q processor. I think I made a mistake by making swap partition too large. Its sitting at 4gb at the moment. I made it twice as my previous amount of ram (2gb) (used to do it like that on older comps). Would I get any performance boost by setting my swap to 1gb or less since I have enough ram ?? Or maybe more than 4gb ?? How about making swap on other hard drives ?? How is it done in linux and is that a better solution ??

Any advice/link/howto would be appreciated.

Cheers

Some users feel machines with 2 gigabytes or more, swap space can be set to one gigabyte, and those machines with 4 or more gigabytes can set a swap size of zero.

Without knowing exactly what the machine primary use will be, it is hard to give a definitive answer, as to how much swap if any you will need.

What you can do is a trial run using  your current configuration, and open all the programs that you make use of, and see if swap is used, as well as how much ram is used.

Or

Open your most ram intensive program, and see what the outcome is.

While the above test is far from perfect it should give you a guide of what you use, and need for swap.

Personally, if I had a machine with eight or more gigabytes I would try first running with no swap or a minimal amount around 256-500mb on the high end 1GB.

As for placing swap on a second hard drive you should be able to using gparted, and you may have to edit fstab.

or 

During a reinstall. 

You would simply allocate space on the second hard drive, and label it as a swap partition. 

IMHO swap on a separate drive will run only slightly faster. It is an improvement, however. I would not expect to see a large performance increase.

---

### Post by tamoneya on 2008-07-29
running swapless just because you have a lot of ram isnt the best idea.  While swaps main purpose is to give you more "ram" incase you run out it also serves as a place to dump the ram incase of some system error.  The computer will try to dump as much of the RAM as it can to the swap partition if there is some failure.  This makes debugging and system recovery easier.  There for you should have at least 8 GB of ram in case you need to dump.  While you will rarely use it it could be very helpful if you run into problems.  Anyways most people who have 8 GB of ram also have multiple hundreds of GB of harddrive space so percent wise it should be a fairly small amount of space.

---

### Post by Thelasko on 2008-07-29
Adding on to what tamoneya said, I think the swap is used for standby or hibernate (I forget which one).  It places the contents of your RAM into the swap and then moves it back when you power up.  In general use, you should only use the swap when you use all of your RAM.  I don't see how making your swap smaller can make your computer faster, it would just leave more space on your hard drive for other stuff.  Hard disk space is cheap right now (~$0.16/GB for a desktop), I would leave it as it is.

---

### Post by mad_max0204 on 2008-07-29
I got some interesting answers from you guys. And fast ones I must add.

Regarding the hibernate function, I dont use it at all and never will.
Basically hard drive space is no problem since I have 2 TBs now but I asked this question because hdds are supposed to be bottle neck of the who system. I know that swap usage fell to none or zero in my case since theres enough ram for everything so I was asking if making swap smaller and by that making computer work less with hard drives which are the slowest thing on my computer would make any speed increase.

I think I got my answers but any other oppinions on this subject are welcome.

Thanks guys

---

### Post by tamoneya on 2008-07-29
I think having smaller swap makes the computer negligibly quicker on start up since it takes less time to initialize the swap space.  I doubt it would be a noticeable difference though considering how most hardware currently is multicore so it will just happen on the side.

---

### Post by stchman on 2008-07-29
How do you configure swap size?  I have a PC with 6GB RAM and want to set the swap size a little smaller.

---

### Post by Jouke74 on 2008-07-29
Note that swap is only used when the computer is 
(1) out of normal RAM,
(2) when the memory pages of programs still running are not being actively used and memory can be used for something better like caching of data
(3) when you use Hibernate all memory will be written to the swap partition. In this case you need at least > 1x the RAM of the computer I suggest ~12 GB of swap.

Therefore, if you have 8 GB of RAM, with daily desktop use and no hibernation you will never touch the swap disk (almost e.g. memory leaks in Compiz or Conky are possible). If you are using very memory intensive programs that eat up more than 8 GB in total (e.g. multiple virtual machines with 2 to 4 GB assigned) then "swapping" occurs. Believe me that everything slows down drastically when you actively swap running programs.

How fast the computer will start swapping/paging is dependent on the swappiness value. With 0 it will try to keep as much in memory as possible, with 100 it will try to swap as much as possible. 0 is of course the best value for you, unless you are using 8 GB and not just showing off with your "impressive machine". :lolflag:

---

### Post by Sef on 2008-07-29
512 mb ram and below, swap should be set for 1 1/2 - 2 times ram.  Above that it should be set at 1 GB.  If you need more than 1 GB swap, then you should be more ram.   I have 2 GB ram, and have swap set at 1 GB.  I rarely use any of it.

---

### Post by Jokimoto on 2008-07-29
Hmm, then I received bad advice when I first installed. I've only got 2G of RAM and was advised to make the swap partition double that, so it's currently at 4G. 
I only have 200G on my drive, and it's dual-booting. I wanted to thoroughly check out Linux before abandoning Windows altogether (except for gaming and Tracktion) so I only set aside another 15G for Linux. I guess when I go to re-install/partition I'll drop the swap from 4 to 2, or perhaps 1.
For what it's worth, all I can say is Ubuntu runs extremely fast, boots fast, and I've never had a problem w/memory other than Skype video using 100% CPU, which I understand is common to many AMD64 users anyway.

---

### Post by Sef on 2008-07-29
> Hmm, then I received bad advice when I first installed. I've only got 2G of RAM and was advised to make the swap partition double that, so it's currently at 4G.

The one and a half and doubling is old advice that no longer applies with the current ram specs of today.

---

### Post by mad_max0204 on 2008-07-30
Heh yeah I would like to have an "impressive machine" to brag about. But its not the case. I think that my peak ram consumption was 7 maybe 7.5 GBs. As I put it to my mind, and as much as I understood, I think that I will resize my swap to 1gb just to check out things. After that I'll experiment with less than 1gb or even none. I repeat, I dont use hibernate so I think i dont need 8gb swap.

Thanks for answers guys

This forum really rocks

---

