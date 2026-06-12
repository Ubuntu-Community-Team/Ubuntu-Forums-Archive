---
title: "Call Of Duty 4 Installation Problems"
date: 2007-11-13
forum: Wine
---

### Post by Cardamar on 2007-11-13
The problem is simple;
I attempt to install CoD4 under Wine and I get this:
WARNING: I had ubuntuforums open in the background when I took the screenshot. The image on this page may be a bit confusing to look at.



[IMG]http://i13.photobucket.com/albums/a271/Zalletook/screenshot1.png[/IMG]



And upon clicking OK, I get this:



[IMG]http://i13.photobucket.com/albums/a271/Zalletook/screenshot2.png[/IMG]



Any help is greatly appreciated (=
Thanks in advance, 
Cardamar~

---

### Post by cogadh on 2007-11-13
Next time, just copy and paste the terminal contents into the post using the forum "code" tags and if you have to use a screenshot, attach it to the post instead of linking to it, makes things much easier to read.

Error 1603 usually indicates a permissions issue on a Windows machine, but it could also mean a lack of sufficient space or an inaccessible file. Considering some of those errors you got seem to indicate directory creation and file copy errors, the latter two issues would seem more likely.

What version of Wine are you using? Also, how did you start the install (i.e. exactly what commands did you use)?

---

### Post by SM0k3 on 2007-11-13
Don't get your hope up on getting this game to run under wine, I got past the installation but haven't been able to even start the game.

---

### Post by cogadh on 2007-11-13
You probably need a cracked exe to run it, CoD games have a history of unsupported copy protection in Wine.

---

### Post by SM0k3 on 2007-11-13
> **cogadh said:**
> You probably need a cracked exe to run it, CoD games have a history of unsupported copy protection in Wine.

Yea I read that Wine doesn't support copy protected games too well but I tried a nocd crack and it still didn't work. I'll try running it via command line and see if I get any error messages back.


 I'll make a separate thread, don't wanna hijack this one for the guy haha

---

### Post by Cardamar on 2007-11-13
As for my version of Wine, it's 0.9.46. Typically, I hate running outdated software, but .49 wouldn't run Team Fortress 2.
As for the command; "wine /media/cdrom/setup.exe"
Setup started, but I immediately got the error =\

---

### Post by cogadh on 2007-11-13
The 0.9.49 update included bugfixes that specifically addressed issues with Steam and TF2, it should work fine. That is a totally different subject, though.

Considering that error could indicate a drive space problem, is it possible that you have run out of space in your home directory?

I'd also like to hear what SM0k3 did to get the game installed. Perhaps he is doing something or using a configuration that is not quite obvious that made the game install properly for him.

---

### Post by SM0k3 on 2007-11-13
> **cogadh said:**
> The 0.9.49 update included bugfixes that specifically addressed issues with Steam and TF2, it should work fine. That is a totally different subject, though.

Considering that error could indicate a drive space problem, is it possible that you have run out of space in your home directory?

I'd also like to hear what SM0k3 did to get the game installed. Perhaps he is doing something or using a configuration that is not quite obvious that made the game install properly for him.


I posted the error I'm getting over here -> [http://ubuntuforums.org/showthread.php?t=612413](http://ubuntuforums.org/showthread.php?t=612413)


As far as how I got it installed, I just opened up my cdrom in nautilus and double-clicked the setup.exe program and it went all the way through without a problem. *shrugs*

---

### Post by MightyMe on 2007-12-25
Trying to to install with wine 0.9.51 and Gutsy gives me "error 1628: Failed to complete installation". Any ideas...?

Had COD2 installed previously and it run without problem.

Attaching screenshot from command prompt.

Any help would be appreciated.

---

