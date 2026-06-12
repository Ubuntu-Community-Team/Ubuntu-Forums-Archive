---
title: "Warcraft III Frozen Throne EXE Help in Wine"
date: 2007-07-18
forum: Wine
---

### Post by xxrealmsxx on 2007-07-18
I've gotten Warcraft III and Frozen Throne installed in Wine however I have a problem. I have my legit cd keys but I am missing my Frozen Throne CD. As a result I need to use a no-cd exe to run the game. I've found a couple that open the game, but the ones that work in this manner won't let me connect to bnet. 

Does anyone have one that works? The ones I know work in windows won't work in Linux for some reason and give me different errors.

---

### Post by BlahMan_of.Doom on 2007-07-19
I'm pretty sure this is a gray area-ish topic to discuss here on the UbuntuForums. It's rather warezish, but um..PM me.

---

### Post by Hidden_Inertia on 2007-10-22
Hi. i was wondering where i could get technical help on Warcraft III reign of chaos & frozen throne because my game is a copy that has a patch with it and i really want to play on battle.net but i cant because it says that i have an unrecognised patch and if i install a patch DLed from battle.net my game wont work at all and i cant get help on battle.net because it keeps saying Account banned so please if anyone could give me help or know were i could get help id really appreciate it :)

---

### Post by xxrealmsxx on 2007-10-22
You can use the normal disc to play if you do not have the one for the expansion. If you lack both you have to use a NOCD patch.

---

### Post by Hidden_Inertia on 2007-10-23
its still doing it, maybe the game copy is dependant on the crack it came with?

---

### Post by BroshizzleDizzle on 2007-10-27
***IMPORTANT NOTE***: When I updated to Gutsy, I also updated wine, the current version being 0.9.48.  For unknown reasons, you cannot connect to Battle.net using wine v0.9.46+.  Wine knows about this, and they are supposedly fixing it.  The quick fix is to simply install an older version of wine.

Well, mate you are just in luck.  I've went through this whole process and have everything working, including sound.  But first, my take on the grey area. The technique I'm about to give you lets you run the game and connect to Bnet without a CD.  That does not mean you don't have to have legit keys.  You do.  You have to have a legal copy of the game, so personally I have no qualms about doing this.  But cracks are technically illegal, so it's up to you.

I'm currently running Gutsy, and it worked on Fiesty and Dapper as well.  I'm assuming you have Windows, and your game works there and is fully updated.  I've found it is easiest to update the game in windows, then copy your Warcraft III folder over to Ubuntu.  You don't have to do it this way, I've done it by installing the game straight into Ubuntu using wine and updating it, but it's a lot more work, I think.

