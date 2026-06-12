---
title: "Age of Empires 3 III + Wine"
date: 2006-08-31
forum: Wine
---

### Post by Senathon on 2006-08-31
I am trying to install Age of Empires 3 III with Wine. When I run setup.exe the installaion allows me to choose what installation(typical and custom) and just freezes on my screen and when I try to kill the app the screen does not go away.

There are no errors.

I have also tried to copy the entire CD to the drive with the same results. If anyone had gotten AOE III work with wine, please provide any suggestions.

---

### Post by croak77 on 2006-08-31
Try this;

[http://appdb.winehq.org/appview.php?iVersionId=3795&iTestingId=3050](http://appdb.winehq.org/appview.php?iVersionId=3795&iTestingId=3050)

---

### Post by Senathon on 2006-09-01
The installation instructions works great.  The hitch I have now is that it is looking for a CD-Rom Drive.  I know that I need to download the No-CD Patch, but I would like someone recommned a site that I can down the patch without all the spyware added.

---

### Post by Anonii on 2006-09-01
> **Senathon said:**
> The installation instructions works great.  The hitch I have now is that it is looking for a CD-Rom Drive.  I know that I need to download the No-CD Patch, but I would like someone recommned a site that I can down the patch without all the spyware added.
[http://m0001.gamecopyworld.com/games/pc_age_of_empires_3.shtml](http://m0001.gamecopyworld.com/games/pc_age_of_empires_3.shtml)

Spyware on Linux? [http://ubuntuforums.org/showthread.php?t=98261](http://ubuntuforums.org/showthread.php?t=98261)

---

### Post by duhsutter on 2007-11-26
I begin installing and it asks me to insert the disk AoE III Disc 1... The strange thing is, it should be looking for disc 2? right? anyway, I've tried a couple of installs... please help

---

### Post by duhsutter on 2007-11-26
err:module:import_dll Library d3dx9_25.dll (which is needed by L"C:\\Program Files\\Microsoft Games\\Age of Empires III\\age3.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Microsoft Games\\Age of Empires III\\age3.exe" failed, status c0000135

Alright, I got by the installer.. now when i try

wine "C:\Program Files\Microsoft Games\Age of Empires III\age3.exe"

I get all that gross mess at the top...

---

### Post by trim17 on 2007-11-26
I have this same problem under Gutsy. Apparently it's a [known bug]("http://bugs.winehq.org/show_bug.cgi?id=4464") of Wine (actually a bug in the installation of DirectX), but at least [one user ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795")found a way around it (Willy Gardiol), but he didn't say how.

:|

---

### Post by duhsutter on 2007-11-26
I'm going to try and uninstall everything, AOE and Wine... start all over, I think I may have used an old repo. I think that he solved it by upgrading... give it a shot and let me know. (I'll try tonight or tomorrow)

---

### Post by trim17 on 2007-11-26
I did a quick google search for the file (d3dx9_25.dll) and placed it in the system32 folder under the Wine C drive. I also updated my version of Wine to 9.49 using the [Wine repos]("http://www.winehq.org/site/download-deb") and tried again (without reinstalling). It worked now - but it turns out, my integrated video can't run it with only 16MB of shared memory :(. I forgot to only change one thing at a time to find which of those changes corrected the error, but it's probably best to try both. Best of luck to you!

---

### Post by duhsutter on 2007-11-27
what does "go to the console and kill the IDriver.exe and IDriverT.exe" mean on the howto page?

---

### Post by duhsutter on 2007-11-27
brent@brent-desktop:~$ wine "C:\Program Files\Microsoft Games\Age of Empires III\age3.exe"
fixme:atl:AtlAxWinInit semi-stub
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg0: Permission denied
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 2.


Huh? i get this now

---

### Post by trim17 on 2007-11-27
> **duhsutter said:**
> what does "go to the console and kill the IDriver.exe and IDriverT.exe" mean on the howto page?

It means open up a terminal on Ubuntu (Accessories > Terminal) and kill those processes. You can either use "killall IDriver.exe && killall IDriverT.exe" or do a "ps -aux" and kill them by the process id.

---

### Post by trim17 on 2007-11-28
I've plugged that error message into "the Google" and got [these results]("http://www.google.com/search?q=+site:ubuntuforums.org+%22fixme:aspi:SendASPI32Command+ASPI:+Partially+implemented+SC_HA_INQUIRY%22&hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=fsj&filter=0"). 

I think the problem is that you need to download a "no-cd" patch for Age of Empires III. The error comes from wine trying to access your CD drive for the game information on Disc 1. What I did was rename the original "age3.exe" to "age3.exe.bak" and then downloaded a no-cd patch (a quick google search). The patch is just another "age3.exe" file that you copy into the game folder to run.

If that doesn't work, then I'm misunderstanding what the error is, which is very likely. Good luck to you!

---

### Post by Dunanjay on 2009-03-12
When i try to install the game, it goes upto the level of Extracting Age Of Empires III trial please wait......and then it says warchiefs trial does not support windows 95/98/me/2k/nt4/server 2003! Wine is installed and works fine in my comp

---

### Post by Fealix on 2009-06-09
I am also having some problems. everything is installed as far as I can tell in the correct way as per winehq. Unfortunately whenever i start up AOE III it kinda just goes the same style as my desktop with the AOE 3 icon in th top left. I have attached a screen shot for a better visual of what I mean. (P.S. i have wobbly windows thats why it looks distorted)

---

### Post by dirleyrls on 2009-10-01
I've got it working with wine 0.9.53. With the newer versions of Wine I can't event see the menu.

And about this "AOE III it kinda just goes the same style as my desktop" error, it's caused by a problem with the l3codecx.ax. Try this:

> **Acquiring the l3codecx.ax file**

There are a few ways you are able to get this file. Choose one of the following:

[LIST=1]
[*]Copy the file from an existing Windows install (C:\WINDOWS\SYSTEM32) 
[*]Copy it from a Windows XP install cd by issuing the following command "wine d:/i386/expand.exe d:/i386/l3codecx.ax_ h:/.wine/l3codecx.ax" assuming wine has d:/ mapped to a cd drive with a Windows XP install cd and h:/ is mapped to your home directory. 
[*]Install a codec pack with the file: 
- Download this file. 
- Run BCM1043.exe with wine, it will ask for installing Gecko HTML engine too, install it. After installing, it will create a folder called ~/.wine/drive_c/Program Files/BCM/. Copy the file l3codecx.ax under 'Codecs/DIRECTS/Fraunhofer/' to ~/.wine/drive_c/windows/system32/.
[/LIST]

Then do this to register the file: 

```
$ wine regsvr32 l3codecx.ax
```

---

### Post by sandpuppies on 2010-01-26
Hello people! Ok, I got AOE3 completely working on my computer. the only thing is now sometimes it says that i don't meet the system requirements when i try to start it. and sometimes i just start it and it messes up my comp. either 1. it'll log me off 2. it'll get stuck on a blank screen with the (in game) cursor. i don't get it :(

---

### Post by Rygaard on 2010-03-21
[IMG]http://ubuntuforums.org/home/william/Desktop/Screenshot.png[/IMG]OK, so, as for me and AOEIII, I have it installed and all, and I believe I patched it, but it still asks for disk 1 when I try running it. Now, I may not have patched correctly with the no cd patch, all I did was double click the downloaded file when it finished, it did it's thing, and said AOEIII was up to date. So if I am supposed to put the patch in a certain folder, then maybe I didn't, but other than that it installed without a problem after doing the how to on the wine hq site. Help is greatly appreciated, and thank you in advance for the help.[IMG]http://ubuntuforums.org/home/william/Desktop/Screenshot.png[/IMG]

---

### Post by Moyamo on 2010-06-26
It probably means go to the gnome-system monitor and end those processes to do that type:

```
gnome-system-monitor
```

in the terminal then go to the process tab then look for those names and click on them and then click on end process

---

### Post by Moyamo on 2010-06-29
If you're still having problems just download PlayOnLinux

---

### Post by DirtyPC on 2010-10-26
> **Dunanjay said:**
> When i try to install the game, it goes upto the level of Extracting Age Of Empires III trial please wait......and then it says warchiefs trial does not support windows 95/98/me/2k/nt4/server 2003! Wine is installed and works fine in my comp

You need to configure wine so it think its using xp.....

---

### Post by zebedeuzeu on 2011-01-16
When I try to run the game I get the following message: Application error 005D... Can anyone help me?

---

