---
title: "HELP: Problem Installing MTGO with Cedega or Wine (Magic the Gathering Online)"
date: 2007-07-11
forum: Wine
---

### Post by jasonkx on 2007-07-11
Hi Guys, I've intalled Linux now and i'm a Newbie user, but some questions i got on net , but this one its making me crazy ^^
I installed Cedega on my linux and tryed to install Magic The gathering Online but when i do i allways get this error, even on Wine
[IMG]http://img67.imageshack.us/img67/2906/capturadatelarh6.png[/IMG]

Anyone knows how i can get this error off?
Or where i got to isntall the windows fonts ??

plz help me!!
i dont wanna go back to windows ^^

---

### Post by cogadh on 2007-07-11
Start by installing the msttcorefonts package. Run this in a terminal:
```
sudo apt-get install msttcorefonts
```
However, according to the Wine AppDB, the game has had problems with fonts in the past, but it doesn't have any test data beyond Win 0.9.17:
[http://appdb.winehq.org/appview.php?iVersionId=4447](http://appdb.winehq.org/appview.php?iVersionId=4447)
Even with the MS fonts installed, you may still have problems.

---

### Post by jasonkx on 2007-07-11
I intalled the sudo apt-get install msttcorefonts but still getting the same error on Cedega.
i know the font erros but the initial font error i know that its not a problem cause on Cedega GameDB MTGO its there with Screen SHoots

---

### Post by cogadh on 2007-07-11
There is a post on that AppDB page that seems to address this:
> I tried to install mtgo and I got this error "Failed to create font resource sserife.fot fontname sserife.fon". I went to my .wine folder and noticed that the fonts folder (windows fonts) was empty, so I made a copy of a ttf file (ms sans serif.ttf) from a computer with windows xp installed. I placed 2 copies into my fonts folder (wine folder) and renamed each one with the name of the files that appeared in the error message (including the extension fot and fon).
It seems that will at least get you past the error. If you don't have access to a Windows XP machine to copy the font files from, you may be able to find them online.

---

### Post by jasonkx on 2007-07-11
i dont know where the folders is ^^ and i find one with Fonts but allways says that i dont have permition to put file there ^^

---

### Post by cogadh on 2007-07-11
You want to put it in Wine's font folder: /home/*username*/.wine/drive_c/windows/fonts

The ".wine" directory is a hidden directory in your home folder. Open the file browser and press CTRL-H to display hidden files.

---

### Post by jasonkx on 2007-07-11
I will try cause my cedega and wine dont want to open the progrmas anymore ¬¬
i will try to get out WINE and CEDEGA and reinstall

---

### Post by jasonkx on 2007-07-11
i have put the fonts there but has 2 diferents area Dosdevices and drive_c what should i put on?

---

### Post by cogadh on 2007-07-11
Put it in .wine/drive_c/windows/fonts

---

### Post by brownbat on 2007-10-07
1) Had the same error as above, right as the MTGO installer finishes unzipping its resources, it crashes with: "Failed to create font resource sserife.fot fontname sserife.fon!!!"

2) Tried placing copies of my windows font files in ".../.wine/drive_c/windows/fonts/" as suggested above.
(I found "sserife.fon" in my "C:\windows\fonts" directory, I just made a copy and renamed it to "sserife.fot" for the second file.)
There was no change in behavior.

3) Then realized it's talking about resources pre-installation. Noted where the installer thought it was unzipping everything to, the "C:\windows\temp" directory. Poking around in there, I found a lot of magic files in the "data" subdirectory. Tried placing my "sserife.fon" and fake "sserife.fot" files in the data directory, ".../.wine/drive_c/windows/temp/data"

This eliminated the error for me.

However, a new error came up asking for vgasys.fon and vgasys.fot.

I will try the process again with these, and let you know of my progress.

 (minutes later... )

Step 2: 
I copied over vgasys.fon, which I found in the same C:\Windows\fonts\ directory. I also noticed a "magic.fot" file while there, so I copied that as well.

This time, out of curiosity, I didn't make an extra .fot file, and even renamed my sserife.fot file to sserife.bak. So I have 3 extra files in that temp/data directory: "sserife.fon" "vgasys.fon" and "magic.fot"

