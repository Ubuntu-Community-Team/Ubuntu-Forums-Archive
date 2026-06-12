---
title: "Rome: Total War - Ubuntu?"
date: 2007-08-09
forum: Wine
---

### Post by buntunub on 2007-08-09
Whats the deal with Ubuntu and this game? I have it running flawlessly on the same machine running Sabayon (seperate partition, same machine). Everything works and the game runs actually smoother than it does on my windows machine. But, same wine/cedega version, same machine, same install method -- wont work on Ubuntu?! Whats the deal here?.. Same thing with Dark age of Camelot -- Same machine, same setups, same app versions -- wont work with Ubuntu but works flawlessly on Sabayon/Gentoo... Uhh.. Hello?! Linux is linux, or so ive been told, but the fact is that only about half of my hardware runs with Ubuntu that works flawlessly with Sabayon on fresh installs of both OS's. Not touting Sabayon in any way mind you, but its just annoying as all getout. I am trying to settle on a single distro that is both fully functional AND stable. Thing is, I get 100% functionality with brand spankin new hardware on Sabayon, but sometimes not so stable system, and with Ubuntu I get stability, but only about 50% functionality. Gah!

Anyway, if anyone has a way to make Rome or Dark age work in Ubuntu, much appreciated.

---

### Post by hikaricore on 2007-08-09
I believe Sabayon comes with restricted video drivers preinstalled.

Have you installed the proper video drivers on Ubuntu Linux?

I could be wrong just offering a suggestion.

---

### Post by buntunub on 2007-08-09
Yes. The NVIDIA drivers have been loaded, although they are not necessary to play this game that I know of. The problem is more with the Buntu's underlying codebase I think.

---

### Post by hikaricore on 2007-08-10
The Nvidia (display) drivers are required for almost anything to function properly that uses the hardware under Linux, even a simple task like web browsing can bog down an improperly configured X server.  What type of Nvidia card are you using? and what driver? 

I think you should narrow it down a bit and stop blaming *buntu when you're not entirely sure what the cause is.

---

### Post by buntunub on 2007-08-10
> **hikaricore said:**
> The Nvidia (display) drivers are required for almost anything to function properly that uses the hardware under Linux, even a simple task like web browsing can bog down an improperly configured X server.  What type of Nvidia card are you using? and what driver? 

I think you should narrow it down a bit and stop blaming *buntu when you're not entirely sure what the cause is.

Good point. Im using whatever NVIDIA drivers came with Fiesty after I clicked on the "yes", "OK", "Yes" buttons to install them. I have an NVIDIA 6150 integrated card. It has no trouble running beryl, compiz and compiz fusion, so the drivers appear to be working just fine for AIGLX and acceleration. I turn all that off for Rome though, because in Sabayon, Rome wont work with anything but Kwin running windows. I do think that source compiled systems tend to run much much better, but im unsure if that would impact a high performance game like Rome. I think the kicker is that I cant get Dark age to run on Ubuntu, and that is a much much older game using very old source codes (7 years old). That game runs with no issues so long as you disable pixel shaders (which of course I tried on Ubuntu but to no avail). I want to try out Oblivion on Ubuntu, but I cant even get Dark age to work on it so im not sure how well it would run an even more demanding game like that one (which of course also runs flawlessly in Sabayon via cedega).

---

### Post by JesterDev on 2007-08-10
Just a thought, but are you running the same verisons of Codega/Wine on both distro's? I have Total War working under Ubuntu and used just a standard installation.

---

### Post by unbuntu on 2007-08-10
> **JesterDev said:**
> Just a thought, but are you running the same verisons of Codega/Wine on both distro's? I have Total War working under Ubuntu and used just a standard installation.

How did you get it working?  I'm running Feisty and Wine 0.9.41 and  a fresh install of Rome:TW.  But after I run the executable, all I got was 
> 
fixme: process:IsWow64Process (0xffffffff 0x34eadc) stub!

 which is quite annoying since it doesn't tell me anything...

---

