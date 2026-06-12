---
title: "flash player 9 doesn't work after reboot"
date: 2007-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Michele84 on 2007-02-18
hI! I installed flash player 9 with npluginswrapper following this how to: [http://www.ubuntuforums.org/showthread.php?t=341727&highlight=flash+player+64+bit](http://www.ubuntuforums.org/showthread.php?t=341727&highlight=flash+player+64+bit). I tried to watch a youtube video and it works! But If I reboot the OS it doesn't work more! How can I fix this problem?
thanks!

---

### Post by John Jason Jordan on 2007-02-18
> **Michele84 said:**
> hI! I installed flash player 9 with npluginswrapper following this how to: [http://www.ubuntuforums.org/showthread.php?t=341727&highlight=flash+player+64+bit](http://www.ubuntuforums.org/showthread.php?t=341727&highlight=flash+player+64+bit). I tried to watch a youtube video and it works! But If I reboot the OS it doesn't work more! How can I fix this problem?
I had the same problem. Even closing Firefox and restarting it caused Flash to stop working.  This is a copy and paste from a post in another thread where I got it working:

```
Quote:
Originally Posted by Footer View Post
That fixes it. For how long, I don't know. But it's not too much trouble to run that command so I'll go with it for now! Thanks!
I now have a workaround that enables me to have flash working always in 64-bit Firefox 2.0, even after shutting it down and restarting it. First, I did the following per pinguin's instructions:
Code:

move the 2 files &#8220;libflashplayer.so&#8221; and &#8220;flashplayer.xpt&#8221; from /usr/lib/mozilla/plugins folder to /usr/lib/firefox/plugins folder then in terminal run: nspluginwrapper -v -a -i

After doing that it worked great, but the minute I shut down Firefox and restarted it, flash no longer worked. Eventually I learned all I needed to do is run the last line as a command in a terminal. Even if Firefox was already launched, that was enough to get it to work again.

So I made myself a bash script that runs the above command and then launches Firefox. To emulate what I did, open Gedit (or whatever you use for a text editor) and paste in the following lines:
Code:

#!/bin/bash 
nspluginwrapper -v -a -i firefox

Save the file as firefox_launch_script in your home folder. Open Nautilus, right click on the file and select Properties. In the Properties window check on the box to make it an executable file.
Now change the launch command in your launch menu item or icon on the panel that you use to launch Firefox. Where it says "firefox %u" change it to read "/home/<your_user_name>/firefox_launch_script."
From now on when you click to launch Firefox it will run the command first, then launch Firefox.
It's kind of a clunky workaround, but it does work and Flash is always working now in 64-bit Firefox.
```

Hope that gets it working again for you.

---

### Post by Michele84 on 2007-02-18
Hi J.J.J...and thanks! It works for me...I read it before you advise me...but thanks again!!! Just one more thing..what about java? Did you install it? if yes, how did you do? I'm running a 1.4.2 version...but it seems that doesn't work on 64 bit Firefox...any suggestion? I read that someone suggest to switch to a 32 bit firefox version.... 
Bye!

---

### Post by Kilz on 2007-02-18
> **Michele84 said:**
> Hi J.J.J...and thanks! It works for me...I read it before you advise me...but thanks again!!! Just one more thing..what about java? Did you install it? if yes, how did you do? I'm running a 1.4.2 version...but it seems that doesn't work on 64 bit Firefox...any suggestion? I read that someone suggest to switch to a 32 bit firefox version.... 
Bye!

The problem is that nspluginwrapper is still beta software. Some sites will cause your browser to crash. This doesnt happen with a 32bit browser.

---

### Post by John Jason Jordan on 2007-02-18
> **Michele84 said:**
> Hi J.J.J...and thanks! It works for me...I read it before you advise me...but thanks again!!! Just one more thing..what about java? Did you install it? if yes, how did you do? I'm running a 1.4.2 version...but it seems that doesn't work on 64 bit Firefox...any suggestion? I read that someone suggest to switch to a 32 bit firefox version.... 
Bye!
I have two Javas installed, Sun and the Blackdown 1.4.2 version that you have. But the only one I use with Firefox is the Blackdown one. I haven't had any problems with crashes or anything. I use the Sun Java with OpenOffice.org and also for a small utility that I use for linguistics syntax work. 

Unfortunately, I don't recall exactly how I installed Blackdown in Firefox. It might be under Edt > Preferences. Or maybe Synaptic did it when I installed it.

---

