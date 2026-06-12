---
title: "Trying to play Diablo iii PLEASE HELP!!!!"
date: 2012-06-05
forum: Wine
---

### Post by SoranSetsuna on 2012-06-05
So I installed the game ad everything but when i try running the game I et the error "An unexpected error occurred.  Please try again." Or "Application Error". The game closes before it actually starts, and when I try opening the game it says that it already exist but I find it nowhere. Also because I'm on the desktop the cursor arrow disappears when in the middle of the screen and appears again when moving away from me. The game is the beta version as well. I have tried looking for answers everywhere but can't find none. This is really frustrating me plz help!.

---

### Post by donkyhotay on 2012-06-05
From not only the content of your post but also your postcount it's obvious you're new. That's ok, everyone is new at one point or another. Here is some advice that will help you avoid newbie mistakes. First of all it helps if you read the guidelines which are stickied at the top of the forum. Had you done so you would have seen a large message in big red letters that reads: 

Wine and Windows related games on linux or related to wine in any kind, please post them in our [ wine forum](http://ubuntuforums.org/forumdisplay.php?f=313). If not they will be deleted or closed.

Furthermore had you continued to read the same guidelines you would have seen it stress the importance of being descriptive. You have told us nothing about your issue besides diablo3 won't launch. In order to help you we are going to need *way* more information then what you provided. What version of ubuntu do you have? What version of wine? What type of graphics card do you have? When you try running via CLI (terminal) what messages does it report? Finally, did you search the forums before posting? They may not be relevant but a quick search showed [multiple threads](http://ubuntuforums.org/search.php?searchid=86719914) that might point you in the right direction. Remember, we're all volunteers here. Help us to help you and you'll be more likely to have your issue resolved in a timely manner.

---

### Post by SoranSetsuna on 2012-06-05
I'm using Ubuntu v 12.04, WIne v 1.5.3 and playonlinux v 4.0.14 with an ATI HD Radeon 4600 graphics card series. 

While trying to run D3 I get this error.  "The application encountered an unexpected error." -    	 	 	 	 	 	   &#8220;Please use the report ID below when communicating with Blizzard about this issue - EB1C5BA5-B159-48B5-A760-13E9782B118F&#8221;

---

### Post by Torgas Prim on 2012-06-05
Soran, I also have Diii and found on the WineHq appdb that basically Diii needs to be copied over from a windows install, then add a command for /launcher in the shortcut and you should be ok. But you need to go read this all on the WineHq site to get exact details for your setup.

---

### Post by brainwash on 2012-06-05
Did you try to install it via PlayOnLinux? POL offers you a special Diablo III installation routine + a patched wine version (wine-1.5.5-DiabloIII_v2).

---

### Post by yaturner on 2012-06-09
I downloaded the latest version of PlayOnLinux 4.1.1 without installing the special version of Wine and just like that, it works again. Now if I can get it to run in full screen mode without a virtual desktop in wine, I'll be happy

---

### Post by arthurzennig on 2012-06-10
My Acer notebook ( core i3 2.4ghz, 4gb ddr3 and geforce 420m ) with ubuntu 12.04 is running fine. Actually, even better than on windows 7. 
I followed this tutorial:
[http://www.playonlinux.com/en/commentaires-1043.html](http://www.playonlinux.com/en/commentaires-1043.html)

- really simple and usefull. Check first the requirements.
But, after starting the game, i had some problems with the authentication, but i solved with this following advice:

[http://switching2linux.wordpress.com/2012/05/31/im-getting-stuck-at-authenticating-credentials-in-diablo-3-then-get-an-error-3007/](http://switching2linux.wordpress.com/2012/05/31/im-getting-stuck-at-authenticating-credentials-in-diablo-3-then-get-an-error-3007/)

the performance is really satisfying. Didn't have any problem until now. Hope it works for you.

---

### Post by geek.de.nz on 2012-06-12
> **yaturner said:**
> I downloaded the latest version of PlayOnLinux 4.1.1 without installing the special version of Wine and just like that, it works again. Now if I can get it to run in full screen mode without a virtual desktop in wine, I'll be happy

I cannot get it to run in full screen as well. Help!

Tried to go to Wine configuration -> tab Graphics and unticked "Allow the window manager to control the windows" to no avail.

Also tried "Emulate a virtual desktop" setting it to my resolution but that put the window on the wrong screen.

I'm using 12.04 with the latest updates.

Help would be greatly appreciated.
Thanks,
Tim

---

### Post by Tweak42 on 2012-06-14
To get fullscreen, the workaround I use is to turn off Nvidia Twinview before starting the game.  D3 then should allow you to choose fullscreen mode.  Changing any of the 3d settings crashes my game but it will remember the setting upon restarting it.  After the game is launched fullscreen I can turn Twinview on again and enable my second monitor.


> **geek.de.nz said:**
> I cannot get it to run in full screen as well. Help!

Tried to go to Wine configuration -> tab Graphics and unticked "Allow the window manager to control the windows" to no avail.

Also tried "Emulate a virtual desktop" setting it to my resolution but that put the window on the wrong screen.

I'm using 12.04 with the latest updates.

Help would be greatly appreciated.
Thanks,
Tim

---

### Post by ergo-proxy on 2012-06-14
For me it works out of the box (PoL) including full screen,etc. Before I installed PoL I already had wine installed.

---

### Post by brasilramos on 2012-06-20
> **ergo-proxy said:**
> For me it works out of the box (PoL) including full screen,etc. Before I installed PoL I already had wine installed.


What's your OS? I can't run fullscreen on Ubuntu 12.04 - I'm using POL

---

### Post by ergo-proxy on 2012-06-20
> **brasilramos said:**
> What's your OS? I can't run fullscreen on Ubuntu 12.04 - I'm using POL

12.04x64 I use PoL too, make sure you have up to date diablo3 pol script.

---

