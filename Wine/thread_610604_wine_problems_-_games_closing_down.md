---
title: "wine problems - games closing down"
date: 2007-11-12
forum: Wine
---

### Post by campkillgemma on 2007-11-12
i have a few problems with wine - well one actually. I was hoping someone can point me in the right direction. Otherwise ill have to run windows from a VM which I really DONT want to do.

Anyway, to the problem, when I run a few windows games it seems to start loading then close down randomly.

This has happened with Trickster Online, Fairyland and American McGee's Alice.

I dont understand why this is happening considering other games i've tried works eg. Heart of Darkness, Orlys Draw-a-Story and The Lost Mind of Dr Brain.

Someone please gimme a clue, im completely stuck :(

---

### Post by aoanla on 2007-11-12
Hrm, Well, American McGee's Alice has a Platinum rating on the Wine AppDB, so it <i>shouldn't</i> be causing any problems.

What would be useful would be if you actually gave us more information. It is difficult to diagnose a solution with just "This Game Doesn't Work"...

So, presumably, when you run these games which crash, you get some errors on the terminal you ran wine on? Can you tell us what those errors are?

Also, can you tell us a bit about your system configuration - version of Ubuntu, version of Wine, graphics card and drivers, etc?

---

### Post by campkillgemma on 2007-11-12
im running gutsy with a nvida geforce 2 graphics card. My version of wine is 0.9.46. When I run that game or any of the other aftermentioned games it says its startin it up then the program just disappears.

Im not running wine in the terminal so im not sure how to get the error messages.

---

### Post by aoanla on 2007-11-12
> **campkillgemma said:**
> im running gutsy with a nvida geforce 2 graphics card. My version of wine is 0.9.46. When I run that game or any of the other aftermentioned games it says its startin it up then the program just disappears.

Im not running wine in the terminal so im not sure how to get the error messages.

Well, the obvious way would be to run wine in the terminal. ;)
The usual procedure is:
cd .wine/drive_c/Program\ Files/GameDirectoryHere
wine nameofgameexecutablehere

Are you using the nv or the nvidia driver with your graphics card?

---

### Post by campkillgemma on 2007-11-12
yeah i am, i switched it on on the restricted drivers section. I still  cant get Alice to run its not actually doing anything when i type that into the terminal :S

---

### Post by aoanla on 2007-11-12
Aha. Checking the AppDB entry for American McGee's Alice in more detail, rather than just glancing at it, I see that there are issues with the SafeDisk copy protection stopping the game from working.

Please follow the instructions on AppDB here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=374](http://appdb.winehq.org/objectManager.php?sClass=version&iId=374)
and tell me if it still doesn't work.

(In general, a good 90% of people's problems with Wine are already documented on the relevant AppDB page, you know...)

---

### Post by gwoodard on 2007-11-12
May I make a game shutting down due to Wine?

Halo+Wine 0.9.49

Starts-->Desktop goes dark (not pitch black but the screen darkens)

Exits the game--> my resolution is screwed up and I have to fix things again

---

### Post by aoanla on 2007-11-12
> **gwoodard said:**
> May I make a game shutting down due to Wine?

Halo+Wine 0.9.49

Starts-->Desktop goes dark (not pitch black but the screen darkens)

Exits the game--> my resolution is screwed up and I have to fix things again

Please read the AppDB entry for Halo (noting the issues with it crashing with later versions of Wine), and report back if making the suggested changes doesn't help.
Entry is here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720)

(Once again, people, checking the AppDB isn't hard, and usually solves your problems. ;) )

---

### Post by gwoodard on 2007-11-13
gwoodard@gwoodard-desktop:~/wine-git$ git bisect good wine-0.9.48
gwoodard@gwoodard-desktop:~/wine-git$ git bisect bad wine-0.9.49
Bisecting: 231 revisions left to test after this
[bb4ba8e21b699889112cd39a479dd4c6dca17969] "netapi32: Fix valgrind warnings."

What does this mean?

---