After just those three files in the data directory, the setup program began just fine.

(*It might be that either magic.fot or vgasys.fon on their own would have been sufficient, I can't say.)

Best of luck.

---

### Post by brownbat on 2007-10-07
After my last post, I was able to complete the installation of MTGO and play a match online against someone else.

Aside from the incredible slowness of the game, everything seemed to work fine.

---

### Post by notdarkyet on 2007-10-07
WOW! Thanks this thread worked perfect for me, thanks for everyones input it solve the same problem you all had for me too.

---

### Post by TheMightyBorys on 2007-10-16
Though I would add my two cents here after trying this process for myself. I would have never thought that in my first post I would be GIVING help. =D

To save yourself some headache, if you have an XP CD, you can extract the fonts from there with [cabextract]("http://packages.ubuntu.com/feisty/utils/cabextract"). (I found that under Feisty it was already installed)

Commands for the lazy (or learning, like me :) ) :

> 
mkdir ~/.wine/drive_c/windows/temp/data
cd /cdrom/I386
cp sserife.fo_  vgasys.fo_ ~/.wine/drive_c/windows/temp/data
cd ~/.wine/drive_c/windows/temp/data
cabextract sserife.fo_ vgasys.fo_


Then download the installer, and install install with WINE (it takes forever, just like in Windows!)

Though now that I have it installed, it seems to just die when it tries to bring up the intro video. =(

---

### Post by kringle on 2007-10-26
Thanks TheMightyBorys!  Your instructions revived my three year old account.  I just played a match, a tad sluggish but totally playable, and won.  Right now Magic is up and running, I'm sitting in the lobby right now, on my Desk2 Screen.

The only instructions I had to modify was changing:
cd /cdrom/I386
to
cd /cdrom/i386

Other than that, worked great!

---

### Post by adarkmethod on 2007-11-05
I don't have access to a windows disk and cant find the fonts online. would anyone mind posting them for me?

---

### Post by natehatewindows on 2007-11-26
i also would like these fonts...anyone have them? thanks!

---

### Post by adarkmethod on 2007-12-12
again, will someone please post these? I'm trying to avoid pirating something for once in my life...

---

### Post by cogadh on 2007-12-13
You're asking us to post Microsoft-owned fonts that are not legally available for free, but only come with Windows and are attached to the Windows license, but you don't want to pirate something... 

You do see the irony here, right?

---

### Post by buttons on 2007-12-14
You don't need them.  If you have tahoma.ttf from msttcorefonts (or windows, or any of the free font websites) you can copy that to sserife.fon/fot and vgasys.fon/fot and it will work.  In fact, I just did it.

---

### Post by hurdlebeast on 2008-02-17
If you are like me, and had your downloader crap out at about 97% (internet connection timed out on blah blah blah):

1) open System Monitor with the installer running.
2) find the "setup.exe" process, under the process tab.
3) right click and choose "Change Priority"
4) move the priority slider to the left, increasing it's priority.

I think this is "common knowledge," but it took me a while to find it online, so i posted it here. also, make sure you close any unneccesary programs while running the downloader, and you might still have to click on the boxes that occasionally pop up.

---

### Post by deadguy on 2008-03-06
Ive gotten past all the fonts issues, thanks to the above posts!  But I've hit another snag: 

"Could not get host by name.  Try again?"

If I say no, don't try again, the installer quits.
If I do try again, the status bar says:

"Checking file: tos.txt"

then pops up the same error again.

I couldn't find tos.txt anywhere, but did find tos.bin in the data directory.

any ideas?

---

### Post by deadguy on 2008-03-06
I found this thread:

[http://www.lathspel.net/MTGOLinux/MTGOLinux1.html](http://www.lathspel.net/MTGOLinux/MTGOLinux1.html)

the initial post seemed to deal with my problem.  being from 2003, I had hoped that it would be fixed in the current release of wine, so I updated mine from

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

but it still doesnt work!

---

### Post by deadguy on 2008-03-06
OK i fixed it.  I had changed my hostname by editing /etc/hostname, but hadn't updated /etc/hosts, which broke gethostbyname_r.

---

