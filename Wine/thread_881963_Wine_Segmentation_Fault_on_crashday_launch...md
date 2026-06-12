---
title: "Wine Segmentation Fault on crashday launch.."
date: 2008-08-06
forum: Wine
---

### Post by cmb11 on 2008-08-06
Hey Guys... i installed a game called "crashday" and when i'm launching the game through wine i get this output:


fixme:wininet:INET_QueryOptionHelper INTERNET_OPTION_CONNECTED_STATE: semi-stub
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
Segmentation fault


I tried the game on :mad::mad: windows vista :mad::mad: and it worked flawlessly.. plus i read on the wine website that this game is supported by wine and doesn't need any sort of tweaking to play it...

PS: I heard that a patch for wine called (3dMark) can solve it.. is it really related??

thanks..

---

### Post by cmb11 on 2008-08-06
anyone?? :(:(:(

---

### Post by cmb11 on 2008-08-06
#
fixme:wininet:INET_QueryOptionHelper INTERNET_OPTION_CONNECTED_STATE: semi-stub
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
Segmentation fault
#


I get this when launching a game in wine... but i don't think its wine related... what is a segmentation fault and how can i fix it ????

---

### Post by cmb11 on 2008-08-06
:confused::confused::confused::confused::confused::confused::confused:

---

### Post by cmb11 on 2008-08-06
:(:(

---

### Post by nbayiha on 2008-08-06
What's the command you are inputing while running your game ?

---

### Post by tech9 on 2008-08-06
> **cmb11 said:**
> #
fixme:wininet:INET_QueryOptionHelper INTERNET_OPTION_CONNECTED_STATE: semi-stub
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
Segmentation fault
#


I get this when launching a game in wine... but i don't think its wine related... what is a segmentation fault and how can i fix it ????


you can try deleting your .wine folder under your home directory - then run wine again and it will create a new cfg... hope that helps!

---

### Post by cmb11 on 2008-08-06
I'm using: 

wine Crashday.exe

and i tried deleting .wine and did install many versions of wine (with clean installations)...

so i don't think the problem is directly related to wine...

PS: the game (Crashday) is supported by wine and it doesn't require any patches.. plus i'm running wow, hl, hl2, portal, nfs, d2, sims2, czero and many more games without a single error!!!

---

### Post by nbayiha on 2008-08-06
@cmb11
[http://ubuntuforums.org/showthread.php?t=881963](http://ubuntuforums.org/showthread.php?t=881963)
Dude don't open same thread like this without a day or two at least. You can try to bump them but opening new thread won't help at all. 
Anyway did you try to google you error ? maybe that will help you.

---

### Post by tech9 on 2008-08-06
> **nbayiha said:**
> @cmb11
[http://ubuntuforums.org/showthread.php?t=881963](http://ubuntuforums.org/showthread.php?t=881963)
dude don't open same thread like this without a day or two at least. You can try to bump them but opening new thread won't help at all. 
Anyway did you try to google you error ? Maybe that will help you.

+ 1 :ks

---

### Post by cmb11 on 2008-08-06
@nbayiha

well you're right about the threads but my first one didn't seem to get any attention...

plus yes i did a google search about the game support in wine and the segmentation fault I'm getting... The game is supported by wine and it should run just fine!!

the thing is that I don't understand the error I'm getting!! Can I get additional details of the error by adding a certain command??

---

### Post by colobix on 2008-08-06
The drive_c folder and its files will not be deleted when you uninstall wine. Delete the config file, drive_c folder manually and then you can uninstall wine.

The problem could be that the emulated c: station isn't pointed to the right folder (drive_c) in the wine folder.

But in the future, do not save your windows programs under c: but under your home folder in z: so you can create program launcher and doesn't need to delete the programs and games when  are bugs with Wine.

---

### Post by cmb11 on 2008-08-06
when I did the installation of different wine versions I deleted manually the files in (.wine) but I kept drive_c bcoz it contains the games and I deleted the (windows) folder in (.wine/drive_c/).. So I only kept the game files...

---

### Post by cmb11 on 2008-08-06
when I installed the different wine versions I manually deleted the files in (.wine) but I kept drive_c bcoz it contains the games and I deleted the (windows) folder in (.wine/drive_c/).. So I only kept the game files...

---

### Post by Dylock on 2008-08-06
Just from my experience from programming, a seg fault is what happens when your trying to access memory you're not suppose too.

---

### Post by colobix on 2008-08-06
Ok but have u ever tried with program launchers to your games insted of commands?
Move everything from the drive_c folder and place them on your own home folder so you can create launchers and place them on your applications menu.

---

### Post by cmb11 on 2008-08-06
@Dylock

Do u mean that I don't have the permission to access some memory? 

I tried "gksudo wine" (graphical sudo) and now i have this output:

#
Could not load Mozilla. HTML rendering will be disabled.
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSwine: configuration in '/root/.wine' has been updated.
fixme:wininet:INET_QueryOptionHelper INTERNET_OPTION_CONNECTED_STATE: semi-stub
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
#

when I got root permission the segmentation fault is gone... [WEIRD, I never used root permissions in wine]  but now what is this "error_handler" thing!!

---

### Post by cmb11 on 2008-08-06
@colobix

yup I did that.. when I click the launchers nothing happens... The virtual desktop opens for like 2-3 seconds and then it closes automatically...

BTW u can create launchers for games in drive_c by using this command:

#
env WINEPREFIX="/home/username/.wine" wine "C:\Program Files\path_to_game.exe"
#

---

### Post by cmb11 on 2008-08-06
Thank you all for helping me !!!!

I'm waiting for your solutions and suggestions...

---

### Post by colobix on 2008-08-06
So have u tried to unactivate visual effects since it starts and stops when u run a program with wine?

---

### Post by cmb11 on 2008-08-06
@colobix

well I disabled all visual effects... but I'm getting the same error..

#
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
error_handler: C:\windows\profiles\All Users\Application Data\Trymedia\data\
#

Thanks colobix for ur tips!!

What do these 4 lines stand for?!?! 

C:\windows\profiles\All Users\Application Data\Trymedia\data\ (The folder is empty!)

---

### Post by bodhi.zazen on 2008-08-06
> **cmb11 said:**
> anyone?? :(:(:(

Moved to the WINE section.

[cmb11]("http://ubuntuforums.org/member.php?u=530014") , please do not start a new thread on the same topic. It causes confusion and duplication of effort. 

Your best source of information on wine is winehq :

[http://www.winehq.org/](http://www.winehq.org/)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12256](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12256)

Not much there, but it is listed a s"silver" with 8.04 and wine RC

IMO, wine is not a drop in replacement for windows and you need to be willing to research and problem solve a little.

Because of this, and because machines have so much or RAM, many people use Vitrualization these days ...

---

### Post by cmb11 on 2008-08-06
@bodhi.zazen

Thank for your reply and sorry for the duplicated thread...

I never had such problem with wine.. as I said I'm running a whole bunch of games (and it's all running much better on linux!) Now for every game I installed I had to tweak or patch something to be able to run it but this time I have no error report!!! I don't know what's wrong!! I did my google search and I knew that winehq says this game is rated silver and does not require wine tweaking!! that's why I opened a new thread that is somehow not related to wine.. I don't know how to delete a thread or move it to another section... Sorry again and thanks for your help.

---

### Post by bodhi.zazen on 2008-08-06
> **cmb11 said:**
> @bodhi.zazen

Thank for your reply and sorry for the duplicated thread...

I never had such problem with wine.. as I said I'm running a whole bunch of games (and it's all running much better on linux!) Now for every game I installed I had to tweak or patch something to be able to run it but this time I have no error report!!! I don't know what's wrong!! I did my google search and I knew that winehq says this game is rated silver and does not require wine tweaking!! that's why I opened a new thread that is somehow not related to wine.. I don't know how to delete a thread or move it to another section... Sorry again and thanks for your help.

LOL, no problem, I understand. The "problem" with wine is it takes a bunch of tweaking and each version of wine is it's own beast.

---

