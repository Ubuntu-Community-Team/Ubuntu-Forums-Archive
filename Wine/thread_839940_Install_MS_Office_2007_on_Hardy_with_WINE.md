---
title: "Install MS Office 2007 on Hardy with WINE"
date: 2008-06-24
forum: Wine
---

### Post by arashiko28 on 2008-06-24
[COLOR="Red"]THIS IS NOT A RANT!!! I NEED HELP![/COLOR]

Even though I'm a complete Linux lover and have deleted windows out of both my Desktop and Laptop... I can't turn every person I know into Linux, even if I did tried to sell it like Amway :lolflag:

Now, I need M$ Office because of the .pptx docs, I can't be guessing where it goes everything every single time I receive a m$o 2007 document. If you don't know what I mean, try to open a presentation made on 2007 with the odf-converter, it's a big mess.
Anyway, my point is that I've been following some instructions where I must delete a couple of .dll files and add another. The delete step and adding one of them went perfect. The other one, that must do trough terminal gave me this:> sudo msiexec /i msxml3.msi
[sudo] password for ****: 
wine: /home/****/.wine is not owned by you

> ~$  msiexec /i msxml3.msi
err:msi:copy_package_to_temp failed to copy package L"msxml3.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"msxml3.msi"
***@***-laptop:~$ wine: Call from 0x7b844b20 to unimplemented function rpcrt4.dll.I_RpcExceptionFilter, aborting

what I'm I doing wrong?
Please help:confused:

---

### Post by tamoneya on 2008-06-24
Try this.  This should fix the problem from the first code segment:```
sudo chown -R your_username ~/.wine
```

---

### Post by arashiko28 on 2008-06-25
> sudo chown -R your_username ~/.wine
remove my user folder? or just the .wine folder. Still, if I have to paste a new file, how does it helps by deleting the full configuration file?

---

### Post by brett123 on 2008-06-25
That command won't remove anything, it is changing the owner of those files/directories.

---

### Post by tamoneya on 2008-06-25
-R stands for recursive not remove.  To remove it would be ```
rm -r ~/,wine
```Please dont do that though that will just make things messy.  It is  however a good thing that you tried to understand what you were doing before you blindly typed in commands.

---

### Post by arashiko28 on 2008-06-27
It isn't solved. I tried to do that and still get the same message of the folder not being owned by me. Sorry I took a time to comeback but I'm on partial exams, so not enough time for me this week.

---

### Post by arashiko28 on 2008-06-28
I managed to work it out. Now on the next step that is running $ wine setup.exe

it starts smootly and progresses lighting fast but right now it's stucked at what I may guess a 60-70% of progress and on the terminal window get this message repeated so many times that the first actions were deleted.

> fixme:xrender:X11DRV_AlphaBlend not a dibsection


I am using the latest version of wine, sice it was updated today.

---

### Post by arashiko28 on 2008-06-28
BUMP
it's been 0 minutes now, is there absolutely no way to get this thing working, if it is, even though i hate the idea, I will have to install windows in another partition just for being able of using .pptx :confused:

---

### Post by pissedoffdude on 2008-06-28
> **arashiko28 said:**
> BUMP
it's been 0 minutes now, is there absolutely no way to get this thing working, if it is, even though i hate the idea, I will have to install windows in another partition just for being able of using .pptx :confused:

There's lots of other ways to open pptx or any other office 2007 files. 
For example, [http://www.zamzar.com/]("http://www.zamzar.com/") can convert them for you.  Though you might be set on using office, and in that case, just install office 2003 and use 2007 compatibility pack from microsoft, [http://www.microsoft.com/downloads/details.aspx?FamilyId=941b3470-3ae9-4aee-8f43-c6bb74cd1466&displaylang=en]("http://www.microsoft.com/downloads/details.aspx?FamilyId=941b3470-3ae9-4aee-8f43-c6bb74cd1466&displaylang=en")

---

### Post by arashiko28 on 2008-06-28
Its a mess, I can't spend two or three hours trying to figure out what goes where as these presentation I'm trying to view aren't made by me. All I want is a way that truly works, because all of what i have tried fails or send some error message. odf-converter is very good for word, but my problem lays now on power point.

I managed to get to a 70%, all i need now is to find out what's missing and finish it.

---

