---
title: "Audiosurf + WINE"
date: 2008-01-20
forum: Wine
---

### Post by LHoT on 2008-01-20
I know that the beta has expired.

I was seeing if there was anyway to play after the beta expired, and apparently last week there was a program called Surfboard. I checked it out, read the readme, and it said that if the program didn't automatically work, to C:\windows\system32\drivers\etc\hosts Now, I checked there in WINE, but I only got to here /home/lhot/.wine/drive_c/windows/system32/drivers 

So, I am just wondering were the equivalent file is.

---

### Post by TomPurnell on 2008-01-21
I assume (without checking) that wine is using the system-wide hosts file. Try making your changes to /etc/hosts, but be sure to make a backup before you go breaking anything :)

You'll need to be a superuser to edit this file 

```
#gksudo gedit /etc/hosts
```

Assuming you want to stop the program from successfully resolving a given address, you would add something like this:

```
0.0.0.0 example-domain.com
```

---

### Post by Zoyx on 2008-02-19
This is my first Wine app (Steam + AudioSurf).  Audiosurf splash comes up wrong ([similar to what is happening here]("http://www.audio-surf.com/forum/index.php/topic,40.0.html")).  I try and mouse around to get the game going and the game isn't registering my mouse clicks.  Anything that I am doing wrong?

---

### Post by vxkid on 2008-02-20
audiosurf works completely fine as long as you disable the option in wine configuration to allow wine to use the window manager. run it. maximize the window. bitch about the "player error: 44" which if you're like me, you will absolutely get.

---

### Post by demauk on 2008-03-06
Steam keeps telling me that I need the latest DirectX :(
In Steam, Help -> System Information shows DirectX driver 7.5, even when I specify -dxlevel 90.

Xubuntu 7.10
Wine 0.9.56
nVidia GeForce FX 5700

Is it my old nVidia card?

---

### Post by Raptormn on 2008-03-17
works for me. fun little game.

---

### Post by demauk on 2008-03-17
Raptormn, do you have an nVidia card as well? Which one?

---

### Post by Raptormn on 2008-03-18
> **demauk said:**
> Raptormn, do you have an nVidia card as well? Which one?

i have the 8800 GTX :)

---

### Post by daniel7860 on 2008-07-02
i had the mouse problem too but i got it fixed thanx to vxkid, but now after it loads the song and i press play it freezes so i have to restart my laptop or it exits the game.:confused::confused::confused:

---

### Post by daniel7860 on 2008-07-02
HELLO??????
ANYBODY WILLING TO HELP??????
:mad::mad::mad::mad::mad::mad::mad::mad:

---

### Post by cogadh on 2008-07-02
Chill out. It can sometimes take days to get a response here, especially if you are encountering a problem that no one else has and you haven't provided many details, such as terminal output or hardware specs.

---

### Post by daniel7860 on 2008-07-02
:popcorn:

M22 ATI Mobility radeon X300


i am using ubuntu 8.04 Hardy heron

on a Dell Inspiron 9300

---

### Post by cogadh on 2008-07-02
Are you using the restricted driver for your video card and what errors are output to the terminal when you run the game?

---

### Post by daniel7860 on 2008-07-03
no i am not using my restricted driver, and how to i get the terminal to output error messages? do i have to run the game through the terminal? if so, how do i do that?

---

### Post by cogadh on 2008-07-03
I forgot that ATI has an open source driver now, I should have asked if you are using the restricted *or* open source driver. Unless you are using one of them, you won't have 3D acceleration functionality and the game will never work. To confirm that you have 3D functionality, run this in a terminal:
```
glxinfo | grep direct
```
If it comes back saying "Direct Rendering: Yes" then 3D acceleration works fine. If it comes back saying "No", then you need to install the restricted or open source driver for your video card.

As for running the game from the terminal, you really should do that, at least until you are certain that you have the game running as well as you can get it to run. To run Audiosurf from the terminal, do this:
```
cd .wine/drive_c/Program\ Files/Steam
wine Steam.exe -applaunch 12900
```

---

### Post by DrMelon on 2008-07-04
> **demauk said:**
> Steam keeps telling me that I need the latest DirectX :(
In Steam, Help -> System Information shows DirectX driver 7.5, even when I specify -dxlevel 90.

Xubuntu 7.10
Wine 0.9.56
nVidia GeForce FX 5700

Is it my old nVidia card?


The problem you're probably having is that you haven't INSTALLED the latest DX Drivers.

---

### Post by cogadh on 2008-07-04
> **DrMelon said:**
> The problem you're probably having is that you haven't INSTALLED the latest DX Drivers.

Check the dates of the posts before you respond, that one was old and way out of date. Besides, there are no DirectX drivers in Linux or Wine, only in Windows.

---

### Post by daniel7860 on 2008-07-05
direct rendering: Yes


and i somehow cant launch it through the terminal, i typed the correct path but it said : no such file or directory......

---

### Post by stwert on 2008-07-07
Hi, I'm new to linux and wine, and I'm trying to play Audiosurf on steam. I've got steam and audiosurf installed fine, but when I try to run audiosurf, it closes immediately after starting. What happens is the steam window opens that says "preparing to launch audiosurf", then after a few seconds, that closes, and then a few seconds later, the audiosurf window itself opens, but blank, and after a few seconds it closes and that's it. I tried running it from the terminal and the same thing happens, but there's no output whatsoever in the terminal either. 
Thanks for any help.

---

### Post by sammydee on 2008-08-20
While I hate to advocate piracy, there is a pirate version of audiosurf floating around the intertubes that has all the steam stuff stripped out of it, and it works much better than the "official" version.

If you've already paid for the game there's nothing wrong with it. If you haven't bought the game, you're a bad bad person :-)

Sam

---

### Post by kn100 on 2009-09-10
I tried installing this, it installs and runs fine up until i try to select a song, as its loading it says Player error 44. It seems to offload audio decoding work onto WMP, which wine doesn't have, but i installed WMP10 which doesn't run, and still the same error

---

### Post by demauk on 2009-09-10
Hey, I posted here on page 1.

My original problem was indeed my video card and driver combination, because I got a new computer with a different card on it and the game worked just fine for several weeks.

Then an Audiosurf update came.

And that's where I left it several months ago. Not working at all. Maybe I should try it again.

---

### Post by kn100 on 2009-09-10
> **demauk said:**
> Hey, I posted here on page 1.

My original problem was indeed my video card and driver combination, because I got a new computer with a different card on it and the game worked just fine for several weeks.

Then an Audiosurf update came.

And that's where I left it several months ago. Not working at all. Maybe I should try it again.

I think imma just give up and stick with Unreal Tournament :P

---

### Post by Nikias on 2010-01-20
I'm running Ubuntu 9.10 and I installed PlayOnLinux from the software center and Steam through that. Audiosurf downloaded and installed within steam without any apparent issues, but when I go to run it the screen is only filling the bottom left quarter of the window (all visible, just smaller) and the rest is black. The loading bar fills and the OK button appears, but when I click OK (I have to click where the OK button is supposed to be and not where it is for anything else to happen) it hangs for a few seconds and closes.

I've tried a few various suggestions I've found online but none of them seem to have any effect at all. If anyone has any advice for things I could try it'd be greatly appreciated.

Edit: one suggestion said the issue with the screen not coming up correctly would be fixed by running in fullscreen. I couldn't set audiosurf to fullscreen from the menus obviously, but I tried editing the config file to make it start in fullscreen. That fixed said issue, but the same thing happens once it loads and I click ok.

---

