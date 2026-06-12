---
title: "Using Wine"
date: 2011-08-16
forum: Wine
---

### Post by alexis44 on 2011-08-16
*I need some help.  I installed Wine, and I tried to install an executable file, and it doesn't see it as an executable, although I have gone in to the properties and and changed the permissions for it.  The program is IrfanView.  Does Ubuntu not support this program even with Wine? *

---

### Post by kyletstrand on 2011-08-16
What version on irfanview are you trying to install?

You might find some useful information here:

 [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834)

You might need to download the MFC42.dll library to install as suggested at the wine appdb.

You can find it here:

 [http://download.microsoft.com/download/vc60pro/update/1/w9xnt4/en-us/vc6redistsetup_enu.exe](http://download.microsoft.com/download/vc60pro/update/1/w9xnt4/en-us/vc6redistsetup_enu.exe)

Hope it helps!

---

### Post by alexis44 on 2011-08-16
The latest version and I don't know how to install what you mentioned.

---

### Post by kyletstrand on 2011-08-16
What's the name of the .exe install file?

Go to the folder that in which it is located in your terminal and type:

```
wine [name of file].exe
```

Or you should be able to find the install file and right click and select 'Open with Wine Windows Program Loader'

---

### Post by JerkyMcgee on 2011-08-16
Hello, having the same sort of problem trying to run final fantasy 7 on wine. How exactly might I do that.
Setup.exe is the file and I just clicked open with wine.

---

### Post by kyletstrand on 2011-08-16
What happens when wine tries to open setup.exe?

---

### Post by JerkyMcgee on 2011-08-16
> **kyletstrand said:**
> What happens when wine tries to open setup.exe?
the file /Downloads/Setup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by kyletstrand on 2011-08-16
Right click the file icon and go to the permissions tab at the top.  Check the box that says 'Allow executing file as a program'

Try running it after doing that.

Let me know what happens.

---

### Post by JerkyMcgee on 2011-08-16
> **JerkyMcgee said:**
> the file /Downloads/Setup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
I went permissions and changed to be able to run as executable... and now I have a disc problem.. Basically my disc drive is full when I installed ubuntu i did it on daemon tools with windows and installed it. THen I started my computer and i got the windows or ubuntu option except I think my disc drives are split up weird...

---

### Post by kyletstrand on 2011-08-16
So you've got a full hard drive then?

---

### Post by JerkyMcgee on 2011-08-16
> **kyletstrand said:**
> So you've got a full hard drive then?
Sort of... I still have like 350 gbs free.
I think I just have to switch drives but idk how. Yes the drive I guess im trying to run this on is full.

---

### Post by kyletstrand on 2011-08-16
Are you running a partitioned install or are you using wubi?

---

### Post by alexis44 on 2011-08-16
> **kyletstrand said:**
> Right click the file icon and go to the permissions tab at the top.  Check the box that says 'Allow executing file as a program'

Try running it after doing that.

Let me know what happens.
In my case, it didn't do anything.  I guess my computer can't use Wine. :confused:

---

### Post by JerkyMcgee on 2011-08-16
> **kyletstrand said:**
> Are you running a partitioned install or are you using wubi?
I think partitioned install, I dont really know how to check, but that wasnt my plan in the first place, I thought I was going to run it off windows IN daemon tools, but I dont even know what was supposed to happen if I did that correctly.

---

### Post by kyletstrand on 2011-08-16
> **alexis44 said:**
> In my case, it didn't do anything.  I guess my computer can't use Wine. :confused:

I'm guessing you need to install that library file.  Or you could try the install using the winetricks front end as suggested on the AppDB.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834)

That link should be very helpful.

---

### Post by kyletstrand on 2011-08-16
> **JerkyMcgee said:**
> I think partitioned install, I dont really know how to check, but that wasnt my plan in the first place, I thought I was going to run it off windows IN daemon tools, but I dont even know what was supposed to happen if I did that correctly.

That could be the problem.  

Go to the terminal and type

```
df -h
```

and post the output.  It will tell you how much disk space you have left on your currently running partition.

---

### Post by alexis44 on 2011-08-16
> **kyletstrand said:**
> I'm guessing you need to install that library file.  Or you could try the install using the winetricks front end as suggested on the AppDB.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834)

That link should be very helpful.
Maybe helpful for a geek, but not for me.  Thanks anyway. :(

---

### Post by JerkyMcgee on 2011-08-16
> **kyletstrand said:**
> That could be the problem.  

Go to the terminal and type

```
df -h
```and post the output.  It will tell you how much disk space you have left on your currently running partition.
/dev/loop/0 is the filesystem I'm using on this partition. (I dont know why...) 
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   16G   16K 100% /


While windows is mounted on host and that has tons of space. (400g)
MAybe I could go back onto windows and change the mount for ubuntu or something? OR would you suggest something else all together...?

---

### Post by kyletstrand on 2011-08-16
Not sure.  It looks as though you installed using wubi. 

Did you install ubuntu with an interface that looks like the pic behind this link?

[http://en.wikipedia.org/wiki/File:Ubuntu_10.04_Wubi.PNG](http://en.wikipedia.org/wiki/File:Ubuntu_10.04_Wubi.PNG)

---

### Post by JerkyMcgee on 2011-08-16
> **kyletstrand said:**
> Not sure.  It looks as though you installed using wubi. 

Did you install ubuntu with an interface that looks like the pic behind this link?

[http://en.wikipedia.org/wiki/File:Ubuntu_10.04_Wubi.PNG](http://en.wikipedia.org/wiki/File:Ubuntu_10.04_Wubi.PNG)
I cant really remember...
But I remember it asking me some sort of partition question and I said that I didn't want a partition, although with my knowledge of what a partition is, it seems like I have one? I can access my windows files while I'm using ubuntu if that means anything.

---

### Post by kyletstrand on 2011-08-16
My guess is you did install using wubi.  It kind of emulates a partition of it's own where you can't use more than that in ubuntu.

IF you do want to play games and other larger applications, I would recommend reinstalling ubuntu with a larger partition.  Create a livecd from the .iso file and you can easily partition the drive sizes.

---

### Post by alexis44 on 2011-08-16
WOOHOO!  I did it!  I installed Irfanview!  I thought it was a lost cause!  Now I have to figure out how to install the plug-ins!  Thanks for your help!!

---

### Post by kyletstrand on 2011-08-16
Glad you got it to work!

---

### Post by alexis44 on 2011-08-16
> **kyletstrand said:**
> Glad you got it to work!
Yes, me too.  I've always loved IrfanView.  It's the best viewer and not a bad editor.  It may take some time to figure out the plug-ins and where they're located on my computer, but other than that, I'm fine. :D

---

### Post by alexis44 on 2011-08-16
It appears that certain programs work with Wine and others don't.  IrfanView seems to have worked, and a game like Hangaroo does, but Media Player Classic doesn't seem to.  Do you seem to know why this is, and what programs won't work with Wine.

---

### Post by JerkyMcgee on 2011-08-16
> **kyletstrand said:**
> My guess is you did install using wubi.  It kind of emulates a partition of it's own where you can't use more than that in ubuntu.

IF you do want to play games and other larger applications, I would recommend reinstalling ubuntu with a larger partition.  Create a livecd from the .iso file and you can easily partition the drive sizes.
A livecd... my laptop doesnt even have a dvd rom drive !!
Yes, I want to make a bigger drive for Ubuntu, I don't really know how to go about that though. How can I transfer all my information over instead of actually reinstalling it fresh?

---

