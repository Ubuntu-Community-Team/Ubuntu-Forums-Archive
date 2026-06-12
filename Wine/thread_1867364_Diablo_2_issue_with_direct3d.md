---
title: "Diablo 2 issue with direct3d"
date: 2011-10-22
forum: Wine
---

### Post by lanzd on 2011-10-22
I'm running wine 1.2.2 and used the blizzard installer while  downloading everything off of their site for d2 - No expansion yet.  I  tried to run d2 to make sure its working up to this point before I  continue to install lod.  I get an error that goes like this: 

Error 25: A critical error has occurred while initializing Direct3D. 

I thought wine didn't support direct3D and that was why I was forced  to play world of warcraft in opengl mode.  I also read that d2 doesn't  have support for opengl mode due to blizzard not finishing it and ending  up taking it out completely despite leaving the tag there.  I've read  the issue has to due with the dlls I have and I think I need to copy the  right ones to my diablo directory (I have no idea what dll files are  for).  I tried running the D2VidTst.exe and after it runs the test the  output says that "No video modes are found".  I hope the solution is as  easy as going into the wine config and specifying a specific dll  override but I'm not sure which one to use (if it is even a solution).  I'm not sure if these assumptions are correct or not. Can someone help  me understand the problem and help point me in the right direction to  fixing it. 

Thank you, lanzd

---

### Post by Soulcage on 2011-10-23
You really should be using wine1.3 from the ppa, you can find instructions at the site.

Also last time I played I used a glidewrapper it seemed to run better.

[http://www.svenswrapper.de/english/index.html]("http://www.svenswrapper.de/english/index.html")

---

### Post by lanzd on 2011-10-23
Yeah, Since I posted I've switched to 1.3 and then uninstalled and reinstalled my video drivers.  I'm still getting the same error.  Does wine support direct3D?  I've read that it has limited support for Directx10 but nothing confirming direct3D.  And the diablo video test says you need atleast Directx6.1 to play and Directx7a is included on the disc.  Ofcourse I can't use that on linux but I would image if Wine has limited support with Directx10 that it surely can support a game that requires Directx6.1.

---

### Post by lanzd on 2011-10-23
the glidewrapper seemed to work.  The video test was successful and I got the the character creation screen.   Then I exited out and then went back and it froze.  I'm still going to look more into it.  This is the farthest Ive gotten in the past 2 days :D.

---

### Post by mastablasta on 2011-10-24
Make sure you also disable those alt combo keys. it seems theyx were causing freezes in my case.
 
also Unity or something like that could also be interfering with wine. who knows.... compiz occasionally had issues with wine before. but it might be a good idea to turn it off if you haven't already.

---

### Post by lanzd on 2011-10-25
I got diablo 2 and diablo 2 lod to work using a glide wrapper specific to diablo 2.

The site was [http://www.svenswrapper.de/english/index.html](http://www.svenswrapper.de/english/index.html)

One issue is sound, I have none once I hit the main menu.  I've seens that issue come up a lot with d2 so I'm sure I can find something on it.

What is Unity or compiz?  

But I am freezing when using the alt key, I'm going to try and find out  how to disable it now, if I don't find it, I will be back.

Thank you

---

