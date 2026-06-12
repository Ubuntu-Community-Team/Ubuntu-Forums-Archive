---
title: "latest AMD updated killed ubuntu"
date: 2006-09-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by kinkdxm on 2006-09-14
i got home today and saw that i had an update that needed done.
there was only 1 update.
something along the lines of "generic AMD processor" something...
did the 1 update and it said i had to restart ubuntu.
went ahead and restarted.
after it booted there was a blue/red/white error messages about X not loading... 
and then it took me to a non-gui (command prompt?) 
screen which allowed me to log in but i have no clue what to do with out a gui.
any one know how to fix this thanks?

---

### Post by kuja on 2006-09-14
Try running startx, perhaps your video drivers are out of date. See if it gives you any error messages. Are you using nvidia-glx or fglrx by chance, I know at least with nvidia- a kernel update will break it unless you update the nvidia-glx too.

---

### Post by kinkdxm on 2006-09-14
> **kuja said:**
> Try running startx, 
i'll try and figure out how to do that.

> **kuja said:**
>  Are you using nvidia-glx or fglrx by chance, I know at least with nvidia- a kernel update will break it unless you update the nvidia-glx too.
i do have a nvidia card so i guess i'm using the nvidia-glk. there is a spash screen that is displayed when i log in that shows nvidia. wouldn't the update for nvidia-glx have show up in the update manager thing?

thanks for the reply!

edit i guess this is how you fix it

> Yes, there was a screw-up with the latest kernel update and if you had nvidia or fglrx drivers. It was caught within an hour of the update being posted, the update was immediately yanked off the servers, and within another hour or so an update was posted that resolved the problem.

I have posted a front-page announcement on the forums to aid users in recovering from the problem. A better link for this article would be: [http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459)

---

### Post by sailors on 2006-09-15
I lost my sound"card" with that update.....](*,)

---

### Post by stephensheppard on 2006-09-16
I have a similar problem with the latest update. I also have an nVidia card, running ubuntu AMD64 on a dual processor Dell. I had everything working reasonably well (after spending a couple weeks fussing to get it working). Today I followed the recommendation and installed updates. They seem to have trashed the video so that X and GTK won't load.

Is there an easy way to undo the "upgrade"? Is there an easy way to fix the video (the envy script was what helped me get it working before)? Or (given that this isn't a hobby and I do have work to do) should I just chalk it up to experience and be glad I didn't delete my Windows XP partition? 

I would really welcome any suggestions.:(

---

### Post by kuja on 2006-09-17
stephenssheppard, if you used the envy script and did an upgrade, it's possible that maybe the small kernel update would have broken it. This leaves you with two options really. You can either re-run the envy script, which is something that you have to do after every single kernel update. Otherwise, you can run run ```
sudo apt-get install nvidia-glx
``` which should keep itself in sync with the kernel updates.

---

### Post by stephensheppard on 2006-09-17
Kuja,
Thanks! Running the envy script again put me back on the road. I just didn't realize I had to run it each time I do a kernel upgrade. 
Cheers,
Steve

---

### Post by rgcrowley on 2006-09-17
Same problem here, this is the second time in a  month that an update has crashed one of my computers.

I tried to update the nvidia and it seemed to complete but I still have no x server.

Not sure what the envy script is.

---

### Post by missmoondog on 2006-09-17
yes, what is an envy script? 

if that update was pulled within an hour of being released, then the newest update is still screwed up. over the course of the days since that update was released, i've updated all 7 of my machines. everyone one of them has gotten foobarred somehow, including the machine i just got updated this morning. not all of them have nvidia either, so it's not just that.

---

### Post by kuja on 2006-09-17
> **missmoondog said:**
> yes, what is an envy script? 

if that update was pulled within an hour of being released, then the newest update is still screwed up. over the course of the days since that update was released, i've updated all 7 of my machines. everyone one of them has gotten foobarred somehow, including the machine i just got updated this morning. not all of them have nvidia either, so it's not just that.
envy is a script, written by, I think, tseliot on this forum, that installs the latest nvidia drivers.

---

### Post by kick6 on 2006-09-18
Apparently there are several different packages (mostly nonfree kernel modules) that are kernel dependent that aren't getting updated with the new kernel.  If you know you have nonfree kernel modules (the obvious example is the nvidia-glx) be prepared to updated these packages as well to return functionality.

---

### Post by missmoondog on 2006-09-18
apparently there are SEVERAL screwed up packages, as i now have 7 different machines, that all have something screwed up on them, or did, since these latest updates. :(

---

