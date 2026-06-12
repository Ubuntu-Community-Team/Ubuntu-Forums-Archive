---
title: "Sharing game files between ubuntu and windows"
date: 2008-03-15
forum: Wine
---

### Post by burnt water on 2008-03-15
Is there a way to have WINE use a game's files from its windows directory?

---

### Post by agtownz on 2008-03-15
I have seperate drives for Windows and Linux, however, is transferring those files over that hard?

---

### Post by vexorian on 2008-03-15
> **burnt water said:**
> Is there a way to have WINE use a game's files from its windows directory?
Why do you mean by game's files? game data or saved games? Either case, it is possible, I need an answer before giving instructions though.

---

### Post by Shootfast on 2008-03-16
I have my steamapps folder symlinked to my windows drive for steam games. That way they share the one folder and I'm not wasting 20+ gb for the same thing twice.

---

### Post by Sockerdrickan on 2008-03-16
I heard that sharing 20gb sucks (performance) but small ammounts are ok

---

### Post by burnt water on 2008-03-17
> **vexorian said:**
> Why do you mean by game's files? game data or saved games? Either case, it is possible, I need an answer before giving instructions though.

Game data. My hard drive is only 80gb and I don't have space to have 20gb of game data on a dual boot machine.

---

### Post by vexorian on 2008-03-17
> **burnt water said:**
> Game data. My hard drive is only 80gb and I don't have space to have 20gb of game data on a dual boot machine.

Well, this depends on the game, but mostly, you can make a symlink (if all the data is in a single subfolder) or many symlinks (otherwise) in your Linux version that points to the windows one. 

[http://learn.clemsonlinux.org/wiki/Symlink](http://learn.clemsonlinux.org/wiki/Symlink)

Perhaps there's a way to automatize the process with a script, but I don't know that much bash yet.

---

### Post by Melhisedek on 2008-03-18
> **Shootfast said:**
> I have my steamapps folder symlinked to my windows drive for steam games. That way they share the one folder and I'm not wasting 20+ gb for the same thing twice.

How do you do that? I have CS:S and TF2 on both my partitions, even WOW, Civ4 and war3. Damn I would love to do the same on most of my games tbh.

---

### Post by brett611 on 2008-03-18
Try this out - its like a wine / vmware alternative.  Main benefit is that it offers vmware stability/ease plus ability to use 1 partition for both linux and "windows"

[http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux)

---

### Post by Melhisedek on 2008-03-28
Can anyone explain to me how to symlink steam games between windows and Linux?

---

### Post by vexorian on 2008-03-29
After installing the game with WINE, move the copy of the game in your Linux partition to some backup folder.

Now go to the folder that holds the windows' copy's folder, drag and drop the game's folder from this location to the one where the Linux copy was, MAKE SURE TO USE THE MIDDLE MOUSE BUTTON during the drag and drop.

A popup menu will appear giving you choices between move, copy and link, try link.

It is harder difficult if you need to crack the game on Linux but not on windows, you are not able to just link the folder, you would need to have a folder keeping the cracked version and then just link the other files individually.

> Try this out - its like a wine / vmware alternative. Main benefit is that it offers vmware stability/ease plus ability to use 1 partition for both linux and "windows"

[http://lifehacker.com/367714/run-win...y-inside-linux](http://lifehacker.com/367714/run-win...y-inside-linux)
Virtualbox is great for apps, but it absolutely sucks for games.

---

