---
title: "How do you run japanese games in linux"
date: 2011-07-15
forum: Wine
---

### Post by TheManno1 on 2011-07-15
Is there any package.

---

### Post by doas777 on 2011-07-15
> **TheManno1 said:**
> Is there any package.
what?

---

### Post by TheManno1 on 2011-07-15
You know a deb or ppa.

---

### Post by Perfect Storm on 2011-07-15
What is Japanese games? I'm not sure I quite get it.

---

### Post by doas777 on 2011-07-15
Are you talking about somthing like the old console mods that would let you play Japanese minted disks/cartridges? The only think like that I know of for PC games is DVD Region Coding. if region codes are at the core of your question,  have a look here:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by TheManno1 on 2011-07-15
[http://forums.animesuki.com/showthread.php?t=60120](http://forums.animesuki.com/showthread.php?t=60120) something like this for linux.

---

### Post by WienerWuerstel on 2011-07-15
If you want to know how to install "Japanese Games" that require Japanese Fonts with Wine then this [Post]("http://ubuntuforums.org/showpost.php?p=10424766&postcount=6") should help you. It helped me too when I had problems playing Touhou Games. But be sure to be more specific the next Time ;).

---

### Post by doas777 on 2011-07-15
if you are working with the games outside of wine, you can find your langague settings under 
System -> Administration -> Language suppport. or in unity, just search for Langague Support.

---

### Post by TheManno1 on 2011-07-16
I pretty sure you can do this with the wine gui if so how.I installed the fonts. Also is this right way to write the  directory /home/family/Downloads/Project/Haruhi

[LIST=1]
[*]Change directories to the game's install directory:      Code:
     cd ~/.wine/drive_c/Program\ Files/asgard/Starry\ Sky\ in\ Summer 
Note the "\" before all the spaces in the file names, like between  "Program" and "Files", they are required (the terminal can't "see" the  space in the file names otherwise). The odd characters in the "Starry  Sky" part might be a problem to type. If you simply type "Starry" and  then hit the TAB key, it should autocomplete the directory name for you
[*]Run the game's executable:      Code:
     wine <appname>.exe 
 You will have to figure out what the actual name for the .exe  file is. Since I don't have the game and your screenshot did not include  the actual files within the "Starry" directory, I can't give you the  specifics.
[*]A ton of output should appear in the terminal. Copy that output and  post it here. Click on the Edit button in the terminal, Select All, then  Copy. Use the [forum CODE tags]("http://ubuntuforums.org/misc.php?do=bbcode") when you post it, it will keep the output readable
[/LIST]

---

### Post by TheManno1 on 2011-07-16
[http://www.haruhisuzumiya.net/haruhiforum/viewtopic.php?f=8&t=990](http://www.haruhisuzumiya.net/haruhiforum/viewtopic.php?f=8&t=990) I am trying to run 
[B]Suzumiya Haruhi no Gyakuten first part. With both patches [http://www.cubetype.com/archives/2006/08/06_work_game_saiban.html](http://www.cubetype.com/archives/2006/08/06_work_game_saiban.html). The text is displaying right but there is black screen when I click on the bottom of the black screen which I think has a quit button there is some sound and it closes
[/B]

---

### Post by TheManno1 on 2011-07-23
Help.

---

### Post by TheManno1 on 2011-07-26
help

---

