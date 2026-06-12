---
title: "Google SketchUp on 64bit?"
date: 2007-08-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by RavanH on 2007-08-25
Hi,

Has anyone got any experience in getting SketchUp (now by Google, used to be @Last) running? Preferably on a 64bit system?

I installed the latest version under Wine but after starting the program, SketchUp opens but acts weird: e.g. the menu's are not visible (scrambled) and the tutorial screen remains empty. I have no experience with SketchUp so cannot tell if anything else works or not...

After a search on the net I found little proof of success except for older examples like [http://www.archilinux.org/wine/wine2.html#sketch](http://www.archilinux.org/wine/wine2.html#sketch) , but that might be really old :(

And if wine cannot do it, what should I try next?

Thanks for any suggestions :)

---

### Post by RavanH on 2007-08-30
OK, no reply... so here's an related question:

Has anyone got an older version of SketchUp for me? Preferably version 3.0 since that one sems to be able to run under Wine...

---

### Post by bouncingmolar on 2007-10-15
[http://aksels.de/software.php#sketch](http://aksels.de/software.php#sketch)

I'm not sure how to follow these instructions because i'm a noob but maybe try them and tell me how to do it once ur done ;)

---

### Post by RavanH on 2007-10-15
> **bouncingmolar said:**
> [http://aksels.de/software.php#sketch](http://aksels.de/software.php#sketch)

I'm not sure how to follow these instructions because i'm a noob but maybe try them and tell me how to do it once ur done ;)

interesting... see if i can make something of this. 

thanks for the link, bouncingmolar. i will report back here :)

---

### Post by RavanH on 2007-10-15
> **RavanH said:**
> i will report back here :)

N00bs galore! I crash at step 1 from the installation instructions:

* Patch the clean Wine Sources with the opengl-patch.
  Run "gunzip -c  opengl.patch.gz | patch -p0"

ehhhhhh.... what :confused:

---

### Post by bouncingmolar on 2007-10-29
Ok i'm going to give it a bash. I will edit this post with updates

```

$ wine iexplore http://winehq.org

```
installing wine gecko....

download stopped responding, quit installer, 

```

$ wine iexplore http://winehq.org

```

wine gecko successful install!

---

### Post by bouncingmolar on 2007-10-29
Installing patch: 

I opened the archive from the aksels.de site in one of the GUI archive managers and extracted the file: opengl.patch.gz

I then navigated to the folder it was located in terminal and typed:
```

$ gunzip -c  opengl.patch.gz | patch -p0

```

I got the following output:
```

can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- dlls/winex11.drv/dce.c     12 Dec 2006 14:42:59 -0000      1.3
|+++ dlls/winex11.drv/dce.c     10 Apr 2007 21:14:30 -0000

```

and now its asking me what file to patch....

---

### Post by bouncingmolar on 2007-10-30
I'm absolutely stuck now. I've been trawling google, the wine wiki, the kubuntu and ubuntu and debian forums. I can't seem to find any more detailed instructions about how to get open GL working

Loading sketchup: 
"
Sketchup was unable to initialise OpenGL!
Please make sure you have installed the correct drivers for your graphics card

Error: ChoosePixelFormat failed
"

---

### Post by bouncingmolar on 2007-11-01
i managed to get Sketchup to work on my kubuntu 64. 

I found at [http://appdb.winehq.org/objectManager.php?sClass=version&iId=6842&iTestingId=12728](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6842&iTestingId=12728)

[quote=kwg]
after the first run i got this every time i launched sketchup

SketchUp was unable to initialize OpenGL!
Please make sure you have installed the correct
drivers for your graphics card
Error: ChoosePixelFormat failed

so i went into regedit: HKEY_CURRENT_USER\Software\Google\SketchUp6\GLConfig\Display\HW_OK

change the value to 1. starts and runs fine. still crashes on save, but when resuming the autosave was still there and reloaded my drawing.

wine 0.9.39
sketchup 6.0.515
[/quote]

i loaded wine regedit. Found the aforementioned key and changed it. Seems to be working so far. However i can't search for models in the 3d warehouse. maybe installing ie6 will help.

---

### Post by bouncingmolar on 2007-11-01
At first i couldn't type anything in the search feild or any editable field within the sketchup object warehouse. 

I installed Ie6 from the ms website... that didn't seem to change anything

I then installed IEs4Linux [http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

I can now type things in the search fields, but i get 

> 
The request is invalid.


whenever i do a search.

---

### Post by ubuntu27 on 2007-11-01
Never heard or read about  [SketchUp]("http://www.sketchup.com/") until now. Thank you RavanH for mentioning it. Hope Google ports it to GNU/Linux like [Picasa.]("http://picasa.google.com/linux/").

I never used wine before so I can't help you with this. Good luck with Wine and Sketchup.

---

### Post by bouncingmolar on 2007-11-04
I uninstalled sketchup coz i was getting frustrated with not being able to use the 3d warehouse. 

However...

When i installed it again... it didn't work!!!!!!! It looked like it was loading and i could see all of the menus but it was frozen. with a dialog window open called instructor.

To FIX THIS:
(i tinkered)

Load "wine regedit" in run command

Go to HKEY_CURRENT_USER\Software\Google\SketchUp6\SnappyInstructor

Change "show" to 0

load sketchup... woot it works again.

---

