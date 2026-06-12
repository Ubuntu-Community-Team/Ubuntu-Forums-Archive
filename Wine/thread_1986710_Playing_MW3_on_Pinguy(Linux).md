---
title: "Playing MW3 on Pinguy(Linux)"
date: 2012-05-25
forum: Wine
---

### Post by SMOR3S on 2012-05-25
So I finally switched from Windows 7 to Linux, and I have to say, I really enjoy it so far.... I am currently using Pinguy 64bit, and I have configured it a bit... I am trying to get MW3 to run through Linux with Wine, but I am having a few issues.... 

1st Issue: I installed MW3 through PlayOnLinux... It boots up fine, but when I go to play online the game says I don't have the current DLC 1, even though I purchased it...

2nd Issue: The game is really laggy playing online without the map pack, and there is a lot of inconsistent mouse input... mouse input lag...

3rd Issue: I have two steam clients supposedly O_o.... I can either launch MW3 through PlayOnLinux, and that launches steam by it self, or I can launch steam through wine... When I launch MW3 through PlayOnLinux, it shows the game, and I can play it some what.... When I launch steam through wine, I get errors like "File Not Found" I can how ever drag the icon from the Pinguy start menu, and mark it as trusted, and then it launches... The issue here though, is that if I launch steam through wine, it doesn't show MW3 in my game library, and it wants me to install it, even though it's already installed through PlayOnLinux -_- fml....

4th Issue: Mother of All Mouse Input Lag!! OMG!! This is so annoying... In Windows I can adjust the mouse settings way better..... I want to turn off mouse acceleration, and just use the Raw Input from my mouse.. I am using a Steelseries Xai, so I don't need drivers, cause I can tweak the DPI/CPI/Pulling rate from the mouse via, the LCD on the mouse itself...

I really want to get this all sorted out.... So far Second Life plays really good, way better than Windows, and my overall experience has been awesome... I am proud to say, I am a Linux user now... :P 

Thanks,

- SMOR3S - Kevin -

---

### Post by nothingspecial on 2012-05-25
*Thread moved to **Wine**.*

---

### Post by SMOR3S on 2012-05-25
> **nothingspecial said:**
> *Thread moved to **Wine**.*

Oh sorry, thanks <3

---

### Post by Dlambert on 2012-05-25
Maybe go into POL, and select configure. Then set your graphics memory to the correct MB/GB. And then get GLGL to Disabled, Direct Draw Renderer to OpenGL, Off screen renderer to FBO. Try this and tell me what happens. You have the proprietary drivers installed coreect? You could also mess around with "Mouse warp override" is MISC settings. And if all else fails, update wine to the latest with the RAWINPUT patch.

> StrictDrawOrdering to "enabled" Some people saw that increases fps. What GFX card?

---

### Post by SMOR3S on 2012-05-25
> **Dlambert said:**
> Maybe go into POL, and select configure. Then set your graphics memory to the correct MB/GB. And then get GLGL to Disabled, Direct Draw Renderer to OpenGL, Off screen renderer to FBO. Try this and tell me what happens. You have the proprietary drivers installed coreect? You could also mess around with "Mouse warp override" is MISC settings. And if all else fails, update wine to the latest with the RAWINPUT patch.

 Some people saw that increases fps. What GFX card?

The current wine version running with MW3 is 1.4.... But this still doesn't explain where I install MW3 from.... PlayOnLinux... Or Steam through Wine?

*EDIT* I am currently using the Nvidia drivers from the Find/Install Missing Drivers.... I got this from using "Sudo Su" then "apt-get update"......

The Nvidia Control panel that I am use to in Windows is called "Nvidia X Server Settings" O_o did I install the correct drivers?

*EDIT #2* Changed the configure settings, I will let you know how they run.....

*EDIT #3* The mouse is still messed up in game, and it's still kind of laggy.... -_- lol.... I also realized I don't have support for steam overlay running MW3 through PlayOnLinux, and I still don't have my DLC 1... Should I just install MW3 through Steam/Wine, and scratch the whole PlayOnLinux thing, cause,  as of now it's really now working to good....

---

### Post by pinguy on 2012-05-25
Playonlinux and wine uses two different install folders.

The apps and games you install with wine goes into ./.wine
and PlayOnLinux goes into ./.PlayOnLinux

So depending on what you used to install it will be where its stored.
So aps/games installed with PlayOnLinux can't be seen in Wine and vice versa.

