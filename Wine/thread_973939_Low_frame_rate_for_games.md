---
title: "Low frame rate for games"
date: 2008-11-07
forum: Wine
---

### Post by Horomancer on 2008-11-07
I justed installed Wine on my system, then set about getting Steam and Portals through the steam client. I was real happy to see that this process went off without a hitch, but when I actually started the game things weren't 100%. I got a steam client message saying that my video card drivers were not up-to-date. I continued without addressing the problem and found the frame rate to be real low. I don't know how to bring up the little display but it's probably not more than 15 fps.
Main specs-
3.20 GHZ Celeron D
nVidea 7950 GT
1GB ram

So what I would like to know is if my problems stem from-
1. Just a weak machine that can't run the wine layer and the game at the same time.
2. Wine not having the drivers to use my video card even though linux does
3. I shouldn't be bothering with such complex games and should go play them on XP

I've seen articles of other people playing TF2 and the like with only slight drops in fps as compared to running them on Windows. I'm really hoping I can get some info from more experienced linux gamers.

---

### Post by ski309 on 2008-11-07
I just recently started playing Portal on my Ubuntu machine with a 7900 GTX card and it works great.  The only problem is, you need to set Portal to run in DirectX 8/8.1 for it to run at a good speed.  To do that:

1) Open Steam
2) Right click on Portal, choose "Properties"
3) Click "Set Launch Options"
4) in the text box, add "-dxlevel 80" or "-dxlevel 81".  Try "81" and go down to "80" if there's a problem.
5) save that and run the game.

This won't look quite as nice as running in DX9 on XP, but on the bright side your card is fast enough that you can pretty much jack all the settings that **are** available with DirectX 8 to the highest setting.

---

### Post by Horomancer on 2008-11-07
Thanks for the info but no change has occured. Portals still runs but at 15fps and about a 1/2 second lag to respond to any input like mouse movements.
I also still get this message when i try to launch the game-

Your Video drivers appear to be out of date and could cause problems if you choose to continue and run the game. We strongly recommend that you follow the link below and update your video drivers to the latest available from your driver vendor.

Your Driver details

Windows Version:        Windows Vista

Description:            Direct3D HAL

Version:                7.15.10.16921

Could running Portals as a different version of Windows help matters? Is there anyway to make steam see the drivers as up-to-date?

Steam itself runs pretty slowly with any window taking some time to think before it closes down or opens.

---

### Post by Dark9204 on 2008-11-08
Change your windows version in wine to Windows Xp and it should work fine.

Performace boost tip:
Open the text editor and save this as steam.sh :
WINEDEBUG=fixme-all wine C:/Program\ Files/Steam/Steam.exe
This will turn off the debbuger, and will result in better performace.

Now, to start your steam, just type sh steam.sh in a terminal. Remember that the file must be in your home folder, unless you want to change dir every time you wants to start it. which you obviously dont want.

Now, leave the terminal open, if you close it you will close steam.
You dont have to do the winedebug command to start steam games because they are started in steam, so they have already the debugger off.

Also dont forget the dxlevel 81 tag. Also, use wine 1.0.1 for best performance.

Also, have you install the graphics card driver at System->Administration->Hardware Drivers?

---

