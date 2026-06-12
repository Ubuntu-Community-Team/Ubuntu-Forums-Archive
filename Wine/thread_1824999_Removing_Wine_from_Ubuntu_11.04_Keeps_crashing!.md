---
title: "Removing Wine from Ubuntu 11.04??? Keeps crashing!"
date: 2011-08-14
forum: Wine
---

### Post by yallaen on 2011-08-14
Ok, I was starting to get the hang of Ubuntu, even started liking it, until this :(

I d/l'ed a file to help me study for a certification exam. Without realizing it, the program is for Windows. So, someone at work knew my PC's HDD had blown up, and I had reformated and have been running Ubuntu until my disks get here. No problem he says...just load Wine! It is used to run Windows applications on Linux or Ubuntu! (And Wine is NOT an emulator he joked).

So, I did some google research, did some reading, and I tried the Software Center. I ended up using terminal mode and installing Wine 1.3 via terminal.

However, once it was installed, and I "think" configured correctly, I tried to run  this .exe file. I would right click it, and told it to install with Wine...it started to install, then aborted. 

I tried again, and it said there was already an instance of setup running. I tried rebooting several times, and trying to reinstall this .exe file. No luck. 

So, I decided to just uninstall Wine. In the Installed Software section, there was an icon for "Uninstall Wine". I tried using that; no go. I also tried in Software Center>Installed Software going to Wine and removing. I keep getting an unhandable exception error msg. 

Well, then I read somewhere that if I installed it via terminal, I had to remove it from terminal. I did the sudo apt-get remove or something similar wine 1.3..and it came up with an error. 

I just want to remove it from my computer so I can try and reinstall. Thoughts?

I've attached screenshots so you can see what's being displayed as I try to remove Wine.

---

### Post by Mrunalinee on 2011-12-14
Hi, I did the same thing and got the same result.
Then I tried the command " sudo apt-get remove wine1.3" (1.3 is the wine version that I installed)
I got some error along with a tip. Use ......... to solve the problem. Actually it was some configuration changing command which ends with "-a".
I used that and then I ended up with loads of problems.. I was not able to install and uninstall any software, not even able to upgrade..

Then I restarted the system using recovery mode and repaired the broken files. Thats it, now everythings fine.

But, actually I don't know whether this is the right way or not. But I didn't have any other option from the internet too..

---

### Post by Soulcage on 2011-12-14
Uninstalling wine probably won't do anything for you, you should try this instead [http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa]("http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa")

---

