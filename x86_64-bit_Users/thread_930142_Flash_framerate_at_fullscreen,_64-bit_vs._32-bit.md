---
title: "Flash framerate at fullscreen, 64-bit vs. 32-bit"
date: 2008-09-25
forum: x86 64-bit Users
---

### Post by nihilion on 2008-09-25
All,

I'm currently running Ubuntu-64. For most intents and purposes, it runs well and does everything I need it to do, except for flash. I mean, I have it and it runs, but if I try to watch a video at full-screen size (or much larger than then standard size 480x window, the framerate becomes totally choppy and imho unwatchable. 

Does 32-bit flash run any better? Sometimes when I want to watch some flash videos, I end up booting windows because it runs so much better at full screen. But I hate windows and would rather not use it.

Thanks.

Nick

---

### Post by Sef on 2008-09-25
1) Adobe flash is always 32-bit.

2) What are your system specs?

3) I don't have this problem, so that is the reason for question 2.

---

### Post by patrickballeux on 2008-09-25
Are you using the Flash player from Adobe (flashplugin-nonfree)?

If so, then it is a 32 bits player, even in 64 bits editions.  Adobe did not release a 64 bits player yet.

I am currently using Flash 10 RC from the site of Adobe, and I find it to be smoother thant the Flash 9 from the repository.

Be aware that the installation requires some command line, but it is worth the effort.  Also, V4L2 webcams are supported.

See this link: [http://meandubuntu.wordpress.com/2008/08/20/flash-10-rc-on-ubuntu-amd64/]("http://meandubuntu.wordpress.com/2008/08/20/flash-10-rc-on-ubuntu-amd64/")


With Flash 10, fullscreen is a lot better than Flash 9.  Also make sure that hardware acceleration (in the option of flash ) is checked.


Let me know!

---

### Post by patrickballeux on 2008-09-25
Just an idea, Totem is able to show Flash movies with a plugin and Eliza Media Player can browser Youtube service...

Far smoother than using the Flash player itself in full screen.

---

### Post by nihilion on 2008-09-25
Thanks for your reply.

My system specs should be good. It's an AMD 4400x2. Video card is an nvidia 7800. 2.5 gigs of RAM. 

I believe what I am running is the flash non-free, as I don't recall downloading anything else. But I honestly am not sure. Most likely that.

---

### Post by nihilion on 2008-09-25
Thanks, I got it working. The framerate is noticably improved, though it seems a little unstable.

---

### Post by chemical0815 on 2008-09-26
:-$

---

### Post by jespdj on 2008-09-26
So, how exactly did you fix it? By installing the prerelease version of Adobe Flash 10?

I have the same problem: full-screen Flash videos are slow and choppy.

It's certainly not because the computer is too slow: I have a 2.5 GHz Core 2 Duo and nVidia 8600M GT video card that can easily play full screen video, and media players other than Adobe Flash can show full screen, high res videos without any problem.

I guess that Adobe's Flash player (the default flashplugin-nonfree that comes with Ubuntu 8.04) is just crappy.

---

### Post by patrickballeux on 2008-10-07
Also, If you have an ATI card with compiz activated, you will have problems.  Disable Compiz to validate the conflict.

I think that there is a special configuration for ATI card to enable Compiz and have a good framerate with Flash player.  Just don't remember where I found it...

---

