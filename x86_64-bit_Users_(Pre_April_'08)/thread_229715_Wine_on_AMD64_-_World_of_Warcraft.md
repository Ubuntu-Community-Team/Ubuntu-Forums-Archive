---
title: "Wine on AMD64 - World of Warcraft"
date: 2006-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by GoLoGo on 2006-08-04
I installed using the install Wine 32-bit on a 64-bit system guide. Everything seemed to work fine, installed wow, no errors, under the fake c drive in the foler program files. When I try to run WoW.exe using wine, it shows the bar down at the bottom panel, then it closes, and doesnt do anything else after that. Any suggestions, I tried checking what I could purge from the WoW dapper guide in the documents archives, but it seems like the "patched" latest release of wine, is made for i386 systems, and does not let me install it.

---

### Post by cocteau on 2006-08-05
> **GoLoGo said:**
> ...but it seems like the "patched" latest release of wine, is made for i386 systems, and does not let me install it.

Well, all that means is that it is 32 bit. i386 is the old set of machine instructions back from the early pentium days, so the one you already installed is for the same type of cpu. Kilz has a very good guide on setting up wine on a 64bit processor here: [http://www.ubuntuforums.org/showthread.php?t=185557](http://www.ubuntuforums.org/showthread.php?t=185557)

I don't play world of warcraft but I hear that it should be quite tricky to get to run with wine but again... Kilz said last night he was going to try and compile wine with the wow patches, so you might want to keep an eye out on this thread: [http://www.ubuntuforums.org/showthread.php?t=229265](http://www.ubuntuforums.org/showthread.php?t=229265)

---

### Post by McMarley on 2006-08-05
hey
wine is a 'fake machine' and your owne changes what it says and sends that to the hardware, then changes the response back, and then wine gets it, all this slows it down.
I dont play WOW, although i'd love to ( :D :D CHEC OUT THE BOTTOM OF MY SIGNATURE!!!:D :D AND MY AVATAR:D :D  ), but I do know alot about WOW, at least enought to know that it is a huge game, and that you need a pretty good computer, so slowing it down trough wine ay be the issue.
I see one other possibility: you install a tiny windows partition, and install WOW and the patches and programs you need to run it with. you may think that installing windows is a sacrilege, but I think that if thats the only way to run WOW, you may have not to take the sacrilege part into account...

if you give me the list of you computers capacities and hardware it may help for finding the problems

---

### Post by Kilz on 2006-08-05
> **cocteau said:**
> I don't play world of warcraft but I hear that it should be quite tricky to get to run with wine but again... Kilz said last night he was going to try and compile wine with the wow patches, so you might want to keep an eye out on this thread: [http://www.ubuntuforums.org/showthread.php?t=229265](http://www.ubuntuforums.org/showthread.php?t=229265)

I dont play wow myself, Im a Diablo 2 fan. But I have no problems helping other Ubuntu users. I was able to complie wine with the wow patch. I could only find a wow patch for wine 9.17 so thats what I built. 
Its still a i386 .deb file so you will have to [follow my install]("http://www.ubuntuforums.org/showthread.php?t=185557") howto, [just use this wine .deb]("http://home.comcast.net/~ubuntu64user/wine_0.9.17_4wow_Ubuntu-6.06-1_i386.deb")

---

### Post by Xordan on 2006-08-05
I followed this guide on the wiki:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

except the line:

sudo dpkg -i wine-0.9.18_wow_i386.deb

needs to be

sudo dpkg --force-architecture -i wine-0.9.18_wow_i386.deb

WoW works perfectly for me on 64-bit dapper now.

---

### Post by GoLoGo on 2006-08-06
Alright, I installed a small Windows XP parition... installed WoW on that. Ill leave my Ubuntu system to only handle the "important" stuff ;). Thanks again.

---

### Post by McMarley on 2006-08-06
good choice

happy 64bit to all

---

### Post by Kilz on 2006-08-06
Personaly I use Cedega to run Windows games. Its click, install, play. I understand it runs WoW. It is $15 bucks, but its worth it to me.
Now that I know there is a wine avaiable for WoW Im going to delete the one I made to make room for other things.

---

