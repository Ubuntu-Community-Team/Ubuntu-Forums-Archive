---
title: "Any of you have installed worms armageddon on wine ? How?"
date: 2008-08-29
forum: Wine
---

### Post by eru777 on 2008-08-29
Any step by step process? Yes I have seen the team17 forum with no luck, since they say you have to find an older distro of the winde program.
[http://forum.team17.com/showthread.php?t=28710&page=9](http://forum.team17.com/showthread.php?t=28710&page=9)

---

### Post by forger on 2008-08-29
how about giving [wormux]("apt://wormux") a try? :)

---

### Post by eru777 on 2008-08-29
:) thanks , looks a fine game but I was looking for the real worms ;)

---

### Post by dioltas on 2008-08-29
I was thinking about trying to get worms working in wine myself. Used to play it all the time.
I think it's possible, but I dont think you can get the online working, which IMO is the best part of the game.

Here is the w:a entry in the wine apps database : [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1308]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1308")

and here is a guide:
[http://jaysherby.blogspot.com/2007/05/howto-run-worms-armageddon-using-wine.html]("http://jaysherby.blogspot.com/2007/05/howto-run-worms-armageddon-using-wine.html") but I think it only gets it partly working.

Let me know if you get wormnet working!


Edit:
Just looked at some of the test results in the wine database, some people seem to have got wormnet working. None of the tests have been carried out on hardy either, so maybe there's some hope. I think you need to get a hacked version of something called ddraw.dll for wine I think. Dont have time to look into it myself at the mo, but I hope this helps.

---

### Post by eru777 on 2008-08-29
I am stuck on step 2 ending. I can't seem to find the directory in which I installed WA (lol) I Put C:/Team17/Worms ARmageddon when i first installed it but now I cant find it ;<

---

### Post by dioltas on 2008-08-29
I have never really used wine, so I cant really help you here. I'm going to try this myself though.
To install it did you change to the cd directory and type wine Install.exe ya?

I'd say it could be in your home folder in a folder called .wine.
So the path of the directory should be something like 

/home/**yourusername**/.wine/drive_c/Team17/Worms ARmageddon/

The .wine folder could be hidden in your home directory, so maybe try and change the view settings to show hidden folders or something.

Im at work at the mo using windows, so I cant try any of that stuff out right now...

---

### Post by eru777 on 2008-08-29
YEah it was hidden. Thanks ILl try it now !
EDIT: It doesnt play, thanks anyway though.

---

### Post by eru777 on 2008-08-29
If I go here
[http://madewokherd.nfshost.com/worms/?M=A](http://madewokherd.nfshost.com/worms/?M=A)
the most recent ddraw file I can find is something like 0.9.0 something when I have wine 1.0
I am pondering wether it will work or not if I put this outdated ddraw version. IS there any newer version ?
(or consider finding an older version of wine, as pointed by the team 17 forum? But that would mean , no web play, which is 95% of fun)

---

### Post by eru777 on 2008-08-30
bump

---

### Post by dioltas on 2008-08-31
Ive been trying to get it working on my machine.
No luck really yet, I did get it working and was able to start a game, but I cant use the mouse when I start a game. When I try to login to wormnet I get the same problem. 

I tried a few things to fix this including patching the wine source and compiling it again, but no good.

I found 2 old copies of the game, but both were very scratched so maybe that was the problem. Downloaded the new edition of it but couldnt get that working at all. Im gonna try and get another copy of the game I think and try it again.


Anyway maybe you wont have the mouse problem,
[URL="http://chthon.f2s.com/ddraw/"]
You can get ddraw.dll for newer versions of wine here[/URL]
Copy the ddraw.dll for your version of wine  and hack.reg into the WA directory. Then open up a terminal, cd into the WA directory and type "regedit hack.reg".

Then type "wine WA.exe /NOINTRO" to start the game. Make sure you've patched the game and instaled the update before all this though. Patch and Update can be found at [URL="wa.team17.com"]wa.team17.com
[/URL]
Install the patch first by typing wine WAPatch.exe, and then the update the same way.

------------------------------------------------------------------------

I read somewhere else that you need user32.dll and ddraw.dll, but I dont think you really need user32. If the above dosnt work for you try putting these in the WA directory.
You can get them here: [URL="http://rapidshare.com/files/136796299/WA_patches_for_1.1.2_Wine_User32_and_ddraw.tar.gz"]http://rapidshare.com/files/136796299/WA_patches_for_1.1.2_Wine_User32_and_ddraw.tar.gz
[/URL]
They are for wine version 1.1.2 though. The one that apt installs by default is version 1. I couldn't find user32.dll for version 1, but Im sure it exists... I just installed wine version 1.1.2 instead.

Type wine --version to check what version you have. Type "apt-get remove wine" to uninstall the version you have. Download wine_1.1.2~winehq0~ubuntu~8.04-2-0ubuntu1_i386.deb from the wine website, and install it. I'd post a link to it but the wine website seems to be down at the moment.

-------------------------------------------------------------------------

And yea, it matters what version of the patches you use. Let me know if you've any luck, I really want to get this working aswell. If anyone knows what might be causing my mouse problem please let me know, because other than that the game seems to run fine. The wine patch I did was to fix a problem with an animated mouse or something but it didnt work.

Thanks

---

### Post by hessiess on 2008-08-31
PSX emulater + worms armageddon iso?

---

### Post by dioltas on 2008-08-31
Good idea, that could work. I'd like to get the PC version working though. Only want it for online play really. PSX version dosnt have online play. I won't be too bothered if I dont get it woking, it'd be nice tho.

---

### Post by eru777 on 2008-08-31
> **hessiess said:**
> PSX emulater + worms armageddon iso?

I want it for online games mainly so PC version.. But it won't work .

---

### Post by dioltas on 2008-08-31
how far can you get with it?
Were you able to install it successfully?
Were you then able to install the patch and the update?
Did you copy ddraw.dll into the Worms Armageddon folder?
Does the game start at all? Does anything happen when you try to run the game?

---

### Post by Oldsoldier2003 on 2008-08-31
Since this thread has gone a couple days without a good result I'm going to move it to the Wine Subforum. There is a good chance that someone there might have additional insights.

---

### Post by eru777 on 2008-08-31
Here is my progress .
[http://forum.team17.com/showthread.php?t=28710&page=9](http://forum.team17.com/showthread.php?t=28710&page=9)

---

### Post by dioltas on 2008-08-31
Got it working! Wormnet and all. Well, i was able to log in, didnt have time to try playing a game online. I used the patched version of wine that lookias posted in that link you gave [http://lookias.inventforum.com/viewtopic.php?t=12]("http://lookias.inventforum.com/viewtopic.php?t=12").

It seems to be working perfectly for me anyway! 

Heres what you have to do:

[B]
1. Download wine4wa.tar.gz and save it in your home directory.
2. Unzip it by typing "tar xvfz wine4wa.tar.gz
3. Install worms the normal way with wine, except install it to H:/wine4wa/wa instead of C:/Team17/Wor...
4. Download WA_update-3.6.29.0_Beta_Installer.exe to /home/username/wine4wa/wa, the folder that you installed worms into.
5. Type "cd ~/wine4wa/wa" to change to the installation folder.
6. Type "wine WA_update-3.6.29.0_Beta_Installer.exe" to install update.
7. Type "cd .." to go back to the wine4wa folder. 
8. Type "chmod a+x wa.sh" to allow wa.sh to be executed.
9. Type "./wa.sh" to run worms.
[/B]

Hopefully worms will then start up successfully for you. You don't need any dlls or anything.

---

### Post by dioltas on 2008-09-01
lol

---

### Post by eru777 on 2008-09-01
> **dioltas said:**
> Got it working! Wormnet and all. Well, i was able to log in, didnt have time to try playing a game online. I used the patched version of wine that lookias posted in that link you gave [http://lookias.inventforum.com/viewtopic.php?t=12]("http://lookias.inventforum.com/viewtopic.php?t=12").

It seems to be working perfectly for me anyway! 

Heres what you have to do:

[B]
1. Download wine4wa.tar.gz and save it in your home directory.
2. Unzip it by typing "tar xvfz wine4wa.tar.gz
3. Install worms the normal way with wine, except install it to H:/wine4wa/wa instead of C:/Team17/Wor...
4. Download WA_update-3.6.29.0_Beta_Installer.exe to /home/username/wine4wa/wa, the folder that you installed worms into.
5. Type "cd ~/wine4wa/wa" to change to the installation folder.
**6. Type "wine WA_update-3.6.29.0_Beta_Installer.exe" to install update. **<--
[QUOTE]preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\WA_update-3.6.29.0_Beta_Installer.exe": Module not found it says that on console

---

### Post by dioltas on 2008-09-01
are you in the wine4wa/wa folder, and is WA_update-3.6.29.0_Beta_Installer.exe in the folder?

Type pwd to check which folder you are in, it should say /home/yourusername/wine4wa/wa.
Also type ls to check if WA_update-3.6.29.0_Beta_Installer.exe is in the folder.

In step 5 when I said Type "cd ~/wine4wa/wa", if you were root when you did this it wouldnt have worked, so maybe that's it. I should have probably said "cd /home/yourusername/wine4wa/wa".

If you browse to your home folder, then wine4wa, then wa, you should see all the worms installation files if it was installed correctly. WA_update-3.6.29.0_Beta_Installer.exe should be there as well. Let me know if this works.

---

### Post by eru777 on 2008-09-01
> **dioltas said:**
> are you in the wine4wa/wa folder, and is WA_update-3.6.29.0_Beta_Installer.exe in the folder?

Type pwd to check which folder you are in, it should say /home/yourusername/wine4wa/wa.
Also type ls to check if WA_update-3.6.29.0_Beta_Installer.exe is in the folder.

In step 5 when I said Type "cd ~/wine4wa/wa", if you were root when you did this it wouldnt have worked, so maybe that's it. I should have probably said "cd /home/yourusername/wine4wa/wa".

If you browse to your home folder, then wine4wa, then wa, you should see all the worms installation files if it was installed correctly. WA_update-3.6.29.0_Beta_Installer.exe should be there as well. Let me know if this works.

whats the difference between the WA folder and the wa folder.. 
:mad: it doesnt work either wway

---

### Post by dioltas on 2008-09-01
The readme that comes with wine4wa.tar.gz says to install worms into the wa folder. Once you do this and install the update, the wa.sh script runs worms using a patched version of wine which is also included in wine4wa.tar.gz. Linux is case sensitive so WA and wa are different folders. 

It runs worms from the wa folder. I don't know why there is a WA folder, maybe it dosn't matter which you install to, I just followed the instructions in the readme.

If your on step 6, and you have successfully installed worms to H:/wine4wa/wa/ (H = home folder in wine), then all you have to do is install the update to the same folder, H:/wine4wa/wa/

---

### Post by eru777 on 2008-09-01
> **dioltas said:**
> The readme that comes with wine4wa.tar.gz says to install worms into the wa folder. Once you do this and install the update, the wa.sh script runs worms using a patched version of wine which is also included in wine4wa.tar.gz. Linux is case sensitive so WA and wa are different folders. 

It runs worms from the wa folder. I don't know why there is a WA folder, maybe it dosn't matter which you install to, I just followed the instructions in the readme.

If your on step 6, and you have successfully installed worms to H:/wine4wa/wa/ (H = home folder in wine), then all you have to do is install the update to the same folder, H:/wine4wa/wa/

I cant do it. It wont update.

---

### Post by dioltas on 2008-09-01
Thats strange, you still getting the same error message?

```
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\WA_update-3.6.29.0_Beta_Installer.exe": Module not found 
```

Make sure you're in the same directory as the update installer when you type ```
wine WA_update.....exe
```

Are you sure you installed the game in the right folder? If you browse to your home folder, then wine4wa, then wa, is the folder empty or full of the worms data from the install?


If your still having trouble try just double clicking the updater.exe and when it asks you for a directory just browse to the wine4wa/wa folder. I know it must be fairly frustrating for you, but i'd say your fairly close. If it worked for me it should work for you.

---

### Post by eru777 on 2008-09-13
> **dioltas said:**
> Got it working! Wormnet and all. Well, i was able to log in, didnt have time to try playing a game online. I used the patched version of wine that lookias posted in that link you gave [http://lookias.inventforum.com/viewtopic.php?t=12]("http://lookias.inventforum.com/viewtopic.php?t=12").

It seems to be working perfectly for me anyway! 

Heres what you have to do:

[B]
1. Download wine4wa.tar.gz and save it in your home directory.
2. Unzip it by typing "tar xvfz wine4wa.tar.gz
3. Install worms the normal way with wine, except install it to H:/wine4wa/wa instead of C:/Team17/Wor...
4. Download WA_update-3.6.29.0_Beta_Installer.exe to /home/username/wine4wa/wa, the folder that you installed worms into.
5. Type "cd ~/wine4wa/wa" to change to the installation folder.
6. Type "wine WA_update-3.6.29.0_Beta_Installer.exe" to install update.
7. Type "cd .." to go back to the wine4wa folder. 
8. Type "chmod a+x wa.sh" to allow wa.sh to be executed.
9. Type "./wa.sh" to run worms.
[/B]

Hopefully worms will then start up successfully for you. You don't need any dlls or anything.

thanks. it works windowed but there are two problems
1.it seems that its running at faster speed
2.the keyboard doesnt respond to the game
3.no sound (that doesnt really bug me lol)

Any way to fix this, and maybe play a little higher resolution as well ?

---

### Post by eru777 on 2008-09-15
morgoth@twilight:~/wine4wa/wa$ cd ~/wine4wa/wa
morgoth@twilight:~/wine4wa/wa$ chmod a+x wa.sh
**chmod: cannot access `wa.sh': No such file or directory**
 


why does this happen ? :(

---

### Post by gloarb on 2008-09-22
> **eru777 said:**
> morgoth@twilight:~/wine4wa/wa$ cd ~/wine4wa/wa
morgoth@twilight:~/wine4wa/wa$ chmod a+x wa.sh
**chmod: cannot access `wa.sh': No such file or directory**
 


why does this happen ? :(

lol you are not on right folder.

../

wa.sh is on ~/wine4wa/

---

