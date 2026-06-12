---
title: "Menu bar visible in fullscreen wine programs"
date: 2012-05-08
forum: Wine
---

### Post by Avaritia on 2012-05-08
I have a problem since upgrading to 12.04, when I launch fullscreen wine applications (ive tried 8 different ones so far, all the same problem) the the top global menu bar (with the time and date on it) still shows and i have the unity bar down the left hand side still.

This makes games unplayable, does anyone know a work around for this?

It's the same problem this guy has:

[http://www.playonlinux.com/en/issue-828.html](http://www.playonlinux.com/en/issue-828.html)

---

### Post by Baldrick_NZ on 2012-05-08
To autohide the launcher, go to the power cog icon top right of your screen, then system settings > Appearance > behaviour, then activate the auto-hide launcher feature.

Launcher should then disappear when you go full screen.

Not sure about the global menu though...

Hope this helps.

---

### Post by dniMretsaM on 2012-05-08
Programs running in Wine are not programmed to integrate with the Global Menu because they were written for Windows.

---

### Post by themainliner on 2012-06-22
Is that it...tough luck Wine programs were not written for the Global Menu.

Is there still no fix for this? Or is Shuttleworth marking it Not Fixing too?

This is a deal breaker, if you cannot use Wine properly in Ubuntu then I see not reason to try to get to grips with Unity. Cinnamon or Xfce are going to have to do.

---

### Post by HiImTye on 2012-06-23
Ubuntu is not free windows
WINE is a compatibility layer (an emulator) to simulate running Windows in Linux but Windows programs make no attempt to 'play nice' with Linux so extra work has to go in to try to get them to. WINE apps don't use windows the same way that Linux apps do (as even Maximus doesn't function correctly with WINE apps). this is an issue that comes from them both being two very different environments, even though various attempts have been made to try and ease the transition between the two. Unity, Ubuntu and WINE are each separate projects and each of them have various targets that they try to meet. perfect desktop integration is not always paramount to any of them as they each have any number of issues to fix at any given time.

in short, it being a 'deal breaker' is on you, not them

---

### Post by pieis2pi on 2012-07-28
I had the same problem. It seems to be a problem with the interaction of wine and compiz ... If you log out and run a unity2d session the problem goes away (for me at least). Hope this helps.

---

### Post by monkeyking009 on 2012-10-05
Go into wine configuration (winecfg) and disable "allow the window manager to control the windows" under the graphics tab. This should remove the unity launcher and panel in full screen mode.

---

### Post by Stephonos on 2012-10-18
You are a genius!

---

### Post by kill o matic on 2012-10-18
That solution brings its own problems though. When I tried running the Touhou games 6 to 9.5 that way, the keyboard input would not focus on the fullscreen window and unless you have a gamepad plugged in, there's no way to kill it except for restarting.

---

### Post by MIC132 on 2012-10-19
Anyone found in-between fix? I have the same problem (and also playing Touhou!!). Disabling control of windows makes it impossible to focus on the game window and not only you can't play, but you can't really quit. I also tried the "emulate desktop" option, but there appears to be no way to make it bigger. No matter the dimensions i put, it ends up the same (quite small for me) size.

---

### Post by thatguruguy on 2012-10-19
Try the following.

Install the Compiz-Config Settings Manager.

```
sudo apt-get install compizconfig-settings-manager
```

Run it by typing CCSM in the Dash.

In the section entitled "Workarounds" (in the "Utility" section) make sure that "Legacy Fullscreen Support" is checked. I can't guarantee it will work, but it can't hurt.

---

### Post by MIC132 on 2012-10-19
Well, this changed exactly nothing. At least in this particular case.

---

### Post by kill o matic on 2012-10-20
> **MIC132 said:**
> Well, this changed exactly nothing. At least in this particular case.

Did you recheck "allow the window manager to control the windows" in the wine settings?

---

### Post by MIC132 on 2012-10-20
At first I didn't, but now that you said that I tried, and effects are interesting. The game isn't "active" at the beginning but after a few alt-tabs and a bit of clicking I somehow gained control. Now to figure this out..

Edit:
Checking "automatically capture mouse in fullscreen (...)" makes it so that after I start it I have to click once and it works!

---

### Post by Mad-Halfling on 2012-10-21
I had this issue before upgrading to 12.10.  Enabling the compiz legacy fullscreen support and/or disabling the WINE config setting to Allow The Window Manager To Control The windows fixed it.  However, after the update (once I got everything working) it no longer seems to fix it.  The strange thing is, if I run winecfg it loads the screen (I was emulating a full desktop) over the top of the Unity launcher and top bar fine, but when I load the program (WoW) it gets displaced down and to the left.  Uninstalling WINE 1.5 and isntalling WINE 1.4 fixed this - for anyone else getting this problem.

---

### Post by danfly on 2012-12-31
> **monkeyking009 said:**
> Go into wine configuration (winecfg) and disable "allow the window manager to control the windows" under the graphics tab. This should remove the unity launcher and panel in full screen mode.

Thanks man, that is the solution.

---

### Post by J4ckz on 2013-05-18
If some applications work better with the [COLOR=#000000]"allow the window manager to control the windows" (winecfg) box ticked, but others work better with it unticked, you could just change the application specific settings.  That way, you can configure which applications have which winecfg settings.  I found this link helpful: [/COLOR]https://help.ubuntu.com/community/Wine#Changing_application_specific_settings[COLOR=#000000]

It reads: [/COLOR][B]Changing application specific settings
[/B]
Type this command into your terminal: winecfg
[LIST=1]
[*=left][FONT=inherit]Click on **Add Application...**[/FONT]
[*=left]Navigate to where the .exe is and choose that program
[*=left]The dropdown at the bottom allows you to choose which version of Windows Wine should emulate. Also, any changes to the Libraries and Graphics tabs will only affect the chosen application in the Applications tab.
[/LIST]
[LEFT]
[/LEFT]
Hope this helps.

---

### Post by Tununias on 2013-09-14
> **monkeyking009 said:**
> Go into wine configuration (winecfg) and disable "allow the window manager to control the windows" under the graphics tab. This should remove the unity launcher and panel in full screen mode.

Thank you very much. I've been using OpenBox all this time to play games, but your way is much easier.

---

