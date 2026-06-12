---
title: "HOW TO: Run Lineage II (2nd throne) on Ubuntu Hardy"
date: 2008-10-05
forum: Wine
---

### Post by anetalaya on 2008-10-05
I'm new to Linux, and all the things I had problems, or to be more accurate, didn't knew how to do, I was able to do it with the help of this forum, so I want to give something back by sharing with anyone who might need it, this guide :)

This guide is intended to be used with a l2j server. If you don't have one, I will recommend you [*L2WorldUk*]("http://l2worlduk.proboards81.com").

**What you will need:**
&#8226; Lineage installer (well, duh)
&#8226; This dll files: dpmodemx.dll, dpnet.dll, dpwsock.dll, dpwsockx.dll (From any working Windows installation or download from internet). This will update DirectX; dont install DirectX from a windows installer, wine doesnt need it (Thanks to [*eledh*]("http://ubuntuforums.org/showthread.php?t=634828&highlight=lineage")!). 
&#8226; Make sure your video card drivers are properly installed.
&#8226; Other things that may help you to make Wine run better, read [*this great guide*]("http://ubuntuforums.org/showthread.php?t=497332") by cogadh.

**[SIZE="2"]How to do it:[/SIZE]**
1.- Install Wine latest version, following [*this instructions*]("http://www.winehq.org/site/download").

2.- Install Lineage and update it; it will ask you to install a plugin for FF, to display html, accept it.

3.- Run command winecfg to open the wine configuration window. On applications add l2.exe and LineageII.exe and set them both to run as Windows XP (You may try with Windows Vista as well). 

4.- Add the DLL files to wine's windows/system32 folder.

5.- Download this [*modified system folder*]("http://rapidshare.com/files/137710831/Linux_Gracia_Testing_rev1.tar.gz.html") (l2j servers dont need that, but it's necessary to make L2 run on linux). (Thanks to [*this guide*]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13378&iTestingId=30179")). If the download doesn't work, let me know and I'll try to upload it somewhere else.

6.- Rename your lineage system folder (Don't delete it, you should save it as backup or to use it when updating the game).

7.- Unpack the file you just downloaded it to Lineage II folder to replace the system folder  you just renamed (if you just overwrite your old system folder, it wont work).

8.- Disable Gameguard: add in your Linux /etc/security/limits.conf file the following line at the end of the file: * hard nofile 16383. (you must open this file as root) (Thanks to [*eledh*]("http://ubuntuforums.org/showthread.php?t=634828&highlight=lineage") again!)

9.- Add the server IP to your Linux /etc/hosts file (you must open this file as root). If you are going to play on L2WorldUK, get the IP [*from here*]("http://l2worlduk.proboards81.com/index.cgi?board=gamreq&action=display&thread=1079").

10.- Run the game by opening l2.exe with the terminal, don't use double click, it wont work.

11.- If you get a AGP consistancy error, just click ok and ignore it, the game will work. and if you know how to fix it, please tell me, I haven't figure it out yet :P. If the camera doesn work properly, disable "tracking" from inside the game on options -> Audio/system.

Tip: save a backup of the modified system folder as well, if you ever need to update the game, this folder will be replaced.
Tip: wine it's a hidden folder in your user's home folder.

Good luck!

---

### Post by grondinmf on 2008-10-29
gotta ask....but how about something like this for 2moons??

---

### Post by smo0th on 2008-11-06
I get stuck in the server selection screen, I click on either server and it does not advance anymore further than that window, any idea :confused:

---

### Post by nackgr on 2008-11-11
Hello I Am Using Wine version 1.0.1... and ubuntu 8.10
I installed Lineage 2 and Downloaded the System From this site ... and i am runnig l2.exe it Warns me about the AGP That is Deactivated.... and then it goes to open the lineage2 window But it Show me a Critical Error Saying : General Protection Error .. and some other
Someone maybe know What can Be The Problem With this ... ??? Plz Tell Answer
:confused:  :confused:



Ok  now When I Downloaded The Patch of the Server i am Playing and replaced the System i Open l2.exe press ok for AGP and then w8 for some minutes while the Splash Screen of lineage2 Getting Grey color and Then  Closes Suddenly without any Message ... :( :(  
---->[http://l2shadows.net/](http://l2shadows.net/) 
 this Is The site of my Server in Case you wanna Se Some From there And help me :/
EDIT
Problem Solved

---

