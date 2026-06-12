---
title: "Wine-&gt;Dosbox-&gt;Heroes of Might and Magic 2 CD mount"
date: 2013-09-09
forum: Wine
---

### Post by e.c.2 on 2013-09-09
Hello all, this is my first post here so I appoligize for lacking in details or specifications (if you need clarification please ask).  I am new to ubuntu (I bought a netbook online and it came with ubuntu on it) and have the urge to play an old game, Heroes of Might and Magic II-Gold Edition.  I did a few hours of research online on how this can be done with linux and found that the place to start is Wine, so I installed it with a tutorial.  I then needed dosbox which was also an easy install.  I think that I set all the paths correctly because the game boots up and all the colors seem fine.  The problem I have run into is that the game is asking for the CD to be able to play anything but multiplayer and the install didnt come with an ISO file to mount as a CD.  The game is from GOG and here is the link I used to get as far as I am now [http://www.gogwiki.com/wiki/Heroes_of_Might_and_Magic_2:_Gold_Edition](http://www.gogwiki.com/wiki/Heroes_of_Might_and_Magic_2:_Gold_Edition)

Now it appears in the tutorial that the last few lines of the config. file including mounting for the CD but nothing I have tried has worked 

> mount C "/home/user/.games/homm2" 
c: 
imgmount d "/home/user/.games/homm2/homm2.inst" -t iso -fs iso 
cls 
heroes2.exe 
exit

[ATTACH=CONFIG]246137[/ATTACH]

Any help would be appreciated

---

### Post by kostkon on 2013-09-09
Is your Ubuntu username *user* or *User*? What do you see when you go into your home folder, do you see the path as */home/user* or */home/User*?

---

### Post by e.c.2 on 2013-09-09
> **kostkon said:**
> Is your Ubuntu username *user* or *User*? What do you see when you go into your home folder, do you see the path as */home/user* or */home/User*?

"/home/user"  I just tried changing the caps on user and it changed nothing, still reports needing the cd.  Interestingly, on the top left of ubuntu next to the time it reads "User", but clicking on the individual folders from "file system" it is lowercase.  

Likely unrelated but it might be important is that after I installed Wine and DosBox, I entered the command path "dosbox -conf ~/games/homm2/homm2.conf" and it said that dos box was not installed so I did a quick "sudo apt-get install dosbox".  But that shouldnt have been necessary should it?

---

### Post by mastablasta on 2013-09-10
why dosbox? it's a windows game as i know. first part had a dos version.

what tutorial did you follow for wine install?

---

### Post by kostkon on 2013-09-10
> **e.c.2 said:**
> "/home/user"  I just tried changing the caps on user and it changed nothing, still reports needing the cd.  Interestingly, on the top left of ubuntu next to the time it reads "User", but clicking on the individual folders from "file system" it is lowercase.  

Likely unrelated but it might be important is that after I installed Wine and DosBox, I entered the command path "dosbox -conf ~/games/homm2/homm2.conf" and it said that dos box was not installed so I did a quick "sudo apt-get install dosbox".  But that shouldnt have been necessary should it?
Have you actually copied all the files in the folder */home/user/games* or */home/user/.games*??

---

### Post by howefield on 2013-09-10
Thread moved to the "*Wine*" forum.

---

### Post by e.c.2 on 2013-09-10
> **mastablasta said:**
> why dosbox? it's a windows game as i know. first part had a dos version.

what tutorial did you follow for wine install?

I installed dosbox because it was recommended over fheroes2 (open source) as it was still in its development phase.
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu), I installed v. 1.4

> Have you actually copied all the files in the folder */home/user/games* or */home/user/.games*??

Yes, it was where I origionally installed the game to.

---

### Post by e.c.2 on 2013-09-12
I installed the same package on windows and it has had no issues with recognising a virtual CD.  Anyone else have experience with this?

---

### Post by e.c.2 on 2013-09-12
Ok, I uninstalled and reinstalled to the origional install location "C:\Program Files\GOG.com\Heroes of Might and Magic 2 GOLD"  However, I cannot seem to find the folder where it installed and I have looked everywhere.  I checked the shortcut which was created on the desktop and this is the path "env WINEPREFIX="/home/user/.wine" wine C:\\windows\\command\\start.exe /Unix /home/user/.wine/dosdevices/c:/users/Public/Desktop/Heroes\ of\ Might\ and\ Magic\ 2\ GOLD.lnk" I have tried checking home/user/.wine but no folder exists.  Does the "." in front of a folder have a special meaning?  Other ideas for this linux noobie?

*EDIT* figured out that the "." in front of the folder indicates it is hidden. :)

---

### Post by e.c.2 on 2013-09-12
Some possible progress.  I have discovered that the CD issue only comes up when I run the Heroes2.exe file this allows the game to boot up corretly but cannot be played because of no CD.  The bad news is that I am still unable to run Heroes2 from terminal dosbox as the tutorial recommends.  

[http://www.gogwiki.com/wiki/Heroes_of_Might_and_Magic_2:_Gold_Edition](http://www.gogwiki.com/wiki/Heroes_of_Might_and_Magic_2:_Gold_Edition)  "Now just run dosbox -conf ~/.games/homm2/homm2.conf to launch the game." When I run this command in terminal, all it does is launch Wine->dosbox but doesnt launch the game.

---

