---
title: "Random Freezing. no logs"
date: 2005-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by IndieRockSteve on 2005-05-31
ECS KN1 Extreme
Athlon64 3200+

at first I thought this might be due to one of my ATA harddrives because the first couple times it froze while writing to it. It froze again today and I don't have that drive mounted. So now I have the problem that its freezing, nothing in the logs that would really indicate why(at least that I can find), and I'm assuming by not having the drive mounted I removed it from the equation.

so, anyone have any ideas for me?

thanks!

---

### Post by jkndrkn on 2005-05-31
I also experienced random freezing, and at first I thought my wireless setup was the cause. Turns out I needed to install the latest nvidia drivers. 

Follow the link below if you need any pointers:

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

---

### Post by thrift on 2005-05-31
I'm not sure if it's still the case, but a couple kernel versions ago if you had over 900M ram you had to install a processor specific kernel or the RAM would get all goofy and you might experience something like what you are saying.  I think this may be fixed in the newer kernels though.

How much RAM do you have?  How much RAM is the Gnome System Monitor aware of?

---

### Post by whiskybar on 2005-06-01
I'd suspect your RAM is faulty. We had this problem in the server, it caused lockups about once in a week for about half a year until it did not boot back up. There were no messages in the logs, nor any logged activity showed anything was wrong in the software.

The problem was, we did every possible test of the RAM but it did not reveal anything. You may want to try running the memtest at the boottime (grub menu) but I hate to tell you it won't detect anything.

---

### Post by thrift on 2005-06-01
memtest86 will detect almost ANY RAM problems.  It even detects a couple spots on my RAM after leaving it run for about 24 hours(my ram is fine), but you can't just leave it run for 15 minutes, and if it doesn't pick up anything it's probably not the RAM, but the way your OS is interfacing with that RAM, such as the 900M limitations on some kernels.

---

### Post by whiskybar on 2005-06-02
Now this is interesting, Thrift. 

One, I don't thing my RAM is faulty, but memtest86 may still detect some weak spots (after 24 hours running and then rebooting to the memtest86)? I will definitely try it. If it finds anything, is it something I have to worry about?

Two, I have two pieces of 512MB DDR 400Mhz PC3200 CL2.5 KINGSTON on Microstar K8N Neo2 nForce3 and AMD64 3000. Are you suggesting there might be some issues with so much RAM on Ubuntu Hoary 64bit? That would be sad news... Can you explain why is that or point me to the site explaining this phenomenon?

Thank you

---

### Post by IndieRockSteve on 2005-06-02
I have two sticks of Corsair RAM, 1gig. I'm running the amd64 k8 kernel (2.6.10 and 2.6.11 interchangeably).

I'll run the ram test and see what happens.

btw, how the hell does the kernel team get away with a bug that prevents you from running more than 900M of RAM?!

I think I'm also going to try running one of the 32bit kernels to see if that has the same problems.

thanks!

---

### Post by thrift on 2005-06-02
If you get a couple bad spots on the RAM it's no big deal at all.  It "happens"  If you get 100s of pages of bad spots after a 24 hour period, there is a decent chance your RAM has a lot of bad spots on it.

I'm not sure if Ubuntu still has the problem with the default kernels or not, I think it only occurs with the default Ubuntu 32 bit kernel and probably not the 64 bit kernel.  I'm not exactly sure why, but there are 3 options for memory size in the linux kernel that I am aware of, 0M-900M, 0M-4G, or >4G.  The default Ubuntu kernel for some reason used to default to the 9-900M version, and I think it still does for 32 bit.  On the processor specfic kernels it's the 0M-4G for 32 bit, so it's no problem for me running the k7 kernel with over a G of ram in 32bit mode.  There was a kernel patch floating around that would use the first 900M of RAM and then the ram after that as extended RAM, so you could have 1.2G and use it without whatever drawbacks some of the other options had.  So I don't know if it's implemented in any of the Ubuntu kernels yet or what they are doing, but you can very easily just check the Gnome system monitor to see if it's effecting you.  If under the Resources tab, if your user memory is around 900M and you have a G, that's probably a big source of your problems.  You'll also see your used memory will be around 800M with nothing but the Gnome desktop  in a few days.

When I ran with only support for 900M of RAM my uptime was about 4 days before everything would start crashing.  Depending on how much I used the machine an the like.  Now I'm using way more RAM than I did before(about 432M) and have an uptime of 23 days.

---

