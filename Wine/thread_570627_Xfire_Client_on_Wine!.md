---
title: "Xfire Client on Wine!"
date: 2007-10-08
forum: Wine
---

### Post by Phrellex on 2007-10-08
[SIZE="6"]**Xfire on Ubuntu**[/SIZE]

I have managed to find an easy way to get Xfire client working through wine. Its operation is limited and I have not tested it greatly.

**Things that work...**

Login
Game Detection
Installation Via Ubuntu
Chat Via Main Menu
Currently Playing Status
Server List
Viewing Buddies Details On Sidebar
File Transfer
Buddy Mouse Hover Over Name (Shows Current Game, etc..)
Sounds

**Things that dont work...**

Ingame Chat With Key Activation (Only Tested On WoW)
Skin Changing
Buddy Names On Main Menu
Voice Chat
Files Tab
Help


You will need to have the latest version of wine and Microsoft fonts packages. These can both be installed via System -> Administration -> Synaptic Package Manager

Search for wine and msttcorefonts. (To get it working correctly you may need to follow instructions to update trusted sources to allow downloads from WineHQ for the latest version.)

[B]
1. [/B]Download the Xfire client from [here]("http://www.xfire.com/download/now/")

*Running the installation now should bring up an error message.*

**2. **Go into terminal and type "winecfg"

**3.** On the first screen that appears, which should be applications tab. In the section which is Windows and change the drop down selection from Windows XP to Window ME.

**4. **Now click the and run the the Xfire setup exe and it should run fine via wine without problems. De-select the options for icons and to boot up on Windows startup for obvious reasons. When the installation is complete you can go back to Terminal and type "winecfg" and change Windows ME back to XP or Vista.

**5. **Xfire will be listed in Applications -> Wine -> Programs -> Xfire

**6.** Loading it will work and prompt you for details to create an account, but the existing user button did not seem to work for me so I closed it and entered my login details in the main menu.
[B]
7.[/B] This should work, and you will be faced with a slightly glitchy scrollbar and menu, but apart from that a sort of working Xfire easy Linux installation. :)

**P.S. I accept no liability for things messing up (existing programs not working, etc) when following this guide. You have been warned, I have not had any problems so far though. :KS**

---

### Post by FRuMMaGe on 2007-10-08
Welcome to the forums!

Great tutorial!  Very helpful :lolflag:

---

### Post by Luister on 2007-10-18
I gave up on trying to make xfire to run smoothly with wine or crossover (with same results as you have posted),  so i use the gaim-xfire plugin and the xqf game browser instead. No more frozen boxes anymore.

---

### Post by mike^_^ on 2007-10-20
above instructions work great, thanks.

---

### Post by Pvt.Addams on 2007-10-21
first, thx for the great tutorial :)

Unfortunately, I can't get xfire to work, maybe someone has an idea..

After launching xfire I get a small window with some pixels in it named "nameless window", maybe it's the xfire window, but very shrinked :confused: I can't resize it :( I also get many errors if I launch it out of the terminal.

However, the tray-icon is working... :)

I attached a screenshot, it shows the little window and the errors in the terminal, I hope its helpful :KS

greetz Niclas

---

### Post by alphabetical on 2007-10-22
Iqm confused at step 4.  How do I run the exe to intstall xfire into wine?  If i click the exe it says 

"Couldn't display "/home/ask/Desktop/xfire_installer_28220.exe"."

Hmmm...  I think I may be doing it wrong...I say that cause I'm a big noob

---

### Post by andtsoreyu on 2007-10-31
Great Tutorial, this actually worked and it solved other problems I was having with Wine/Steam.... weird I know.

---

### Post by yekim on 2007-10-31
Thanks for the post!  I got this working with the same functionality as you - its a shame the friend names down't show up properly, and that XFire doesn't just support Linux natively!

---

### Post by eaglesfan17 on 2007-11-06
> **yekim said:**
> Thanks for the post!  I got this working with the same functionality as you - its a shame the friend names down't show up properly, and that XFire doesn't just support Linux natively!

I wonder if it is just some fonts that we are missing or something...I'm gonna try to copy all of my fonts from my Windows partition into the wine fonts folder and see what happens.

---

### Post by Xero117 on 2007-11-30
I don't have Linux on here yet but I will thanks for this though!

---

### Post by wwarsin on 2008-01-06
i dont know if i did something wrong but when XFire trys to run i get a Xfire exception, and it wants to upload some info.... so it didnt work for me

---

### Post by wwarsin on 2008-01-07
ok i got it to work... but i think i cheated... i just used the install from my windows partition and ran it as is, so far it runs... i do get the name problem, i see "<<<<<<" as a name... but i can mouse over them to see their login name... it did detect my Starcraft+broodwar installation idk if it will show my status as "Playing starcraft: broodwar" or not yet

--edit---

ok it does detect games you play

---

### Post by jasonp on 2008-03-20
awsum great post

---

### Post by Fr3y on 2008-03-26
Great and thanks so mcuh..

who would know that windows ME would fix anything:)


Buggy yes, works yes.

ty

---

