---
title: "Trouble with Starcraft/Battle.Net with Wine 0.9.46"
date: 2007-10-10
forum: Wine
---

### Post by ghindo on 2007-10-10
I am running Feisty Fawn on a Dell Inspiron 1420n.

I am attempting to play Starcraft:  Brood War with Wine 0.9.46, but every time I attempt to connect to Battle.Net, the program freezes.  The screen I get when I attempt to connect to Battle.Net shows some of the graphics, but none of the text.  (See attached image)

I realize that there have been multiple threads about this subject, but try as I might I could not find a solution in any of them.  

Help please?

---

### Post by TidusBlade on 2007-10-10
I don't have much info about Battle.NET but theres a possibility that Battle.NET dosent work on WINE, didn't work for me on Warcraft III...

---

### Post by ghindo on 2007-10-11
Bump.

---

### Post by ghindo on 2007-10-12
Bump.  Considering how common this question seems to be, someone must have an answer.

---

### Post by Enverex on 2007-10-12
It sounds like this bug - [http://bugs.winehq.org/show_bug.cgi?id=5253](http://bugs.winehq.org/show_bug.cgi?id=5253)
Always check the Wine bug site.

---

### Post by donkyhotay on 2007-10-13
It is *possible* to configure starcraft so it will connect to battle.net under wine but is pretty frustrating to set up. I did it once last year but after repartitioning my drives decided it wasn't worth trying to do again (I generally use hamachi to play with my friends anyway). While I can't remember the exact steps to get it working anymore I do remember that the main problem that prevented me from connecting turned out to be something with the fonts. As I said it's been a long time since I've done it but if you do a google search for 'starcraft wine battle.net fonts' you should find working instructions to get connected. Personally though I would recommend hamachi which is much easier.

---

### Post by Enverex on 2007-10-13
It's not difficult at all and I already posted a link to the instructions.

---

### Post by ghindo on 2007-10-15
> **Enverex said:**
> It sounds like this bug - [http://bugs.winehq.org/show_bug.cgi?id=5253](http://bugs.winehq.org/show_bug.cgi?id=5253)
Always check the Wine bug site.Thanks for the link.

From what I could understand from it, the issue is either one of Fonts or a Rendering engine.  Am I correct?  The Wine site was somewhat ambiguous and I couldn't figure out how to fix it.

Sorry if I'm being dense.  :-#

---

### Post by Enverex on 2007-10-15
It's the missing fonts issue.

---

### Post by ghindo on 2007-10-15
> **Enverex said:**
> It's the missing fonts issue.I'm still confused.  Does that mean I should follow instructions in [**Post 56**]("http://bugs.winehq.org/show_bug.cgi?id=5253#c56") and delete the following?```
/usr/share/wine/fonts/sserife.fon
/usr/share/fonts/truetype/ttf-arabeyes/ae_AlBattar.ttf
/usr/share/fonts/truetype/ttf-devanagari-fonts/samanati.ttf
```
Or does that mean I should follow the instructions in [**Post 78**]("http://bugs.winehq.org/show_bug.cgi?id=5253#c78")?```
To overcome this problem you need to install some components to Wine.

Use WineTools to install them (I use version 0.9.12).
You can get WineTools here: http://www.von-thadden.de/Joachim/WineTools/

In the "Base Setup" menu install:

1. "TrueType Font Arial"
2. "DCOM98"
3. "Microsoft Foundation Clases 4.0"
4. "Internet Explorer 6.0 SP1" (twice, if needed)
```
If it's the latter, is there any way I can solve this issue without WineTools?

Thanks again!

---

### Post by Enverex on 2007-10-15
Install the Arial font first, that fixed it for me.

---

### Post by SaMuRaI_777 on 2007-12-25
Unfortunately wine 0.9.46 didn't work for me, But with wine 0.9.43 it works pretty well, do the same with the settings on replacing arial and taking out the fonts
with this you'll at least be able to login into Some servers on Battle.net, (Europe and Asia for me)
I couldn't logon to Us.east or west

---

### Post by MaindotC on 2007-12-30
I get the "wine tools cannot run with a Wine version older than 20050628" message.  Using 9.52.  Sweet.  Ya, ya, I know - it's free and nothing is guaranteed.  I'm just letting you know.  Seems a little odd to be getting that msg.

---

### Post by pizpot on 2008-02-08
Solution to get right wine so battlenet works:

To downgrade wine, uninstall it:

sudo apt-get remove wine

Then get wine 9.45 for ubuntu 7.04 (even though you are at 7.10 don't fret) from here:

i386:
[http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine-dev_0.9.45~winehq0~ubuntu~7.04-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine-dev_0.9.45~winehq0~ubuntu~7.04-1_i386.deb)

Then run that, then go into Synaptic and lock the version so it does not upgrade by clicking System->Administration->Synaptic Package Mager and searching for wine, selecting "wine" in the list, and clicking Package->Lock Version

Tada, now you can join Battlenet and play warcraft3 or the war3 demo till you are blue in the face. :-)

---

### Post by JJMarvin on 2008-02-10
I've installed wine 9.45. and even 9.43. Winetools are not running with message cannot run with wine version older than 20050628.

Can it be since I'm not removing starcraft it self from wine?

---

### Post by parkus on 2008-03-16
my problem is that i can only run the game in a windowed mode. in winecfg when i allow window manager to control, it crashes when connecting to battlenet. however when i set a virutal desktop, it runs fine, but in 640x480, and not at what i set the virtual desktop to be.

---

### Post by NightwishFan on 2008-03-16
The game is hardcoded to run in 640x480.

---

### Post by parkus on 2008-03-16
oh and i found that you can run

 apt-get install msttcorefonts; fc-cache -fv

and that font will be installed for you

---

### Post by Enverex on 2008-03-16
> **parkus said:**
> my problem is that i can only run the game in a windowed mode. in winecfg when i allow window manager to control, it crashes when connecting to battlenet. however when i set a virutal desktop, it runs fine, but in 640x480, and not at what i set the virtual desktop to be.

Virtual Desktop spoofs the desktop space, but if an application goes "full screen" then the Virtual Desktop will change to the size that the application wants (in this case Starcraft is 640x480). Wine won't force-resize fullscreen applications (as it would require more processing time and code).

---

### Post by prssn on 2009-03-30
I don't even have the folder ttf-arabeye
I deleted sserife.fon, but it didn't work! Help?

---

### Post by malathion on 2009-03-31
I've been connecting to battle.net with wine 1.1.18 with no problems. The trick is to go into Winecfg and reate a special application setting for StarCraft.exe and set under Graphics, uncheck window manager control and decoration. I'm not sure if that's your problem but it's worth a shot.

For more info on how to run SC/BW on Battlenet under linux, check out this post: [http://www.teamliquid.net/forum/viewmessage.php?topic_id=61452#14](http://www.teamliquid.net/forum/viewmessage.php?topic_id=61452#14)

---

### Post by golem1989 on 2009-07-11
same problem... and can't download winetools
did sth work for you?

---

