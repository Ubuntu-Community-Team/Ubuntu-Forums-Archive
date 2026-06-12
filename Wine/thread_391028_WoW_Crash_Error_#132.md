---
title: "WoW Crash Error #132"
date: 2007-03-22
forum: Wine
---

### Post by UbuntuniX on 2007-03-22
As seen here: [http://ubuntuforums.org/showthread.php?t=374435](http://ubuntuforums.org/showthread.php?t=374435)

My video card is an ATi Radeon PowerColor X300SE.
I have WoW installed with TBC Expansion.

I've done everything in the ubuntu HOWTO guide, installed drivers, edited config.WTF, etc.

But still, when I start WoW, the screen is black for a moment before I get that error message.

Anyone know how I can fix this? :(

---

### Post by lakersforce on 2007-04-16
A lot of windows users experience this. If I remember correctly it is a video-driver issue. Over at the official wow forums all the advise that is given in blue to this is "update your video-driver", and when the users come back and say that that did not solve their problems they are unfortunately ignored.

---

### Post by Tanoku on 2007-04-16
Even Blizzard doesn't really know what causes the dreaded Error #132 (bad programming -> generic error codes -> anything goes wrong, you get #132).

As Lakersforce suggests, it probably doesn't have anything to do with the fact that you are running WoW non-natively. It could be caused by either your videocard's drivers, your GPU's memory, your RAM, a corrupted WoW installation or a random piece of Hardware.

Yes, I know it sucks. I'd start with a memcheck and a reinstall, we have no magic answers here. :/

---

### Post by MurnShaw on 2007-04-16
I remember reading in a nother thread that sometimes the wow mpq files get corrupted. Apparently the safest bet is to run the NT 4.0 emulation on wine with wow to maximize stability. Try that, see if it helps.

---

### Post by Death_Sargent on 2007-04-16
Ok running with openGL is not always the best idea infact it can even cause a los in preformance. 

Try running it the way it was intended instead of with OpenGL rendering.

---

### Post by hikaricore on 2007-04-16
> **Death_Sargent said:**
> Ok running with openGL is not always the best idea infact it can even cause a los in preformance. 

Try running it the way it was intended instead of with OpenGL rendering.


....

---

### Post by Tanoku on 2007-04-16
Actually, do not try to run WoW under DirectX unless you have Cedega 6.0.

...Even then, don't try to run WoW under DirectX. It's just... No.

---

### Post by Arcarna on 2008-01-30
I just recently installed Ubuntu 7.10 on my laptop and just finished installing WoW and so far the only time I get the #132 error is when I try to change anything video related. Haven't had mush time to log any serious game time for more info. If there have been any fixes please let me know.

---

### Post by coljnr9 on 2008-11-06
A small disclaimer to start out with: I am very much a newbie when it comes to ubuntu.  These are simply the steps I fuddled with from different guides, and finally got wow working under wine after my update to 8.10.  These steps may be redundant, and there might be easier ways to do what I did. 


In 8.04 WoW was running flawlessly (under WINE) after a bit of tinkering.  I recently upgraded to 8.10, and I was getting the #132 error evertime I started the game up.  I couldn't even see the login screen, which meant I couldn't log into a character to create the config.wtf file where you switch the game to OpenGL mode.  To fix this I tried two things.

1) I went to the ~/.wine/drive_c/Program Files/World of Warcraft/WTF folder and right-click > create file and names the doc "config.wtf".  It opened up in a text editor and I pasted the line:

SET gxApi "opengl" (from the Ubuntu WoW article).

I saved the file and then moved on to use the video driver from the nvidia website (I have a geforce 7800)

2) Here is how I installed my drivers, because the Hardware Drivers window in Ubuntu has let me down before.  I found the driver I needed on the nvidia site (using their driver search page).  It comes in a *.run file, which I was able to run in a round about way. 
I went to alt+f2 to get to a full screen terminal. I shut down the graphics display with

sudo /etc/init.d/gmd stop

then I ran the .run file, which in my case went like this:

sudo ~/Desktop/NVIDIA-Linux-x86-177.80-pkg1.run

note that capitalization of the folder/file names are important.

I followed through the nvidia installer process, then restarted the graphics display.

sudo /etc/init.d/gdm start

I restarted and logged in and it worked like a charm.  I also added some of the other graphics tweaks from the WoW in Ubuntu page here: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I hope this helps people, sorry if its too long of a post.  Message me if it works or if you found easier ways of doing anything.

---

### Post by peteratyorkshire on 2008-11-10
This solution has fixed the 132 error for me...
[http://appdb.winehq.org/commentview.php?iAppId=1922&iVersionId=9429&iThreadId=27152]("http://appdb.winehq.org/commentview.php?iAppId=1922&iVersionId=9429&iThreadId=27152")

---

### Post by Blaklafter on 2008-11-10
> **coljnr9 said:**
> 

1) I went to the ~/.wine/drive_c/Program Files/World of Warcraft/WTF folder and right-click > create file and names the doc "config.wtf".  It opened up in a text editor and I pasted the line:

SET gxApi "opengl" (from the Ubuntu WoW article).



This fixed the error for me.  Good Luck.

---

### Post by Zigon on 2009-06-03
> 1) I went to the ~/.wine/drive_c/Program Files/World of Warcraft/WTF folder and right-click > create file and names the doc "config.wtf".  It opened up in a text editor and I pasted the line:

SET gxApi "opengl" (from the Ubuntu WoW article).


This fixed it right up for me, thanks.

---

