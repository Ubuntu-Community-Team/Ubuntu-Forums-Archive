---
title: "Blender 3D modeller"
date: 2006-06-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Endow on 2006-06-30
So I had Blender installed and for some reason when i clicked the icon on the applications thingy on the top of the screen nothing ahppened.

I uninstalled it and reinstalled it.I still can't acess the program but the program is installed...


What might be the problem??

---

### Post by thingy on 2006-06-30
See the ~/.xession-error file to find out if any messages are displayed when the icon is clicked.

OR

Launch a terminal and type in blender in it to launch the application and see what message are printed there.

---

### Post by Endow on 2006-06-30
Used the terminal...this is what I got :

"Using Python version 2.4
Xlib:  extension "GLX" missing on display ":0.0".
ERROR: Unable to open Blender window"

What should I do?Update Python or something(btw what is Python;how do I do that)?

---

### Post by Beamerboy on 2006-06-30
[QUOTE=Endow]Used the terminal...this is what I got :

"Using Python version 2.4
Xlib:  extension "GLX" missing on display ":0.0".
ERROR: Unable to open Blender window"

What should I do?Update Python or something(btw what is Python;how do I do that)?[/QUOTE]

Have you configure xorg to use GLX?  It looks like you haven't.  You need GLX enabled for 3D.

---

### Post by Endow on 2006-06-30
That's gibberish for me man.What do I need to do to configure it?Well I don't know what either of them are anyways...

---

### Post by Ric95 on 2006-06-30
Make sure to update the video drivers. That made the difference for me.

---

### Post by Shadow_ on 2006-07-01
I'm having the same problem.
I've installed all the 'latest' updates, and upgraded from Ubuntu 5.10 to Dapper.
But I've literally been using Linux for 3 days, so I'm not completely sure what else to do.
Help would be appreciated :)

~Nathan

EDIT: I've just noticed this is a 64 bit forum :S
would that affect the fixes people post?

---

### Post by Shadow_ on 2006-07-01
Ok, so I tired the terminal method and this is what I got:
```

Using Python version 2.4
Unable to load: libtiff.
Try setting the BF_TIFF_LIB environment variable if you want this support.
Example: setenv BF_TIFF_LIB /usr/lib/libtiff.so
Error: Rage 128 timed out... exiting
```

I typed in the example and got this:
```

nathan@ubuntu:~$ setenv BF_TIFF_LIB /usr/lib/libtiss.so
bash: setenv: command not found
```

Any suggestions?

---

### Post by thingy on 2006-07-02
Shadow,

Blender needs a 3d card to work and so you can show us the output of:

glxinfo

Also, as you did a upgrade, can you rule out the config files in your account as a possible source of the problem and create a new user and login as that user and aunch blender to see if its the same issue.

regards

jin

---

### Post by Shadow_ on 2006-07-03
Thanks for replying Thingy :)

The output for glxinfo can be found [in this post.](http://ubuntuforums.org/showthread.php?t=207266&highlight=Blender+3d+modeller)

Once again, sorry for the multi-post confusion...

~Nathan

---