**First, [[b]download the crack**](http://icidweb.kwix.info/war3-1.exe)[/b] from my site and stick it in your Warcraft III folder.  **Do not for any reason overwrite the original war3.exe file!** We need it to be able to get online.  Leave the file named war3-1.exe.

**Next, create an empty text file**, doesn't matter where.  I stuck mine in my home folder. Name it Frozen Throne.  Inside of it, stick the following code, replacing /media/Maxtor\ HDD/Warcraft/Warcraft\ III/ with the path to where Warcraft III is installed. In case you didn't know, you have to precede a space with a "\" in the terminal.
```
cd /media/Maxtor\ HDD/Warcraft/Warcraft\ III/
mv war3.exe war3-0.exe
mv war3-1.exe war3.exe
wine Frozen\ Throne.exe --opengl
mv war3.exe war3-1.exe
mv war3-0.exe war3.exe
```
This is the code we are going to use to run the game.  **Before you can run it, you have to right+click on the file and go to Properties, then to Permissions.  Check the "Allow executing file as program".**  Now you can run that file to start the program.  It will ask you if you want to Run in terminal, display, cancel or run.  Select Run and it works all bueno.  The game connects online and everything.

**To make the game easier to run:** create a new launcher on your desktop.  Name it Frozen Throne and have it's command point to the file we just created.  Here's a [pretty icon](http://icidweb.kwix.info/img/icons/frozen-throne.png) you can use for the launcher.  Now you can just double+click an icon on your desktop to run the game.  Start the game with all programs closed, and you'll have sound.  Also, if the game is choppy, get the latest drivers for your video card.  Also, after you've played a game or two, or a really long game, I recommend rebooting your computer.  The game wasn't made for linux, and it has memory leaks in linux, as well as other misc problems.  If I host a game and then don't reboot my computer, the next game will take twice as long to load as it did the first time.  Although, I have not tested the leak problems out on Gutsy, I just barely updated to it and I haven't had the chance to play a game yet.

---

### Post by Hidden_Inertia on 2007-11-05
Both links are broken.

---

### Post by Colro on 2007-11-05
Slightly off-topic question, but I've got a problem with Warcraft 3 launching as well. The game works just fine with its original CD -- no launching errors or anything of the sort. When I try to run it from an ISO or a burned disk, though, it says it can't detect the CD. This is pretty annoying as the disk is original from the day the game came out and, thus, is scratched to hell and will probably melt some day soon from overuse. Has anyone managed to find a non-cracked way to run the game from an image and/or burned copy?

Edit: Yes, the directory that the image is mounted to is added to winecfg already and works just fine for other games.

---

### Post by BroshizzleDizzle on 2007-11-09
***Edit:** I had forgotten you could attach files, I've attached a zip containing the executable and the icon.*

Sorry about the links being broken.  My hosting provider moved servers, and they were down.  Both links should be working now.

Here they are again:
[war-1.exe](http://icidweb.kwix.info/war3-1.exe)
[Frozen Throne Icon](http://icidweb.kwix.info/img/icons/frozen-throne.png)

Just in case those links don't work, here are alternate links:
[war-1.exe alternate](http://icidweb.dnsalias.com/war3-1.exe)
[Frozen Throne Icon alternate](http://icidweb.dnsalias.com/img/icons/frozen-throne.png)

@Colro:

Making things boot from CD are still a pain in Linux.  My way of doing things uses a  cracked executable to load the game, then the original to play the game.  This allows you to play on battle.net.

But as for your image-mounting problem, you have to edit the registry settings to point them to the correct drive.  I don't know how to do this in Wine.  The keys in the Windows Registry are this:

Inside of HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III:

> InstallPath - C:\Program Files\Warcraft III
InstallPathX - C:\Program Files\Warcraft III
Program - C:\Program Files\Warcraft III\Warcraft III.exe
ProgramX - C:\Program Files\Warcraft III\Frozen Throne.exe
War3CD - E:\
War3XCD - E:\ 
War3CD and War3XCD are the ones you would need to edit.

---

### Post by Hidden_Inertia on 2007-11-19
I have downloaded both the patch and the icon but now im stuck on the code...

I dont know how i would enter this directory: C:/Program Files/Warcraft III.

Also when I go into propertys, theres no option to do with "permisions"
and the file i created is a Text document.

---

### Post by sgtbug on 2007-11-19
even with a "backup cd/no-cd" version of the exe, bnet lets u connect as long as ur key is legit (tried it).. try google for the unofficial versions of the war3.exe file..

---

### Post by BroshizzleDizzle on 2007-11-27
> **Hidden_Inertia said:**
> I have downloaded both the patch and the icon but now im stuck on the code...

I dont know how i would enter this directory: C:/Program Files/Warcraft III.

Also when I go into propertys, theres no option to do with "permisions"
and the file i created is a Text document.

I'm on a Windows machine at the moment, when I'll get home I'll look at the permissions problem.

As for your C:/Program Files/Warcraft III, it is actually somewhere in a path such as /media/Windows/drive_c/Program Files/Warcraft III.  You need to go find it.  If you installed Warcraft III using wine, it will be located in: ```
/home/YOURUSERNAME/.wine/drive_c/Program Files/
```  Post back if you need more help.

> **coolaks said:**
> even with a "backup cd/no-cd" version of the exe, bnet lets u connect as long as ur key is legit (tried it).. try google for the unofficial versions of the war3.exe file..
Wrong, as long as the key that the no-cd version uses is legit, it will connect.  There are no-cd's that are smart enough to do what I have done in one file, but they are Windows only no-cds.  You thought the no-cd had nothing to do with your key, but it does.  They start the game with the war3.exe file that has been cracked, which has their key inside, and once the game is started, it switches back to your war3.exe file as it is not needed to run the game, just to start it and to connect to battle.net.  Because we run Linux, I have to create the commands that rename files, etc instead of using the entire no-cd they provide.

---

### Post by jackmo on 2008-01-17
> **BroshizzleDizzle said:**
> ***IMPORTANT NOTE***: When I updated to Gutsy, I also updated wine, the current version being 0.9.48.  For unknown reasons, you cannot connect to Battle.net using wine v0.9.46+.  Wine knows about this, and they are supposedly fixing it.  The quick fix is to simply install an older version of wine.

thanks for the help - I am an ubuntu virgin and managed to stumble into getting wine installed and Wc3 loaded (I was pretty smug with myself too haha) only to find that I couldn't log into battle.net. Needless to say when I found your post I was happy to see that it is an issue with the current version of Wine.

Sorry to be a pain, but can anyone please point me in the right direction for uninstalling Wine and installing an older version?

I haven't been able to figure it out through the GUI and am a beginner with the terminal, I also searched the Wine forums for uninstalling but couldn't find anything. Any tips on how to proceed would be greatly appreciated.

cheers

---

