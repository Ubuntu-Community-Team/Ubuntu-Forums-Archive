---
title: "Steam.... Nothing happens!"
date: 2011-10-17
forum: Wine
---

### Post by Pr0t3us on 2011-10-17
Ubuntu 11.10 + wine 1.2.3

I installed the steam client with wine and then from within the client i downloaded a couple games. I try to click "Play" except nothing happens. I tried going into the steam folder where the games are installed and launching directly the executeables for the games with wine... still nothing

I switched to Ubuntu from windows a couple days ago because i want a fast and stable system (and some other reasons) but i am a complete linux noob/ computer noob in general at that; I have no idea what to do.

Whats going on?

---

### Post by lovinglinux on 2011-10-17
I haven't installed Steam on 11.10 yet, so I can't check if this is a bug or not. However, I would recommend using Playonlinux to install wine applications.

I will try Steam today and will post the results.

---

### Post by lovinglinux on 2011-10-17
I am experiencing the same problem. Possible solution:

Right-click on the game you want to play and select Properties, then click "SET LAUNCH OPTIONS" and put **-dxlevel 80** in the field. Click OK, then Close. Launch your game.

BTW, you will have a much better experience with Steam if you log into Unity 2D instead of 3D. As least on my system the performance of games on Unity 2D is much better.

---

### Post by Pr0t3us on 2011-10-17
Im in the steam folder now; right clicking the .exe for the game and i selected properties but I dont see any launch options anywhere..

also whats 2d unity and 3d unity?

---

### Post by lovinglinux on 2011-10-17
> **Pr0t3us said:**
> Im in the steam folder now; right clicking the .exe for the game and i selected properties but I dont see any launch options anywhere..

You need to launch Steam first, then click the game on the steam list of games you have installed.

> **Pr0t3us said:**
> also whats 2d unity and 3d unity?

