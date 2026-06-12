---
title: "Two problems"
date: 2007-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by DaGGer on 2007-08-12
Let see first thing first. Sometimes when I open up my firefox and say I'm surfing through streefire.net and I go to view a video it will just shut firefox down when it starts to load the next page.  Thats one problem thas pretty annouying.

Second thing is that I've installed Beryl and well it makes my system crash, or well freeze. the clock still run, everything still runs but I can't slick on anything and no keyboard combos change it. Now I tried to install Compiz to see how that would work but I can't for the life of me get it to work.  But I couldn't get it to.

Now I have Gnome and KDE installed. I got Kubuntu installed through Ubuntu just to see how it worked and thats how I tried to install it the first time. I installed it with Gnome and KDE. I used this link to install it:

[http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)

but it didn't work so I tried to installl it under Gnome to and it didn't work either. Everything is installed and I can see the Compiz Fuzion Icon under apps->system tools but when I click on it, it does nothing. I don't know what I'm doing because there isn't really anything for me to follow but that. Should I reinstall my Nvidia drivers again or what?

---

### Post by scrooge_74 on 2007-08-12
Did you check that your video drivers can handle 3D? That could be the problem.

I wanted to check the website and see if I got the same error, but I think you typed the wrong one.

---

### Post by DaGGer on 2007-08-13
I've got a Geforce 7800Gt. I hope it does?

---

### Post by scrooge_74 on 2007-08-13
As per recommendend in another thread, check if Nvidia has drivers for it.

Check the help section for Nvidia cards [https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

and post back if something does not works or you get stuck with the info

---

### Post by DaGGer on 2007-08-13
well I did the command

```
sudo apt-get install nvidia-glx
```

And it came up with that I'm using the lastest drivers.

---

### Post by scrooge_74 on 2007-08-13
From what I have read around sometimes there are not enough support and drivers for the 64 version.  Some people have just installed regular 32 bits on their system to get around this. Others had to compile things themself.

Sorry I can be of no more help

---

### Post by Kilz on 2007-08-13
> **scrooge_74 said:**
> From what I have read around sometimes there are not enough support and drivers for the 64 version.  Some people have just installed regular 32 bits on their system to get around this. Others had to compile things themself.

Sorry I can be of no more help

There are 64bit video drivers, nvidia makes them. I don't think its a driver problem. But a expecting perfection out of Beta software. Beryl, compiz., and compiz fusion are still under heavy development. They can make the desktop look pretty, but the flip side is that things crash and don't work right when you run them sometimes. While they have attracted a lot of users to Linux, it is not something that I would recommend to someone who doesn't have a firm knowledge of Linux troubleshooting.

---

### Post by DaGGer on 2007-08-14
Well I have beryl, thats no porblem. It does crash on me sometimes. I don't know why but I figure it because its still under development. But I wanted to check out Compiz just to see how it works and all but I couldn't get it started LOL. Beryl looks great on my computer. it does, but I just wanted to play with a few things.

---

### Post by dabl on 2007-08-14
> **DaGGer said:**
> well I did the command

```
sudo apt-get install nvidia-glx
```

And it came up with that I'm using the lastest drivers.


The fact that the latest driver is installed doesn't necessarily mean that glx is enabled, which you need for the Compiz/Beryl stuff to work.

Back up your /etc/X11/xorg.conf, so you can restore it if I happen to make it worse, rather than better.  :lolflag:

Then, in a console, enter ```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
``` This will write a new /etc/X11/xorg.conf file that has glx and compositing enabled.  Now restart your xserver with Ctrl-Alt-Backspace.

Next, open the console and enter ```
beryl
``` you should get a series of messages that indicates whether Beryl is finding all of the glx bits that it needs to run correctly.  If there are no errors, enter ```
beryl-manager
``` to run the app.  Right click the red Beryl icon, click "Window Manager" and choose "Beryl", then click "Window Decorator" and choose "Emerald".

Have fun!:)

---

### Post by DaGGer on 2007-08-16
ok well I installed newer drivers. I used nvidia-glx-new instead of just nvidia-glx. So I'll back up my xorg.conf and then do those commands. Btw how do install my backup if I mess up my xorg.conf lol. I only know how to remove it, install it, then reconfigure it.

---

### Post by dabl on 2007-08-16
> **DaGGer said:**
> Btw how do install my backup if I mess up my xorg.conf 

It's just a process of renaming files.  You rename the one that's not working to something else, and then you rename the one you backed up to "xorg.conf", and restart the X server.  :)

---

### Post by DaGGer on 2007-08-16
ok, well I did all that stuff that you guys said to do but when I type in Beryl in the terminal it goes through everything but when it says reloading option (something like that) it just hangs.

Also I'd like to ask, how in the hell do I get my window borders back. I can't remember how to get them back.

---

