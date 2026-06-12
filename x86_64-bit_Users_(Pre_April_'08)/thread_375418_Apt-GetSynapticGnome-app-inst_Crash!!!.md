---
title: "Apt-Get/Synaptic/Gnome-app-inst Crash!!!"
date: 2007-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by DaRush on 2007-03-03
Ubuntu 6.10, Amd 64 on Compaq Pressario V200 laptop.

Had to Install a custom kernel 19.1 among other things, in order to get my broadcom wifi to work.
That ran fine, but I didn't update the kernel packages for fear of troubleshooting my wifi again.  Worked like this for more than a month (including updates and synaptic manager), but today I noticed that my update icon is no longer showing.  When I run add-remove programs, the window loads for a second then just shuts off by itself.  I try running Synaptic package manager, that prompts me for a password, then just closes by itself too.  Finallly I ran sudo apt-get upgrade, this produced:
Segmentation faultsts... 0%

I did not install anything new on the computer, just mildly used it for typing, etc.  This just seems to have stopped working by itself!

this is the relevant system log that I think has something do with the problem...
Mar  3 18:17:02 vlady-laptop kernel: [   76.031466] gnome-app-insta[4784]: segfault at 0000000000000000 rip 00002ae72bfa30f0 rsp 00007fff7f134848 error 4
Mar  3 18:25:40 vlady-laptop kernel: [  339.297670] synaptic[5156]: segfault at 0000000000000000 rip 00002b26205700f0 rsp 00007fff8d6dd9a8 error 4
Mar  3 18:32:56 vlady-laptop kernel: [  557.427183] apt-get[5502]: segfault at 0000000000000000 rip 00002ae98024c0f0 rsp 00007fff2b051c58 error 4
Mar  3 18:33:14 vlady-laptop kernel: [  566.568350] apt-get[5519]: segfault at 0000000000000000 rip 00002b053a7d50f0 rsp 00007fff70ac7338 error 4
Mar  3 18:34:48 vlady-laptop kernel: [  613.542225] gnome-app-insta[5577]: segfault at 0000000000000000 rip 00002b535ec6a0f0 rsp 00007fff4c46bb78 error 4
Mar  3 18:35:01 vlady-laptop kernel: [  620.750975] python[5606]: segfault at 0000000000000000 rip 00002b6ab93150f0 rsp 00007ffff1dc4bc8 error 4
Mar  3 18:35:02 vlady-laptop kernel: [  620.983935] synaptic[5605]: segfault at 0000000000000000 rip 00002b1aa92d80f0 rsp 00007fff04973758 error 4

I would appreciate any help... 
Thanks

---

### Post by John Jason Jordan on 2007-03-03
> **DaRush said:**
> Ubuntu 6.10, Amd 64 on Compaq Pressario V200 laptop.

Had to Install a custom kernel 19.1 among other things, in order to get my broadcom wifi to work.
That ran fine, but I didn't update the kernel packages for fear of troubleshooting my wifi again.  Worked like this for more than a month (including updates and synaptic manager), but today I noticed that my update icon is no longer showing.  When I run add-remove programs, the window loads for a second then just shuts off by itself.  I try running Synaptic package manager, that prompts me for a password, then just closes by itself too.  Finallly I ran sudo apt-get upgrade, this produced:
Segmentation faultsts... 0%

I did not install anything new on the computer, just mildly used it for typing, etc.  This just seems to have stopped working by itself!

this is the relevant system log that I think has something do with the problem...
Mar  3 18:17:02 vlady-laptop kernel: [   76.031466] gnome-app-insta[4784]: segfault at 0000000000000000 rip 00002ae72bfa30f0 rsp 00007fff7f134848 error 4
Mar  3 18:25:40 vlady-laptop kernel: [  339.297670] synaptic[5156]: segfault at 0000000000000000 rip 00002b26205700f0 rsp 00007fff8d6dd9a8 error 4
Mar  3 18:32:56 vlady-laptop kernel: [  557.427183] apt-get[5502]: segfault at 0000000000000000 rip 00002ae98024c0f0 rsp 00007fff2b051c58 error 4
Mar  3 18:33:14 vlady-laptop kernel: [  566.568350] apt-get[5519]: segfault at 0000000000000000 rip 00002b053a7d50f0 rsp 00007fff70ac7338 error 4
Mar  3 18:34:48 vlady-laptop kernel: [  613.542225] gnome-app-insta[5577]: segfault at 0000000000000000 rip 00002b535ec6a0f0 rsp 00007fff4c46bb78 error 4
Mar  3 18:35:01 vlady-laptop kernel: [  620.750975] python[5606]: segfault at 0000000000000000 rip 00002b6ab93150f0 rsp 00007ffff1dc4bc8 error 4
Mar  3 18:35:02 vlady-laptop kernel: [  620.983935] synaptic[5605]: segfault at 0000000000000000 rip 00002b1aa92d80f0 rsp 00007fff04973758 error 4
I have Compaq Presario R3240 laptop with Ubuntu Edgy amd64. I started with Hoary a year and a half ago when the computer was new, upgrading each time a new version came out. Throughout that time I had constant crashes and all sorts of other problems. I saw lots of segmentation faults too. 

One day I was at the university and the computer would not boot. The Compaq splash screen came up, disappeared, and then nothing. After much futzing around I discovered that the hard drive was not seated properly. Eventually I cobbled up a fix -- a piece from a cardboard box between the drive and the outer plastic part that it is fixed into. The drive was too slim and was not seated all the way down into the connector. Since then I have not had any further segmentation faults and lockups.

I offer this story just because there is a possibility that your problems are simple hardware issues rather than software-based. Compaq laptops are not as bad as some, but in my estimation the quality and fit and finish of the hardware is not very good.

---

### Post by DaRush on 2007-03-03
That might be a good call on the hardware as my fan died recently and the laptop was running pretty hot.  I'm using a chill mat with it now, and that keeps it cool, but there might be some Hard Drive damage.  I doubt it, because everything still runs, I'm using it as I type this.    Nevertheless, if there is a way to update the system in order to solve this It would be good. 

Btw, the problem is still present even if I load another kernel.

Please help, as I'm a noob to Linux in general and need to solve this problem.

---

### Post by John Jason Jordan on 2007-03-03
> **DaRush said:**
> That might be a good call on the hardware as my fan died recently and the laptop was running pretty hot.  I'm using a chill mat with it now, and that keeps it cool, but there might be some Hard Drive damage.  I doubt it, because everything still runs, I'm using it as I type this.    Nevertheless, if there is a way to update the system in order to solve this It would be good. 
Btw, the problem is still present even if I load another kernel.
Please help, as I'm a noob to Linux in general and need to solve this problem.
I am also a n00b -- only about a year and a half with Linux. However, if you are seeing segmentation faults the problem is 99% for sure hardware. Go here:
[http://aplawrence.com/Unixart/segmentation_fault.html](http://aplawrence.com/Unixart/segmentation_fault.html)
In your case, I bet the problem is that busted fan. Running too hot can cause all kinds of other stuff to flake out. Can you stick it in the freezer for a couple of hours and try again?

---

### Post by DaRush on 2007-03-04
OK, I performed a memory test (from an Ubuntu live CD - left it running for a day) and that showed no errors.  I scanned the HD from the bios, and had no erros there either....

What else could be causing the segfaults???

---

### Post by John Jason Jordan on 2007-03-04
> **DaRush said:**
> OK, I performed a memory test (from an Ubuntu live CD - left it running for a day) and that showed no errors.  I scanned the HD from the bios, and had no erros there either....
What else could be causing the segfaults???
I regret to say that you have exceeded my ability to reply. In other words, I have no clue. :(

Hopefully someone else will know more about these issues.

---

### Post by DaRush on 2007-03-04
Thanks Jason, you've been very helpful...

One more thing... the command I ran to check my hd, was: sudo fsck -cf /dev/hda1 once I booted into Ubuntu from the live CD.   Is there any other way I can check my hard drive and/or memory for errors?

Thanks again

---

### Post by John Jason Jordan on 2007-03-05
> **DaRush said:**
> One more thing... the command I ran to check my hd, was: sudo fsck -cf /dev/hda1 once I booted into Ubuntu from the live CD.   Is there any other way I can check my hard drive and/or memory for errors?
There may be some utilities that will churn the drive for a while to see if it will fail, but I don't know of any. And I'm not sure such a utility would help. My problem was a flaky connector. The drive worked perfectly 99.9999% of the time. But once every few days it would bite me in the butt. Actually, I'm not even 100% positive the problem was the drive. All I know is that once in a while the computer wouldn't boot and reseating the drive fixed it. And since inserting the cardboard I haven't had a segmentation fault. But that doesn't mean I really fixed it. Maybe the damn thing is sitting in there grinning to itself as it plots how it's going to screw me the night before a large paper is due. Inanimate objects think like that, you know.

---

### Post by DaRush on 2007-03-05
Haha, I'm in the same boat.... I'm supposed to be writing a paper on Baudrillard right now...

Anyway, thanks for the help... I guess I'll be opening my laptop

---

### Post by DaRush on 2007-03-07
Problem Solved....

Turns out, the apt-get cache files were corrupt.  Simply erasing these files did the trick, everything seems to work now!

I was already shopping around for memory and maybe a new HD :)

---

