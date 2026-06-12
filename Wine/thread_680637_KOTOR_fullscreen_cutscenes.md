---
title: "KOTOR fullscreen cutscenes ?"
date: 2008-01-28
forum: Wine
---

### Post by Cornichon on 2008-01-28
Hi, I'm a newbie...

Took a look at the older threads, and could not find any answer.

I have just installed Wine, PlayonLinux and the KOTOR 1.03 game on my machine :

- Intel Core 2 Duo ;
- Asus Motherboard ;
- ATI Radeon HD 2600 XT with restricted catalyst drivers (fglrx) in perfect working order ;
- Ubuntu Gutsy, 1024x768 display, and compiz-fusion is disabled.

I patched KOTOR to avoid the securom protection.

Here is my issue :

- if I use GDI as the DirectDraw renderer in Wine, the fullscreen game itself runs perfectly, but only if I disable the cutscenes (otherwise the game freezes) ;

- if I use OpenGL as the DirectDraw renderer in Wine, the cutscenes seem to work, the graphics seem much better, but the resolution is messed up : it's a fullscreen, but the game's display (not windowed - I don't know how to obtain windowed mode in wine) only occupies a small part of the screen.

My alternative seems to be :

Either run the fullscreen game without the cutscenes, or run the not-fullscreen cutscenes and not being able to play the game.

My question is : Is there a way for me to run KOTOR fullscreen with cutscenes & all ?

I cross-posted in the games & leisure section, but I now realize this is the better place to ask my question...

Thanks for your help.

---

### Post by Ferrat on 2008-01-28
To get windowed mode in wine just enter winecfg and select the grafic tab then check windowed mode and set the resolution =)

As for the grafic sounds weird but looking at appdb for wine it looks as if fullscreen has given people alot of trubble.

---

### Post by Cornichon on 2008-01-28
No dice, didn't work...
I'm unable to locate the problem as yet..

---

### Post by Ferrat on 2008-01-29
> **Cornichon said:**
> No dice, didn't work...
I'm unable to locate the problem as yet..

Gonna try to install it ect. and see if I can make it work :)

---

### Post by Ferrat on 2008-01-29
Well tried it and got it to work, well fullscreen is a no go, crashes after Lucas Art's logo in the beginning but using emulate desktop it works, you just have to make sure the desktop is the same resolution as the game of you get alot of grafic weirdness ^^ 
Other than that everything works for me really well except the cursor is half hidden but you see i while you click and most things you can navigate with the keyboard =)

---

### Post by Cornichon on 2008-01-30
Still didn't work.

I'll try to reinstall the game tonight using the PlayOnLinux script, but with the latest version of Wine.

Which version of Wine did you use, by the way ?

---

### Post by Ferrat on 2008-01-30
I use 0.9.52 and used no extra installation program except Kotors normal one 

I think the problem in fullscreen is that cutscenes are in 800x600 while if you play in 1024x768 the problem is that the switch makes some errors 

However I've been playing for a day and haven't had a singel real problem yet =)

---

### Post by Ferrat on 2008-01-31
Well played it from beginning to end without any major problems, sound crashed twice maybe three times over the span of the entire game and had one game crash but other than that no problems at all. 

Have you gotten yours to work yet?

---

### Post by Cornichon on 2008-02-05
Okay, somewhat good news from the frontlines, here.

The installation used to fail, the InstallShield Wizard appearing unresponsive.

I think I have located the problem :

There is a bug in the PlayOnLinux script, and perhaps a regression in the latest version of Wine.

Therefore, I cheated.

I used the PlayOnLinux script to get a temporary directory with all relevant installation files.

I then entered ```
sudo apt-get autoremove --purge wine playonlinux
```

I then installed an older version of Wine (9.4x).

I ran the setup program for KotOR. It worked !

Now, the game runs correctly, but my keyboard is not recognized : I cannot type nor use keyboard shortcuts.

I'd update Wine to 9.54, but I'm afraid of potential regressions.

Any ideas for the keyboard thing (which yet used to function perfectly in the previous, working-without-cutscenes installation of KotOR) ?

---

### Post by Ferrat on 2008-02-05
if the keyboard isn't working then most likely is that in winecfg you haven't checked the option to let the linux windowmanager handle wine windows (it's at the grafic tab)

Altho checking this makes the game faulty when running fullscreen and you have to use emulate desktop

---

### Post by Eniak on 2008-05-01
Is there anyway of getting a resolution bigger then 1024x768 on it?

---

### Post by cogadh on 2008-05-01
The largest resolution the game can do is 1280X1024. As long as you have that resolution available in your xorg.conf, the game can run up to that. This is also probably why the OP had a problem with the cutscenes. The cutscenes are rendered in 640X480 resolution and if you don't have that resolution available in your xorg.conf, then the cutscene will play in a 640X480 section of your existing resolution.

---

### Post by Eniak on 2008-05-01
Where exactly in xorg.conf?
In the available modes of my video card?

*me sorta noob yet

---

### Post by Poyntz on 2008-11-19
/etc/X11/xorg.conf - it's here

---

