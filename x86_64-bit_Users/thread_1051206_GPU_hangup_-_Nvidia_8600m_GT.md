---
title: "GPU hangup - Nvidia 8600m GT"
date: 2009-01-26
forum: x86 64-bit Users
---

### Post by vandorjw on 2009-01-26
Hi,

About a month ago I installed ubuntu 8.10 64-bit on my laptop.
Everything went well. However, some times the display goes fuzzy and the system hangs up. It happened about 3 times now. Each time I did something different when it happend.

Is there something I can check to find out what causes the problem.

I think it is the Nvidia Driver but I am unsure.
I downloaded and installed one from the Nvidia website.


180.22 = Driver Version

Cheers - CC7

---

### Post by jespdj on 2009-01-26
What brand and model laptop do you have? A few months ago, there was some information in the news that some nVidia cards were produced badly and when the card gets too hot then strange things could appear on screen. This was the case with some Dell laptops (such as the Dell XPS M1530, which I have - but fortunately mine does not have this problem). So it might be a hardware problem. You'd have to contact the manufacturer of your laptop about this issue.

The nVidia driver 180.22 however also doesn't work well on my system. I sometimes get artifacts or the screen doesn't redraw properly. I'm now using driver version 177.13 which you can [download here](http://www.nvidia.com/object/linux_display_amd64_177.13.html), and it doesn't have these problems.

---

### Post by ditsch on 2009-01-26
Besides hardware quality issues, the current Nvidia drivers also have some trouble with Linux, especially on Desktops with Compiz enabled. Please see the infamous bug: [https://bugs.launchpad.net/bugs/269904](https://bugs.launchpad.net/bugs/269904)

---

### Post by vandorjw on 2009-01-26
Thanks for the replies so far.

My machine is the Inspiron 1520 and its been working very well for almost a year and a half. I also read about the batch of bad GPU's made by nVidia, however, I do not think that mine is effected.

The temperature rarely goes about 50 degrees Celsius and other than the random crashes, I have not experienced any glitching or visual artifacts.

I will try drivers version 177, hopefully that will fix the issue.

Cheers - cc7

---

### Post by vandorjw on 2009-02-04
I haven't had the hangup for many days now. I hope the strange phenomenon is now gone. I didn't do anything to try and fix it.

The 177 driver had something missing so it couldn't compile.
After I upgraded the kernel version I had to recompile the nVidia Driver to get it to work again. Maybe that fixed it.

Cheers - CC7

PS: How do I mark a thread as solved. I have done it before, but the option to do it from thread tools is gone.

---

### Post by jespdj on 2009-02-05
> **cc7gir said:**
> PS: How do I mark a thread as solved. I have done it before, but the option to do it from thread tools is gone.
A while ago there was a problem with the database for the Ubuntu forums and the administrators of the forum have disabled some features, like setting a thread to solved and the thanks option, to prevent problems with the database from happening again.

---

### Post by vandorjw on 2009-02-10
I have attached two videos of what happens. (The quality of them is very bad however and they are in 3gp format [cellphone])

Using Envyng, the driver 177 or 173 don't install properly.

Trying to install 177 or 173 on its own doesn't work due to something missing. So far, my solution to this problem is to stop using firefox.
It only happens when firefox is running, so I do not believe it is an issue with the card, just the driver.

Hopefully nVidia will release another driver soon.

Cheers - CC7

---

### Post by norwoods on 2009-02-12
you can install newer driver with synaptic from [https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa)

---

### Post by vandorjw on 2009-03-02
Thanks,
I found the same drivers on nvidia's main site.
Ever since, I have not crashed.

Cheers - CC7

---

