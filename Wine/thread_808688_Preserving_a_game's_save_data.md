---
title: "Preserving a game's save data"
date: 2008-05-26
forum: Wine
---

### Post by Johnny K on 2008-05-26
I have been playing Chip's Challenge on Windows for a while now and was able to get up to level 88. Today I moved the game's program folder (.../Program Files/Chip's Challenge) to my Ubuntu machine.

Wine can run the game perfectly well, but the game's save data was not preserved. When Wine launches the game, it starts me off at level 1.

Does anybody know why this could be? Is there a file that I forgot to copy over or something like that? Thanks in advance!

---

### Post by diaa on 2008-05-26
Almost all modern apps save any user-related files, preferences, etc in application data folder (Start Menu > Run > %appdata%), so you should look there for a folder that has the same name as the game, also look into %userprofile% (Start Menu > Run > %userprofile%).
Note that some games(NFS IIRC) choose to store saves in My Document so it can be accessed easily by the user, so have a look there too

---

### Post by Johnny K on 2008-05-28
> **diaa said:**
> Almost all modern apps save any user-related files, preferences, etc in application data folder (Start Menu > Run > %appdata%), so you should look there for a folder that has the same name as the game, also look into %userprofile% (Start Menu > Run > %userprofile%).
Note that some games(NFS IIRC) choose to store saves in My Document so it can be accessed easily by the user, so have a look there too

Thanks for the help! I looked in %appdata%, %userprofile%, and My Documents and was not able to find any file which would be relevant to the game. The game itself is a port of an old DOS game, and I'm pretty sure that most if not all of the game's data is located in the main install folder (the one I copied over to my Ubuntu machine). Could the loss of save data be due to any other issue?

---

### Post by diaa on 2008-05-28
> **Johnny K said:**
> Thanks for the help! I looked in %appdata%, %userprofile%, and My Documents and was not able to find any file which would be relevant to the game. The game itself is a port of an old DOS game, and I'm pretty sure that most if not all of the game's data is located in the main install folder (the one I copied over to my Ubuntu machine). Could the loss of save data be due to any other issue?

That's strange... I'm not aware of other reasons that might lead to this, What's the name of this game, I'd like to give it a try ...

---

### Post by Johnny K on 2008-05-28
> **diaa said:**
> That's strange... I'm not aware of other reasons that might lead to this, What's the name of this game, I'd like to give it a try ...

The game is called "Chip's Challenge" and it's incredibly addicting for such an old game. You can download it [here]("http://www.freewebs.com/chipshome/chips.html").

What's interesting is that Wine preserves this game's save data just fine. That is, if I play the game on Wine and advance to level 2, I will start on level 2 the next time I play the game with Wine. Would there be any way for me to determine which file Wine is writing to as the game is saved? If I could determine that, I could just copy that same file (with its original save data) over from my Windows machine.

---

### Post by happyhamster on 2008-05-28
The file you're looking for is "entpack.ini" I think. Wine stores it in:

/home/username/.wine/drive_c/windows/entpack.ini
(use the correct username instead). Note that .wine is a hidden folder.

On a windows pc, it will probably be in the c:\windows folder (and perhaps it's a hidden file).

---

### Post by Johnny K on 2008-05-28
> **happyhamster said:**
> The file you're looking for is "entpack.ini" I think. Wine stores it in:

/home/username/.wine/drive_c/windows/entpack.ini
(use the correct username instead). Note that .wine is a hidden folder.

On a windows pc, it will probably be in the c:\windows folder (and perhaps it's a hidden file).

That looks like the file I was looking for. I can't access my Windows machine right now, but I'll report back after I try copying that file from Windows to Ubuntu.

By the way, how did you determine that was the file?

---

### Post by happyhamster on 2008-05-28
I tried the game (it's pretty fun). When I completed a level, I issued:

find $HOME -name '*.*' -mmin 1

Which shows all the files in my home dir that changed the last 1 minute. And entpack.ini was one of them (and in the .wine folder). A bit of googling confirmed it's Chip's Challenge related, so I was pretty sure it's the one you wanted. It appears to store the levels by writing the level-passwords into it.

---

### Post by doorknob60 on 2008-05-28
Heh, thanks, that's a sweet game, even though it's made by Microsnot :P

---

### Post by Johnny K on 2008-05-29
I just copied over the entpack.ini from C:\WINNT on my windows machine to /home/[username]/.wine/drive_c/windows on my Ubuntu machine, and now the game works just like it did on the Windows machine and I am now able to start at the level I left off at on Windows.

I did run into one simple problem, though. At first the game could not load the midi files and was giving me an error. I realized that the entpack.ini file contains the locations for midi files. In the endpack.ini file, it lists the base location for the files as C:\WINNT (as my Windows machine uses a WINNT directory for some reason). So I just changed that line so that it said C:\windows (the directory that wine uses). After that simple edit, the game was able to load the midi files just fine and stopped giving me errors.

Thanks for all the help, and let me know how far you get in the game!

---

