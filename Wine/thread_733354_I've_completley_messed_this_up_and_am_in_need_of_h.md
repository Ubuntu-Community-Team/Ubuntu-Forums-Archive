---
title: "I've completley messed this up and am in need of help!"
date: 2008-03-23
forum: Wine
---

### Post by thehereaway on 2008-03-23
I am an absolute beginner at Ubuntu, i only first heard about it when my windows crashed, which i found out was an illegal copy so therefore couldn't reinstall, and my friend offered me this free downloadable alternative. Obviously i was over the moon, because i needed my important files i had on my PC. 

However, i find Ubuntu very very confusing. Half the time i have no idea what i am doing, for example when i am looking around at the files on my computer (on windows it was easy to navigate, where as on Ubuntu you have 'lib' and 'bin' and i have no idea what any of this means lol)

So anyways, i was really desperate to install Guitar Pro and Acoustica Beatcraft one night so i downloaded Wine off of synaptic. I installed the demos for both but it went crazy and instead of text in the Wine Config i had little music notes :confused: So i figured i would just uninstall both the programs and start fresh. However i am an idiot, and they wouldnt uninstall so i tracked down the files and deleted them however this didnt remove the programs from the  main menu (On windows i think you could right click and delete something from the start menu)

anyways i was left with this...(grrr seems i cant print screen whilst i am looking through the main menu) but basically the menu shows the programms, even though they arent not isntalled and now there is no way to uninstall them because im stupid and deleted the files.  

I tried re-installing wine to see if it would get rid of them, but no they were still there. Then i did something utterly utterly stupid, god knows what i was on but i think (this was a few weeks ago) i deleted the Wine folder...the actual Wine folder, if that makes sense...

because i wanted to play FM08, so have been looking into how to install it, and when ever i try to run something with Wine it says

> darren@Darren:~$ wine jre-1_5_0_09-windows-i586-p-s.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/darren', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\jre-1_5_0_09-windows-i586-p-s.exe": Module not found
darren@Darren:~$ 


Any ideas how i get Wine back? ...yes im an idiot, im not normally this stupid but its a new OS and i wasnt really sure about anything, please be nice and dont laugh at me lol

---

### Post by happyhamster on 2008-03-23
> **thehereaway said:**
> However, i find Ubuntu very very confusing.It's a new OS, and it isn't like windows, so it will take some time to get used to.

> Half the time i have no idea what i am doing, for example when i am looking around at the files on my computer (on windows it was easy to navigate, where as on Ubuntu you have 'lib' and 'bin' and i have no idea what any of this means lol)
As a user, you normally only have to deal with your home dir, because everything important is there.

> So anyways, i was really desperate to install Guitar Pro and Acoustica Beatcraft one night so i downloaded Wine off of synaptic. I installed the demos for both but it went crazy and instead of text in the Wine Config i had little music notes :confused:Apparently there are other people with font problems. Perhaps you'll find some info here:
[http://appdb.winehq.org/appview.php?iAppId=246](http://appdb.winehq.org/appview.php?iAppId=246)

A standard font-solution is to install the ms truetype fonts, (although I doubt it will help in this case it won't hurt to try) :

sudo apt-get install msttcorefonts

> 
 So i figured i would just uninstall both the programs and start fresh. However i am an idiot, and they wouldnt uninstall so i tracked down the files and deleted them however this didnt remove the programs from the  main menu (On windows i think you could right click and delete something from the start menu)
To uninstall a wine program, open a terminal and type:

uninstaller

> anyways i was left with this...(grrr seems i cant print screen whilst i am looking through the main menu) but basically the menu shows the programms, even though they arent not isntalled and now there is no way to uninstall them because im stupid and deleted the files.  This is an Ubuntu/wine bug I believe. Anyway, to get rid of the menu entries, right-click the main menu and choose Edit Menus. 

> I tried re-installing wine to see if it would get rid of them, but no they were still there. Then i did something utterly utterly stupid, god knows what i was on but i think (this was a few weeks ago) i deleted the Wine folder...the actual Wine folder, if that makes sense...
Deleting the hidden .wine folder is actually a good way of creating a fresh wine. I do it several times a week on average :)
After deleting the folder, to create a new .wine folder, issue the command:

winecfg

> Any ideas how i get Wine back?
- First get rid of wine completely:

sudo apt-get remove --purge wine

- Delete the .wine folder, and re-install wine:

sudo apt-get install wine

- Run winecfg to configure wine:

winecfg

- It's usually best to start with a virtual desktop, and also to take a look at the audio settings before trying to install anything. For a lot of info on wine, see this excellent thread:
[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

>  ...yes im an idiot, im not normally this stupid but its a new OS and i wasnt really sure about anything, please be nice and dont laugh at me lol
Wine is still beta software, so there are no guarantees: trying to get something to run can be frustrating at times. But as long as you don't run wine as root you're basically safe to experiment. (If you bork wine, just uninstall and wipe the .wine folder and start afresh.)

Good luck.

---

### Post by happyhamster on 2008-03-23
> **thehereaway said:**
> Then i did something utterly utterly stupid, god knows what i was on but i think (this was a few weeks ago) i deleted the Wine folder...the actual Wine folder, if that makes sense...
Perhaps I misunderstood: deleting the hidden .wine folder in your home dir is good. (Go to Places-->Home Folder and press ctrl-h to be able to see hidden files.)

Deleting "wine" folders down below in the file sytem is bad. They and their contents are taken care of when uninstalling wine (sudo apt-get remove wine).

---

### Post by thehereaway on 2008-03-23
> **happyhamster said:**
> Perhaps I misunderstood: deleting the hidden .wine folder in your home dir is good. (Go to Places-->Home Folder and press ctrl-h to be able to see hidden files.)

Deleting "wine" folders down below in the file sytem is bad. They and their contents are taken care of when uninstalling wine (sudo apt-get remove wine).

hey, thanks for the really good reply...ill test it all out in a second. I THINK it was the bad wine folder, where would i find it on my computer to check? if i have deleted this one, do you have an idea what i would do to fix it?

---

### Post by happyhamster on 2008-03-23
> **thehereaway said:**
> hey, thanks for the really good reply...ill test it all out in a second. I THINK it was the bad wine folder, where would i find it on my computer to check? if i have deleted this one, do you have an idea what i would do to fix it?
You don't have to do anything special I think, just try to uninstall and re-install wine (and get rid of the .wine folder). If that succeeds, then the system was able to fix it  itself. If not, your friendly terminal will tell you what is wrong (and will offer suggestions on how to repair the breakage).

---

### Post by thehereaway on 2008-03-23
> **happyhamster said:**
> You don't have to do anything special I think, just try to uninstall and re-install wine (and get rid of the .wine folder). If that succeeds, then the system was able to fix it  itself. If not, your friendly terminal will tell you what is wrong (and will offer suggestions on how to repair the breakage).

oh wow, i think it worked after i deleted the hidden file then re-installed. i now have the 'drive c' in my places menu...thanks so much :)

---

