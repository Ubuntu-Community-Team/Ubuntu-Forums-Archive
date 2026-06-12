---
title: "Some helpwith wine please?"
date: 2008-03-13
forum: Wine
---

### Post by Wletnzft on 2008-03-13
Ok, I've been trying to install battlefield 2142 but can't start to play, because everytime it displays this error message:

"please ensure battefield 2142 install disc is in drive, select OK, and restart the application"

Now, I searched the internet, and found this site: 
[http://appdb.winehq.org/appview.php?iVersionId=6637](http://appdb.winehq.org/appview.php?iVersionId=6637)


Well, the only problem is that I, beeing a complete noob a this, can't actually understand what they are trying to say very well. This for instance:

 [I]To run the game you should use the Autorun.exe program instead of running BF2142.exe directly. The copy protection system is much more likely to work if you use the Autorun program. If it still says the disk is not in the drive, running cd .. && umount d\: && mount d\: && cd d\: from d: usually fixes it. Sometimes you will need to do this a few times. If it still doesn't work you can try ejecting the disc and reinserting it. You should also set WINEDEBUG to "-all" otherwise all the terminal output will significantly slow down the game.

cd "${WINEPREFIX}"/dosdevices/d\:
WINEDEBUG=-all wine Autorun.exe

[/I]

Now, I'm proficient in the english language, but I really can't understand what these instructions tell me to do.


So the question is: can any one of you kind souls out there please translate this to "ordinary english" for me. I just don't understand what "running cd .. && umount d\: && mount d\: && cd d\: from d: usually fixes it" means.


Kind thanks!

---

### Post by {BzF}~JOKesTER on 2008-03-13
Dude Ok Just Do This:

Go To Your Battlefield Install Folder {In The Wine C:\ Drive}

*** Game license breaking explanations removed by staff ****

Hope This Helps -Keep Me Updated!!!

Thank Me Pls!

---

### Post by p_quarles on 2008-03-13
Moved to the Wine forum, mainly so that I can point the OP to the helpful stickies at the top of this page. You will get a much better sense of what Wine can/cannot do, and how it works, after reading those.

---

### Post by Wletnzft on 2008-03-13
> **{BzF}~JOKesTER said:**
> Dude Ok Just Do This:

Go To Your Battlefield Install Folder {In The Wine C:\ Drive}

*** Game license breaking explanations removed by staff ****

Thank Me Pls!

I might just be stupid, but what are you referring to when you write "extract the file" ??

thanks for the answer

---

### Post by {BzF}~JOKesTER on 2008-03-13
Right Click The Downlaoded File And Click "Extract Here" And Than Open That Folder And Place BF2142 In The Battlefield Folder -{Your Not Stupid - Don't Say That}

---

### Post by Wletnzft on 2008-03-13
ok. Now, where do I download this file? link?

---

### Post by {BzF}~JOKesTER on 2008-03-13
I Gave It To You Already Here It Is Again:

[http://www.freeinfosociety.com/downloads/nocdcracks/battlefield2142-nocd-1_1-ENG.zip?phpMyAdmin=af0f6b4465fe3f904426eaeb3dc0e3fa](http://www.freeinfosociety.com/downloads/nocdcracks/battlefield2142-nocd-1_1-ENG.zip?phpMyAdmin=af0f6b4465fe3f904426eaeb3dc0e3fa)

:):):)

---

### Post by Wletnzft on 2008-03-13
Oh, yeah, sorry.

When I right-click the icon, and click "open with wine windows emulator" nothing happen though.

---

### Post by {BzF}~JOKesTER on 2008-03-13
It Has To Be In The Battlefield Folder.

---

### Post by Wletnzft on 2008-03-13
it is

---

### Post by Wletnzft on 2008-03-13
well, I don't get any error message, but the game won't start anyways. 

Anyways: thanks for you help!

---

### Post by {BzF}~JOKesTER on 2008-03-13
Nevermind what i said before than

You Backed Up The Original BF2142.exe Right - Ok Now Put It Back In The Battlefield Folder.

Ok Next.

Place Your CD In Your CD Drive - Now Open The CD Drive -{By Going To Computer And Than CD Drive}

And Run Run:

Autorun.exe With Wine

And Click "Play"

If It Gives An Error I Have A Fix So If So Pls Reply!!

---

### Post by Wletnzft on 2008-03-13
This happens:

If i just right click I get "couldn't setup.ini"

If Run it in terminal I get the "start bf2142 button"
clicking it gets me the "please ensure cd rom" error message

---

### Post by {BzF}~JOKesTER on 2008-03-13
I Need You To Give Me The Path To Your Battlefield Driectory

---

### Post by Wletnzft on 2008-03-13
/home/christian/.wine/drive_c/Program Files/Electronic Arts/Battlefield 2142

---

### Post by {BzF}~JOKesTER on 2008-03-13
Ok Do This:

Run This File By Double Clicking On It -

Give Me Any Error Code {It Will Probly Give You 1-But I Can Fix It If So}

---

### Post by Wletnzft on 2008-03-13
this is the error code I get:


fixme:mountmgr:harddisk_ioctl unsupported ioctl 70020

---

### Post by {BzF}~JOKesTER on 2008-03-14
Ok I Got It!

First:
Download This Version Version Of Wine. - It Is An Older Version - But It Works With Copy Protected Games.

[http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.48~winehq0~ubuntu~7.10-1_i386.deb]("http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.48~winehq0~ubuntu~7.10-1_i386.deb")

Install It By Double-Clicking It And Hitting Install.

{If It Won't Let You - In A Terminal Type: apt-get remove wine
And Than Try Again}

Now Re-install The Game...

Download:

[http://www.dll-files.com/dllindex/download.php?d3dx9_29download0VMhS0ZDhT]("http://www.dll-files.com/dllindex/download.php?d3dx9_29download0VMhS0ZDhT")

And Extract The Folder And Place The .dll In The:

C:/Windows/System32

Folder.
-----------------------------------------------------------------------------------------
Now Do This:

Browse To This Directory:

C:/Program Files/Electronic Arts/Battlefield 2142/mods/bf2142/Movies: 

And Delete These Files:

Dice.bik 
Intro.bik 
Legal.bik 
Legal_na.bik 
EA.bik

Now Last But Not Least.

Install That CD Patch

And Run The Shell Script I Gave You.!!!:)

If You HAve Any Problems Please Let Me Know-

Otherwise Please Feel Free To Hit "Thank" As Much As You Can!!!!:)

---

### Post by Wletnzft on 2008-03-14
Wow! Thanks for all the help!

But I'm stuck though. I can't seem to uninstall bf. 

What should I do?

---

### Post by {BzF}~JOKesTER on 2008-03-14
Why Can't You??

Could You Give Me More Info Please??:)

Does It Give An Error Message Or What??:confused:

---

### Post by lol3r on 2008-03-15
it's works for unpatched version but not for the version with 1.40 patch


so i need help!!!:confused::confused::confused:

---

### Post by frodon on 2008-03-16
Ok i will try to make it clear :

Any explanaition/details on how to use a NoCD crack is not allowed here. Use of NoCD crack brakes the game license even if you own the game.
We all perfectly know wine don't support all copy protection systems and that in some cases they are needed.
It is ok to mention the need of it but not more, any additional link or explanaition about NoCD crack will make the thread closed.

---

