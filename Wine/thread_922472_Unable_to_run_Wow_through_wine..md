---
title: "Unable to run Wow through wine."
date: 2008-09-17
forum: Wine
---

### Post by Alfx on 2008-09-17
Greetings

-I have Wow installed on my windows partition(Which is mounted and I have full access to it through unbuntu)

-I installed wine in my add/remove program thing in linux

-When I try to run wow.exe nothing happens at all.

-When I try to run wowlauncher.exe, I see the world of warcraft logo, then it dissappear and nothing happens.

How I am supposed to know what went wrong without any error message!?


so how do I fix this?

---

### Post by Alfx on 2008-09-17
Greetings

-I have Wow installed on my windows partition(Which is mounted and I have full access to it through unbuntu)

-I installed wine in my add/remove program thing in linux

-When I try to run wow.exe nothing happens at all.

-When I try to run wowlauncher.exe, I see the world of warcraft logo, then it dissappear and nothing happens.

How I am supposed to know what went wrong without any error message!?


so how do I fix this?

---

### Post by EmanresuusernamE on 2008-09-17
For me, running anything with Wine can be flaky using the gui.  Open up a command prompt, and then cd into your wow directory, then run:

wine wow.exe

See if that helps.  Also make sure you configured wine:

winecfg

---

### Post by Alfx on 2008-09-17
> **EmanresuusernamE said:**
> For me, running anything with Wine can be flaky using the gui.  Open up a command prompt, and then cd into your wow directory, then run:

wine wow.exe

See if that helps.  Also make sure you configured wine:

winecfg

I tried with the terminal, didnt help.

How I am supposed to have wine configured to play wow?

---

### Post by EmanresuusernamE on 2008-09-17
It's mainly opinionated how you should setup wine to work with any programs.

Could you please post what happens after you type in wine wow.exe?

Use the wincfg command in your terminal to get the Wine Configuration program.  Head to the graphics tab, and setup your wine to no use a virtual desktop, I personally can't get wow to accept mouse or keyboard inputs if it uses a virtual desktop.  Also make sure in the Audio tab that you have a decent level of hardware acceleration, and at least one of the drivers checked.

This is where you'll have to start playing with it a bit.  I don't know of where else to play with the wine settings just yet, (so I'm hoping someone else on the forums here can point me in the right direction ;) ).

---

### Post by anotherdisciple on 2008-09-17
ummm... perhaps I'm mistaken, but I think you have to install it on your ubuntu partition through wine. wine accesses a wine C: drive and a wine registry... all of the information needed to run Wow is currently in a windows C: drive and a windows registry... it doesn't access those.

---

### Post by cj2003 on 2008-09-17
Sorry, I don't have direct answers for you, but you might find tips in one of these two how-to's

[World of Warcraft in Ubuntu -- the easysauce way]("http://ubuntu-news.net/modules/news/article.php?storyid=3912")

[Ubuntu, Wine and World of Warcraft]("http://ubuntu-news.net/modules/news/article.php?storyid=3912")

---

### Post by EmanresuusernamE on 2008-09-17
Pssst, those two links are the same.

---

### Post by Booga71 on 2008-09-17
This is the one I followed: 
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Works just fine under wine. Make sure you change your interface to opengl.

---

### Post by karlr42 on 2008-09-17
The problem seems obvious to me:  you can't do what you're trying, install WOW on a windows partition, then just run the .exe from Ubuntu and expect it to work. The .exe will try to find files like C:/Program Files/WOW/some_file, which you have on the Windows partition, but since the .exe is running under wine,*wine will try to find the file in it's own virtual file system, not your windows partition*, and obviously won't find them- killing the game. **Hence, you have to install WOW on your Ubuntu partition with wine!**

---

### Post by EmanresuusernamE on 2008-09-17
> **karlr42 said:**
> The problem seems obvious to me:  you can't do what you're trying, install WOW on a windows partition, then just run the .exe from Ubuntu and expect it to work. The .exe will try to find files like C:/Program Files/WOW/some_file, which you have on the Windows partition, but since the .exe is running under wine,*wine will try to find the file in it's own virtual file system, not your windows partition*, and obviously won't find them- killing the game. **Hence, you have to install WOW on your Ubuntu partition with wine!**

Eeeeent! Wrong, Wow doesn't look for a particular path to where it's installed at.  I haven't installed Wow on many of the machines I play it on.  You only have to copy it from one directory to another and then run it as normal.

---

### Post by karlr42 on 2008-09-17
Ah, in that case I'll defer to your greater knowledge, just it was my interpretation of the problem! Apologies :)

---

### Post by overdrank on 2008-09-17
duplicate [[COLOR="DarkRed"]Here[/COLOR]](http://ubuntuforums.org/showthread.php?t=922473)
Please do not create multiple threads on the same issue.

---

### Post by Booga71 on 2008-09-17
> **EmanresuusernamE said:**
> Eeeeent! Wrong, Wow doesn't look for a particular path to where it's installed at.  I haven't installed Wow on many of the machines I play it on.  You only have to copy it from one directory to another and then run it as normal.
True for WoW, but can wine *see* the Windows partition/installation? 

I copied my Windows installation over under the wine c, and configured it. I rather have two separate installations (one for Windows, one for ubuntu) then one that I use for all. I think it boils down to wine not being able to recognize the windows partition.

*Edit*: Just re-read the first post. Looks like you mounted things correctly. How far do you get in the login process? Or does just nothing happen?

---

### Post by Gokudan on 2008-09-17
Hi there!!

I run flawlessly wow under ubuntu 8.04 LTS, refer to these links:

[https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting]("https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting")


But, as someone said earlier, you can't expect a program to run on linux when it was installed over windows and it is on a different partition, you need to copy the entire directory and run it from you linux partition.

**NOTE:** If you are running Burning Crusade you need to update wow manually from 2.x to 2.4.x, unless you fully patched wow under windows. It simply won't run without being updated to 2.4.x first; after that it will update automatically with no problems.



BR's
Gokudan

---

### Post by EmanresuusernamE on 2008-09-17
:) Not all programs in Windows force an installation, I found that out on accident when I moved wow from one failing hard drive to another, but forgot to install it on the second hard drive.

Hope my earlier reply didn't come off as harsh.  I didn't mean it to be, honest. O:) (I just looked over it and realized that, my bad).

