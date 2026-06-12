---
title: "Problems with Ubuntu 9.04 64bit"
date: 2009-10-08
forum: x86 64-bit Users
---

### Post by ksp1717 on 2009-10-08
Hi I had a dual boot of ubuntu 8.10 64 and windows xp 32  for quite sometime. 

I upgraded my RAM from 2GB to 4GB and then the problems started. Half the times my system did not boot properly, I had problems with grub and even if the desktop came up there are many problem and the system crashed quite often. Then i realised i hav to increase my swap space and reconfigure the installation. 

I completely removed 8.10 and installed a fresh copy of ubuntu 9.04 64bit with increased swap space. The installation did not go smooth the first two times. The third time however it went all the way and i can see the desktop and my system is up and running. 

Now, I still have some problems left some of which are as follows:
1. Firefox is not running after i upgraded the kernel.
2. I cannot install somepackages as it always shows some problems as archive not opened or something like that. 
3. I installed edubuntu and after that the situation became worse, every now and then it shows some filesystems errors while booting and i have to run fsck and after this it boots up.

Any idea why all this is happening??? and possible solutions?

Thanks, Shyam

---

### Post by Dougie187 on 2009-10-08
Just because you add ram doesn't mean you have to increase your swap space. All your swap space really is is extra 'ram' space that is on your hard drive. It's basically backup for the ram if it gets full. You only really even need a decent amount of it if your ram is very small. 

It sounds like you have other problems to me. Does windows run well? You might try checking that the ram you installed is good.

---

### Post by Yellow Pasque on 2009-10-08
Now would be a good time to back up your data if you haven't already...

---

### Post by ksp1717 on 2009-10-09
Yes my windows is working perfectly fine. As a matter of fact I m back to using it right now.

I thot I should maintain a swap of >=RAM.

---

### Post by P.KO on 2009-10-09
Well, if you use hibernation or suspend you need to have enough RAM on swap. If you don't use these features, your system with 4 GB might run without any swap.

---

### Post by Rizlaw on 2009-10-11
Without knowing more about the RAM you added, I strongly recommend running "Memtest86+" which you will find on any Ubuntu LiveCD for about an hour, more if you have patience or if you are overclocking.

If it checks out without errors, then RAM is probably not the issue. I have had 2 or 3 issues with new RAM causing strange behavior in Ubuntu and until I tested my new RAM I would never have suspected my new or old RAM as the culprit. This is particularly true if you don't have matched pairs of RAM or in the case of i7 x58 motherboards, triple sets of matched RAM.

---

### Post by grege on 2009-10-13
Just adding to what rizlaw said.

Just because XP is working does not mean much. Firstly it can only read three quarters of the ram so if there are errors in the last gig it would never know. Secondly XP does not use much ram and tolerates errors, it is probably rarely out of the first gig unless you really stress it.

You may have dud ram or BIOS limitations on installed amounts. I would pull out the new ram and reinstall Ubuntu 64bit and see if it is stable, then experiment. Another test, take out the old ram and only use the new stuff and see what happens - it may be they will not work together.

good luck

---

### Post by ksp1717 on 2009-10-14
hi thanks for your suggestions. 

I hav checked the installation with only a single RAM and everything worked fine. 

I actually removed the ubuntu and installed fedora 11 64 and it is working without any problems. So probably something wrong with the cd i installed ubuntu from. I will try it with a fresh copy and check my luck with it.

shyam

---

