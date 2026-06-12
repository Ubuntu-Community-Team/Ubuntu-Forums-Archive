---
title: "Flash plugin stopped working after update"
date: 2008-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by ExquisiteDeadGuy on 2008-02-04
I've been using 7.10 with Firefox and the Flash plugin for a while now. Yesterday the Ubuntu software update popped up telling me there was an update available for Flash.

Since then, I haven't been able to use Flash at all in Firefox 2.0.0.11. It says I need to install a plugin and when I follow the prompts to install it, it gives the error:  Package 'flashplugin-nonfree' is already installed

Anybody know what I need to do to get this working again?

---

### Post by Yellow Pasque on 2008-02-04
Try this in the terminal:
```
sudo apt-get remove flashplugin-nonfree
```
Now start FF and go to a site that uses Flash. The plugin should now install automatically.

---

### Post by ExquisiteDeadGuy on 2008-02-04
Worked great, thanks!

---

### Post by crjackson on 2008-02-04
Strange thing is this.  My system did the same thing, so installed the pluging using the kilz script.

Just for grins, I tried the sudo apt-get remove command, then went to youtube to test it out.  I was expecting to no flash.  I wanted to install using the browser just to see if it now worked.  Get this...  **I still have flash even after the remove command....**

---

### Post by crjackson on 2008-02-04
So now I used the autoremove command and killed the flash.  However, the browser also will no longer request to install the plugin either. I reinstalled the kilz script and flash is back again.

I then went into synaptic only to find that the flashplugin-nonfree wasn't installed from there.  I installed it too just to see the results.  Nothing changed.  Flash is working fine.

---

### Post by Yellow Pasque on 2008-02-04
> **crjackson said:**
> Strange thing is this.  My system did the same thing, so installed the pluging using the kilz script.

Just for grins, I tried the sudo apt-get remove command, then went to youtube to test it out.  I was expecting to no flash.  I wanted to install using the browser just to see if it now worked.  Get this...  **I still have flash even after the remove command....**
Did you happen to remember to restart your browser somewhere in between there?

---

### Post by crjackson on 2008-02-04
> **Temüjin said:**
> Did you happen to remember to restart your browser somewhere in between there?

Yeah, I did...  I also found that after using the script to install some flash sites worked and some didn't.  So what I did was to remove everything again, and install the pluginwrapper and the plugin through synaptic and flash plays on all the sites I tested.

What I couldn't get working again, was the prompt from firefox to install the plugin.  In fact, with the plugin removed, the browser would freeze when trying to load youtube or anyother flash enables site.  The browse would crash and / lock.  Only a force quit would close it.

I was trying to get my browser to prompt me for an install of the pluging and handle it automatically.  I wanted to see if it was working for myself.  I was disappointed to say the least...

---

### Post by Kilz on 2008-02-04
> **crjackson said:**
> Yeah, I did...  I also found that after using the script to install some flash sites worked and some didn't.  So what I did was to remove everything again, and install the pluginwrapper and the plugin through synaptic and flash plays on all the sites I tested.

What I couldn't get working again, was the prompt from firefox to install the plugin.  In fact, with the plugin removed, the browser would freeze when trying to load youtube or anyother flash enables site.  The browse would crash and / lock.  Only a force quit would close it.

I was trying to get my browser to prompt me for an install of the pluging and handle it automatically.  I wanted to see if it was working for myself.  I was disappointed to say the least...

I wonder what version of the script you installed? There was a lot of problems with r115. I hope we dont have these issues with the just released version in synaptic.

---

### Post by crjackson on 2008-02-04
> **Kilz said:**
> I wonder what version of the script you installed? There was a lot of problems with r115. I hope we dont have these issues with the just released version in synaptic.

Yeah, I was trying the r115 version (I know it has a buggy warning).  I was experimenting with different ways.  The only issue I've had since messing around is that firefox didn't prompt to install the plugin automatically anymore.  I had to do it through synaptic.  So far all the websites I've tried work fine with it.

---

### Post by vwm8534 on 2008-02-07
I had this problem on my desktop with Ubuntu 7.10.
I did the apt get remove, but when I go to a site with flash, there is no prompt to install.
My system will lock up when I try a flash site as well.
I am fairly new to linux/Ubuntu.
Any ideas? This all happened after I was prompted for system update.

---

### Post by utUtu on 2008-02-07
> **Kilz said:**
> I wonder what version of the script you installed? There was a lot of problems with r115. I hope we dont have these issues with the just released version in synaptic.

Still r115.

---

### Post by Kilz on 2008-02-07
> **utUtu said:**
> Still r115.

Well the r48 plugin is still available with my script if anyone has problems with r115.

---