---

### Post by SMOR3S on 2012-05-25
> **pinguy said:**
> Playonlinux and wine uses two different install folders.

The apps and games you install with wine goes into ./.wine
and PlayOnLinux goes into ./.PlayOnLinux

So depending on what you used to install it will be where its stored.
So aps/games installed with PlayOnLinux can't be seen in Wine and vice versa.

To make that simpler? I am going to have to use Wine to play it then?, cause with PlayOnLinux, I don't get full steam support, nor do I have the ability to use my DLC....

---

### Post by SMOR3S on 2012-05-25
I un-installed MW3 on PlayOnLinux, and re-installed it on Wine, but the IW5MP.exe keeps crashing at startup...... I have it installed on Wine, but it's not installed on PlayOnLinux.. Can I get some help? I really want to play my games, I don't want to have to go back to Windows.......

---

### Post by SMOR3S on 2012-05-25
Hello? can I get some help... I am trying to run Steam through PlayOnLinux, and it's crashing... Please, I need help... All I want to do is play MW3....

---

### Post by SMOR3S on 2012-05-25
Hello? can I get some help please? I am pulling my hair out, really....

---

### Post by SMOR3S on 2012-05-25
Fine what ever, you guys win, I can't get any help... I am going back to Windows 7, at least it can run games....

---

### Post by haqking on 2012-05-25
everyone here are volunteers.

Bumping your own thread is ok usually if once every 24 hours.

You are being impatient and rude.

Also it is a game, hardly high priority.

take a chill pill or pay for support.

Peace

---

### Post by SMOR3S on 2012-05-25
> **haqking said:**
> everyone here are volunteers.

Bumping your own thread is ok usually if once every 24 hours.

You are being impatient and rude.

Also it is a game, hardly high priority.

take a chill pill or pay for support.

Peace

I want to play it on Linux.. please help..

---

### Post by haqking on 2012-05-25
> **SMOR3S said:**
> I want to play it on Linux.. please help..

read again what i said.

PATIENCE.

If i want to play games i boot into windows, so i cant help you.

Those that can can and will only help if and when they read the thread and feel obliged too.

Peace

---

### Post by CharlesA on 2012-05-25
> **SMOR3S said:**
> Fine what ever, you guys win, I can't get any help... I am going back to Windows 7, at least it can run games....
Threatening to go back to Windows doesn't really help.

+1 to Patience. I use Windows to play games, same as haqking.

---

### Post by SMOR3S on 2012-05-25
> **haqking said:**
> read again what i said.

PATIENCE.

If i want to play games i boot into windows, so i cant help you.

Those that can can and will only help if and when they read the thread and feel obliged too.

Peace

:( I might just go back to Windows.... I thought Unbuntu would be awesome, but it just sucks... it's useless really...

---

### Post by haqking on 2012-05-25
> **SMOR3S said:**
> :( I might just go back to Windows.... I thought Unbuntu would be awesome, but it just sucks... it's useless really...

Use what works for you or what you can make work.

Peace

---

### Post by SMOR3S on 2012-05-25
> **haqking said:**
> Use what works for you or what you can make work.

Peace

Pinguy runs Second Life smooth and good, but it's such a headache to get games in steam working... :( I am so stressed if you couldn't tell...

---

### Post by lisati on 2012-05-25
Thread closed to give the OP a chance to cool down. We are all volunteers here. Bumping your thread more than once every 24 hours is considered rude here.

---

### Post by lisati on 2012-05-25
Thread re-opened.

---

### Post by Dlambert on 2012-05-26
You will  not have full steam support until it's native on Linux. Your DLC should work as long as you download it, and the Steam overlay causes problems. Disable it.

---

### Post by Brebs on 2012-05-29
For the mouse issue:

Put e.g. *usbhid.mousepoll=1* in the grub config, to poll for mouse movements at 1000hz rather than the default of 125hz.

And for mouse acceleration:

[http://xorg.freedesktop.org/wiki/Development/Documentation/PointerAcceleration](http://xorg.freedesktop.org/wiki/Development/Documentation/PointerAcceleration)
[https://bbs.archlinux.org/viewtopic.php?id=88104](https://bbs.archlinux.org/viewtopic.php?id=88104)
[http://www.gdargaud.net/Hack/LinuxMouse.html](http://www.gdargaud.net/Hack/LinuxMouse.html)

---