### Post by Nameless One on 2007-08-11
What do you mean Cedega/Wine? They are both two completely different beasts and you're either using one or the other.
It's rather well known that 'Rome: Total War' is unplayable on Wine, even on the most recent version. 
[http://appdb.winehq.org/appview.php?iVersionId=4496]("http://appdb.winehq.org/appview.php?iVersionId=4496")

Only Cedega 6 can run RTW well ([http://www.cedega.com/forum/viewtopic.php?t=8134&highlight=rome+total+war]("http://www.cedega.com/forum/viewtopic.php?t=8134&highlight=rome+total+war")) so make sure you have Cedega 6.0.2 installed and then you might want to look at this link here: [http://cedegawiki.sweetleafstudios.com/wiki/Rome:_Total_War]("http://cedegawiki.sweetleafstudios.com/wiki/Rome:_Total_War")
There are several tips and notes there on how people got the game to work.

---

### Post by buntunub on 2007-08-13
"The game DOES work fine in Cedega 6.0.1, just start the game up in WinXP mode for Copy Protection to pass."

Figures. I installed it under WinME and attempted to play under WinME, NT40 and NT351. The Debugger says to run it under NT351. It runs flawlessly in Sabayon if you run it under NT351, but not in Ubuntu. Im pretty sure I tried to run it under XP with no joy but ill try again tonight.

---

### Post by buntunub on 2007-08-13
Well ill be a...

Downgraded to cedega 6.0.1 and ran it under XP and it loaded right up without a hitch and running flawlessly. Now, on to Oblivion heheh.

---

### Post by geezerone on 2008-09-30
Just trying to run RTW in Wine but when starting the application the credits appear then the message about file missing:  *data/animations/SG 01 idle.cas*?

---

### Post by LeftHander on 2008-12-16
same here, any help?
3 cds install used, worked ok, not great, loads credits wieirdly in disconfigured ws-fs screen for milisecs then the same error message above, animation file missing (nocd patch in use for launch)

---

### Post by Rytron on 2011-09-12
I loved RTW when I was using XP {pre 2008} Has anyone got RTW to work in Ubuntu 10.04 or similar distro? I'd greatly appreciate it. Thanks.

---

### Post by 5dolla on 2011-09-12
well im in archlinux but i imagine ubuntu would produce the same 
results. I have rome total war working great with the new build of wine :)[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22972&iTestingId=62562]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=22972&iTestingId=62562")

---

### Post by Rytron on 2011-09-13
> **5dolla said:**
> well im in archlinux but i imagine ubuntu would produce the same 
results. I have rome total war working great with the new build of wine :)[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22972&iTestingId=62562]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=22972&iTestingId=62562")

Cheers. Are there any special steps I should take or is it a straight forward install?

---

### Post by 5dolla on 2011-09-14
I'm not sure really ... I installed it in a pre existing wine prefix that had vrun2005 and d3dx9. you do have to make sure you tick on the capture mouse option in your winecfg

---

### Post by Rytron on 2011-09-15
> **5dolla said:**
> I'm not sure really ... I installed it in a pre existing wine prefix that had vrun2005 and d3dx9. you do have to make sure you tick on the capture mouse option in your winecfg

Ok, I will give it a go. Thanks.

---

### Post by Rytron on 2011-09-22
> **5dolla said:**
> I'm not sure really ... I installed it in a pre existing wine prefix that had vrun2005 and d3dx9. you do have to make sure you tick on the capture mouse option in your winecfg

Did you mean [COLOR="Magenta"]vcrun2005[/COLOR]? I installed that and [COLOR="Magenta"]d3dx9[/COLOR]. I launch the game, it goes black and then brings me back to POL. I also checked '[COLOR="Magenta"]Automatically capture the mouse in full-screen windows[/COLOR]' - I presume you meant that.

What WINE version are you using in POL for RomeTW?

Update: I ran the RomeTW fixed exe with regular WINE (I mean without POL) and it got to the menu. It had sound. When to select a battle it begins to load but then crashes!

---

### Post by Rytron on 2011-09-23
I enabled 'GLSL' in POL and it works! WINE is incredible! :popcorn:

---

