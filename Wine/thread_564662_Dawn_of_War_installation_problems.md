---
title: "Dawn of War installation problems"
date: 2007-10-01
forum: Wine
---

### Post by madsmeg on 2007-10-01
Hey all

I may not have many posts, but trust me i have read through everything to find a solution to this, so don't pass me off too lightly

I am trying to install Dawn of War (who would have guessed by the topic title eh?)

I have tried installing from the CD and every time i get to put disk 2 in it the first WILL NOT come out. i have tried unmounting, and i have tried "wine eject d:" (says there is no cd drive there apparently) i even tried "wine eject -a" with no luck either.

so i went with putting all the cd's into 1 folder and doing a wine install from there, now im having an error turn up, please help, altho its fun to figure out how to install things... im now lost and cant find any way of doing it

Thanks in advance


Cappy :
Hi, try running this from your HOME directory
Code:
```

wine /media/cdrom/setup.exe

```
You'll need to edit that for the correct path. The important thing is that you don't navigate the console into the cdrom's folder(s).
When you get ready to switch cds you'll probably need to open a new terminal and type
Code:
```

wine eject

```

My second suggestion is to open the cdrom in Nautilus (the file browser) and then right click on the setup.exe or install.exe (or whatever) and click "open with" and click "Use a custom command" and type in "wine". Now click "open".
When you need to switch CDs you can try the "wine eject" or you can try right clicking on the CD-ROM on the Desktop and clicking "eject".

	
madsmeg :
tried both of these suggestions, wine isnt seeing my d: as a cd device for some reason

thanks for the quick reply to a cackly spelt thread

so basically it wont let me eject the CD no matter what i try

I dont really understand why it will not install out of the folder though. This is the what my terminal is telling me

Code:
```

jon@jon-desktop:~$ wine Desktop/DoW/DawnOfWar.exe
fixme:advapi:LookupAccountNameW (null) L"jon" (nil) 0x34f7fc (nil) 0x34f800 0x34f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"jon" 0x12f058 0x34f7fc 0x12e5f0 0x34f800 0x34f7f4 - stub
err:msi:call_script Could not find CLSID for Windows Script
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 6 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 15 ignored L"CreateFolder" table values
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\BugReport\\BugReport.exe" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\BugReport\\BugReport.ini" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Drivers\\shader.txt" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Drivers\\ati.txt" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Drivers\\nvidia.txt" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Drivers\\spdx9_config.txt" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Engine\\Engine.sga" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\GraphicsOptions\\GOTData.sga" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\W40kData-Whm-Low.sga" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\W40kData-Whm-Medium.sga" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\W40kData.sga" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\W40kData-Whm-High.sga" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Engine\\Movies\\relic_intro.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Engine\\Movies\\credits.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Engine\\Movies\\relic_intro.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Engine\\Movies\\dow_intro.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Engine\\Movies\\credits.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\Engine\\Movies\\dow_intro.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS11_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS05_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M11.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS06_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS03_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M01.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS09_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS09_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS02_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M02.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S10.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS11_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M03.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S11.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M04.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S01.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS10_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS06_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M05.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S02.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M06.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S03.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS08_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS05_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS03_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS02_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M07.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S04.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M08.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S05.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M09.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S06.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS07_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S07.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S08.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS04_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS04_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS01_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\S09.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS07_brief.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS08_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS01_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\MS10_static.avi" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\Movies\\DOWMissions\\M10.lua" (error 2)
err:msi:cabinet_notify failed to create L"c:\\Program Files\\THQ\\Dawn Of War\\W40k\\W40kDataGOTY.sga" (error 2)
err:msi:ACTION_InstallFiles compressed file wasn't extracted (L"c:\\Program Files\\THQ\\Dawn Of War\\BugReport\\BugReport.exe")
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603

```


Cappy :
Have you run
Code:
```

winecfg

```
and gone to the "Drives" tab and added your CDrom drive to the list as D


Sandlst :
Have you tried looking up the AppDB entry for Dawn of War under winehq? If you haven't, some special instructions are down the page for installation: [http://appdb.winehq.org/objectManage...rsion&iId=2576](http://appdb.winehq.org/objectManage...rsion&iId=2576)


madsmeg
@ Cappy, yes i have

@ Sandlst thanks i'll take a look now and try it when i get home.

---

### Post by madsmeg on 2007-10-01
this is a repost of my first thread which i mis-spelt with the replies to that post

reposted as not alot of people were looking at "daen of war problems" :p silly me :)

---

### Post by madsmeg on 2007-10-02
*Bump*

