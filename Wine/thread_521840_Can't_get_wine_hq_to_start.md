---
title: "Can't get wine hq to start"
date: 2007-08-09
forum: Wine
---

### Post by hyg71886 on 2007-08-09
This is my 1st day with Ubuntu Linux, I have everything running good except a good wma music player. But I installed wine hq(at least thats what the screen said), but i cant find it anywhere. I dont even know how to run the program. I tried to use the guide at [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)
but i couldnt get it. Can anyone help?

---

### Post by cogadh on 2007-08-09
Wine isn't really a program that you can run, it's just a compatibility layer that allows Windows apps to run in Linux. Click on the "Stuff I've learned about Wine" link in my sig for more information.

---

### Post by hyg71886 on 2007-08-09
> **cogadh said:**
> Wine isn't really a program that you can run, it's just an emulation layer that allows Windows apps to run in Linux. Click on the "Stuff I've learned about Wine" link in my sig for more information.

excuse the dumbass question but, I read ur thread, and im still lost. I dont even know how to start the prog:confused:. Forgive the slowness this is my first day with ubuntu linux i had to skip my workout for yesterday and today just to get my laptop where its at now.

---

### Post by cogadh on 2007-08-09
I guess the first step is to ask what Windows application do you want to run in Linux?

---

### Post by hyg71886 on 2007-08-09
> **cogadh said:**
> I guess the first step is to ask what Windows application do you want to run in Linux?

Half life which means i have to run steam, also myspace im, o media monkey cuz all the media players i tried for linux sucks

---

### Post by cogadh on 2007-08-09
You don't like to start with easy things, do you. :) Okay, lets start with Steam.

The first thing you need to do is download the Steam client installation (SteamInstall.msi). I recommend saving it to your home folder. Once you have downloaded it, do this in a terminal to start the install:
```
wine msiexec /i SteamInstall.msi
```
The install should progress just as it does in Windows. After the install, Steam will launch and may fail to update at 26%, if it does, do this:
```
wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```
Once you've got it installed, post back and we'll move on to the rest. I may not be available to help for much longer, but there are plenty of people on these forums who can assist further.

EDIT - I just did a check on Wine's AppDB (the Wine Application Database) and both MySpace IM and Media Monkey won't run in Wine. There are plenty of IM alternatives available on Linux, but I don't know if they are compatible with whatever protocol MySpace uses. As for a media player, there are literally dozens of alternatives available on Linux, but they do require you to install some proprietary codecs before they will support wma playback. If the files you are trying to play have DRM applied to them, you won't be able to play them at all in Linux.

---

### Post by hikaricore on 2007-08-09
> **hyg71886 said:**
>  media monkey cuz all the media players i tried for linux sucks

Errmm... what exactly do you expect out of a media player?  There's dozens of amazing cross-platform audio and video players in existance.  Many of them are in the repos.

---

### Post by hyg71886 on 2007-08-09
> **cogadh said:**
> You don't like to start with easy things, do you. :) Okay, lets start with Steam.

The first thing you need to do is download the Steam client installation (SteamInstall.msi). I recommend saving it to your home folder. Once you have downloaded it, do this in a terminal to start the install:
```
wine msiexec /i SteamInstall.msi
```
The install should progress just as it does in Windows. After the install, Steam will launch and may fail to update at 26%, if it does, do this:
```
wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```
Once you've got it installed, post back and we'll move on to the rest. I may not be available to help for much longer, but there are plenty of people on these forums who can assist further.

EDIT - I just did a check on Wine's AppDB (the Wine Application Database) and both MySpace IM and Media Monkey won't run in Wine. There are plenty of IM alternatives available on Linux, but I don't know if they are compatible with whatever protocol MySpace uses. As for a media player, there are literally dozens of alternatives available on Linux, but they do require you to install some proprietary codecs before they will support wma playback. If the files you are trying to play have DRM applied to them, you won't be able to play them at all in Linux.

After the 26% thing happened i did step 2 and got this

hyg71886@Vanessa:~$ wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
wine: could not load L"c:\\windows\\system32\\SteamTmp.exe": Module not found

---

### Post by cogadh on 2007-08-10
I was afraid that might happen. Do you have Steam installed on a Windows machine already?

---

### Post by hyg71886 on 2007-08-10
> **cogadh said:**
> I was afraid that might happen. Do you have Steam installed on a Windows machine already?

no, all i have is linux now

---

### Post by cogadh on 2007-08-10
Okay, then let's try this. Open up the file browser and hit CTRL+H to show hidden files. Look for the .wine directory and go to .wine/drive_c/Program Files/Steam. Once you are there, look for a file called "ClientRegistry.blob" and delete it. Then open a terminal and re-run this:
```
wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```
Post back with your results.

