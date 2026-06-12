---
title: "Downgrading to 32bit?"
date: 2008-08-01
forum: x86 64-bit Users
---

### Post by MasterNetra on 2008-08-01
I am one who would like my system to run at its fastest. So i was wondering if i should downgrade to 32bit and what files would i need to uninstall and install to downgrade ubuntu to 32bit? (Signture has my general system specs)

---

### Post by jocko on 2008-08-02
If you really want your system to run the fastest possible, you should absolutely stay with the 64 bit version, as it will take full use of your processor.
And there is no way to downgrade from 64 to 32 or upgrade the other way around. A clean install is the only way. But you can keep your /home if you have it on a separate partition (otherwise, back it up before you start).

---

### Post by Kilz on 2008-08-02
Ill second that, the only thing that moving to 32bit will do is slow your computer. It will not make it faster.

---

### Post by elmoosecapitan on 2008-08-02
There isn't really any way to put it other than 64-bit OSs on 64-bit machines are the more efficient, and just plain faster, than 32-bit OSs on 64-bit machines. This issue comes with parallel processing in which your computer can literally multi-task when it comes to running a program. One reason why some 64-bit programs seem slow is because they are often based on their 32-bit counter parts, but also since they are more powerful, manufacturers will add more things to the 64-bit versions. Thus, more time to do more things.

cheers

---

### Post by MasterNetra on 2008-08-02
ok. But i figured sense you could convert Ubuntu to Kubuntu and vica versa via installing/Uninstalling stuff i thought you might be able to do the same for the 64bit/32bit thing but if 64bit is faster then i'll stick with it then. Thanks

---

### Post by insane_alien on 2008-08-02
changing between ubuntu and kubuntu does not require replacing every part of the operating system though. in particular, it does not require changing the behind the scenes stuff like the kernel and libraries.

---

### Post by jocko on 2008-08-02
Changing from ubuntu to kubuntu is very simple. Just install some new packages (kde etc.) and, if you want to, remove some other packages (gnome etc.).
Going from 64 to 32 bit or the other way around would require exchanging *every* installed package, but that's probably not all. I'd guess it's not completely impossible to come up with a way of doing it, but a clean install just has to be both faster and easier...

---

### Post by Sef on 2008-08-03
> Changing from ubuntu to kubuntu is very simple. Just install some new packages (kde etc.) and, if you want to, remove some other packages (gnome etc.).
Going from 64 to 32 bit or the other way around would require exchanging every installed package, but that's probably not all. I'd guess it's not completely impossible to come up with a way of doing it, but a clean install just has to be both faster and easier...

Changing Ubuntu to Kubuntu or vice versa simply replaces the desktop, but leaves the backend.  64 - 32 bit would include the backend too; hence, you cannot do it.

---

### Post by MasterNetra on 2008-08-04
Yea, stick to 64bit. Of course i still have the problem with my Wireless connecting at only 10% of whats there..of course i have a thread for it in Wireless & Networking

---

### Post by crgutierrez on 2008-11-02
Can I use the **SAME** separate /home partition for both, a 32 and a 64 bit OS? How do I proceed with the instalation of the second one so it uses the same /home as the first one? Thks

---

### Post by Artemis3 on 2008-11-02
Don't use 32 bit when you can use 64 bit, which is slightly faster and lets your programs use +4g of ram.

---

### Post by crgutierrez on 2008-11-02
Gracias!

It is just my Epson Scanner(V350), which makes me dependent on 32bit. But actually I run it from another PC and basically use only 64 bit

---

### Post by joebuntu_2 on 2009-03-13
I *know* 64 is meant to be much better, I just don't think we're at that point yet. Has anyone really noticed an improvement when using a 64bit os? Seems to me like you just get a reduced choice of software, some instability and a slower system for your troubles.

