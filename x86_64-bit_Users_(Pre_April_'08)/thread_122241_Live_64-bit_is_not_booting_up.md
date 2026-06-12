---
title: "Live 64-bit is not booting up"
date: 2006-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by LavaHot on 2006-01-27
So I'm trying to run 64-bit live ubuntu on my compaq presario r4000 laptop, and when i try to, the screen goes blank. if i turn on the vga=771, i can get into the setup, but the colors are wierd, and when the setup is done, and the bootup finishes (where it lists off the OKs), the screen also goes blank. any help guys?

---

### Post by skylark on 2006-01-27
Since nobody has replied yet I'll give it a shot, but I don't have your laptop so I'm only guessing here:

* Read this thread: [http://www.ubuntuforums.org/showthread.php?t=112640](http://www.ubuntuforums.org/showthread.php?t=112640)
* when you are editing your xorg.conf, do the following:
   1) use driver "fglrx",
   2) add the following option: Option "VideoOverlay" "on" 
   3) set your DefaultDepth to 24

Hope it helps. 

edit: steps 2 and 3 may not be needed

---

### Post by LavaHot on 2006-01-27
well, maybe I need to give some more info. the card in my laptop is an ATI radeon xpress 200m. What's the deal with the ATI cards anyway? Why can't Ubuntu handle them correctly? 
So once I'm able to change my conf file, wont I have to reboot in order to implement it? That's a catch 22 friends.

---

### Post by skylark on 2006-01-28
Yeah, getting stuff configured right when it doesn't work out of the box is a real pain. In this case you shouldn't need to reboot though. It's just a matter of restarting x windows. So if you can get to a terminal and make the changes then yuo can test if it works by typing "startx" (or "sudo /etc/init.d/gdm restart"). If you are stuck in x-windows at bootup with a blank screen then "<ctrl> <alt> <backspace>" should kill it and hopefully give you a terminal. All this is a lot of hassle though so possibly not worth it for a live cd (unless you want to check out Ubuntu to see if a full install is worth it). 

I run an ATI card myself on my AMD64 desktop, a basic X300, and haven't had any major hassles. Obviously laptop AMD64 support for ATI might not be so hot though. Maybe you could give the most recent Dapper flight live CD a shot (and cross your fingers).

---

### Post by John Jason Jordan on 2006-01-28
[QUOTE=LavaHot]well, maybe I need to give some more info. the card in my laptop is an ATI radeon xpress 200m. What's the deal with the ATI cards anyway? Why can't Ubuntu handle them correctly?[/QUOTE]
I bought an R4000 with exactly the same video as yours by mail order directly from HP last April. HP offers a 30-day "no hassle" return privilege. On day 27 I called them up for an RMA and returned it. Luckily they meant it about no hassle, because they refunded every penny.
I returned it because I tried everything I could think of and asked on every Linux forum and board trying to get the video working at least in 1280 x 800. I tried half a dozen different distros in 32-bit and 64-bit. Nothing helped. Ask anyone who's an expert about Linux and video and you'll get the same response: ATI sucks and NVidia rocks.
So after returning it I bought a brand new R3240 with NVidia chipset on eBay for half what I paid for the R4000. Sure, it's not quite as nice as the R4000 - 60 Gb hard drive instead of 80, slower CPU, DVD-RW instead of +-. But when I installed Ubuntu 64 Hoary on it the video came right up at 1680 x 1050 without having to tweak a thing. The most gorgeous screen I have ever seen on a laptop.
You sound like you know more about Linux than I do (the R4000 was my first attempt at Linux) so maybe you'll eventually succeed. I just know that from now on if a computer of mine is going to run Linux the video is going to be NVidia.
I wish I could give you the answer, but all I can offer is the story of my pathetic failure with ATI.

---

