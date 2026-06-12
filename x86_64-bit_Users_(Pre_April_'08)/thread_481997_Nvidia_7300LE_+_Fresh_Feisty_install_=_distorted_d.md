---
title: "Nvidia 7300LE + Fresh Feisty install = distorted displays"
date: 2007-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tim T on 2007-06-23
So My Nvidia 6600GT went bust the other day while playing KOTOR 2 in XP, and I bought this 3d Fuzion nvidia 7300LE off a friend of mine, hooked up the water cooling block and booted into xp. All fine and dandy. Now to linux. I couldn't get into the live cd with the desktop install of linux without using safe graphics mode. But since I wanted to use XFS, I d-loaded the Alternate 64-bit download cd for 7.04 . I installed Linux, and just like when I did the basic load from the desktop live cd, after showing the ubuntu loading screen, the whole screen becomes distorted showing several colours in a bizarre pattern. when I hit ctrl-alt-f2 to get to the CLI I was presented with a black and white version of the same pattern. I think if I reinstalled the nvidia drivers this could all be fixed, but since I cant see what i am doing, this makes it difficult. 

On a side note, I know I have seen this issue posted here before, but after a half hour of searching, I can't find the answer I am looking for (which basically means I can't figure out the correct terms to search for).

Ideas, anyone? Links? Anything? I'd really appreciate the help!

---

### Post by Cappy on 2007-06-23
[http://ubuntuforums.org/showpost.php?p=2794799&postcount=9](http://ubuntuforums.org/showpost.php?p=2794799&postcount=9)

Looks like you must install with an onboard or different video card.
I searched the forums for "7300LE".

Also:
[http://ubuntuforums.org/showthread.php?t=406205&highlight=7300LE](http://ubuntuforums.org/showthread.php?t=406205&highlight=7300LE)

---

### Post by Tim T on 2007-06-23
Unfortunately my motherboard doesnt have onboard video (abit kn9 sli) so I'm going to try and borrow a 7600gt to do the install (after i check the forums to be sure it will work that is...)

---

### Post by BobCFC on 2007-06-23
If you managed to install Ubuntu from the AlternateCD you should be able to select Recovery Mode from the Grub menu.   This will boot without the graphics and let you log-in to the console to install Nvidia drivers and setup X.

you would run  *sh nvidia.something.run*  as root from the directory containing the drivers.



if you haven't setup root yet you could do commands using sudo.    To set your first root password use

sudo passwd root

---

### Post by Tim T on 2007-06-23
> **BobCFC said:**
> If you managed to install Ubuntu from the AlternateCD you should be able to select Recovery Mode from the Grub menu.   This will boot without the graphics and let you log-in to the console to install Nvidia drivers and setup X.

you would run  *sh nvidia.something.run*  as root from the directory containing the drivers.



if you haven't setup root yet you could do commands using sudo.    To set your first root password use

sudo passwd root

To use xfs, i had to install lilo. So no grub for me sadly... I did however just walk in the door with two fresh nvidia 7600 gt ko cards, and i'll update you guys on how that goes.

EDIT 1: I just installed the 2 7600's in sli mode, and 1 monitor works (dvi) and one doesn't (vga). I'm updating the system now (gah! 70 updates!) and will install the nvidia drivers for dual monitor support, and all should be fine! on a side note...  anyone want a slightly used 7300LE? haha!

EDIT 2: Everything is fixed. I got the latest Nvidia drivers installed, loaded beryl, and all is smooth.

---

