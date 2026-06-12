---
title: "Possibly stupid question involving Firefox 3.5 and Flash"
date: 2009-10-14
forum: x86 64-bit Users
---

### Post by Algus on 2009-10-14
So I've been trying to get Flash working in Firefox 3.5.3.  Tried everything, every walkthrough guide I could find and checked this forum and read some relevant threads.

Now, am I understanding that THIS is my problem - Firefox 3.5 is "32 bit" and as such won't use the 64-bit stuff? 

I choose to update as some of the add-ons I like got updates that I wanted.  If I want flash am I looking at "rolling back" to the Ubuntu 3.0 version of Firefox (whatever) and getting flash that way?

---

### Post by imigueldiaz on 2009-10-14
Hi! 

Yesterday I was all evening probing karmic solution (nspluginwrapper + flash 10 32 bits) on FF 3.5 and It produces bizarre situations with some flash sites like megavideo, the buttons on the control don't work at all.

When I installed ALPHA 64 bits version from Adobe Labs I had to reboot completely the machine to make it work (I' still don't know the technical reason for it) and It works but seems to crash FF 3.5.3 with segmentation faults ramdomly (using megavideo fullscreen).

Today I'll try with FF daily builds and FF 3, to compare the behaviour.

Have any of you any good method to do the tests or wants me to do any specific test?

---

### Post by hal10000 on 2009-10-14
> Now, am I understanding that THIS is my problem - Firefox 3.5 is "32 bit" and as such won't use the 64-bit stuff?

Why don't you install the 64 bit version with your package manager, it's called shiretoko:

[COLOR="Red"]sudo apt-get install shiretoko
sudo apt-get install flashplugin-nonfree[/COLOR]

---

### Post by nzadLithium on 2009-10-14
hal u sure about that?

shiretoko does not appear in my package lists. Firefox however does.

algus, you should probly check whether firefox is 64bit or 32bit on your pc. Unless you specifically tried to install the 32bit version your probably running the 64bit one.
To check that open firefox click help then about shiretoko
Near the bottom of the windows is a scroll bar look to the left of that and it should say something similar to:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.5pre) Gecko/20091007 Ubuntu/9.04 (jaunty) Shiretoko/3.5.5pre
If it shows that Linux x86_64; then your running the 64bit if it says i686 instead there then your running the 32bit version.

If your runnning 32bit firefox:
sudo apt-get install firefox
sudo apt-get install flashplugin-nonfree
That should install the 64bit version with flash.

If your running the 64bit version just do:
sudo apt-get install flashplugin-nonfree

The only reason you would be running the 32bit version is either your actually using 32bit ubuntu, or you installed the 32bit version yourself, the 64bit version of ubuntu comes with 64bit firefox :D

---

### Post by kixome on 2009-10-14
flash never crashed n slamd/slackware64

---

### Post by nzadLithium on 2009-10-14
lol well its never crashed for me either :p

---

### Post by hal10000 on 2009-10-14
> shiretoko does not appear in my package lists. Firefox however does.

Yes you are right, it's called firefox-3.5, so it has to be 
[COLOR="Red"]sudo apt-get install firefox-3.5[/COLOR]

---

### Post by bford16 on 2009-10-14
I have been using Firefox-3.5 (Shiretoko) 64-bit, with the 64-bit Flash from Adobe Labs, for quite some time now. Both work just fine on my 3 Ubuntu machines.  I didn't have to do anything weird to install them, either.  I just followed instructions (found 'em on Google).

For the 64-bit Flash from Adobe Labs,

1. Remove all installed versions of Flash first
2. Download and extract the 64-bit Flash plugin
3. Close all open browser windows.
4. Manually install the plugin (libflashplayer.so) in the /usr/lib/mozilla/plugins folder.```
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so
```

---

### Post by Algus on 2009-10-14
> **nzadLithium said:**
> hal u sure about that?

shiretoko does not appear in my package lists. Firefox however does.

algus, you should probly check whether firefox is 64bit or 32bit on your pc. Unless you specifically tried to install the 32bit version your probably running the 64bit one.
To check that open firefox click help then about shiretoko
Near the bottom of the windows is a scroll bar look to the left of that and it should say something similar to:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.5pre) Gecko/20091007 Ubuntu/9.04 (jaunty) Shiretoko/3.5.5pre
If it shows that Linux x86_64; then your running the 64bit if it says i686 instead there then your running the 32bit version.

If your runnning 32bit firefox:
sudo apt-get install firefox
sudo apt-get install flashplugin-nonfree
That should install the 64bit version with flash.

If your running the 64bit version just do:
sudo apt-get install flashplugin-nonfree

The only reason you would be running the 32bit version is either your actually using 32bit ubuntu, or you installed the 32bit version yourself, the 64bit version of ubuntu comes with 64bit firefox :D

Thanks for the reply! 

I actually ~am~ running the 32 bit version (I do have 64 bit Ubuntu though).  I couldn't figure out how to update Firefox earlier and was googling solutions.  The solution I found told me how to get this version.  It must have been out of date or something?  

I'm going to go back and follow the advice you gave to get the 64-bit version on my comp (since it seems like a good idea) but for anyone that is interested I actually ~did~ find a solution to my problem after I posted this thread.

I ended up getting the tar.gz archive of the 32-bit plugin and unpacked it to .mozilla/plugins and after that my flash started working.  

Thanks a lot guys.  I'll edit this post with a followup if I can get everything working.

edit: Alright, well I ran the commands you guys gave me and each time they were installing the 32 bit version of Firefox 3.5 on my system.  Query - could my addons be causing some sort of crisis here? Is there a good way to wipe my system of any and all firefox related files on it so I can do a "clean" install? (Do I even need to do this?) 

Also I ran uname -a (even though I KNEW it was 64 bit since I only burned a 64 bit disc lol) just to be safe and predictably

```
Linux curtis-laptop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux
```

edit #2: Well after playing around with it some more I'm thinking that part of my problem is that I've got some scripts and such installed (I was using ubuntuzilla as my google searches pointed me in that direction) that are interfering with my ability to get different versions of the browser as even if I try add/remove (and tell it to install 3.0) and such it is giving me 3.5.3 32-bit

Final Edit: 

Ok, I managed to get ubuntuzilla uninstalled.  It was what was forcing 32-bit Firefox on me

I can now get the 64 bit version of Firefox, however I can only seem to get version 3.0.14.  I've tried the various commands you guys gave me but they all seem to want to install 3.0.  

I'm wondering if I should just tough it out for now and forego the addons I like that are wanting me to update to 3.5  Good news is that flash DOES work so I guess I just have to take the good with the bad.  There might be something else conflicting on my system of course from all the workarounds I was trying to get 3.5 

Anyway thanks for the help guys.  This has been a mess for me lol

---

### Post by hal10000 on 2009-10-14
> I can now get the 64 bit version of Firefox, however I can only seem to get version 3.0.14. I've tried the various commands you guys gave me but they all seem to want to install 3.0.

You need to activate the universe repositories to install firefox-3.5

---

### Post by Algus on 2009-10-14
lol, well my problem, at least at the end, was that I was running the wrong program! (FF 3.0 instead of Shiretoko) 

So yeah, basically I've just demonstrated that I am a gigantic noob 

Anyway, I ended up doing a fresh install, made the setting adjustments recommended, and it looks like everything is up and running.  

Thanks a lot for your help guys.  It's all working correctly now.  

Of course now that I've got it right, I find that FEBE is having issues so importing all my settings is going to be a pain =(

---

