---
title: "Trouble installing Steam - Help please"
date: 2008-02-06
forum: Wine
---

### Post by jamespickles on 2008-02-06
Hi everyone, Ive just installed wine .9.54 and i installed steam,

I then started up steam it says updating, when it gets to 26% it stops and say "you can only run one copy of steam at the same time"

And if i dont play a game soon im going to die lol im very frustrated please someone help me out :)

Thanks.

---

### Post by fizur2002 on 2008-02-06
i have a similar problem as you, but using the latest Cedega 6.05.  Getting to the 26% update and then i get the Support for steam is no longer supported on this computers operating system.

---

### Post by p_quarles on 2008-02-06
Moved to the Wine forum. Be sure to read the stickies at the top of this forum for some Wine basics.

---

### Post by cogadh on 2008-02-06
You can fix that problem by doing this:
[LIST=1]
[*]Open a terminal and change directories to Steam's install directory:
```
cd ~/.wine/drive_c/Program\ Files/Steam
```
[*]Run the following:
```
nice -n 19 wine steamTmp.exe SelfUpdate "Steam.exe" 14
```
[/LIST]

---

### Post by fizur2002 on 2008-02-06
actually what i did was change the global settings to run as winxp instead of 98 and the GDDB profile to steam and that fixed it.

---

### Post by Cariro on 2008-02-06
This is moved, but if anyone stumbles over it heres the solution:

Step 1. Open a terminal window and type
```
sudo apt-get update
```

Step 2. In same terminal window type
```
sudo apt-get install wine
```

Step 3. Go to [HTML]http://www.google.com[/HTML] and search for: Tahoma.tff (This is the font that steam uses for the login window and all messages)

Step 3. Go to [HTML]http://www.google.com[/HTML] and search for steam install.exe. N.B!!! Don't download from steam's web-page, as this is an .msi file that is executable by Windows only.

Step 4. Install the .exe file using wine. If wine isn't set as a default option for .exe files then right-click->Properties->Open With, and choose Wine.

---

### Post by fizur2002 on 2008-02-06
you have google on there twice

---

### Post by Cariro on 2008-02-06
Thats cause you have to google twice!!:lolflag:
First for the font so that you can read and write in steam, then for the steam_install.exe file.

---

### Post by jamespickles on 2008-02-06
> **cogadh said:**
> You can fix that problem by doing this:
[LIST=1]
[*]Open a terminal and change directories to Steam's install directory:
```
cd ~/.wine/drive_c/Program\ Files/Steam
```
[*]Run the following:
```
nice -n 19 wine steamTmp.exe SelfUpdate "Steam.exe" 14
```
[/LIST]


Thank you very much, i did this and its now fully working, Thanks for the support everyone.

---

### Post by Cariro on 2008-02-07
If any admins see this, plz make a sticky thread with the steam setup help.

---

### Post by fizur2002 on 2008-02-07
2nd vote for a sticky, too much information in here for it to get lost in the dog pile.

---

