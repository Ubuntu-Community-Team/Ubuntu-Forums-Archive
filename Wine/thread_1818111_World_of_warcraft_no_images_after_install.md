---
title: "World of warcraft no images after install???"
date: 2011-08-04
forum: Wine
---

### Post by Clegro on 2011-08-04
Ok I was able to install wow and run it but I am getting this black screen and unable to see the images. I do see words and this is not the only game i have trouble like this with. I also have the same issue running guildwars. I was able to take a screenshot to show what the heck is going on here. If anyone has an idea on how i can repair it I am open for suggestions. 

[IMG]http://i51.tinypic.com/iddlzd.png[/IMG]

PS I did not know if this was the right forum to put this in.

---

### Post by akoskm on 2011-08-04
Just a guess: have you tried to start it with -opengl option, like:
```

wine /path/to/Wow/Wow.exe -opengl

```.
What is your PC's specification? Please provide more information.

---

### Post by Clegro on 2011-08-04
im not quite sure all the system specs i know wow was played on the computer before useing windows. I have tryed the opengl and thats what got me to the screen im at now. But with all that black i dont know what to do I can click on what words i see but still no images.

---

### Post by Soulcage on 2011-08-04
Did you read this? [http://ubuntuforums.org/showthread.php?t=885111]("http://ubuntuforums.org/showthread.php?t=885111") Are you using an intel gpu?

---

### Post by Clegro on 2011-08-04
Ok yes I am on intel. It is a laptop about 4 years or so old. I am not sure the wine version. I am pretty new to linux I did check out that post before hand. I have used wine for several games and they work just fine. The only 2 I can not get wine to work for properly is Guildwars and World of warcraft. The games load up but they are that black screen I am showing. I am still not sure what it is I have tried many diff settings and tried to search for the issue.

---

### Post by Tweak42 on 2011-08-04
> **Clegro said:**
> Ok yes I am on intel. It is a laptop about 4 years or so old. I am not sure the wine version.

Not to discourage you from trying, but if it's that old of intel video then you're in for a fight to get it working.  If you do get it working, performance will very likely be far slower than in windows.  There just search for "wow intel" in the wine forum and see what I mean.

Easiest way to get wine version is open a terminal and run: "wine --version"  Or you can launch the "Configure Wine" from the gui menu and look on the About tab.

Addendum: ah and yes please try following the wine forum sticky [** Before asking for help with Wine << PLEASE READ BEFORE POSTING **]("http://ubuntuforums.org/showthread.php?t=885111")

---

