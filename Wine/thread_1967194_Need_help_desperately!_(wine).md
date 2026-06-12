---
title: "Need help desperately! (wine)"
date: 2012-04-27
forum: Wine
---

### Post by grubbyfoot on 2012-04-27
Alright, guys I only have enough experience with linux to install it and know that wine can be used to run windblows programs, and i am LOST! I am trying to play EverQuest on Ubuntu Studio 12.04 and I am getting a message after pressing the play button on the SOE launchpad that says "Internal Errors- Invalid parameters received". I have googled this issue for about 4 hours now to no avail and my fingers are goin numb. So far I've figured out that I need to "add a workaround to ubuntu's stupid ptrace breakage", and I have no idea how to do that or even wtf it means. Any help would be awesome. Please guys, Im desperate!

---

### Post by llamabr on 2012-04-27
> **grubbyfoot said:**
> Alright, guys I only have enough experience with linux to install it and know that wine can be used to run windblows programs, and i am LOST! I am trying to play EverQuest on Ubuntu Studio 12.04 and I am getting a message after pressing the play button on the SOE launchpad that says "Internal Errors- Invalid parameters received". I have googled this issue for about 4 hours now to no avail and my fingers are goin numb. So far I've figured out that I need to "add a workaround to ubuntu's stupid ptrace breakage", and I have no idea how to do that or even wtf it means. Any help would be awesome. Please guys, Im desperate!

I assume you're reading this:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2939](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2939)

FWIW, Wine is very rarely the correct solution to your problem.  It often works poorly, or not at all.  If you absolutely need to run some windows software, you might consider installing windows, or dual booting, your machine.

---

### Post by grubbyfoot on 2012-04-27
Yea, thats one of the fifteen articles that said the exact same thing. I had xp on this machine (downgraded from vista) and I cannot find drivers that work anywhere. I dont have any OEM disk besides xp and cannot afford them, so does this mean Im potentially screwed?

---

### Post by forrestcupp on 2012-04-27
Did you do what it said in the app database post that llamabr linked to? You need to go into winecfg and set it for Windows XP as the OS, if it isn't already like that. Then you also need to open a terminal and run the winetricks listed:
```
winetricks corefonts d3dx9
```
Before doing any of that, you need to make sure you're using the latest version of Wine. You also need to remember that Wine doesn't work with every Windows software out there. But it does look like people have gotten this to work.

---

### Post by grubbyfoot on 2012-04-27
He says in the articles that 
I created a new prefix to see what was required, the Launcher needed "winetricks corefonts" and the game needed "winetricks d3d9x".  That was it for me.

Does that mean that he had to set a seperate prefix for both the launcher and the game? If so, how does one do this? Like I said I am a complete ubuntu n00b, so sorry for all of the questions.

---

### Post by grubbyfoot on 2012-04-28
Ok, I figured it out enough to make it run. However, it is soooooolaggy. I have a dual core @1.7Ghz a piece and two gigs of RAM, which is more than enough to run EQ, so I am guessing it wine. Any tips on how to make it run faster and smoother?

---

### Post by vanquishedangel on 2012-04-28
> **grubbyfoot said:**
> Ok, I figured it out enough to make it run. However, it is soooooolaggy. I have a dual core @1.7Ghz a piece and two gigs of RAM, which is more than enough to run EQ, so I am guessing it wine. Any tips on how to make it run faster and smoother?

Are you using the opensource graphics drivers? they have 3d acceleration but it is not as good as the proprietary ones yet, eventually will be better but until then you need the proprietary ones. In one of your menu's you should see an entry for Hardware Dirves or Additional drivers, mine is under preferences in Lubuntu. Also Playonlinux ( everquest 2 is in the installer list)can be a big help to new people or those that just don't wanna go through the trouble.

Also wine is rarely the issue, the issue is usually P.E.B.K.A.C. (problem exists between keyboard and chair)in most cases, there are many configurations in wine that can be tweaked for any program just like many do in windows, but this isn't for the lighthearted and takes patience.

I have been through this many times myself but hang in there ( I am from the times when you had to compile your own graphics drivers :)).

This may help if not already posted [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2939](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2939)

Also if you have an ati card and dont want to use the proprietary from the repo's [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by grubbyfoot on 2012-04-28
Sounds good I just downloaded PoL and now I need to find the prop. drivers. As far as I knew Linux didnt support prop. drivers or there was none. ???

---

### Post by vanquishedangel on 2012-04-28
> **grubbyfoot said:**
> Sounds good I just downloaded PoL and now I need to find the prop. drivers. As far as I knew Linux didnt support prop. drivers or there was none. ???

Depends on the graphics card nvidia and amd/ati have linux drivers, I am only familiar with ati tho

