---
title: "Really struggling to install Internet Explorer 6"
date: 2007-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by UberKnight on 2007-03-17
Hi Guys

I have installed Wine 0.9.32 successfully (I think), however, I am finding it terribly difficult to install IE6.  I have followed all the guides I could find here without success.  The closest I came was with IEs4Linux, but although IE was running, fine, it wasn't incorporated with my Wine installation.

Before you flame me, I need IE6 installed on Wine so that I can install [Libronix]("http://appdb.winehq.org/appview.php?iVersionId=4705").

Any help getting IE6 installed on Wine on Ubuntu 6.10 AMD64 would be GREATLY appreciated!

Thanks
UberKnight

---

### Post by r4ik on 2007-03-17
Seems to be a Deb.

[http://www.ubuntuforums.org/showthread.php?t=370705&highlight=internet+explorer](http://www.ubuntuforums.org/showthread.php?t=370705&highlight=internet+explorer)

Maybe you could use it.
Have not read it all so please do.

---

### Post by UberKnight on 2007-03-17
Thanks for the reply.  However, I've already tried that one.  I could not solve the wine dependency.   I don't think it works on AMD64 as I installed Wine with a --force modifier.

---

### Post by Kilz on 2007-03-17
> **UberKnight said:**
> Thanks for the reply.  However, I've already tried that one.  I could not solve the wine dependency.   I don't think it works on AMD64 as I installed Wine with a --force modifier.

Installing wine with a --force modifier makes no difference. You are just overriding a requirement in the .deb's control file. It changes nothing to the application. 
Internet Explorer is difficult to install and run with wine. Perhaps one of the hardest. But there is a solution that is simple and works.[ Ies4linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

---

### Post by UberKnight on 2007-03-18
Thanks for your answers Kliz, but as I mentioned, I already tried IEs4Linux.  It actually worked beautifully in that it enabled me to use IE6.  Problem was that it did not install IE6 under wine which is what I need as IE6 is a dependency requirement for getting Libronix working on wine.

---

### Post by Kilz on 2007-03-18
> **UberKnight said:**
> Thanks for your answers Kliz, but as I mentioned, I already tried IEs4Linux.  It actually worked beautifully in that it enabled me to use IE6.  Problem was that it did not install IE6 under wine which is what I need as IE6 is a dependency requirement for getting Libronix working on wine.

Just a question, but what is Libronix? Is it a Bible? If so you may want to install GnomeSword. 

[To get IE installed you might want to read this page.]("http://appdb.winehq.org/appview.php?iVersionId=469")

---

### Post by mhancoc7 on 2007-03-18
> **UberKnight said:**
> Thanks for your answers Kliz, but as I mentioned, I already tried IEs4Linux.  It actually worked beautifully in that it enabled me to use IE6.  Problem was that it did not install IE6 under wine which is what I need as IE6 is a dependency requirement for getting Libronix working on wine.

You could try this.

Install IEs4Linux using either the script or the .deb package.

Then install Libronix using the code below. This will install Libronix to the IE6 Wine directory. Then all should work fine.
```

WINEPREFIX="$HOME/.ies4linux/ie6" wine "/path/to/libronix/installer.exe"
```Just replace "/path/to/libronix/installer.exe" with the path to the setup/installer for Libronix.

Jereme

---

### Post by UberKnight on 2007-03-19
Hi Kliz and Jereme

I really appreciate the help you chaps are giving me.

**to Kliz**: Libronix is a modular Bible Study engine.  While I am happy to use GnomeSword, I have a selection of Bible Commentaries and other study material that I purchased a year or two ago that uses the Libronix engine, hence my desire to get it working to help me further my transition to Linux.

**to Jereme**: I've actually learned (inferred) several things from your post:

1.  IEs4Linux sets up a special Wine instance in the "~/.ies4linux/ie6" directory
2. WINEPREFIX is used to specify the particular Wine instance/installation
3. I can use $HOME in scripts/menu entries rather than specifying my /home/{username} directory

Once I had figured out what WINEPREFIX meant, I realised that you had forgotten to place an " in the code you helped me with.  It should be (in case others use this thread):
> WINEPREFIX="$HOME/.ies4linux/ie6" wine "path/to/libronix/installer.exe"

I have set up the IE4Linux instance of Wine by using:
> WINEPREFIX="$HOME/.ies4linux/ie6" winecfg
I needed to do this in order to set my CDRom / DVD drives and also set up a virtual window in the specific Wine instance IEs4Linux creates.

However, when I now enter:
> WINEPREFIX="$HOME/.ies4linux/ie6" wine "E:\Setup.exe"
the Wine virtual window opens, but the setup.exe file does not run and the Wine virtual window just closes again.  I have triple checked the drive letter as well as the spelling of the setup file.

Do you happen to have any other suggestions for me?
Thanks!

---

### Post by mhancoc7 on 2007-03-19
> **UberKnight said:**
> 
However, when I now enter:
```
WINEPREFIX="$HOME/.ies4linux/ie6" wine "E:\Setup.exe"
```the Wine virtual window opens, but the setup.exe file does not run and the Wine virtual window just closes again.  I have triple checked the drive letter as well as the spelling of the setup file.

Do you happen to have any other suggestions for me?
Thanks!

Thanks for correcting my typo. :)

Did you run the code above in terminal? If so did it give you any errors? Do you need to install the visual basic runtime to run Libronix? You might try installing that to the ie6 directory. A lot of times Wine fails due to missing .dll or .ocx files. Maybe the terminal output can shed some light on it.

Jereme

---

### Post by Kilz on 2007-03-19
> **UberKnight said:**
> 

**to Kliz**: Libronix is a modular Bible Study engine.  While I am happy to use GnomeSword, I have a selection of Bible Commentaries and other study material that I purchased a year or two ago that uses the Libronix engine, hence my desire to get it working to help me further my transition to Linux.



Not a problem, but its always nice to have multiple applications. Also wine isnt perfect (as you are seeing), I hope it runs your application. But its better to have something over nothing while you work out the bugs. :)

