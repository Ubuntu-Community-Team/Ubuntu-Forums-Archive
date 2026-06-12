---
title: "Installing League of Legends"
date: 2013-01-18
forum: Wine
---

### Post by Hamsamwich on 2013-01-18
Hello,

I Have been trying to install League of Legends using this guide [http://na.leagueoflegends.com/board/showthread.php?t=2107392](http://na.leagueoflegends.com/board/showthread.php?t=2107392)


I have gotten to step III B. (Play LoL) and am getting the following error after running the SH file.

The program rads_user_kernel.exe has encountered a serious problem and needs to close. We are sorry for the invoncenience (the details are in an attached document below).

I have checked to make sure I have done all of the steps properly, and have googled as much as I can to try to find the answer, and have had no luck.

Any idea what is causing this?

---

### Post by Lightning Dragon on 2013-01-19
Hello,

Which version of wine are you currently running? I realize that the guide says to use "1.5.3" but from my own experience on several distros, it is unstable and often never works for me. But what works for him or even myself could very well not work for you. I don't know why it is, but it just happens. My first form of advice is to downgrade the wine version to a stable version like 1.3 or 1.4, and then install LoL again. 

However, when I helped my friend (*so please, if you are uncomfortable about this, please do not continue*) get this to run, it was because of installing problems and it looks like something did not install right for winetricks for you. 

Go to your System Monitor and make sure all instances/processes of LoL have been ended, next please install vcrun2005, corefonts and the DLLs listed in that thread as root ("admin"). Also, if you encounter the log in disappearing or whatnot afterward, please install net 1.1 the same way and d3dx9_XX dlls.

Next, restart the computer. Now attempt to re-run the game. Make sure the patches have been applied. 

Please report problems should you attempt my solutions and I will offer all the assistance I can muster up. 

*I also, highly, suggest installing with PlayOnLinux. Or trying to.

---

### Post by Hamsamwich on 2013-01-19
Thanks for the help, although I don't have it working yet (I don't have the time At the moment, and won't for a few hours. But one thing I just realized, I never installed the patches, and am not really sure what to do with the patch files (and the dll.so files)

---

### Post by jerome1232 on 2013-01-19
Did you do it the hard way (self patching) or the easy way (Playonlinux)


I Highly advice that you use playonlinux. It automatically does the dirty work and does it in a wine bottle so it doesn't affect (effect? I always get those wrong) your other wine programs.

---

### Post by Hamsamwich on 2013-01-19
I definitely did it the PlayOnLinux way, and I just realized those patches were in the "hard way" section, my bad!

Also, I am using wine 1.5 I believe, and will try downgrading it to 1.3/1.4 in a little bit, along with reinstalling.

---

### Post by Hamsamwich on 2013-01-19
I made a new wineprefix directory, made sure everything was installed, reinstalled LoL and used wine1.3.26 instead of 1.5.3 and I got the same error, however, it now says League of legends in the middle of the screen (linked below). It apears after I hit the "okay" thing for the error report, which does not have options to "Show details".

---

### Post by Lightning Dragon on 2013-01-19
Hello,

I guess that is an improvement, right? So you ran the patches, correct? Here, try the following link's tutorial, but only following from "Step 2: Installing Winetricks Extras" onward, and tell me if that changes anything.

[http://na.leagueoflegends.com/board/showthread.php?t=2957372](http://na.leagueoflegends.com/board/showthread.php?t=2957372)

---

