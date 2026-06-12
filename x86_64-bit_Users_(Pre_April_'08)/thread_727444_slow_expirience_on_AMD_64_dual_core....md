---
title: "slow expirience on AMD 64 dual core..."
date: 2008-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mia_tech on 2008-03-17
after installing ubuntu 64 on my new AMD 64 dual core, I notice slow performance, compare, to my intel pentium 4 2.0 G...I was exited at first, but after running several apps at the same time, including the memory demanding vmware server, running 3 vm machines, I notice that computer start it to drag, then I fired up system monitor and TOP to see what the system was doing and the CPUs were in between 20 at 30 % which is not bad, and the memory was at 550 M, from 1G, although apparently the system wasn't using many resources it was dragging down, and it was b/c it was allocating lots of those programs in swap memory ( at 700M)...which makes apps respond a lot slower, this has not been my past experience with the i386 version, on intel...it used to allocate all running programs on physical memory until it run out of it, then it use swap, not in 64 bit at least in my case.. now this brings me to the next question.. is there a way to change the way linux handles memory usage?

thanks

---

### Post by damvcoool on 2008-03-18
make sure that VMware is not set to send Memory to Swap. this is a feature of VMware.

---

### Post by Jouke74 on 2008-03-18
Also you can set the swappiness value lower, if you have enough of memory.

---

### Post by Mia_tech on 2008-03-18
> **damvcoool said:**
> make sure that VMware is not set to send Memory to Swap. this is a feature of VMware.

and how would you do that?

thanks

---

### Post by Jouke74 on 2008-03-18
I don't know about vmware. But here is the trick for swappiness, most people switch it to 10 btw: 

Since 2.6, there has been a way to tune how much Linux favors swapping out to disk compared to shrinking the caches when memory gets full.

When an application needs memory and all the RAM is fully occupied, the kernel has two ways to free some memory at its disposal: it can either reduce the disk cache in the RAM by eliminating the oldest data or it may swap some less used memory (anonymous pages) of processess out to the swap partition on disk. It is not easy to predict which method would be more efficient. The kernel makes a choice by roughly guessing the effectiveness of the two methods at a given instant, based on the recent history of activity.

Before the 2.6 kernels, the user had no possible means to influence the calculations and there could happen situations where the kernel often made the wrong choice, leading to thrashing and slow performance. The addition of swappiness in 2.6 changes this. Thanks, ghoti!

Swappiness takes a value between 0 and 100 to change the balance between swapping processess anonymous pages and freeing cache. At 100, the kernel will always prefer to find inactive pages and swap them out; in other cases, whether a swapout occurs depends on how much application memory is in use and how poorly the cache is doing at finding and releasing inactive items.

The default swappiness is 60. A value of 0 gives something close to the old behavior where applications that wanted memory could shrink the cache to a tiny fraction of RAM. For laptops which would prefer to let their disk spin down, a value of 20 or less is recommended.

As a sysctl, the swappiness can be set at runtime with either of the following commands:

sysctl -w vm.swappiness=30 
echo 30 >/proc/sys/vm/swappiness

The default when Gentoo boots can also be set in /etc/sysctl.conf:
File: /etc/sysctl.conf

# Control how much the kernel should favor swapping out applications (0-100)
vm.swappiness = 30

---

### Post by fjgaude on 2008-03-18
> **Mia_tech said:**
> and how would you do that?

thanks

In vmware server this feature is selectable in the menu Host/Settings/Memory. Use the Fit all virtual memory check. That should stop all swapping. There are other options less severe. <smile>

---

### Post by Mia_tech on 2008-03-18
> **fjgaude said:**
> In vmware server this feature is selectable in the menu Host/Settings/Memory. Use the Fit all virtual memory check. That should stop all swapping. There are other options less severe. <smile>


I have used vmware on linux before, and never had to touch the way vmware handles memory...I set vmware to use all available ram and it is still crashing the machine, as it get unresponsive...I tend to think that this behavior is b/c the new AMD 64 and the way it handle s memory...it is supposed to be faster, but not in my experience, next I will try to play with the swappines to see if that way it gets better

thanks

---

### Post by keratos on 2008-03-19
I see this problem also, with the entire system not in my view being as responsive at 32bit install, and I've tried several including Vector, Zen, Xubuntu, Ubuntu ,Debian, Mepis, SuSE and more.

I read a significant amount of view on 64bit should/does outperform 32bit and I ahve been involved in many discussions and debate on the subeject in these and other forums.

In my view, from my analsysis of data, reports,thesis, posts etc, the common denominator is memory. It would seem low amounts of RAM favour 32bit, whereas say 1GB RAM favours 64bit, and favours it in a big way.

This isnt surprising if you think how memory addressing and alignment works in both achitecutures:

In 64bit addressing and data allocation, much more memory is swallowed up, however the processing of instructions and data is much more improved than over 32bit.

What this could mean therefore is that whilst execution of 64bit is far in excess in terms of performance over 32bit, the memory usage in 64bit is bloated and hence more, potentially, disk activity as memory is swapped out/in. As we know, disk activity is the bottleneck and more of it will slow or at least give the perception of slower, system.

One way to verify this is to add a gadget to your desktop to actively monitor swap and memory usage during your desktop work. Do this between the 32bit and 64bit installs. Try to use the same O/S for "equal" comparison.

This is not in any way a scientific test however it is very much a "real life experience test". All the labs in the world cannot reproduce YOUR specific setup and desktop experience.

I did this and my results were significant. On average I found that 64bit ubuntu with 512MB ram was using swap space and frequently! 32 bit performed much better in terms of the desktop experience because less swapping was taking place. With 1GB RAM the situation improved. With 2GB RAM the position was completely reversed as 64bit became far far far more responsive than 32bit, noting zero swap activity.

In all cases hdparm was used to set all disks to "optimal performance", JFS, XFS, Reiser, ext2 and ext3 filessytems were used for the [many] assessments, and the same kernel [2.6.23]  was used. 

Try it for yourself.

I think the answer is to ensure your 64bit O/S is afforded sufficient amount of RAM and if this is the case, the desktop experience in terms of performance should and usualyl will, outperform 32bit.

Again this is very subjective based on specific hardware, desktop install and the O/S in use - so please no posts about the scientific debate - but I would urge like minded people to do what I did if so inclined.

I think, for me, the key is not to take too much notice of the "purisitic scientific" debate because these can never reflect your system, in front of, that you are ACTUALLY using. Thefore the only realistic way foward is to simply try different approaches and determine for YOURSELF what system(s) and config works for YOU.

;-)

---

### Post by fjgaude on 2008-03-19
From my experience, a megabyte or more of RAM makes the 64-bit OS the winner. If you have two so much the better.

---

### Post by keratos on 2008-03-19
Agreed.

But as above and I think there is concensus, it is probably all down to workflow requirements, in other words the personal usage of the desktop including applications, together with the types of data being processed and concurrent activities (for example one might be complining a kernel whilst using the Gimp to paint a fluffy penguin!!)

Naturally the hardware spec needs to be harmonised with the workflow requirements. For me, 2GB, for you 1GB, for others maybe 4 perhaps as little as 1.

I think what is not in doubt is the specific capability and performance of a 64bit Processor over a like-4-like 32bit Processor (or effective modes thereof). However, the processor is but one of the many components driving the performance and I doubt whether we all have idential hardware as we contribute to this thread. :-)

---

### Post by VyperX on 2008-03-21
reinstall it

---

