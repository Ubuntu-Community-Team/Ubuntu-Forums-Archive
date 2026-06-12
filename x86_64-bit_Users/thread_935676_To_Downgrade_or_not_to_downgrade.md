---
title: "To Downgrade or not to downgrade?"
date: 2008-10-01
forum: x86 64-bit Users
---

### Post by ICantBelieveItsLinux on 2008-10-01
Hey guys, it's my first time posting on the forum, so sorry if i dont do anything I'm supposed to, and sorry if this is in the wrong section. Wasnt sure whether I should put my question here or in the "Absolute Beginner" section since that's what I am. 

I've been running ubuntu for about 2 days now, I switched to Linux in order to rescue some information from my systemroot registry screwed XP.... Anywhoo... 

Right now I'm using an HP L2000 Special Edition Laptop with Hardy Heron, I've got an AMD Turion 64 Mobile Technology, and 60 GB of memory.

I've currently got the 64-bit ubuntu installed on my laptop right now, and I was wondering whether I should downgrade to 32-bit. I know that there are lots of pros and cons that have been posted, argued, and stickied... my problem is not that things dont work with my ubuntu, everything works fine, my flash works, wireless, havent tried any video codecs, but I'm assuming they will work. However, it seems that my ubuntu is running a little sluggish sometimes, if I minimize a window, or try to open an application it will take my system a good chunk of time to process that. Or if i try to zoom by ctrl+scroll wheel, it wont do anything for a while, than suddenly start zooming in or out like 10,000 times. There's sometimes a delay when I type, and just general all around kind of sluggish performance. It's not unbearable, but it is irritating. 

I had heard that 64-bit can keep up more RAM quicker than 32-bit so I was wondering, if I downgrade from 64 to 32 would that improve my laptop performance? Or at least theoretically cut down on this sluggish performance from my laptop?

Oh and my graphics card is an ATI Radeon Xpress 200M... In case a 32-bit will screw my graphics card over or something...

Thanks for your help and time

---

### Post by cariboo on 2008-10-01
Your laptop performance has nothing to do with which version you are using. You have something running that is using all the cpu time. You could have a look at System-->Administration-->System Monitor to see if there is something using all your cycles. Be aware that System Monitor has its own overhead, so you won't get a true reading, but it should be able to tell you if you have a program misbehaving. You didn't mention how ram you have, because that can be a problem if you don't have enough. I find that you need at least 512mb to run Ubuntu comfortably. 

You could also open a Applications-->Accessories-->Terminal and run top
This will give you a true indication of what is stealing all your cycles.

Jim

---

### Post by ICantBelieveItsLinux on 2008-10-02
Oh, my bad haha forgot to. I have 1 GB of RAM, although System Monitor is reporting only 877.7 MiB

Thanks for the help! I must say despite the sluggish performance on my end... I'm loving linux...

---

### Post by Sef on 2008-10-02
In the terminal, type this: top.   (Applications > Accessories > Terminal)

It will also show you what's running and see if something is taking up too much ram.

---

### Post by Jouke74 on 2008-10-02
I think it's a video card ehh chip related issue. The ATI Raedon express 200 card is using normal memory to work, instead of it's own video memory. That's why you also see that a part of the memory is not visible when using free -m. 128 MB is probably your reserved video memory size. It also means that all your video processing goes through the normal memory bus, which makes it slow.

My questions: 
1. Which drivers did you install for your ATI "videocard"?
2. Did you disable the desktop effects (Compiz) and see how it goes then? Probably a lot better.
3. If you want to keep desktop effects you can tweak them to minimize the delay. Also turn a few of them off. Install the compizconfig-settings-manager.

---

### Post by Thelasko on 2008-10-02
I agree with Jouke74, sounds like a classic video card issue.  You may have to play with the drivers/configuration.

I have a 1GB of RAM with the dreaded Intel 965 on board graphics card, and my system is quite speedy.

---

### Post by ICantBelieveItsLinux on 2008-10-05
I'm not sure if I installed any of my ATI drivers... I'm a bit new to all of this hahaha :] How can I check, and how can I install the appropriate ones if I need to?

Thanks for all the help so far guys really appreciated

---

### Post by Kilz on 2008-10-05
I also agree on the video issue, especially if running desktop effects. The 200m is the bargain basement card. It really isnt a card but an onboard graphics. I am not sure if even the video drivers will allow you to run desktop effects with it. It will not make one iota of difference if you are running the 32bit version. Desktop effects are resource hungry.
If you dont remember installing ati drivers, odds are you havent. Here is a link to the best howto imho. [Use method 2. ]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8_or_8.9.29")

---

### Post by ICantBelieveItsLinux on 2008-10-05
I used the automatic installation thing in Hardy Heron, I checked the box next to the ATI Driver when I first installed Linux and I've been using that ever since

By the way, my firefox is running at 113 MiB according to my system monitor, and all I am currently doing with Firefox, is posting on this forum, is this normal memory usage, or do I have a leak? (Sorry if this is a stupid or obvious question)

---

### Post by ryry46d9 on 2008-10-05
my fire fox is running @ 52.2 MB with only one tab open (do you have more?)

click on tools then add-ons  and remove anything you might not need

---

### Post by Kilz on 2008-10-05
> **ICantBelieveItsLinux said:**
> I used the automatic installation thing in Hardy Heron, I checked the box next to the ATI Driver when I first installed Linux and I've been using that ever since


Read post 8, follow the link, do the howto.

---

### Post by ICantBelieveItsLinux on 2008-10-06
It killed my system, I can only run it in a low graphic setting and forced me to reformat my system... Although admittedly I found the method kind of confusing and am unsure of whether I followed the instructions correctly. For example:

"If you are using the x86_64 architecture (64 bit), be sure to inst "ia32-libs" before proceeding!


Make sure universe and multiverse are enabled in your repository sources.


Switch to the directory you downloaded the installer to. "

I am unsure of whether or not I did any of those already, or how to check whether I did them or not, or how to do follow those steps if I need to.

---

### Post by Yellow Pasque on 2008-10-06
Please, please, please, seek help before reformatting or reinstalling. Linux IS NOT Windows. Your problem could have easily been solved by switching back to the open-source driver.

> Make sure universe and multiverse are enabled in your repository sources.

Go to System -> Administration -> Software Sources and check the appropriate boxes.

> "If you are using the x86_64 architecture (64 bit), be sure to inst "ia32-libs" before proceeding!
```
sudo apt-get install ia32-libs
```

> Switch to the directory you downloaded the installer to. "
For example, if you downloaded the installer to your desktop:
```
cd ~/Desktop
```

---

### Post by getnripped on 2008-10-20
wrong thread.

---

