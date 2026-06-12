---
title: "Problems with StarCraft and PlayOnLinux on x64"
date: 2013-01-04
forum: Wine
---

### Post by Aeonis on 2013-01-04
I'm running Ubuntu 12.04.  I am using PlayOnLinux and installed StarCraft II.

When I open SC, it goes to load, then quits with this message:

[I]Microsoft Visual C++ Runtime Library
Runtime Error!
Program C:\Program Files\StarCraft II\Support\BlizzardError.exe

R6034
An application has mad an attempt to load the C runtime library incorrectly.[/I]

I did some looking around and everyone mentioned using WineTricks to install the VC2005Express (or something like that).  When I try to do that, it gives me a message that says something like there isn't a package/build for 64-bit operating systems.  I'm stuck at this point.

I would love some help.  I've been working on it for a couple days now and am noobish, but want to learn.  Thank you in advance.:)

---

### Post by matze76 on 2013-01-04
Same Problem. Ubuntu 12.10 + PlayOnLinux 4.1.8  
 

 1. Start PlayOnLinux 4.1.8
 2. inside the list is:
 

 StarCraft II Editor
 StarCraft II Wings... ?
 

 3. Mouse - Right-Click on &#8222;StarCraft II Wings of Liberty
 4. select: Wine configuration
 5. CHANGE Windows-Version: into Windows Vista or Windows XP
 6. OK
 7. Start the Game
 8. Have Fun
 

 - maybe the graphic is **** . I try to fix that later
 

 

 Selbe Problem. Ubuntu 12.10 + PlayOnLinux 4.1.8  
 

 1. Starte PlayOnLinux 4.1.8
 2. in der Liste sollte stehen:
 

 StarCraft II Editor
 StarCraft II Wings... ?
 

 3. Rechtsklick auf : &#8222;StarCraft II Wings of Liberty
 4. auswählen Wine Konfiguration
 5. wechsel die Windows-Version: in Windows Vista oder Windows XP
 6. OK drücken  
 7. Start the Game
 

 Die Grafik ist beim Spiel bei mir leider noch beschissen und es läuft nicht flüssig.

---

### Post by Umbra Diaboli on 2013-01-04
BTW: Is it safe to play SC2 on Battlenet? Are there any problems by bans through warden? (their anti-hack system).

I really want to play this game on Ubuntu, but I fear warden will confuse wine with hacks and ban my account.

Thanks!

---

### Post by Aeonis on 2013-01-04
> **Umbra Diaboli said:**
> BTW: Is it safe to play SC2 on Battlenet? Are there any problems by bans through warden? (their anti-hack system).

I really want to play this game on Ubuntu, but I fear warden will confuse wine with hacks and ban my account.

Thanks!

I called Blizzard yesterday and talked to a gentleman who said, "Yeah, you need Wine to really run StarCraft on Linux.  We don't see it as a third party tool that gives you an advantage.  That's really what we look for.  If you're running a piece of software that gives you an unfair advantage, we will see those games and then ban the account without any questions.  It's an automated system."

I have no interest in cheating.  I want to compete this year sometime, but I have to get out of Silver league first (don't laugh too hard).

@Matze:  I will try this on my lunch break today.  I went into the configuration and set it to Windows 7, but I didn't think to try it in XP or Vista.  If these don't work, is there a way to get that vc2005express on a 64-bit system?

---

### Post by KBentley57 on 2013-01-04
I've been having problems running SC2 smoothly too, it's what inspired me to post this thread, to which I've gotten no responses yet: [http://ubuntuforums.org/showthread.php?t=2100033](http://ubuntuforums.org/showthread.php?t=2100033) .  

I use PoL, and wine 32 bit version 1.5.10, 1.5.19, and 1.5.20 smoothly.  I've installed about everything that is able regarding the vcruns and d3dx, but I can't get it to run past ~30 fps.  I've also had a problem where I have to select low shaders, else I get a pink background that will not go away.  I'll leave the specs of my system out, as they are in the other thread.

Can any of you get your hardware shaders to run on anything but low?

BTW, I run multiplayer just fine.  I've never had a problem with authentication or online play.

---

### Post by Aeonis on 2013-01-04
> **KBentley57 said:**
> I've been having problems running SC2 smoothly too, it's what inspired me to post this thread, to which I've gotten no responses yet: [http://ubuntuforums.org/showthread.php?t=2100033](http://ubuntuforums.org/showthread.php?t=2100033) .  

I use PoL, and wine 32 bit version 1.5.10, 1.5.19, and 1.5.20 smoothly.  I've installed about everything that is able regarding the vcruns and d3dx, but I can't get it to run past ~30 fps.  I've also had a problem where I have to select low shaders, else I get a pink background that will not go away.  I'll leave the specs of my system out, as they are in the other thread.

Can any of you get your hardware shaders to run on anything but low?

BTW, I run multiplayer just fine.  I've never had a problem with authentication or online play.

Way back when, I got SC to work in Ubuntu, but I could only use Low settings and it still lagged the entire time.  When I switched to Win 7, defaults were "EXTREME".  It was awesome.  I know you can get great performance out of Ubuntu/Linux, but I just don't know how.  So, I want to learn it.

---

### Post by Aeonis on 2013-01-04
> **matze76 said:**
> Same Problem. Ubuntu 12.10 + PlayOnLinux 4.1.8  
 

 1. Start PlayOnLinux 4.1.8
 2. inside the list is:
 

 StarCraft II Editor
 StarCraft II Wings... ?
 

 3. Mouse - Right-Click on „StarCraft II Wings of Liberty
 4. select: Wine configuration
 5. CHANGE Windows-Version: into Windows Vista or Windows XP
 6. OK
 7. Start the Game
 8. Have Fun
 

 - maybe the graphic is **** . I try to fix that later
 

 

 Selbe Problem. Ubuntu 12.10 + PlayOnLinux 4.1.8  
 

 1. Starte PlayOnLinux 4.1.8
 2. in der Liste sollte stehen:
 

 StarCraft II Editor
 StarCraft II Wings... ?
 

 3. Rechtsklick auf : „StarCraft II Wings of Liberty
 4. auswählen Wine Konfiguration
 5. wechsel die Windows-Version: in Windows Vista oder Windows XP
 6. OK drücken  
 7. Start the Game
 

 Die Grafik ist beim Spiel bei mir leider noch beschissen und es läuft nicht flüssig.

I just tried this and it didn't work :(

---

### Post by matze76 on 2013-01-04
@aeonis. i forgot to say, i use ubuntu 32bit. and my experiences with ubuntu are limited to only 1 week. 
i' ve had some install-deinstall-procedures to reach that its running. MY steps were to kick out WINE and PLAYONL. completely, 
# then installing P-O-L
# then in the menu 3.position "german: "Wine-Versionen-Verwalten" /Wine-Versions-dontknwohowinenglish
# i choosed manually from list to add versions: 1.5.10, 1.4 and 1.2 (with the faith, it will work any of that)
# then i made the steps, how i wrote before.

but i am glad to have win7 as 2nd option until it will work.

---

