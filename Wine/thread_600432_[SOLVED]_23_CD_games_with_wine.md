---
title: "[SOLVED] 2/3 CD games with wine"
date: 2007-11-02
forum: Wine
---

### Post by snickers295 on 2007-11-02
i was woundering how to do 2/3 CD games under wine.
if i can i can work on getting madden to work under wine ok.

---

### Post by cogadh on 2007-11-02
I'm not sure I understand the question correctly, but, if you are asking if games that require multiple CDs for the install work with Wine, then the answer is yes, but you have to run the install from outside the CD-ROMs directory, i.e.:
```
wine /media/cdrom/setup.exe
```
NOT
```
cd /media/cdrom/
wine setup.exe
```
If you don't do it that way, you will likely run into problems when you need to switch CDs. If you do run into problems with the CD swap anyway (it can happen), you usually just need to use the "wine eject" command to swap the CD:
```
win eject D:
```
Obviously change the drive letter to match what you have configured in Wine.

If that is not what you are asking about, then explain things a bit more, maybe I can still help.

---

### Post by snickers295 on 2007-11-02
i found a better way, copy data of the second and third cds and put them in folders and in winecfg set the drive letter to the folder.

---

### Post by disturbedite on 2007-11-02
> **snickers295 said:**
> i found a better way, copy data of the second and third cds and put them in folders and in winecfg set the drive letter to the folder.
you could do that.  or you could do what i do (for convenience):  put multiple cds on a single dvd.  then you can copy the individual folders (discs) to your hdd if you need to.

---

### Post by snickers295 on 2007-11-02
> **disturbedite said:**
> you could do that.  or you could do what i do (for convenience):  put multiple cds on a single dvd.  then you can copy the individual folders (discs) to your hdd if you need to.
i have no blank dvds and the game won't work anyway.
when i start it it pops up two small windows in almost the same place and won't do anything else.

---

### Post by BrandxG on 2012-07-25
-----I was trying this from somebody else but when I got to the terminal step I couldn't get it to work. I typed cd Desktop pressed enter then I typed cd 1-NBALIVE2005_1(the name of the game i'm trying to install) then it shows "file or directory not found).
THANX in advance

1. Insert your 1st CD into the CD tray (note: it should appear on the desktop (NFSMW_DISC1 or whatever your installing).

2. Create a folder with exactly the same name as the CD (I have not tested same name, but lets do it just to be safe).

3. Double click the 1st CD icon on your desktop (not the folder). You  should have a window with all the stuff of CD-1 in it, hopefully. 

4. Copy and Paste everything in that window into the folder you just  created on your desktop. Grab a paper or something to read while you  wait (mine took 3 minutes).

5. Repeat step 1-4 with all other CDs needed to install the game you want.

6. Run Configure Wine which is located under application/Wine menu. The  program can be from terminal as well with the following command:
 	Code:
 	winecfg & 
7. On Configure Wine look for the driver tab near the title bar,  and click on it. Here look for D: under letter. If it is not there click  on add button and it will usually have it ready, so click okay. Once  you see D: listed click on it and click on the browse button next to the  "path:" suggestion. Browse  through home/username/Desktop/CD1FolderName  folder you created. and click  okay (don't open the folder as we want  this to be where it looks). It  should list D: and the location of where  your copy of CD1 folder is located. Click on apply button at the bottom  of the window to save the settings.  Leave the window alone in the  background for now.

8. Run a terminal (Application/Accessories Menu) and type (or copy and  paste with your mouse) in the following commands, with each line meaning  after you click enter for the previous one. Note edit your  CD1FolderName with the actual CD1FolderName (don't just copy & paste  this and hit enter, or I will give you such a pinch! :evil:) : 
 	Code:
 	cd Desktop cd 1-CDFolderName: 
9.Look in here for an install.exe, AutoRun.exe, or Setup.exe  by  using the folder you have on your desktop or after following the  terminal command above type (don't be lazy):
 	Code:
 	ls 
10. Use the following command once you find that install.exe or  whatever the program is  named (don't just  copy & paste this and  hit enter, or I will give you such a pinch!):
 	Code:
 	wine Install.exe 
11. That should startup the wizard or game's installation program,  and go fairly smoove till you come across the insert CD-2 pop-up. Here  we go back to that Wine configuration window you had opened (don't close  the game's installation program). We need to change the path of D: to  the next copy folder of CD-2 you created. click on the browse button  next to the "path:" suggestion. Browse  through  home/username/Desktop/CD2FolderName folder you created. and click  okay  (don't open the folder as we want this to be where it looks). It  should  list D: and the location of where your copy of CD2 folder is located.  Click on Apply button at the bottom of the window to save the settings.   Leave the window alone in the background for now.

12. Go back to the wizard you have running for your game (don't tell you  closed it!?!) and click ok for that pop-up we got talking about  inserting CD2. Now it should continue till the pop-up about CD3 (Or CD1  or finish. If finished, congratulations. And by the way, you owe your  soul!:lol:).  What is that?...you know what to do now?..Repeat step 11 and edit the  path to the new copy of the CD folder it wants? Yes, How did you know?:-k

13. Hopefully, your installation should finish well and you will have an  idea where to run the game from. Now, cross your fingers and hope that  wine will take care of running the game without you needing to tweak it.[-o<  If the game runs with the CD, simply switch the path of D: in Configure  Wine to your CD1Folder in your desktop or switch it back to default  which will make it look at the CD Tray. Don't pick install program again  in the CD1Folder on your desktop (or CD1 from your CD tray) since we  already did that step silly.:wink:

---