ati drivers here [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
just enter your info correct and it will take you to the webage with the drivers for ati (if your graphics is too old they will not support it and you will be stuck with the opensource ones or need to find them else where online)

Also it is best if you are new to ubuntu to only use software from the repo's just fyi, so always try that first k.

---

### Post by grubbyfoot on 2012-04-28
It runs just as choppy on PoL, but Im sure it due to the lack of drivers. I cannot figure em out. I have downloaded every driver matching ATI thru the synaptics manager and I cant get anything to work. I even managed to get CCC but it wont open because I dont have any drivers. I thought maybe its configured wrong, so I opened a terminal and typed in aticonfig. It told me I was missing the drivers This is becoming a HUGE pain in the ***.](*,)

---

### Post by houseworkshy on 2012-04-28
You could try running windows in virtual box.  It's in the repros.  It's a virtual machine but cripple ware, unless one pays for it it won't recognise external drives.  A workaround to this is to tell it iso's are it's drives. It would be another way of doing it, windows would think it was running on whatever you told it it was.  
EverQuest isn't a bad game but there are others,  Try searching on youtube "+game +ubuntu"  some are pretty amazing ( linux can usuallly do more with a machine than windows ) and many are free.

---

### Post by vanquishedangel on 2012-04-28
> **grubbyfoot said:**
> It runs just as choppy on PoL, but Im sure it due to the lack of drivers. I cannot figure em out. I have downloaded every driver matching ATI thru the synaptics manager and I cant get anything to work. I even managed to get CCC but it wont open because I dont have any drivers. I thought maybe its configured wrong, so I opened a terminal and typed in aticonfig. It told me I was missing the drivers This is becoming a HUGE pain in the ***.](*,)

they can be, try hardware drivers or additional drivers in one of your menus after you uninstall the things you did install, I assume you are using an ati card then so it should install the proprietary drivers from there for you, note: do not install the one marked post release. the guide I linked before tells how to do that.
a great game for ubuntu is heroes of newerth here [http://www.heroesofnewerth.com/spotvid_splash.php](http://www.heroesofnewerth.com/spotvid_splash.php) and it is free, it is like league of legends

insted of looking in the menu's you can open the terminal and type "sudo jockey-gtk" and after you password the driver installer should open ( am checking this thread often)

---

### Post by oldos2er on 2012-04-28
Moved to Wine.

---

### Post by ExSuSEusr on 2012-04-29
Ok, I feel your pain!  It took a while to get Everquest working on my machine too.

For those of you telling him "to just find another game..."  You don't understand how one game can be THAT game for someone.  It's like you craving... I mean seriously craving a pizza and someone telling you to eat a hot pocket instead, because it's easier.  

So, first I am not sure if you are talking about EQ1 or EQ2 - I will assume you mean EQ2.

It's not as simple as installing wine and downloading the game.

Here's what I did.  Now, before I get into this... keep in mind I left Ubuntu and went to Linux Mint - since Mint is based on Ubuntu / Debian I am sure it will work for you too.

1. Install **wine**, **winetricks**, **wine configuration manager**.
2. Install PlayOnLnux - you can get it from your Ubuntu Software Center and I think Synaptic has it too.

3. Once you have those two installed.  Make sure your video card is installed properly.  *lscpi | grep VGA* will tell you what type of video card you have. Going to your Systems Settings and clicking "Additional Drivers" will show if you the current driver for your card installed.  If it not, make it happen.  Direct3D is included with Mint distro - so I am sure it is with Ubuntu too (since I have played EQ2 on Ubuntu).

4. Bring up your terminal and type "regedit"

5. In regedit do the following:

- Go to HKEY_CURRENT_USER tab.
- In the HKEY_CURRENT_USER tab go to "Software" and then "Wine"

You will need to add some strings here since they aren't going to be there.

Right click on Wine and select Add Key.  Name it Direct3D.

Now on Direct3D right click and Add String

Name it DirectDrawRenderer.  Now right click on the newly created string and select Modify.  Type opengl

Repeat this process for the following:

OffScreenRenderingMode -> fbo
PixelShaderMode -> enabled
RenderTargetLockMode -> texdraw

Now close out of regedit.

Open up Wine Configuration - should be in your applications menu under Wine.

Go to the Graphics tad and Uncheck Allow the  Window Manager to Decorate Windows. 

Check Emulate a Virtual Desktop and  put the 1280x960 size in there or whatever size you like. Make sure it is the same size you set up for the game in EQSettings.exe

Almost there...

You MUST have mscorefonts installed.  The game need Arial to run.

To do this bring up your terminal and type: sudo apt-get install ttfscorefonts-installer.

Once you have done all that start PlayOnLinux (this is a user friendly front end to Wine).

Select Add and under games you will see Everquest II Sentians Fate.  Install and follow the directions.  It will put a launcher on your desktop.  

If you were talking about Everquest I - I am sure the same will work, but I don't know for sure.

Voice chat is sketchy - I never quite got it work in Linux.  Still one of those annoying things I want to fix but I hope this install of Linux Mint will prove more friendly than Ubuntu.

Summary:

You need:

Wine
Winetricks
Wine Configuration Manger
PlayOnLinux
MScorefonts

Correct video driver with Open GL

Configure your "regedit" 
Configure your Wine Config

Should get you up and going. I hope.

I know how it feels not to be able to play - makes it worse when someone tells you go play something else.  :mad:

---