---

### Post by UberKnight on 2007-03-20
Hi Jereme and Kliz

**Jereme**, you asked:
> Did you run the code above in terminal? If so did it give you any errors? Do you need to install the visual basic runtime to run Libronix? You might try installing that to the ie6 directory. A lot of times Wine fails due to missing .dll or .ocx files. Maybe the terminal output can shed some light on it.
I ran the code in terminal but didn't get any error message at all.  This is what the terminal shows me (Note: I have changed my username and computername from the terminal output.):
> username@computername:~$ WINEPREFIX="$HOME/.ies4linux/ie6" wine "F:\Setup.exe"
username@computername:~$ 
**Kliz**, after that I tried installing Wine using your script (which I modified to use Wine 0.0.33).  It worked!  I tried to install IE6 and it seems to work in that it runs through installshield and gets to the point where it tells me to click "Finish" and that my computer needs a restart.  However, the terminal outputs a lot of info.  [Please see the attached file.  For some reason my post is not allowed when I include it.  I get a forum error message about too many images?!?]

---

### Post by cowlip on 2007-03-20
Winetools is another method to install IE and it's dependancies, for anyone else who reads this thread: [http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

---

### Post by Kilz on 2007-03-20
> **UberKnight said:**
> Hi Jereme and Kliz

**Jereme**, you asked:

I ran the code in terminal but didn't get any error message at all.  This is what the terminal shows me (Note: I have changed my username and computername from the terminal output.):

**Kliz**, after that I tried installing Wine using your script (which I modified to use Wine 0.0.33).  It worked!  I tried to install IE6 and it seems to work in that it runs through installshield and gets to the point where it tells me to click "Finish" and that my computer needs a restart.  However, the terminal outputs a lot of info.  [Please see the attached file.  For some reason my post is not allowed when I include it.  I get a forum error message about too many images?!?]

Ok, if you ran my script, here is a cheap easy way to get things working, but only if you havent installed anything else with wine, if you have, you will have to reinstall it. 
First install ies4linux if you havent already.
Open your home folder, click edit, then preferences, click on the box that says show hidden and backup files then click close. Close the home folder and reopen it. You will see the .ies4linux folder, open it, inside you will see an ie6 folder, open it. Highlight the followng files and copy them
system.reg
user.reg
userdef.reg
.firstrun
now go back to the home folde and open up the .wine folder and paste those files in , let them overwrite the existing files if any.
Go back to the .ies4linux/ie6 folder and open up the drive_c folder
Copy the 2 folders
Back out to the home folder, you will see a C folder, open it and paste in the 2 folders letting them overwrite.

You now have ie6 installed in wine. Inside the C folder is your virtual drive for wine, inside the program files is an Internet explorer folder with the exe, you will need to make a shortcut to it. Since its installed in wine, you can remove the .ies4linux folder if you want.

---

### Post by S29K on 2007-03-20
I found this thread looking for a solution to a problem that's been plaguing me for some time now and I'm very happy to say that Kilz's instructions worked perfectly for me.

 I am running a piece of software that requires something from IE to check for a valid license key on the network.  I needed IE to be installed in the same directory as the application (ERALink32) to work properly.

Thanks a million for solving this problem for me. :KS

---

