---
title: "Trouble with Guild Wars 2"
date: 2013-04-06
forum: Wine
---

### Post by fernetekhd on 2013-04-06
So I'm having a problem with Wine and the Guild Wars 2 launcher. Using Playonlinux I was able to download the two latest wine versions (both have the same problem) and I added Guild Wars 2 with ease. Upon launching the patcher, however, I get a major error; the launcher first appears within a large, black window covering ~1/3 of the screen, and it pings the download servers and collects files and whatnot; however, once it starts the actual patching it completely disappears in this black screen.

Find attached a screenshot of the problem.

I do NOT have any graphics drivers installed, although even when I did (Nvidia drivers for my GTX 560 Ti) this problem still occurred.

I appreciate any help in this matter!

P.S. ~10 seconds after I finished the post the client finally crashed and asked me to send an error report to ArenaNet.

---

### Post by fernetekhd on 2013-04-06
Any ideas at all :(? Might tweaking some Wine settings help?

EDIT: Sorry for the hasty bump, I misunderstood the thread creation/bump times and thought that every thread but mine was getting very quick responses :S

---

### Post by fernetekhd on 2013-04-08
Alright, so a Google search led me to this video:

[http://www.youtube.com/watch?v=QZQHO7IbvOA](http://www.youtube.com/watch?v=QZQHO7IbvOA)

Which explained that the main cause of the black screen was using an incorrect version of Wine.

Even after follow his instructions, however, I'm still having a problem. Although the black screen is gone, the launcher still seems to be frozen, in that I don't see it pinging the update server or...anything (also, it sorta looks like the black screen is still there just invisible; ex. when I tabbed out of this post a small chunk of the webpage surrounded the client). Along with that, when I added the -dxsingle like he instructed Ubuntu froze up and crashed.

---

### Post by zobo90 on 2013-04-15
When you say it downloads the files, has it downloaded all of them?  If not, does the .dat file get bigger each time you launch it?  Which desktop environment are you using? There are known issues with the downloader crashing quite often, but the download carries on from where it started when you relaunch it.  

Another thing that has caused a lot of problems for some people is PulseAudio, so if your system is using that, you may want to remove/disable it.  

I managed to get GW2 working, but the frame rate wasn't good - so even if you don't get it working, don't get your hopes up too much!  (Around 8 - 15 FPS on lowest graphics settings, but I'm using AMD Radeon HD 6700.  I had to use AMD's driver, as the opensource one didn't want to work :( )

---

### Post by Bucky Ball on 2013-04-15
Hi fernetekhd. I have removed the large image from the body of your first post, attached it, and edited the post accordingly. Please refrain from inserting large images in the body of the post and attach them instead. This can be done by clicking 'Go Advanced' when creating a new post and clicking the paperclip icon. Good luck. ;)

---

### Post by myromance123 on 2013-04-17
> Alright, so a Google search led me to this video:
I'm sorry if my video guide didn't work for you, it was made during the game's release. Now that there have been many updates to GW2, there are new things Wine needs to handle.

PlayOnLinux have just released a new compiled Wine version 1.5.28-GuildWars2. I urge you to try that in PlayOnLinux. You do not have to reinstall GW2 to be able to change Wine versions.

Instead, highlight your GW2 install in PlayOnLinux. To the right is some text labeled as Configure. Click that. Now, under the General tab you'll see a dropdown menu titled Wine version. Click the arrow to see what Wine versions you have and select the 1.5.28-GuildWars2 version. Now try and run GW2 again. Hopefully this helps you get past the launcher issues at least.

Not sure how to install a new Wine version in POL? To the right of the arrow, there's a small + button. Click that, and select the Wine version on the left in the new window that pops up. Click the > button in the middle, and follow the on screen instructions. After that, you should have your selected Wine version installed. All the best!

---