About Unity: [http://en.wikipedia.org/wiki/Unity_%28user_interface%29](http://en.wikipedia.org/wiki/Unity_%28user_interface%29)

Unity 2D is essentially the fall-back for machines that cannot handle the 3D environment. They are very similar outside, but different inside.

When you start your Ubuntu and prompted to insert your login and password, there is a button on the right of the login panel, that allows you to choose between Unity 3D and Unity 2D.

---

### Post by Pr0t3us on 2011-10-17
> **lovinglinux said:**
> I am experiencing the same problem. Possible solution:

Right-click on the game you want to play and select Properties, then click "SET LAUNCH OPTIONS" and put **-dxlevel 80** in the field. Click OK, then Close. Launch your game.

BTW, you will have a much better experience with Steam if you log into Unity 2D instead of 3D. As least on my system the performance of games on Unity 2D is much better.

Found the "Set launch options" and i put in -dxlevel 80 ; still nothing happens

Also i tried logging in under 2d unity and when i started steam it seemed to work fine but i got all kinds of static outside the window, so i've switched back to what i guess was 3d.

---

### Post by lovinglinux on 2011-10-17
That fixed for me. I would recommend uninstalling Steam, installing Playonlinux and installing Steam from it. Then applying the -dxlevel 80 option.

---

### Post by Pr0t3us on 2011-10-17
uhm... how do i uninstall steam when its been installed with wine?

 (ubuntu is not proving to be particularly user freindly >.< )

---

### Post by lovinglinux on 2011-10-17
> **Pr0t3us said:**
> uhm... how do i uninstall steam when its been installed with wine?

 (ubuntu is not proving to be particularly user freindly >.< )

Click the home button to bring the Dash, then type *wine* and click the "Uninstall Wine Software".

Keep in mind installing and removing native applications using the Software Center is a breeze. Much easier than on Windows. Wine on the other hand is a complex tool that allows to install Windows applications on it's own fake Windows directory. So, don't be discouraged by how Wine works and if applications running on it doesn't work as expected. Most of the time, you will find similar native applications, usually better than the Windows counterparts, that can be easily installed or removed. Unfortunately, in regard to games, using wine is pratically unavoidable.

---

### Post by Formerly on 2011-10-17
I'm having the same issues. It began by installing Steam's .msi file under Wine, it would download games and when starting it would say "Preparing game ..." after this, the preparing window would close yet no game would start. I've uninstalled Steam and tried again, same issue over and over on all games.

So then I tried the suggestion of PlayOnLinux, but I'm not sure exactly how to work this application no matter how hard I look. I try its build-in "install" option, and when doing so a new screen opens that instantly freezes (gray), when force quitting this random frozen screen then the PlayOnLinux installer screen opens, installing Steam. I follow all the options and ... Then what? I open Steam from the wine directory? Same problem.

Except now after uninstalling Steam (I forget which way I uninstalled it) a blank file seems stuck within the Wine shortcut under "applications," but the file is blank. Apparently I cannot run Steam within PlayOnLinux no matter what is done, so everything seems jarbled and I'm unsure what to do.

---

### Post by lovinglinux on 2011-10-17
> **Formerly said:**
> I'm having the same issues. It began by installing Steam's .msi file under Wine, it would download games and when starting it would say "Preparing game ..." after this, the preparing window would close yet no game would start. I've uninstalled Steam and tried again, same issue over and over on all games.

So then I tried the suggestion of PlayOnLinux, but I'm not sure exactly how to work this application no matter how hard I look. I try its build-in "install" option, and when doing so a new screen opens that instantly freezes (gray), when force quitting this random frozen screen then the PlayOnLinux installer screen opens, installing Steam. I follow all the options and ... Then what? I open Steam from the wine directory? Same problem.

Except now after uninstalling Steam (I forget which way I uninstalled it) a blank file seems stuck within the Wine shortcut under "applications," but the file is blank. Apparently I cannot run Steam within PlayOnLinux no matter what is done, so everything seems jarbled and I'm unsure what to do.

When you install Steam using Playonlinux, it creates by defualt a Desktop luncher or you can launch the application by selecting it in Playonlinux list and then clicking "Run".

---

### Post by Pr0t3us on 2011-10-17
Ok I uninstalled the two games i downloaded (becuase i assumed there will be some new path something thingy when steam is installed with a different program) then I uninstalled the Steam client itself. I then installed via PLay on Linux  and it did its thing. So now i have steam installed again and am atm re-installing one of the games; will see how this works later when it finishes.

*sidenote* If i thought logging in before was bad; now with the play on linux installtion i thought i would have to reboot my computer , app was stuck for like 3+ minutes

also I noticed while playon linux went through its setup that it installed wine 1.3.something but when i look in wine config in the about tab it says its version 1.2.3

---

### Post by lovinglinux on 2011-10-17
> **Pr0t3us said:**
> Ok I uninstalled the two games i downloaded (becuase i assumed there will be some new path something thingy when steam is installed with a different program) then I uninstalled the Steam client itself. I then installed via PLay on Linux  and it did its thing. So now i have steam installed again and am atm re-installing one of the games; will see how this works later when it finishes.

*sidenote* If i thought logging in before was bad; now with the play on linux installtion i thought i would have to reboot my computer , app was stuck for like 3+ minutes

also I noticed while playon linux went through its setup that it installed wine 1.3.something but when i look in wine config in the about tab it says its version 1.2.3

Playonlinux can use multiple versions of wine.

---

### Post by Pr0t3us on 2011-10-17
so i have two versions of wine on my computer now? how do i know which one is the default?

---

### Post by Formerly on 2011-10-17
> **lovinglinux said:**
> When you install Steam using Playonlinux, it creates by defualt a Desktop luncher or you can launch the application by selecting it in Playonlinux list and then clicking "Run".
Hope I'm not hijacking but, the run option does nothing when I click it, nor did it create a desktop launcher.

---

### Post by lovinglinux on 2011-10-17
> **Pr0t3us said:**
> so i have two versions of wine on my computer now?

Don't worry. The other version resides in the Playonlinux folder and it is used only by it, so it won't affect your system or other applications installed directly via Wine.

> **Pr0t3us said:**
> how do i know which one is the default?

Launch Playonlinux, click "Tools >> Manage Wine Versions >> My Applications", then select the application to see which version of wine is being used.

---

### Post by lovinglinux on 2011-10-17
> **Formerly said:**
> Hope I'm not hijacking but, the run option does nothing when I click it, nor did it create a desktop launcher.

Close Playonlinux, start a terminal, type this on the terminal:

```
playonlinux
```

Hit *Enter* to start Playonlinux. Keep the terminal open, otherwise it will close Playoninux as well.

Select the Steam launcher, click *Run*. Check if you get any errors on the terminal. If yes, select them, right-click and copy. paste here between code tags.

---

### Post by Formerly on 2011-10-17
> **lovinglinux said:**
> Close Playonlinux, start a terminal, type this on the terminal:

```
playonlinux
```Hit *Enter* to start Playonlinux. Keep the terminal open, otherwise it will close Playoninux as well.

Select the Steam launcher, click *Run*. Check if you get any errors on the terminal. If yes, select them, right-click and copy. paste here between code tags.
No error dialogue

```
PlayOnLinux v3.7.3

Checking python :                 [ Ok ]
Running Steam

```
And just stops there.

---

### Post by Pr0t3us on 2011-10-17
ok game finished re installing  i put in "-dxlevel 80" in the set launch options; now when i go to launch the game i get a program error "The program AlphaPrime.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience." followed then by a suggestion to check out the wine appdb

---

### Post by lovinglinux on 2011-10-18
Have you both checked if you  have the latest proprietary driver for your video card installed?

I don't know what else it could be, except for one of those bugs in Wine. Unfortunately, Wine doesn't work all the time with all programs. Since Ubuntu 11.10 has just been released, I would keep an eye on WineDB to see if other users are experiencing the same problems and could find a solution.

Also, I am not an expert on Wine, so it is still possible that someone else could provide a better insight and solve the problem.

Although Steam is running on my machine, is far from being as good as it was on Ubuntu 11.04.

---