### Post by UberKnight on 2007-03-21
Kilz, thanks so much, I now have IE running properly from my Wine directory.  One more thing though, when I deleted my old wine installation (C and .wine), I also deleted the menu entries using "Menu Layout" under preferences.  I thought that it would be better to delete them so that the new installation of Wine would have no conflicts.

However, after reinstalling Wine with your script, the menu entries have not been set up.  I assume this must be because I deleted them previously...

Any suggestions to get them back?  Sorry to take up so much of your time!

[Edit. I got the menus fixed by using the revert button.  I was afraid this might remove entries for all the apps I have installed since default Ubuntu installation, but this works perfectly!  Cudos to Ubuntu!]

---

### Post by UberKnight on 2007-03-21
Jereme, I'm not sure what I'm doing wrong, but even with IE now working under Wine as per Kilz's instructions, Libronix still won't install... no error messages either...

I think I'll try and install the Libronix engine that can be downloaded from the internet rather than my CD and see what happens.

---

### Post by UberKnight on 2007-03-21
Ok, I downloaded DLSSetup.exe (Libronix engine) and it installed fine.  Still can't figure out how to run it (not sure about which .exe to use) -- might have to log back into windows to see what file the shortcut points to.

I have just made and image file of my Libronix CD (with commentaries, etc.) to see if I can run the setup from a mounted image...

Will update on results.

---

### Post by UberKnight on 2007-03-21
Browsing the Logos website, I found this page: "[Installation will not start]("http://www.logos.com/ArticleViewer/328")" which states:

> Problem:

Libronix installation does not even start -- bad disk?
Solution:

To see if the disk is Ok, try the two-step install. If you cannot even view the contents of the CD, check for scratches or dirt. If it still does not work, call for a replacement disk.
Two-step installation

Quick instructions:

1. Run x:\Setup\Installs\DLSSetup.exe (where "x" is the letter designation for your CD-ROM drive). 
2. Run x:\Setup\AutoUpdate.lbxupd. 

Step 1: Running the DLSSetup.exe file with Wine works.
Step 2: Does not work as Wine cannot interpret the "lbxupd" extension.

I get the following error message:

> wine: could not load L"E:\\Setup\\AutoUpdate.lbxupd": Bad EXE format for 

Is there any way to force the execution of a file?

---

### Post by mhancoc7 on 2007-03-21
I am really not sure at this point. I have never install Libronix. Have you read anywhere about success installing it in Wine?

Jereme

---

### Post by Onesimus on 2007-05-13
I too am attempting to install Libronix and have had similar experiences due to wine not 
recognising the installation of IE6 (even with Ies4Linux).  From the dates that these posts
were made, presumably you were installing onto Edgy Eft.  Have you had any success
with Feisty ?

I am really keen to get Libronix installed on Ubuntu, as it is the only reason why I still
have a copy of Windows.

---

### Post by shaft350x on 2007-05-14
I as well have been wanting to get Libronix running under Ubuntu.

It is listed as a program that someone got working with Wine according to their website.  With the caveat that you must install IE6 to run it.

I have tried it on several installs, not to much avail.  I think at this time I've tried on Edgy 64bit, and two different computers running Feisty i386.  Though the latter two I have admittedly not tried that hard.

I wonder if we could get enough people to hound Logos about making a Linux compatible version of the Libronix program, since one buys the books rather than the library software, which comes with any book that Logos has made an electronic copy of.  (Almost any book I suppose, the Book of Concord is available just on CD)  Regardless I think they would benefit from being even more available cross-platform. [You can make suggestions to them by e-mailing them here: [email]suggest@logos.com[/email] (I'm going to post this somewhere else so as to not highjack this helpful thread)]

Though my rant aside, I will be trying to get this running as well and will be checking in to see if you get a solution or to let you know if I manage to get it running.  Godspeed!

---

### Post by riles01 on 2007-06-11
Not sure if this will help at all, but I found [this post]("http://blog.higherthings.org/borghardt/article/2359.html") that appears to document a successful installation of Libronix. I'm looking to make the switch soon, now that someone appears to have figured it out. This has been the only thing stopping me for about a year and a half. I'd love to know if it works.

You might also try CodeWeavers [CrossOver Office]("http://www.codeweavers.com/compatibility/browse/votes/?app_id=321;tips=1"). I think someone has finally gotten Libronix up using their app.

---

### Post by capecove on 2007-06-11
Sorry for the delay in getting in on this thread. :)

I hope to be of assistance here, what about running a VirtualBox install of Windows and using it inside Ubuntu? That is what I am doing with QuickVerse since I had trouble with WINE myself. So, I got VirtualBox running (it was really easy for me), installed Windows XP, then installed QuickVerse. 

I know it may not be the best solution out there but is better than losing it completely. :)

---