### Post by vwm8534 on 2008-02-07
I got mine working again.
First I downloaded the tar.gz file from here:[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)
After extracting the folder, I directed the terminal to the newly downloaded folder and typed the following,(I renamed the folder install and placed it in /home/my name folder to make it easier to navigate to), now the command in the terminal: ./flashplayer-installer.
Hit enter and follow directions.

---

### Post by Kilz on 2008-02-07
> **vwm8534 said:**
> I got mine working again.
First I downloaded the tar.gz file from here:[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)
After extracting the folder, I directed the terminal to the newly downloaded folder and typed the following,(I renamed the folder install and placed it in /home/my name folder to make it easier to navigate to), now the command in the terminal: ./flashplayer-installer.
Hit enter and follow directions.

How did you generate the wrapper on your amd64 install? To my knowledge the flash installer from adobe does not work without a wrapper on a 64bit install.

---

### Post by BigDaddy-CF- on 2008-02-07
I may be wrong about this vwm8534 but the official adobe installer you refer to does not support the x86_64 platform. I saw that there was an update available for flash using the update dialog.  I have build a new 64 bit machine this week for a friend of mine and came across this same problem witht he latest version of flash in the repos(medibuntu gutsy repos added). As of this writing that is 9.0.48.0.2+Really0ubuntu12.1 package.  Having had problems with another 64 bit computer I built this weekI I backed up the two files  most important to flash before updating.  Namely /usr/lib/firefox/plugins/flashplugin-alternative.so and /usr/lib/flashplugin-nonfree/libflashplayer.so.  After the update everything seemed to work ok even after exiting and restarting firefox until that is I loaded up arstechnica.com after that flash didn't seem to work as it should meaning flash ads showed up pure white.  Copying the old libflashplayer.so over the new one seems to restore flash to its full glory.  Maybe this is a bug in the version of flash in the 64 bit repos I don't know

---

### Post by vwm8534 on 2008-02-08
Geez.

Sorry guys, I didn't realize I was in the 64 bit forum.
My goof.
I am running 32 bit and was having the same problem.

Thanks for straightening me out.:oops:

---

### Post by timzak on 2008-02-08
Here's what happened to me:

Installed the new flash from update manager.  Didn't try a flash site right away.  Later in the evening, went to youtube to watch some classic cartoons with my toddler son, got a message that flash wasn't installed or working properly.  Son doesn't have patience for me to fiddle with this, so when a window pops up for me to install Adobe flash or Gnash, I first choose Adobe.  Doesn't work.  So then I try Gnash.  It does work on youtube, but not as smoothly as I had it running before the update manager put its stick in my spokes.  Gnash doesn't work on some other flash sites I visit, but I can't figure out how to get rid of Gnash and get my Adobe flash working the way it was prior to update manager fiasco.

Running 64 bit Gutsy.

Any help appreciated.

Thx.

---

### Post by Footer on 2008-02-08
Glad I found this thread.  I just did an apt-get update/upgrade and saw that flashplugin-nonfree was going to get updated.  I said, "Uh oh" but did it anyway.  Boy am I sorry!  My flash has been working flawlessly for weeks (don't ask me how because I don't even know!) including numerous (almost daily) restarts of the browser and I couldn't have been happier until now.  Just get the white box now.  I've tried everything in this thread so far except the Kilz script (which I've used with success in the past) to no avail.  I'm running Kubuntu 7.10 64 bit and actually Swiftweasel 3 Beta 2 instead of FF but I'm testing with FF as Swiftweasel behaves accordingly.

I'll give the Kilz script a try but if anyone comes up with a permanent fix, it would be GREATLY appreciated!

Thanks!

---

### Post by Thelasko on 2008-02-08
So, Yesterday I received a message from the update manager that I need to update Flash.  What should I do?  Does everyone have this problem, or is it just a few isolated incidents.?

---

### Post by Kilz on 2008-02-08
Update if you want, if flash stops working, run my script.

---

### Post by Footer on 2008-02-09
Kilz -- you're my hero once again!  Ran your script (the stable one) and all is well again with flash on 64 bit!  WHOOHOO!!!

Seems that it's related to /usr/lib/flashplugin-nonfree/libflashplayer.so  Before running your script again, I found a really old copy of libflashplayer.so (12/17/2006) which I replaced with the one that the recent update put in there (2/8/2008 in my case) and then fired up FF and low and behold, it worked!  But I decided to try your script anyway and sure enough that file was replaced with one dated 6/19/2007 and flash seems to be working fine now again.

So whatever the recent update did, the file libflashplayer.so is critical and the new one with the update screws up flash.  But your script replaces it with a working one and saves the day!

Thanks again!!!

---