Check out: [http://www.phoronix.com/scan.php?page=article&item=998&num=3](http://www.phoronix.com/scan.php?page=article&item=998&num=3)

I'm running 64 Intrepid ( my first foray into Ubuntu) and it's pretty crap. Slowdowns are common and programs often lock up for 5-10 seconds when doing simple tasks. Running 4gb of ram, of which only 3gb is recognised.

Don't get me wrong - I can't wait for 64 bit computing, I just don't think it's really arrived yet. Let's see how Snow Leopard does.... for now I'll be "upgrading" to 32 bit so I can use Skype and see if it's any quicker/more stable.

---

### Post by jespdj on 2009-03-13
joebuntu_2, you probably have a specific piece of software or hardware in your particular system which unfortunately doesn't work well with 64-bit Ubuntu.

It's not normal or common that a 64-bit system is not stable or has strange 5-10 second pauses like you describe. Just because you have a particular problem doesn't mean that 64-bit Ubuntu is less stable or slower for anyone, or that "64-bit computing hasn't really arrived yet" in general.

What hardware do you have? Look in the BIOS settings if there is a feature named "memory remapping" or something similar, and enable it. That might help to let Ubuntu recognise more than 3 GB RAM.

---

### Post by joebuntu_2 on 2009-03-13
> **jespdj said:**
> joebuntu_2, you probably have a specific piece of software or hardware in your particular system which unfortunately doesn't work well with 64-bit Ubuntu.

It's not normal or common that a 64-bit system is not stable or has strange 5-10 second pauses like you describe. Just because you have a particular problem doesn't mean that 64-bit Ubuntu is less stable or slower for anyone, or that "64-bit computing hasn't really arrived yet" in general.

What hardware do you have? Look in the BIOS settings if there is a feature named "memory remapping" or something similar, and enable it. That might help to let Ubuntu recognise more than 3 GB RAM.

Hi Jespdj,
Don't mean to bash 64 bit computing - just warning that I don't think it's quite here yet. The fact that I possibly have some software or hardware that doesn't work well with it illustrates my point exactly.

Can you point me to any benchmarks or proof that the 64 bit runs quicker during normal - or even any tasks? I haven't seen any - just lots of talk about how it SHOULD be quicker. 

Maybe i'm exagerrating the slowdowns but I dual boot with Win7 (32bit) - which boots in about 1/3rd the time and multitasks everything seemlessly (I know you guys hate Windows but 7 is impressive). It's only because i'm used to that speed that my Ubuntu installs occasional slowdowns stand out like a sore thumb.

However, even with the slowdowns I find I rarely boot into Win7 since I installed Ubuntu. Maybe it's novelty factor, but it's kind of nice exploring and learning about a different approach to O/Ss. I need Ubuntu to run router emulation software (GNS3), which runs MUCH better in Ubuntu. It's just other normal stuff that seems to trip it up sometimes.

Let me know if anyone finds any decent benchmark proof that shows which is faster.
Thanks!

---

### Post by joebuntu_2 on 2009-03-13
> **jespdj said:**
> 
What hardware do you have? Look in the BIOS settings if there is a feature named "memory remapping" or something similar, and enable it. That might help to let Ubuntu recognise more than 3 GB RAM.

Got an Acer 5680 with Centrino Duo 2ghz & 4gb ram. I checked the BIOS, it's just a barebone BIOS with no sharp edges to hurt yourself. No reference to memory. The fact that it shows 4gb in the bios (and when I installed Vista 64bit) and that other users have reported Feisty showed 4gb but Intrepid only 2.9gb makes me think it's a possible bug. Be nice if they fixed it but don't think the upgrade from 3-4gb will affect the normal running too much. 

Thanks for the tips though.

---

### Post by MACDSE on 2009-03-13
> **joebuntu_2 said:**
> I *know* 64 is meant to be much better, I just don't think we're at that point yet. Has anyone really noticed an improvement when using a 64bit os? Seems to me like you just get a reduced choice of software, some instability and a slower system for your troubles.

Check out: [http://www.phoronix.com/scan.php?page=article&item=998&num=3](http://www.phoronix.com/scan.php?page=article&item=998&num=3)

I'm running 64 Intrepid ( my first foray into Ubuntu) and it's pretty crap. Slowdowns are common and programs often lock up for 5-10 seconds when doing simple tasks. Running 4gb of ram, of which only 3gb is recognised.

Don't get me wrong - I can't wait for 64 bit computing, I just don't think it's really arrived yet. Let's see how Snow Leopard does.... for now I'll be "upgrading" to 32 bit so I can use Skype and see if it's any quicker/more stable.

Not sure when this thread was created but, I guess I can add my two cents and say that I had installed win x 64 OS and it hung up on simple tasks such as closing browser. Not sure I saw any real improvement regarding speed or anything else. So, now I am here contemplating as to wether I should install the 32 bit version of Ubuntu or the 64 bit. I guess I will just continue to read on and see wether I can make up my mind or not.

---

### Post by joebuntu_2 on 2009-03-13
> **MACDSE said:**
> Not sure when this thread was created but, I guess I can add my two cents and say that I had installed win x 64 OS and it hung up on simple tasks such as closing browser. Not sure I saw any real improvement regarding speed or anything else. So, now I am here contemplating as to wether I should install the 32 bit version of Ubuntu or the 64 bit. I guess I will just continue to read on and see wether I can make up my mind or not.

It's easy enough to assess - they both come on a live cd. I get the impression that 64 is great if you're really taxing the crap out of your machine with some real heavy memory/ cpu usage. However for the average desktop user 32 seems to be just as fast if not slightly faster, but with less issues with applications and drivers.

---

### Post by t-mo_ on 2009-03-13
> Can you point me to any benchmarks or proof that the 64 bit runs quicker during normal - or even any tasks? I haven't seen any - just lots of talk about how it SHOULD be quicker.

Aaah, yes I can. I've tested all the nvidia-drivers with glxgears, for example.
On 32bit Ubuntu (Intrepid) I have around 2900 - 3600 FPS
On 64bit Ubuntu (Jaunty) I have around 4300 - 6500 FPS


If you are really interested in, make a dual boot and do some benchmarks by yourself. You're right, there are still some issues with 64bit. For me almost everything works great with Jaunty x86-64.

---

### Post by athaki on 2009-03-13
It's good for BOINC manager.  It's shaved an hour off of processing from 32bit Vista (not really a comparasion, I know)

---

### Post by 3Miro on 2009-03-13
For all that my opinion/experience is worth:

64 bit is faster in just about anything it does, I used to dual-boot 8.04 kubuntu between 32 and 64 and yes you feel the difference (it is not 2 time faster, it is lttle faster and definitely smoother).

Right now I am using only 8.10 Kubuntu and Ubuntu both 64 bit (desktop and laptop). I have no problems or whatsoever. There were few software issues in the past, not they are all gone. Only drivers could be the problem, actually all 32-bit apps run under 64-bit just fine.

Crashes and hang-ups are abnormal and definitely not the status quo. I have been using (for work) 64-bit K/Ubuntus since 6.10, never had problems with stability (just sometimes drivers and software, but that is gone now). If you guys have hand-ups and such, try to find the problem, it is not inherit for the 64-bit.

There are some apps (video editing, scientific computer simulations and others) that run 2 - 4 times faster simply because of 64-bit support. If you are using such apps, however, you probably already know that.

---

### Post by joebuntu_2 on 2009-03-13
> **t-mo_ said:**
> Aaah, yes I can. I've tested all the nvidia-drivers with glxgears, for example.
On 32bit Ubuntu (Intrepid) I have around 2900 - 3600 FPS
On 64bit Ubuntu (Jaunty) I have around 4300 - 6500 FPS


If you are really interested in, make a dual boot and do some benchmarks by yourself. You're right, there are still some issues with 64bit. For me almost everything works great with Jaunty x86-64.

Hmmm, might give Jaunty a whirl and see how that fairs. Dual booted 32 & 64 as of last night, so far 32 seems oddly more quiet on the CPU and mem usage during basic tasks, although GNS3 will be the ultimate test for me.

---

### Post by jespdj on 2009-03-14
In theory a 64-bit operating system should run faster, especially with processor-intensive programs, for example for decoding or encoding audio or video.

Some technical details:

In 64-bit mode, the processor has 16 instead of 8 general-purpose registers available and they are 64 instead of 32 bits long. There are also twice as many 128-bit SSE registers (16 instead of 8). See [x86-64](http://en.wikipedia.org/wiki/X86-64) on Wikipedia for full details.

Also, the [calling convention](http://en.wikipedia.org/wiki/X86_calling_conventions) is different for 64-bit; arguments for subroutine calls are passed through registers instead of through the stack. This makes subroutine calls faster in 64-bit software.

So, in 64-bit mode, you're making full use of the capabilities of your processor and software runs more efficiently. In practice, you'll most likely only really notice these differences in software that heavily uses the processor.

---

