---
title: "Heed help with Steam!"
date: 2008-03-27
forum: Wine
---

### Post by volksgewer on 2008-03-27
](*,) I have Steam running and I have games downloaded too. But, when I go to play them the get up to the menu screen and then the screen goes blank and "Cannot Display This Video Mode Optimum Resolution 1280x1024 60Hz. I HAVE MY RESOLUTION SET TO THAT! Can some one help me? ](*,)

---

### Post by Zaneyard on 2008-03-28
I, too, am receiving this error. When I load up CounterStrike: Source, I get my monitor's "Cannot display this video mode".
I haven't had the time to check if this is with other full screen games or not.
After a little searching I couldn't find anything, but I don't have the time right now. I will repost my solution here if I can find one.

---

### Post by Zaneyard on 2008-03-28
The only thing so far, that I have found, is this [http://ubuntuforums.org/showthread.php?t=561981&highlight=scripts]("http://ubuntuforums.org/showthread.php?t=561981&highlight=scripts")
Not completely sure if this is related, or works for this problem, but I will test It out and see what happens when I get the chance.
I have also read that disabling compiz can help things, I will also try that when I get the chance.
P.S. You spelled Need wrong.

---

### Post by Zaneyard on 2008-03-28
If you go down to the "How To" section of this page, [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731)
there are several startup options that may help. Again, I will try this when I get the chance.

This may work also
cd ~/.wine/drive_c/Program\ Files/Steam && WINEDEBUG=-all wine steam -applaunch 240



FYI, I have my wine configured in the "graphics" tab as follows: I have the window manager check box, checked, and the virtual display is not active. I will try using the virtual display sometime, though if I change these settings at all, the steam "tray icon" is unusable. I would like to play this fullscreen, but if i have to have it in the virtual window it won't be that big a deal.

---

### Post by Zaneyard on 2008-03-28
I do have my steam installed per the How-To specified on winehq. I installed CS:S through steam.

---

### Post by volksgewer on 2008-03-28
Thank you for all the help you have given me. I will also try to fix this problem too.

---

### Post by Zaneyard on 2008-03-28
According to WineHQ [http://appdb.winehq.org/commentview.php?iAppId=871&iVersionId=3731&iThreadId=21436]("http://appdb.winehq.org/commentview.php?iAppId=871&iVersionId=3731&iThreadId=21436")
All you have to do is disable pixel shaders, this looks promising and worth trying real quick after I get home.

---

### Post by Zaneyard on 2008-03-28
If anyone is following this thread, I frequently edit my posts. So it might be helpful to re-read anything you see as edited by me.

---

### Post by Zaneyard on 2008-03-28
I tried disabling pixel shaders altogether.
Did absolutely nothing for this problem.



Launching with this in the terminal did not do anything for me, I got a couple errors at first though
cd ~/.wine/drive_c/Program\ Files/Steam && WINEDEBUG=-all wine steam -applaunch 240


Disabling compiz did not work, unless I did not properly disable it.


Running Steam in the Wine virtual window is a success. Could you please change the name of this thread to "CS:S in fullscreen problems" or something like that.
Fonts are really mussed up, but it isn't a big deal.


The only thing I have to test is this [http://ubuntuforums.org/showthread.php?t=561981&highlight=scripts]("http://ubuntuforums.org/showthread.php?t=561981&highlight=scripts")

I do only get 10 FPS in windowed mode, where I usually got >30 when I had Windoze on my system.

---

### Post by volksgewer on 2008-03-28
Will do, I have tried some things also but have not succeeded.

---

### Post by Zaneyard on 2008-03-29
would you happen to have a Radeon GPU?
If so, I have concluded that there is no hope at the moment for fullscreen games that use "DirectDraw"
Unless someone comes up with a workaround that is...

---