### Post by h4mx0r on 2008-03-26
pidgin has an xfire plugin that works pretty well I don't know how far its come along but its good for basic chatting and keeping yourself informed.

---

### Post by DeathStrikeVirus on 2008-12-12
I realize this thread is old, but I've noted on the XFire forums AND these ones that everyone has a problem with Wine/XFire displaying names as [].  Well, a friend of mine found the solution. Here's the link to the post:
[http://z6.invisionfree.com/Angels_Of_Fire/index.php?showtopic=8308&st=0&#entry6361693](http://z6.invisionfree.com/Angels_Of_Fire/index.php?showtopic=8308&st=0&#entry6361693)

Just in case you have to register to view it, here's the meat:
> I am using wine 1.1.9, not sure how imporant that is, well onto the important part. Installing native win32 libs is equal to absolutely 0 support from wine. I had issues the first time around with winetricks because i went overboard and had to nuke my _entire_ .wine folder (Except the few programs I backed up outta ~/.wine/drive_c/Program\ Files\ that had no sysregilstry requirments).

Rationale:

I knew that Xfire depended on Internet Explorer 6.1 and mscomctrl and the windows fonts. Knowing that, I knew that it would work best with the native libraries. I have wine setup to show itself as windows 2000, not sure how important that is. Anyway.

Open up a shell on the same acct you use wine from and type the following commands at a bash shell:

CODE

wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
sh winetricks allfonts
sh winetricks ie6
sh winetricks comctl32
sh winetricks comctl32.ocx


Please note that it may fail on allfonts a few times, i had timeout issues with the liberation font pacakge. To remedy that you can download them in the web browser of your choice (or use wget). Assuming you are at terminal, the following commands will download them and put them where winetricks expects them to be:

I use -v out of preference, I like verbose output on any file activity
CODE

wget [https://fedorahosted.org/releases/l/i/liberation-fonts/liberation-fonts-1.04.tar.gz](https://fedorahosted.org/releases/l/i/liberation-fonts/liberation-fonts-1.04.tar.gz)
mv -v liberation-fonts-1.0.4.tar.gz ~/.wine/drive_c/winetrickstmp


Please note that if you use a different user for wine, it needs to be placed into
CODE

export WINEUSR=/home/<wineusrid>/.wine
$WINEUSR/drive_c/winetrickstmp


The export line is also something you can put into your main userid's /.bash_profile or /.bashrc file if you do use a different user for wine. (Some people have different uid/gid for each program, especailly something large like wine, so that its easy to track what wine is doing and what files it has created on disk...). This way any time you need to use the wine dir you can cd $WINEUSR and avoid a few keystrokes

---

### Post by 3mb0 on 2009-03-12
> **alphabetical said:**
> Iqm confused at step 4.  How do I run the exe to intstall xfire into wine?  If i click the exe it says 

"Couldn't display "/home/ask/Desktop/xfire_installer_28220.exe"."

Hmmm...  I think I may be doing it wrong...I say that cause I'm a big noob

I know i'm a bit late to this scene, but what you wanna do is right click the .exe file and click "run in wine programme loader" as long as you have wine installed, you will successfully install the exe to the best of wines abilities.

---

### Post by Kaigeos on 2009-04-18
Thanks so much for this how to. I am however still having some problems with chat, I click on any part of the client and it crashes. makes it hard to get to the text box to write back.

---

### Post by Jesdisciple on 2009-07-12
The installer now says ME isn't supported.  :(  Vista gave an error about being "Unable to elevate, error 1"  NT 4.0 asked me to upload an Xfire error report like XP.

---

### Post by modelrockettier on 2010-01-02
The latest xfire installer stops and displays an error if you try installing it in ME, after installing it and running xfire in a variety of different settings, about 75% of the time that I try to start it, BOOM GOES THE DYNAMITE, and not only does xfire crash, but I also get logged out

(64-bit ubuntu 9.04, wine version 1.1.35, xfire version 1.118)

---

### Post by SirRedTooth on 2010-01-31
Everything works fine until it finishes detecting games then I get e exception error.

---

### Post by asdfoo on 2010-03-12
These instructions are horribly outdated.

The problem with xfire is that it tries to hook several windows functions and this support is only available in Wine if you are using one of the most recent versions of GCC.

---

### Post by lodman on 2010-05-12
recently tried to install xfire on ubuntu 10.04 and got the following message

The file '/home/lodman/Desktop/xfire_installer_42654.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by ginderhulk on 2011-01-12
> **lodman said:**
> recently tried to install xfire on ubuntu 10.04 and got the following message

The file '/home/lodman/Desktop/xfire_installer_42654.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Same^

---

### Post by Soulcage on 2011-01-13
wine ~/Desktop/xfire_installer_43094.exe

---

### Post by Gaming4JC on 2011-01-13
Xfire has been broke in wine for quite some time. There's some work arounds and patches described on the AppDB.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2573](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2573)

My suggestion, just use Gfire - it rocks. :)
[http://gfireproject.org/](http://gfireproject.org/)

---

### Post by rocka120 on 2011-06-08
for the above error about executable bit, just right click the file, go to properties and click on permissions, then click on "allow executing file as program" :)

---

