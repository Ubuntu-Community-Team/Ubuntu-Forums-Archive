---
title: "Running wine not starting app"
date: 2008-06-29
forum: Wine
---

### Post by SteveF on 2008-06-29
I installed a program.  When I navigate to folder in Nautilus, right-click and choose Open with Wine Emulator on the EXE, the app starts without problems.  But if I open a console, navigate to the folder with the EXE and enter wine appname.exe, the app does not start.

Wineserver and winedevice show up when I enter ps -ef | grep wine, but the app never starts.

What could opening with wine and running wine be doing differently?

Thanks,

Steve

---

### Post by plinydogg on 2008-06-29
Have you been using double quotes? For example, type something like the following into the terminal:

wine "c:\Program Files\Game\Game.exe"

Where the c drive actually represents the folder in your /home/.wine folder.

---

### Post by SteveF on 2008-06-30
> **plinydogg said:**
> Have you been using double quotes? For example, type something like the following into the terminal:

wine "c:\Program Files\Game\Game.exe"

Where the c drive actually represents the folder in your /home/.wine folder.

I tried wine "c:\appfolder\appname.exe"
I tried changing to .wine/drive_c/appfolder and entering wine "appname.exe"
I tried wine ".wine/drive_c/appfolder/appname.exe
I tried changing to .wine/drive_c/appfolder and entering wine appname.exe

None of these worked.  But right-clicking did.  I'd understand if right-clicking did not work either, then it would obviously be an app issue.

Steve

---

### Post by mc4man on 2008-07-01
You only need quotes or apostrophes when there are spaces in the path. 
Two ex., one with, one without 
> wine '/home/doug/.wine/drive_c/Program Files/DVD Audio Extractor/DVD Audio Extractor.exe'
> wine /home/doug/.wine/drive_c/dvdsoft/VobBlanker.exe

Note the complete path and positioning of apostrophes when needed

---

### Post by SteveF on 2008-07-01
> **mc4man said:**
> You only need quotes or apostrophes when there are spaces in the path.

Thanks.  I understand the quotes.  Just trying out different options.  

Does anyone know how choosing Open With from Nautilus would differ from executing from the command prompt?  Does it add options or set an environment variable?  Anything?

Steve

---

### Post by mc4man on 2008-07-01
> Does anyone know how choosing Open With from Nautilus would differ from executing from the command prompt? They are the same
In most cases from cli 
 wine <space><full path>.
If the exe is in windows dir. (or you place it there) then wine <space><appname.exe>

---

### Post by cogadh on 2008-07-01
When you try running it from the terminal (by whichever method you choose), is there any terminal output at all?

---

### Post by SteveF on 2008-07-01
> **cogadh said:**
> When you try running it from the terminal (by whichever method you choose), is there any terminal output at all?

None.  Doing a ps -ef, I see the prgram along with wine loaded.  But there's no sign the app is running.  When I right-click Open With, the app's window appears within 2-3 seconds.  I've let the terminal version go for a couple of minutes and nothing.

[Edit]
I ran both ways and looked at ps -ef for a few things.  The one thing I see different is that when running from Nautilus (right-click) wine-console --use-event=40 appears.  When I run from the terminal, that item does not appear.

Steve

---

### Post by cogadh on 2008-07-01
Try running it like this:
```
cd .wine/drive_c/Program\ Files/<app directory>
WINEDEBUG=warn+all wine <app executable>.exe
```
You should get some kind of terminal output with that which might explain what is happening.

---

### Post by SteveF on 2008-07-01
> **SteveF said:**
> None.  Doing a ps -ef, I see the prgram along with wine loaded.  But there's no sign the app is running.  When I right-click Open With, the app's window appears within 2-3 seconds.  I've let the terminal version go for a couple of minutes and nothing.

[Edit]
I ran both ways and looked at ps -ef for a few things.  The one thing I see different is that when running from Nautilus (right-click) wine-console --use-event=40 appears.  When I run from the terminal, that item does not appear.

Steve

Well, looks solved.  After seeing wine-console, I searched around the internet and found out there was a program wineconsole that can be used to run apps.  I did not know the app I was running was a windows console app.  Running wineconsole appname worked.

So apparently, right-click on Nautilus was able to determine that.

I didn't realize there was two separate apps (wine and wineconsole).  Learned something.

Steve

---

