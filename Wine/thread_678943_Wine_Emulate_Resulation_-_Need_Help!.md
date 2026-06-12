---
title: "Wine Emulate Resulation - Need Help!"
date: 2008-01-26
forum: Wine
---

### Post by Sugi on 2008-01-26
I need some help.  I have read and read many posts, threads, and google searches, but nothing is helping me. I am trying to set resolution for each program within Wine.  The only thing that works is the "Default Settings" in the Graphic tab, but that isn't good enough for me.  And when I trying "Emulate Virtual Desktop" within each Application Rule (like each game), it's always grayed out no matter what.  I have even tried starting up the Applications within the Terminal.  But That will not work either.

First, I will turn off Emulate Virtual Desktop within Default Settings.
 - Wine>Wine Config>Default Setting>Graphic tab> Emulate Virtual Desktop = OFF
 - Terminal>$ wine "C:\Program Files\Path/Game.exe" --emulate-virtual-desktop 1024x768
or
 - Terminal> wine explorer /desktop=MyDesktopName,1024x768 /path/program.exe

Both of those command lines does not affect the wine applications.  They both start up the application, but it won't emulate a desktop like  "Emulate Virtual Desktop" can.  What should I do?

I am currently runnning Gutsy Gibbon, NO Beryl or Compiz-Fusion, Wine 0.9.5.1, and Gnome.


Thank you for any help that may come,
Sugi

---

### Post by CarpKing on 2008-01-26
For whatever reason, the virtual desktop seems to be a global preference that can't be changed per application.  From your experience, it sounds as if you can't invoke it with the command line either if it isn't set globally (unless you've read somewhere that it is supposed to be possible, in which case the goal of this thread would be to find out why it doesn't work for you).  If this is the way it's designed, this could probably use to be an enhancement bug on Wine's Bugzilla.

---

### Post by CarpKing on 2008-01-26
I just tried launching something with the --emulate-virtual-desktop 1024x768 and got the same result as you.  

If you really need this functionality, it can probably be achieved with separate preferences directories (the default is .wine but you can set it to use another when you launch the program).  Unfortunately I don't know any more about how that works.  If anyone reading this does, their input would be appreciated.

---

### Post by Sugi on 2008-01-27
I was reading through the forums and I came across this.  I am unsure if it will work or not, because I am on windows platform OS.  But I thought I would keep everyone updated on this issus.

Try:
-vidmode w,h,r
IE:
- $ wine explorer /path/program.exe-vidmode 1024,768,60
or 
- $ wine /path/program.exe-vidmode 1024,768,60

Good luck,
Sugi

---

