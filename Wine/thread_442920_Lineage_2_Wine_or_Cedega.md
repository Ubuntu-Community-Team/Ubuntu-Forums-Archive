---
title: "Lineage 2: Wine or Cedega"
date: 2007-05-14
forum: Wine
---

### Post by Sugi on 2007-05-14
I've tryed lineage 2 with both wine and cedega.  In wine, i get this error "AGP is disabled" but how do i enable it?  Maybe, I need something close to directx for wine?
  Now within Cedega, It says,
"No acceptable display modes found (D3D_OK). Please delete your Option.ini file if this error prevents you from starting the game."  Note:  I deleted the Option.ini file and nothing happens.  It still won't load.

I don't know where to go next.  Though within my research, I found out lineage 2 has worked with both wine and cedega.  So, i just need to do some configing and I should be set, but I don't know why it's being so difficult.  In recent news for configing Lineage 2, they say it doesn't run anymore, because of this program with Lineage 2 called gameguard.  It stops 3th party programs (IE: bots, and in our case, wine or cedega.)  The good news is, I'm on a private server, so no game guard, but then that means, gameguard isn't the problem.  So, whats stopping lineage 2 from booting up?  
Please, if anyone knows how to fix this.  Let me know.  I've seen people run lineage 2 in feisty fawn, but how?  it's possible.

I have this tutorial I'll to link, but I don't know how to compile one of the steps.  It looks really confusing.  Can anyone help me with it??
[http://appdb.winehq.org/appview.php?iVersionId=5069]("http://appdb.winehq.org/appview.php?iVersionId=5069")

"1: Download modified here: (13.7mb file)
Wine modified (l2 crash fixed)
2: Compile it like u always do that... "

"cd /home/%USER%/~/wine (~ path to downloaded and uncompressed wine)
./configure
make depend && make
su (or sudo if u use ubuntu... well just switch to superuser ;) )
make install "

These steps did not work for me.

If anyone can help, it would be great.  Any help is good help. :)

**MY FIX:**
I just installed Lineage 2 within a Windows partition and copied it over to my wine folder.  Run the l2.exe file within the system and your set.  Enjoy


UPDATED: 03-18-09
**^By the way, You do NOT need to compile wine for Lineage 2, thus wine is able to run Lineage 2 without compiling it with a special patch.  As well, the appdb link does not work anymore.**

I noticed people still check this thread.  If you are having issues with Lineage 2 and wine.  Check out this following link, it's for troubleshooting.  If you can't find anything to fix your problem, post in the thread.  It's been updated for the past two years. :D
> [http://ubuntuforums.org/showthread.php?t=634828](http://ubuntuforums.org/showthread.php?t=634828)

Sugi

---

### Post by AndrewRiedi on 2007-05-14
Make sure you have the nvidia-glx, nvidia-glx-new, or nvidia-glx-legacy drivers installed.  That doesn't appear to be a Wine problem, more of a driver problem.

---

### Post by Sugi on 2007-05-14
how would i update my drivers?  from nvidia's website?  how do i know if my video card is support under linux drivers?  that worries me.  >.<

i have geforce go 7700.

---

### Post by lakersforce on 2007-05-14
```
glxinfo | grep rendering
direct rendering: yes
```

If it says no, or does not support at least openGL version 2.0 you have to install your [video-drivers]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"). Your videocard would be the nvidia-glx package.

---

### Post by Sugi on 2007-05-14
ahhhh, is that in th exorg,conf file?  isn't that file for my video card?  if so, how do i get to it?   where is it in my file system??

---

### Post by lakersforce on 2007-05-14
> **Sugi said:**
> ahhhh, is that in th exorg,conf file?  isn't that file for my video card?  if so, how do i get to it?   where is it in my file system??

Click the above link.

/etc/X11/xorg.conf

---

### Post by Sugi on 2007-05-14
"Restricted Devices Manager"
I did that when i first installed ubuntu feisty fawn.  I went into my xorg.conf and i couldn't find anything with 
"glxinfi | grep rendering
direct rendering: yes"

I did "control + f" in gedit.  It might be my graphic card.  It's for a laptop.  Geforce GO 7700.  I went to your link and it didn't seem to help me.  It talked about crt outputs.  Not my problem within laptop.  What should I do?

---

### Post by lakersforce on 2007-05-14
You have to type it in at a terminal:

```
glxinfo | grep rendering
```
and you should get the following output:
```
direct rendering: yes
```

---

### Post by Sugi on 2007-05-14
oooh, my bad.  yea, the direct rendering: is yes.  so, whats the next step then??

---

### Post by lakersforce on 2007-05-16
I have no idea. Can you start other openGL enabled games? Seems wierd that you are told by the game that you have no 3d card, when you do have it and its enabled :confused:

---

### Post by Sugi on 2007-06-05
I know, I know.  I'm going to try it on VM and see how that goes (something like vmwarea, maybe.)  In the game, my clan leader is doing the same thing (not vmware though, he uses red boot)  So, maybe I'll have some luck like he did.


Currently playing:  diablo 2, warcraft 3, starcraft, and maybe someday lineage 2.  (maybe starcraft 2 when it comes out. ^_,^)

So, I can play other games too, but no lineage 2.  It was a great game with shitty coding. I knew this back in the days of windows.

---

### Post by pappapump on 2007-06-05
No, that doesn't mean gameguard has no effect at all.
Gameguard STILL loads and will stop your game from working.
What you need to do is discuss the problem with the private servers admin and see which workaround they use.
When I ran the XTC L2J server we just used a 127.0.0.1 redirect for gameguard and fixed it that way.
Since the advent of the newer lineage clients gameguard has started discovering this little redirect script.
There should be a script that you can download from them that wil deal with this problem for you.
If that don't help, go to [http://l2.hopzone.net/](http://l2.hopzone.net/) and ask for kadar after you enter the L2 area.
Go to the forums and post your question there, most likely they can walk you through it.

---

### Post by pappapump on 2007-06-08
Heres a link to a pre-made wine x script for Lineage 2

[http://www.4shared.com/file/11853611/67b056c9/wine_mod_fixed_2_tar.html](http://www.4shared.com/file/11853611/67b056c9/wine_mod_fixed_2_tar.html)

OOPS forgot to include instructions.

[http://appdb.winehq.org/appview.php?iVersionId=5069&iTestingId=10255](http://appdb.winehq.org/appview.php?iVersionId=5069&iTestingId=10255)

---

### Post by DaveBG on 2008-05-06
I managed to run Lineage2 in WINE but i do not get sound :(
Does anyone know how to enable the sound?

---

