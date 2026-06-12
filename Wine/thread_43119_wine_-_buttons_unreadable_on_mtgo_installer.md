---
title: "wine - buttons unreadable on mtgo installer"
date: 2005-06-20
forum: Wine
---

### Post by josephwalter on 2005-06-20
The labels on the buttons of the magic online (mtgo) installer are unrecognizable characters. The rest of the installer, including the text on the title bar, looks fine (of course, I've only seen 1 screen!).

Here's how far I've gotten:

I installed wine and then clicked on Applications > Run Application and typed "wine /home/josephk/downloads/mtgodl2.exe".  I got the .exe file from the Magic: The Gathering website.  After about a minute, a winzip self-extractor window appeared and proceded to unzip a bunch of files.

The "when done open ./setup.exe" was checked, so next the Magic Online (mtgo) installed appeared. Unfortunately, the labels on the buttons were unreadable. The characters looked something like this:i|jL|i (That's not an exact copy of the text, but my keyboard doesn't have some of the letters).  The two buttons and the pop-up text (that appears when I hold my mouse over a button) have these odd characters. I'm guess the buttons are supposed to be labeled "Continue" and "Cancel".

I have a $home/.wine directory, but I don't have a $home/.wine/config file. The documentation and websites I've read about wine reference this file. I don't know why I don't have one. I was hoping I could find something about fonts in it...

What do I need to install or configure so that these buttons will be readable? And does anyone know why I don't have the config file in my wine directory?

---

### Post by Breeegz on 2006-12-04
bump...


I'm having the same problem

---

### Post by Diabolis on 2007-07-03
Check this folder ".wine/drive c/windows/fonts" not quite sure if this is the exact route but look for fonts folder. Mine was empty so I pasted into it some fonts.

similar error:
[http://ubuntuforums.org/showthread.php?t=480217&highlight=magic+the+gathering](http://ubuntuforums.org/showthread.php?t=480217&highlight=magic+the+gathering)

---

### Post by AJB2K3 on 2007-07-03
I hope some one sort this because its the only reason i havent deleted my xp partition.
Can i just copy the folders over from the xp drive?

---

### Post by hikaricore on 2007-07-03
[http://appdb.winehq.org/appview.php?iVersionId=4447](http://appdb.winehq.org/appview.php?iVersionId=4447)

Known issue with little or no solution.  End of story.

---

### Post by buttons on 2007-07-04
Buh?  What exactly can't you see?

---

### Post by Insomn1a on 2007-07-04
he can't see any letters, which i would guess would be a font issue, i had the same problem with source, so i booted up windows and just burned the entire windows/fonts/ directory to a cd then copied them up into .wine/drive_c/windows/fonts

everything has worked since regarding fonts,

someone reply and help me out with this problem below, i feel like a lepper (8^(
[http://ubuntuforums.org/showthread.php?t=491423](http://ubuntuforums.org/showthread.php?t=491423)

---

### Post by Slimo on 2007-07-05
Can someone who has got MTGO working please tell me what font files are in their wine folder?
If I don't have Windows, can I get these font files from somewhere?

Thanks!!

---

### Post by buttons on 2007-07-05
```
arialbd.ttf        gautami.ttf        micross.ttf        times.ttf
arialbi.ttf        georgiab.ttf       mvboli.ttf         trebucbd.ttf
ariali.ttf         georgiai.ttf       palabi.ttf         trebucbi.ttf
arial.ttf          georgia.ttf        palab.ttf          trebucit.ttf
ariblk.ttf         georgiaz.ttf       palai.ttf          trebuc.ttf
comicbd.ttf        Guitar Pro 5.ttf   pala.ttf           tunga.ttf
comic.ttf          HALFLIFE2.ttf      raavi.ttf          verdanab.ttf
courbd.ttf         HL2crosshairs.ttf  shruti.ttf         verdanai.ttf
courbi.ttf         impact.ttf         sylfaen.ttf        verdana.ttf
couri.ttf          kartika.ttf        symbol.ttf         verdanaz.ttf
cour.ttf           l_10646.ttf        tahomabd.ttf       vrinda.ttf
Dingbats.ttf       latha.ttf          tahoma.ttf         webdings.ttf
estre.ttf          lucon.ttf          timesbd.ttf        wingding.ttf
framdit.ttf        mangal.ttf         timesbi.ttf        
framd.ttf          marlett.ttf        timesi.ttf         

```

Boy, THAT isn't going to format correctly.

I just copied my fonts directly from an old windows xp installation.  Nothing special was done to wine (0.9.40) to get it to work, except I use schedtool to make sure wine uses only one cpu, otherwise updates fail.

No changes were made to config.

```
schedtool -I -a 1 -e wine "c:\Program Files\Wizards of the Coast\Magic Online\magic.exe"
``` is the command.  Works fine with just wine magic.exe if I don't have updates.

---

### Post by Slimo on 2007-07-07
I copied all the font files from a Windows XP installation - still getting the same error (Failed to create font resource sserife.fot fontname serife.fon!!!)
I even made a copy of the sserife.fon file and renamed it serife.fot...but then the installation says it can't find the kickimgs folder (which is in the .wine/drive_c/windows/temp/data folder after extracting the installation program)
Just before the serife.fon error comes up a black window pops up that looks like the MTGO installer.

Can any people who have MTGO working on Ubuntu please let me know what version of Wine they are using, any tweaks, etc because this is really frustrating!!!

Thanks

---

### Post by Slimo on 2007-07-18
Has anyone had any luck with this?
Or should I just wait for MTGO III and hope it works better with WINE?

---

### Post by Diabolis on 2007-07-18
Today I got MTGO working. I'm running **wine-0.9.35** on edgy and I didn't have to do anything special or tricky. I just ran the installer like this: 

```
wine mtgodl2.exe
```

I made a script in my home folder, so I can launch the game easily. This is my file:

```
#!/bin/sh

# Launches game (modify as needed)
WINEDEBUG=-all wine .wine/drive_c/Program\ Files/Wizards\ of\ the\ Coast/Magic\ Online/magic.exe -opengl
```

I gave a look to my fonts folder under wine and it stills empty, fortunately I didn't get any error messages. I've been playing for a little while and everything seems correct.

Recommended reading: [http://ubuntuforums.org/showthread.php?t=497332]("http://ubuntuforums.org/showthread.php?t=497332")

**Once again, newer isn't always better...**

---

### Post by Breeegz on 2007-07-18
> **Slimo said:**
> Has anyone had any luck with this?
Or should I just wait for MTGO III and hope it works better with WINE?

Mine was working until I uninstalled Ubuntu to run a Clark Connect Firewall.  I can't remember what I did, but I think I did the how to on this thread.  Oh, I remember now, I ran MGTO with sudo- I think.

---

### Post by Slimo on 2007-07-20
Hey thanks so much everyone!!  I managed to install MTGO with the "wine mtgodl2.exe" command.
The game is a bit laggy but playable, however the fonts are really small...any luck with fixing this?

---

### Post by malt64 on 2009-06-27
After running wine and being happy, I download a Ubuntu upgrade without thinking it would damaged my wine. 
And then a few weeks later I open wine and run a window program and all the fonts were WINGDING's. :confused:

Search the net and found several leads, none seemed to work out (regidet, etc)....so finally I found this article (link below) and gave it a go. It Worked!!! :D

[http://embraceubuntu.com/2005/09/09/installing-microsoft-fonts](http://embraceubuntu.com/2005/09/09/installing-microsoft-fonts)

---

### Post by Elfy on 2009-06-27
thread closed - a little long in the tooth here I think ;)

---

