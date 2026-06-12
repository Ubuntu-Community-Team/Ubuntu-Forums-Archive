---
title: "Games almost starting"
date: 2012-12-10
forum: Wine
---

### Post by MrGrim48 on 2012-12-10
Hi,

I've recently become a ubuntu user on my laptop with 12.10
I managed to install steam through wine and installed Half Life 2 to try out but with little to no results.
When I attempt to start the game, it shows up in what I would assume is the taskbar for 5-10 seconds and then, nothing.

Is there something I am missing?
Does my graphics card driver have any affect in the results?

---

### Post by Tweak42 on 2012-12-11
> **MrGrim48 said:**
> Hi,

I've recently become a ubuntu user on my laptop with 12.10
I managed to install steam through wine and installed Half Life 2 to try out but with little to no results.
When I attempt to start the game, it shows up in what I would assume is the taskbar for 5-10 seconds and then, nothing.

Is there something I am missing?
Does my graphics card driver have any affect in the results?

I don't have steam or half life 2 but there are many reports of people getting it working with and without steam.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2095](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2095)
 
Yes, the graphics card driver is critical, but we need to know what graphics hardware and which driver you are running.

---

### Post by MrGrim48 on 2012-12-12
I have been doing a bit more reading and am to believe that the graphics driver is the cause.
My laptop has Nvidia GT 525M graphics and having the current driver did not seem to work.

I tried downloading the Nvidia 713(Can't remember the exact number) which according to the software centre should support the 5 series.
However I received error messages which I think, according to other people, would be an issue with xorg server or something.

So I attempted to downgrade the xorg server thing which seemed to be fine then tried to install the 713 driver manually which I don't think ended in my favour.

In the end I ended up with a graphics driver that didn't solve my initial problem and no clue how to uninstall it.

Perhaps I should mention that nothing comes up in the additional drivers thing.

Edit: Since I've been having little success with this I will my laptop running windows 7 again and will try dual booting ubuntu on my desktop.

---

### Post by Tweak42 on 2012-12-12
> **MrGrim48 said:**
> I have been doing a bit more reading and am to believe that the graphics driver is the cause.
My laptop has Nvidia GT 525M graphics and having the current driver did not seem to work.


You didn't state your laptop model, but I'm going to take a guess that you are using one with a hybrid Intel/Nvidia Optimus video implemetation.  If that is the case the intel video is used for normal operation and to use the nvidia you would need to specifically install and setup bumblebee and nvidia drivers to utilize the nvidia chip only when launching games.  It is abit of a hack solution but it's either that or just not using nvidia under linux.  Nvidia is supposed to be working on an offical optimus on linux solution.

Here's a guide for setting up optimus on linux:
[http://www.howtogeek.com/124685/how-to-make-nvidias-optimus-work-on-linux/](http://www.howtogeek.com/124685/how-to-make-nvidias-optimus-work-on-linux/)

---

