---
title: "Starcraft on Wine"
date: 2007-08-08
forum: Wine
---

### Post by amazingtaters on 2007-08-08
So I'm a complete noob at using wine, as in I've never used it before ever. It is installed and that's about it. So, with that said, I want to install starcraft onto my laptop. It's an Acer Aspire 5100, AMD Turion x2 at 1.6 GHz per core, ATI Radeon Xpress 1100, 1 Gig of ram. So, I've got my starcraft discs and wine, where do I go from here?

---

### Post by cogadh on 2007-08-08
First click on the "Stuff I've learned about Wine" link in my sig to get some general Wine info. Then look here for Starcraft specific info:
[http://appdb.winehq.org/appview.php?iVersionId=51](http://appdb.winehq.org/appview.php?iVersionId=51)

EDIT - I think I might have come off a little bit rude in the original post. If so, I didn't mean that. Since you already said you didn't know anything about Wine, I thought it best to direct you towards a few resources that might answer some of your questions before they are asked. 

Wine is easy to learn, but complex to master. Before you jump into a particular game, it is best to learn all the basics you can, then apply what you have learned with that particular game. Starcraft is a good choice to learn Wine on, since it is known to work well with Wine already and does not require too much customization to run.

---

### Post by sep1318 on 2007-08-08
Well, my first intuition (since I have the SC CD in my drive right now) is to insert the cd, and run install.exe with wine. Theoretically that should wrok, though I don't wanna try (not enough room on my hdd, and I already have it installed under windows...next question, can I run it?). Hope that helps.

---

### Post by amazingtaters on 2007-08-08
Thanks for the link, I do need to learn more about wine, and it looks like a good place to start.

Edit: One quick question. From the post above I get the impression that I could install Starcraft to my windows partition (I've got a dual boot w/ Feisty and Vista) and then use wine to run it off of my Vista partition. True ou non?

---

### Post by sep1318 on 2007-08-08
You can. It runs, as far as I can tell from testing it out for a couple minutes. I'm not sure that's what you want to do, but you can. Just run the exe that you'd normally run (i.e. Program Files/Starcraft/starcraft.exe). Though I'm not sure if multiplayer works, since when I tried to connect to Battle.net it quit out. oh well. Good luck, whatever you decide to do! (Hope I don't run you astray.)

---

### Post by AnRa on 2007-08-08
StarCraft runs perfectly in Wine and doesn't need any tweaks! ;)

---

### Post by cogadh on 2007-08-08
> **amazingtaters said:**
> 
Edit: One quick question. From the post above I get the impression that I could install Starcraft to my windows partition (I've got a dual boot w/ Feisty and Vista) and then use wine to run it off of my Vista partition. True ou non?
I *strongly* discourage this. If the game needs to read or write to the registry or any files/directories on your Windows partition, it will have problems. I don't think it would screw up your Windows partition, but why risk it? Besides, Wine works best if you actually install the game through Wine into its fake Windows directory on the local Linux drive.

---

### Post by amazingtaters on 2007-08-08
Allright then, I'll have to give installation a try here in a litle bit.

---

### Post by bigboy_pdb on 2007-08-08
I've installed Starcraft using wine. I did it when I first started using wine to see how it would work. Then I got nostalgic and I ended up wasting over 24 hours playing it (and then I got bored and stopped).

Wine creates a folder in "/home/your_user_name/.wine". In that folder there is a folder called "drive_c" which is like your C drive in windows. To install Starcraft put the CD into your CD-ROM drive. Open a terminal (Applications -> Accessories -> Terminal) and change the directory so that you are in the directory where your CD-ROM drive has been mounted to (so you would type something along the lines of "cd /media/cdrom" and if you're not certain which directory is the one for the CD-ROM drive just double click the icon for the CD on your desktop and it will be displayed in the "Location" text field). When you're in the directory for the CD-ROM just type "wine install.exe" and wine will run the installer. Then just run install Starcraft as you normally would.

Once you've installed it you might want to download the patch from Blizzard. Get it from their website and then open a terminal, change the directory to the directory where you saved the patch to, and install it using "wine patch_name" (where patch_name is the name that the patch was saved using) and you install it the way you would in Windows.

To run the game open a terminal and type:
wine 'C:\path_to_starcraft_executable'
(with the single quotes)

If you used the default installation path "path_to_starcraft_executable" will be "Program Files\Starcraft\Starcraft.exe".

* to configure wine type "winecfg"
* to uninstall a program type "uninstaller"
* to edit the registry type "regedit"
* to view the Windows directory (open the wine file browser) type "winefile"

If you're having problems with sound, you may need to check the "Driver Emulation" box or select "Emulation" under the hardware acceleration drop down menu (you can experiment with the sound settings).

If for some reason you want a fresh start without uninstalling and reinstalling wine just delete the ".wine" folder which is under your "/home/user_name" folder (you will need to press CTRL-H in the File Browser to see it).

---

### Post by bigboy_pdb on 2007-08-08
There are a few other things that might be helpful as well. If you don't want to insert the CD every time you want to play Starcraft. Insert the CD into the CD-ROM drive. When the icon for the CD appears on your desktop, right click on it and select "Copy disc...". In the "Copy Disc" window in the "Copy Disc to:" drop down menu select "File Image". Select "Write" and choose where you want to save the disc image to.

You'll need to create a folder for where the CD-ROM image is supposed to be mounted to so open a terminal and type "sudo mkdir /mnt/loop" (this will require root privileges so you will need to type your password).

Now when you want to play Starcraft you can open a terminal and change the directory so that you are in the directory where the Starcraft iso image is located. At the prompt type:
sudo mount -o loop starcraft_iso_name /mnt/loop

where starcraft_iso_name is the name of the ISO file that you created beforehand (if there are spaces in the name place single quotes or double quotes around the name). This will require root privileges so you will need to type your password.

If after doing what was stated in the last paragraph you type "cd /mnt/loop" (in the terminal) and then type "ls" (or you open a file browser and go to "/mnt/loop"), you'll notice that the contents of the Starcraft CD are in the "/mnt/loop" directory.

To unmount the ISO image open the terminal and type "sudo umount /mnt/loop" (this will require root privileges so you will need to type your password).

**EDIT:** I forgot to mention that you'll have to tell wine where to look for the CD contents. In the terminal type "winecfg" select the "Drives" tab and then click "Add...". A new drive letter will be added. Select that drive letter and in the text field that is labeled "Path:" type "/mnt/loop" and then click "Apply" and then click "OK". Now wine will know where to find find the Starcraft CD. You'll have to use the "mount -o loop" command to re-mount the CD image after you restart your computer or after you unmount the CD image.

**EDIT:** I just double checked that last statement and I remember it working before with wine but for some reason it isn't working correctly. To get it to work, instead of using 'sudo mount -o loop starcraft_iso_name /mnt/loop' use 'sudo mount -o loop starcraft_iso_name cdrom_folder' where "cdrom_folder" should be the directory that your cdrom is usually mounted to (ie. /media/cdrom). Then in the command line type "winecfg", click the "Drives" tab, click the "Autodetect..." button, click the "Apply" button, and then click the "OK" button. You should now be able to play Starcraft using the ISO image instead of the CD-ROM.

---

### Post by shynko on 2007-08-08
good luck! 

the only true way anyone can 'master' wine is to  use it often  although reading guide's like cogadh's never hurt :grin:
with that said I need to go install diablo ll  :lolflag:

---

### Post by amazingtaters on 2007-08-08
Allright, Starcraft is up and running, no problems. Thanks guys!

---

### Post by bigboy_pdb on 2007-08-08
There was a problem with my post about playing Starcraft without using the CD. I made an edit to the post so that the process will work correctly.

---

### Post by sep1318 on 2007-08-08
@amazingtaters & codagh: I only mention going through windows because I already have SC installed there. I agree, not an ideal solution. If you're/he's installing it fresh for the first time, by all means do it the wine way!! :)

---

### Post by chaos2286 on 2007-09-19
hey guys, sorry if I'm a little late on this thread but I could use some help.  Everything went fine with my starcraft install except about 15 minutes into the game it stalls and I have to reboot.  I had this problem with war3 and it seems like a common problem.  if anyone experienced this I'd appresh if you post the fix

---

### Post by bigboy_pdb on 2007-09-19
Unfortunately, I wouldn't know how to fix that problem, but installing the most recent version of wine might be helpful. To do this go to the following page and perform the instructions that are listed:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Following this you should be notified that there's an upgrade for wine. If you're running the latest version then it could be a problem with the version (although it might be a problem with how wine works with your computer). Hopefully someone else will have something more for you.

---

### Post by TC-cheesy on 2007-09-19
I am having trouble running starcraft. I have it iinstalled, I also installed the latest drivers for my ati card (8.41) but I keep getting this error message no matter what I try:
[IMG]http://75.165.46.188:8000/stuff/snapshot23.png[/IMG]

---

### Post by chaos2286 on 2007-09-20
I updated my wine and it WORKED.  THANKS a lot

---

### Post by tatrefthekiller on 2007-09-20
TC-cheesy, you have drivers 8.41, what's your graphic card ? 8.41 drivers are designed only for HD2xxx cards.

---

### Post by bigboy_pdb on 2007-09-20
You're welcome

---

### Post by TC-cheesy on 2007-09-20
yeah, I know. I have a ATI RADEON 9600 XT I figured I'd give it a try sine other people I know that have similar cards installed them and they worked fine. I noticed some big performance improvements in other games too

---

### Post by Aishiko on 2007-09-27
I can't install Starcraft I get to the install part and it hangs on StarDat.mpq and stays that way for over half an hour nayone had this problem?

I have everything updated and the latest Wine installed.

---

### Post by Perfect Storm on 2007-09-27
You guys might to check this; [http://ubuntuforums.org/showthread.php?t=547989](http://ubuntuforums.org/showthread.php?t=547989)
(go for the SVN (subversion))

---

### Post by Aishiko on 2007-09-30
turned out my install disc was dirty wash and dry and it installed fine.

---

