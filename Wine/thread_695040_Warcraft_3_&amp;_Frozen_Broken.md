---
title: "Warcraft 3 &amp; Frozen Broken"
date: 2008-02-12
forum: Wine
---

### Post by Sugi on 2008-02-12
How some reason unknown to me, My warcraft 3 and Frozen is broken.  I think Diablo II and Maybe Starcraft isn't working as well.  I could be wrong about the starcraft and diablo II, but warcraft 3 isn't working for sure.  I don't think I did anything to my wine directory, if any I did install Call of Duty 4, but that didn't work for me yet.  I have to do some config with that game, but thats the only thing I can come up with that may have broken warcraft 3.  A while ago, I was getting error that my cd wasn't right or something.  But I have been playing this installation of warcraft 3 (same directory) maybe since dapper.  I do not know what to do?  I have reinstalled warcraft 3 and wine, but that is not working.

My terminal:

> :~$ wine /home/LongPENIS/Trash/Games/Video\ Games/Warcraft\ III\ \&\ Frozen\ Throne/Frozen\ Throne.exe
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34f3f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f7d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f3dc,0x00000000), stub!
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34f3f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f7d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f3dc,0x00000000), stub!
:~$


Sugi

---

### Post by Sugi on 2008-02-12
UPDATED:

Current Games before Warcraft 3 Broke:
Oblvion
Starcraft (Maybe Up to Date)
Diablo II (Up to Date)
Warcraft 3 & Frozen
Lineage 2

Working:
Oblivion
Starcraft
Diablo II

Not Working:
Warcraft 3
Lineage 2 (just needs more configing, it's a little *****)

Uninstalled
Call of Duty 4 (gonna try to reinstall it later)

---

### Post by Sugi on 2008-02-13
Bump

---

### Post by Toffeeapple on 2008-02-13
Hi..

You don't mention versions..

But for me Warcraft will not run with 0.9.54 but it will for 0.9.51

I use PlayOnLinux which makes it very easy to assign different versions of wine to different games, if you haven't already you should try it.

---

### Post by FrozenFox on 2008-02-13
[http://ubuntuforums.org/showthread.php?t=695302](http://ubuntuforums.org/showthread.php?t=695302)

Please see my second and third responses on this thread.

---

### Post by Sugi on 2008-02-14
Toffeeapple:  **WOW** I actually have not heard of PlayOnLinux before just installed it on two PC.  (One PC is my testing software box)  I am installing Dark Crusade at the moment.  Is there a way to just drap and drop a directory or use a pre-installed game with PlayOnLinux?  That's going to be the only way I am going to be able to play warcraft 3.

My current version of wine: 0.9.54

Under PlayOnLinux 0.9.29 soon to be 0.9.35

FrozenFox:  Currently Searching through your hyperlink...

---

### Post by Toffeeapple on 2008-02-14
I suppose you could just move your present wine install of warcraft to..

yourhomefolderwotever/.PlayOnLinux/wineprefix/

and then edit an existing configuration file in the configurations folder.. I've not tried it but I don't see why not.

If you add a folder to /wineprefix it will appear when you install something through Playonlinux if you select 'edit' rather than 'new'
If you make a copy of a configuration file in /configurations it will appear in the main window when you start up Playonlinux.

Ive gotten best results with 0.9.51 for playing Warcraft

: )

---

### Post by Sugi on 2008-02-14
Toffeeapple:  
Install >
LiveInstall >
Next >
New or Edit >
(New) Path.to.CD.or.ISO(which one you have) or (Edit) Path.to.Game.Folder >
Config.Game.if.Needed >
Enjoy

It works :) I got Warcraft 3 & Frozen Throne under 0.9.51  I also got Dark Crusade working under 0.9.35  I swear to god, it works better under linux then windows. 1680x1050 32 bit Windows Mode everything max out :)  it look beautiful and fast.

Thanks man for the head up.   PlayOnLinux is amazing.  I am making this apolication a standle for my PCs.

Sugi

---

