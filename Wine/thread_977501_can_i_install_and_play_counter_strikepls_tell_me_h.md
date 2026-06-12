---
title: "can i install and play counter strike?pls tell me how"
date: 2008-11-10
forum: Wine
---

### Post by abhilashm86 on 2008-11-10
i wanted to know procedure to install counter strike because i want to remove completely windows xp from my computer.I depend on xp due to this counter strike,pls help................

---

### Post by GSZX1337 on 2008-11-10
Google is your friend.

[http://developer.valvesoftware.com/wiki/Steam_under_Linux](http://developer.valvesoftware.com/wiki/Steam_under_Linux)

---

### Post by abhilashm86 on 2008-11-10
get me some instructions of doing this installation.............do i need to download all the game or what to do?

---

### Post by kristian304 on 2008-11-10
Hi

Yes, you can play Counter-Strike 1.6 and Source on Linux:) 
You need to install Wine
Wine: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Search for Counter-strike in: [http://appdb.winehq.org/](http://appdb.winehq.org/) to find a guide. I have tried CS 1.6 and it worked perfect;)

---

### Post by GSZX1337 on 2008-11-10
> **abhilashm86 said:**
> get me some instructions of doing this installation.............do i need to download all the game or what to do?
This came straight from my link.

> Wine doors seems to be another simple solution for installing steam. 

Step 1: Install Wine-Doors 
[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/) 
navigate to the downloads page, and install your installation type. I had the easy route and could install from an RPM. 
Step 2: Run the program from your main menu Applications--> System --> Wine-doors. This was for Fedora 9, I did not try any other distro's yet. 
Step 3: Fill in some basic username information that is in regards to YOUR computer. 
Step 4: choose which programs you would like to install. I Choose Steam, the Tahoma truetype font, and the DirectX 9 runtime stuff. 
Step 5: Hit apply 
Step 6: Programs are downloaded and installed automatically. 
Step 7: VERY IMPORTANT!!! Restart your os. For some reason it took me two or three restarts but I have a fully functioning steam client. 



At first I was disappointed because my steam client didn't show up with the tahoma font, but now everything is visible. Also something of note, I installed the adobe flash player before trying to run steam. I'm not sure if it affected it or not, but if your superstitious, reboot 3 times, install adobe flash player (rpm) and then open steam from main menu Applications --> Other --> Steam. 



Any questions can be e-mailed to [email]fserravalli@optonline.net[/email]. I would be happy to help out. 

---

### Post by lakersforce on 2008-11-11
How about that you just do "sudo apt-get install wine", double-click setup.exe, install, go into /home/<username>/.wine/drive_c/<your windows path to the game>/hl.exe -cstrike

worked for me! That's without steam ofc

---