---

### Post by hyg71886 on 2007-08-10
nother mind im workin on it

---

### Post by hyg71886 on 2007-08-10
> **cogadh said:**
> Okay, then let's try this. Open up the file browser and hit CTRL+H to show hidden files. Look for the .wine directory and go to .wine/drive_c/Program Files/Steam. Once you are there, look for a file called "ClientRegistry.blob" and delete it. Then open a terminal and re-run this:
```
wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```
Post back with your results.

i dont see any thing that says .wine, am i looking in the wrong place

---

### Post by cogadh on 2007-08-10
Sorry, I should have specified; open your file browser in your home folder, that's where you will find the .wine directory.

---

### Post by hyg71886 on 2007-08-10
I did it in this is what i got

hyg71886@Vanessa:~$ wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
wine: could not load L"c:\\windows\\system32\\SteamTmp.exe": Module not found
hyg71886@Vanessa:~$ wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
wine: could not load L"c:\\windows\\system32\\SteamTmp.exe": Module not found

---

### Post by cogadh on 2007-08-10
Try this:
```
cd .wine/drive_c/Program\ Files/Steam
wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```
If that doesn't work, then we have hit the same brick wall I hit when trying to install Steam, which forced me to copy my Steam install off of my Windows partition (hence why I asked you about a Windows install). Supposedly one or both of the things I have told you to do will correct the 26% update problem, but they never worked for me. Maybe one of the other Steam users on the forum can help with it, but if this last one doesn't fix it, I'm out of ideas.

---

### Post by Zylar on 2007-08-10
According to [this thread]("http://ubuntuforums.org/showthread.php?p=1580033"), try:

wine "C:\Program Files\Steam\SteamTmp.exe" SelfUpdate "C:\Program Files\Steam\Steam.exe" 14

Also, have you run winecfg in a terminal to create the fake c: (~/.wine/drive_c)?

Edit: Yeah, Cog's above post does pretty much the same thing as I mention here.  I'll leave it to the master, never even tried steam myself.

---

### Post by hyg71886 on 2007-08-10
ok i just ran it for the first time lol sorry just figured out how to, i put in both codes and this is what i got

hyg71886@Vanessa:~$ cd .wine/drive_c/Program\ Files/Steam
[email]hyg71886@Vanessa:~/.wine[/email]/drive_c/Program Files/Steam$ wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
wine: could not load L"c:\\windows\\system32\\SteamTmp.exe": Module not found
[email]hyg71886@Vanessa:~/.wine[/email]/drive_c/Program Files/Steam$ wine "C:\Program Files\Steam\SteamTmp.exe" SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
wine: cannot find 'C:\Program Files\Steam\SteamTmp.exe'
[email]hyg71886@Vanessa:~/.wine[/email]/drive_c/Program Files/Steam$ winecfg
[email]hyg71886@Vanessa:~/.wine[/email]/drive_c/Program Files/Steam$ winecfg
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
[email]hyg71886@Vanessa:~/.wine[/email]/drive_c/Program Files/Steam$
[email]hyg71886@Vanessa:~/.wine[/email]/drive_c/Program Files/Steam$ wine "C:\Program Files\Steam\SteamTmp.exe" SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
wine: cannot find 'C:\Program Files\Steam\SteamTmp.exe'
[email]hyg71886@Vanessa:~/.wine[/email]/drive_c/Program Files/Steam$ cd .wine/drive_c/Program\ Files/Steam
bash: cd: .wine/drive_c/Program Files/Steam: No such file or directory
[email]hyg71886@Vanessa:~/.wine[/email]/drive_c/Program Files/Steam$ wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
wine: could not load L"c:\\windows\\system32\\SteamTmp.exe": Module not found
[email]hyg71886@Vanessa:~/.wine[/email]/drive_c/Program Files/Steam$

---

### Post by Zylar on 2007-08-10
Might want to start over, it kinda looks like SteamTmp.exe isn't there.  

-Open you home folder, click View -> Show hidden files.  
-Delete the .wine folder. 
-Open a terminal and run winecfg.  
-Then pick back up at: wine msiexec /i SteamInstall.msi

This is all the help I can provide for now.  Getting on the road for a while.  

Good luck,

---

### Post by hyg71886 on 2007-08-10
thanks i actually also just found my xp pro, media center, etc cds lol. il try thst n see what happens

---

### Post by hyg71886 on 2007-08-10
no good, i did everything u said n stil got the same messages in terminal.

---

