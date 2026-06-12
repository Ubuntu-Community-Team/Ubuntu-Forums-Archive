---
title: "Team Fortress 2"
date: 2008-05-11
forum: Wine
---

### Post by Arphahat on 2008-05-11
I just installed Ubuntu on Friday and have been trying to get some of my most frequently used apps working via Wine.  I can run Steam, and I can launch TF2, but when it gets past the Valve logo, it never displays the loading screen and when it gets to the menu, I can hear the music and when I move the mouse, I can hear it clicking over the menu items.  However, the screen remains black and my only recourse is to hit F10 to quit.

Now, I didn't install TF2 through Wine.  I re-installed Steam via Wine, then used links to point to the correct folders (like steamapps, for instance).  I wouldn't think this would be the problem, but who knows?

Did I miss any necessary steps?  Thanks.

---

### Post by Sleaka J on 2008-05-11
Try adding -window as a Launch Option for TF2 in the Steam menu. It's what I had to do.

---

### Post by ExRarne on 2008-05-11
I haven't been able to install TF2 yet (some unrelated issues) but I hear it works great with DirectX 8.1 mode (rather than DX9). Think the launch option is -dxlevel81

---

### Post by Arphahat on 2008-05-12
I tried both those options, but neither seem to help.  This might be a dumb question, but do I need to install DirectX in Ubuntu?  Also, do I need to have specific drivers for my video card, or will the default ones do?

---

### Post by aoanla on 2008-05-12
This sounds like the classic problem with TF2 in DirectX 9 mode. The correct launch option to use is "-dxlevel 81" (with space, without the quotes), so if you only tried it without the space, try it this way.
I'd advise upgrading your video card drivers to the latest version available from your provider's website, as well, just to be sure.

You don't need to (and indeed shouldn't) install DirectX - Linux itself doesn't use it, DirectX being a proprietary Microsoft API, and Wine contains all the code to emulate it itself.

---

### Post by helino on 2008-05-12
I have the same problem, it used to work earlier, although I can't remember which wine version, somewere 0.9.56...

I've always used -dxlevel 81 as a launch parameter, and it worked really good until now

---

### Post by ExRarne on 2008-05-13
Suffering same problem on 0.9.59 Hardy, even with -dxlevel 81 and -window. Anyone on Gutsy able to clarify if the situation's any better for them?

---

### Post by Trance56k on 2008-05-13
I can get TF2 to run with -dxlevel 81 performance is playable, but I have no issues launching etc.

---

### Post by aoanla on 2008-05-13
This is very odd - I'm using Hardy, and -dxlevel 81 has always fixed my TF2 problems, and still does.

Have you tried upgrading to 0.9.60, or 1.0-rc1? The latter fixed a problem with the Steam webbrowser stuff for me...

---

### Post by ExRarne on 2008-05-13
I've updated to RC1, still blackscreening with -dxlevel 81.

---

### Post by Trance56k on 2008-05-13
Could be drivers, do you have an ATI card?

---

### Post by benwoodc0ck on 2008-05-13
Works (ish) for me, wine 1.0rc1, ubuntu hardy 32, ati X1950 Pro 512mb pcie with restricted drivers enabled. Have you got in game steam freinds enabled? I hear that could be a problem. Now it crashes within 15mins of play and I normally just reboot.

I got this in feisty when gutsy was available, I had to change all settings to low and even then it was a bit iffy.

---

### Post by benwoodc0ck on 2008-05-13
Dang it , you can tell im new here huh!

---

### Post by VgForce on 2008-05-21
I have same problem. Direct x doesnt fix either and i have my graphic card install and configured already. :(

---

### Post by zzzPOOHzzz on 2008-05-22
my issue is fairly odd....
whatever screen comes up first... the intro steam "video"... or the regular menu (if i use launch option -novideo) when it tries to go to the next screen it freezes... like if i click on find server... it freezes right then... not my computer the program

---