---

### Post by EmanresuusernamE on 2008-09-17
> **Booga71 said:**
> True for WoW, but can wine *see* the Windows partition/installation?
If you mount it first, it doesn't matter from what I can tell.  I just run Wow in Wine off of my windows partition directly.  Works like a charm. I'm not sure where he's stopping at, or what going on right now fully.  He hasn't posted the results of his wine wow.exe command yet. :|

I think Wine only looks at the virtual C: when you attempt to run a program that's not in the directory that you're currently in when using terminal.  Kinda like using the Run window, or the Start command.

---

### Post by Alfx on 2008-09-17
-I just copied my wow installation in unbuntu

When I try to run wow through the terminal through wine.

This is the errors I get:

wine "C:\Program Files\World of Warcraft\WoW.exe"
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000005

What does that means?

---

### Post by karlr42 on 2008-09-17
try ```
wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl
```

---

### Post by Alfx on 2008-09-17
> **karlr42 said:**
> try ```
wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl
```

```
darkalfx@Darkempire:~$ wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000005
darkalfx@Darkempire:~$ 
```

Thats what I get.
What do I do now?

---

### Post by EmanresuusernamE on 2008-09-17
Try out the wtf file tweak, as well as the registry tweak from this site:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329)

..........This is starting to seem hauntingly familiar....  Do you have wine set to act as Windows XP?

---

### Post by Alfx on 2008-09-18
> **EmanresuusernamE said:**
> Try out the wtf file tweak, as well as the registry tweak from this site:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329)

..........This is starting to seem hauntingly familiar....  Do you have wine set to act as Windows XP?

Probably? Does this make any difference??

---

### Post by EmanresuusernamE on 2008-09-18
Yeah, Wine will act flakey if it's not set properly.  It should give you the option to change which windows it's pretending to be on the first tab of Wine near the bottom.

---

### Post by Alfx on 2008-09-18
> **EmanresuusernamE said:**
> Yeah, Wine will act flakey if it's not set properly.  It should give you the option to change which windows it's pretending to be on the first tab of Wine near the bottom.

I grew tired of all this last night.

So I uninstalled unbuntu.




Then I installed back again,

Now Im able to actually run wow.(I did the reg fix and the config.wtf fix)

Only problem is,upon opening Wow my entire display becomes fractured and unintelligible. This issue does not resolve upon exiting the game, only when the OS is rebooted(alt+ctrl+backspace)

Now how do I fix this huh?

---

### Post by Sammi on 2008-09-18
What graphics card do you have?

---

### Post by Alfx on 2008-09-18
> **Sammi said:**
> What graphics card do you have?
I have an ATI radon 4870

I used envyNG to install the 8-6 drivers(its the only thing they let me install)

---

### Post by tuxinside on 2008-09-18
> **Alfx said:**
> I have an ATI radon 4870

I used envyNG to install the 8-6 drivers(its the only thing they let me install)

ATI cards are notorious for not working with Wine.

[http://www.wowwiki.com/Linux/Wine/Troubleshooting](http://www.wowwiki.com/Linux/Wine/Troubleshooting) 

This has a work around to get WoW working with ATI on Wine. Let me know if it helps, as it may help me decide on whether or not I'll be purchasing a 48xx series card.

---

### Post by Alfx on 2008-09-18
> **tuxinside said:**
> ATI cards are notorious for not working with Wine.

[http://www.wowwiki.com/Linux/Wine/Troubleshooting](http://www.wowwiki.com/Linux/Wine/Troubleshooting) 

This has a work around to get WoW working with ATI on Wine. Let me know if it helps, as it may help me decide on whether or not I'll be purchasing a 48xx series card.

None are these are the problem I am experiencing.

What I have is the "Checkboard Of Doom"

Unless I find a way to install the new ATI drivers, my graphic card is useless for any 3d games.

The only way I can install ATI drivers is through envyNG and it doesnt have the lastest drivers.

---

### Post by tuxinside on 2008-09-18
> **Alfx said:**
> None are these are the problem I am experiencing.

What I have is the "Checkboard Of Doom"

Unless I find a way to install the new ATI drivers, my graphic card is useless for any 3d games.

The only way I can install ATI drivers is through envyNG and it doesnt have the lastest drivers.

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by Alfx on 2008-09-18
> **tuxinside said:**
> [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

I have successfully installed the lastest binary drivers.

Everything works flawlessly now.

Im off to play Wow!

---

### Post by tuxinside on 2008-09-19
Let me know how it works. It'd be nice to have an alternative to nVidia for us Linux gamers.

---

### Post by Booga71 on 2008-09-19
> **Alfx said:**
> I have successfully installed the lastest binary drivers.

Everything works flawlessly now.

Im off to play Wow!
Kewl, what server are you on, maybe we can hook up some time and do some Linux instances :lolflag:

---

