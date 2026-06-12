---
title: "Can't edit reg in wine...help?"
date: 2007-07-13
forum: Wine
---

### Post by Ripfox on 2007-07-13
I am following the tutorial to run Oblivion with Wine, and it tells me to edit HKEY_CURRENT_USER / Software / Wine / Direct3D

but I dont see an entry "Direct3D" under those headers...

Whats up with that?

Thanks for anyone who can help me here.

Also...I do not understand this instruction:

"Desktop Integration tab.
Here you should make a folder as your 'Windows folder base' and populate it. I use ~/Documents/Windows/. After you make these folders match them up in this interface, since Oblivion follows the logo requirements and uses a 'My Games' folder.

	mkdir -p ~/Documents/Windows/{Desktop,Documents,Pictures,Music,Video}


Your ini and saved games will be under:

	~/Documents/Windows/Documents/My Games/Oblivion/


I copied my old save games and autosaves to the 'Saves' folder under Oblivion, and they all worked fine. Remember to make sure any saves you copy have permissions set read/write by the user running Wine."

I ran the command, but  I don't get what he is saying to do in the drives tab.

---

### Post by cogadh on 2007-07-13
Not sure about the Desktop Integration part (still haven't messed with those settings myself), but the registry key doesn't exist because you need to create it. Just click on the Wine directory in the registry tree then right click in the right pane and select New > Key. Name the key Direct3D and you're all set. You will also need to create any of the individual registry entries within "Direct3D" the tutorial instructed you to edit.

---

### Post by Ripfox on 2007-07-14
Ah ha...thanks for that. Did you get it working ok?

OK, I am getting the error: "invalid handle"

---

### Post by cogadh on 2007-07-14
Nope, I don't have Oblivion, so I've never tried to get it working. I did just take a look at its entry in Wine's AppDB, and it doesn't look like the game has any kind of consistent performance with Wine on several systems:
[http://appdb.winehq.org/appview.php?iAppId=3150](http://appdb.winehq.org/appview.php?iAppId=3150)
You may have several issues trying to get this to work and it may not work at all.

---

### Post by Ripfox on 2007-07-14
I am getting the error: "invalid handle" when I try to create a key in regedit.

BTW, what game have you had the best exp. with under wine? Preferably an mmo  or rpg?

---

### Post by cogadh on 2007-07-14
Is that error happening when you try to create the "Direct3D" key, or does it happen when you try to create a new string value within the Direct3D key?

The only RPG game that I really play through Wine is Star Wars Knights of the Old Republic, it works fantastically with Wine. I've also had great experiences running American McGee's Alice, Hitman 2, GTA Vice City (with some graphical issues), Call of Duty and Star Trek Armada 2.

---

### Post by Ripfox on 2007-07-14
it happens when I try to create the direct3d key. Also, I have now tweaked the oblivion.ini file to the  point that i got the intro movies working flawlessly, but when it trys to go to the actual game, crash to 640x480 desktop! ooh this is fun! lol

---

### Post by cogadh on 2007-07-15
That shouldn't be happening. Are you sure you are creating it in the right place? You should have the HKCU/Software/Wine key highlighted when you go to create the key, that way the Direct3D key ends up created within the Wine key. See attached screenshot for my Direct3d key placement.

---

### Post by Torgas Prim on 2008-09-25
I am having the same issue on a new install of 8.04, completely updated.
Trying to create a Direct3D key in regedit and get "Invalid Handle" error.
In other words, I do not have the authority to add keys in regedit.
What is the workaround?

Never mind I figured it out. Instead of right-clicking and getting the error, I went to Edit, the New, then Key and it worked.

---

