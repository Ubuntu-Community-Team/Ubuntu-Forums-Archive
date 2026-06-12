---
title: "Compiz/Emerald problems in 9.04...(working, but issues)"
date: 2009-05-03
forum: x86 64-bit Users
---

### Post by allandelmare on 2009-05-03
Hey, I know everyone is sick of Compiz noob questions, but I've done my homework and can't find the solution...

I've searched everywhere for fixes, tried a bunch, re-formatted and re-installed Jaunty bc I messed everything up so bad...and still:

From a clean install, I have compiz working no problem. Emerald installs no problem. All the compiz effects work without trouble. 

So whats the issue?

After importing a compiz/emerald theme to emerald, I can select it...the window pauses for a second, then resumes normal behavior...without changing the theme. 

I went to terminal and typed: 

emerald --replace

This causes the top-bar on every window to change to the appropriate theme, but after pressing enter, the terminal response is a blank line, and trying to kill the terminal says it still has something it's working on. 

 After removing the theme, the top-bar on all my windows is either gone or malfunctioning until I reboot. 

Everyone says "change your window manager"...okay, I don't know how. I've looked everywhere. No clue where I can find "change window manager" option...

So then I try 

compiz --replace

And yuck....the screen refreshes like 2 or three times, then spits out this: 

user@user-desktop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
Starting gtk-window-decorator

and stays like that...it doesn't create another

user@user-desktop:~$

line, which I assume means it has crashed. 

This is my xconf file:

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection


I'm using a NVIDIA 7300 GT with latest drivers. 

Any help much appreciated. New to Linux.

Thanks

---

### Post by allandelmare on 2009-05-04
Doh!...I got it figured out...install Compiz Icon ...

uuuuberrrrr noooobbbb...

Thanks anyhow

---

### Post by bford16 on 2009-05-04
Just a note for those reading this thread: emerald --replace should be run in the "Run Program" dialog box.  Just hit Alt+F2, then type```
emerald --replace
```Then hit Enter.  This causes emerald to keep running in the background.  When you run this program in a terminal, you have to keep the terminal open, or the 'emerald --replace' process will terminate.

If you want to try the "Compiz Icon," they you should do:```
sudo apt-get install fusion-icon
```(In a terminal)  Or use Synaptic to find the package.  I was unable to find it in 'Add/Remove...'

---

### Post by sarahlizz3 on 2009-09-25
Thank you for posting this - I was having the same problem.  I took a forced break from Ubuntu (when my computer died, and only my XP machine was running that I keep for Dreamweaver and work) and completely forgot the command went in run and not in the terminal.

---