---

### Post by disturbedite on 2007-10-02
hmmm...the link you have posted above is dead, the new link for that appdb entry is:
[http://appdb.winehq.org/appview.php?iAppId=1918](http://appdb.winehq.org/appview.php?iAppId=1918)

you also failed to mention which version of wine you are using.

it appears looking through the different versions that they have a gold rating with most distros, so you shouldn't have a problem installing & running it.

so that could mean two different things:

1.  dow works better with 0.9.42+ so you should try installing that version of wine and try again if you aren't using wine 0.9.42+.
OR
2.  dow has actually regressed with more recent versions of wine and has issues.  but i don't know that to be the case necessarily cuz, as i said before, the latest version listed on the wine appdb is w/ wine 0.9.42.  (assuming you are using a recent/latest version of wine).

---

### Post by madsmeg on 2007-10-02
Hmm didnt really want to downgrade my wine, but i might give that a go when i have the time, if you have any other ideas please let me know

---

### Post by donkyhotay on 2007-10-03
I had the same problem with DoW, even 'wine eject' didn't work (it would pop out the disc but the installer would hang). The way to get around that is to copy all of the files on the DoW CD's onto your hard drive and then run the installation program from the hard drive. I've found using this method to install works well for just about any multi-disc wine install.

---

### Post by disturbedite on 2007-10-03
he said he already tried that but was getting an error...

---

### Post by madsmeg on 2007-10-06
*bump*

---

### Post by mad chey on 2007-10-12
i have the latest version of wine and it installed flawlessly from the disks, by using the wine eject to release the disks

my problem is that after it told me the installation was a success, it asked for disk 1 again, and went to play, but came up with an error about how i should be using an original disk not a copy and giving me a link

WTF these are originals!!!!!

anyway went to the site it pointed me to 

[http://www.securom.com/message.asp?m=copy](http://www.securom.com/message.asp?m=copy)

and that is telling me how to fix, presumably this is for windows only so if anyone can translate that into a wine/ubuntu fiix i would be mucho obliged

---

### Post by cogadh on 2007-10-12
Wine does not have complete copy protection support, you will need to use a cracked executable to get around the CD check at game launch. However, there is a note on the game's AppDB page that says if you update the game to 1.5, that copy protection check is removed and the problem shouldn't occur anymore.

@madsmeg - Have you tried creating a symbolic link to you CD-ROM drive's /dev entry in Wine's dosdevices directory? That will sometimes correct the drive detection issues:
```
$ ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
```
Obviously, change the "/dev/hdc" line to reflect your actual drive.

---

### Post by mad chey on 2007-10-12
> **cogadh said:**
> Wine does not have complete copy protection support, you will need to use a cracked executable to get around the CD check at game launch. However, there is a note on the game's AppDB page that says if you update the game to 1.5, that copy protection check is removed and the problem shouldn't occur anymore.



anytips on updating, i know that if you have the game running you can update thru that, obvioulsy i cant so i downloaded a couple of the patches and ive tried installing them and it just says that the installation was unsuccessfull

---

### Post by cogadh on 2007-10-12
There is some mention of patch failures, but the solution listed doesn't make much sense to me. Check the Notes section under the Known Bugs section:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2576](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2576)

---

### Post by mad chey on 2007-10-13
cheers for that, it seems to make sence i will give it a go when i get chance and report back

chey

---

### Post by markackerman8@gmail.com on 2009-06-03
Solution for me for an installation problem

Extract all CD1 archives to a folder. Extract Data2.cab and Data3.cab from cd2 and cd3 in the same folder.
Run the setup.exe.
The installer will not ask for CD2 or CD3, but will ask for cd1 in a windows behind the installer main window in the end, move the installer window and press ok, no more trouble.

---

### Post by whoey on 2009-08-21
> **markackerman8@gmail.com said:**
> Solution for me for an installation problem

Extract all CD1 archives to a folder. Extract Data2.cab and Data3.cab from cd2 and cd3 in the same folder.
Run the setup.exe.
The installer will not ask for CD2 or CD3, but will ask for cd1 in a windows behind the installer main window in the end, move the installer window and press ok, no more trouble.

This worked for me more or less... then installed the 1.41 full patch, 1.41-1.50 patch and 1.50-1.51 patch... now it doesn't ask for the CD to play (CD check was officially removed as of v1.50 I think)

having a display bug with game text and some buttons... lots of info here:
[http://bugs.winehq.org/show_bug.cgi?id=14174](http://bugs.winehq.org/show_bug.cgi?id=14174)

---

