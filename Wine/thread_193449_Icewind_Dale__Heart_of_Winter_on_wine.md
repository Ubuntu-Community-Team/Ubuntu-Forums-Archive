---
title: "Icewind Dale:  Heart of Winter on wine"
date: 2006-06-10
forum: Wine
---

### Post by Reducer on 2006-06-10
Hi,

I've got the main Icewind Dale game running superbly in wine, however when I try to install the Heart of Winter expansion pack, it tells me that I don't have Icewind Dale installed.  Has anyone else run into this?

Thanks.

Reducer

---

### Post by ShanghaiTeej on 2006-08-17
Did you ever fix your problem?  I'm about to install the icewind dale expansion and want to know if you fixed the problem before I install.

---

### Post by Reducer on 2006-08-17
I ended up installing the game + expansion under Windows then just copying the directory over.

---

### Post by ShanghaiTeej on 2006-08-17
Where would you copy the whole directory (I need the gritty details)?  Thanks for the response.

---

### Post by Reducer on 2006-08-20
Yes.  Copy the 'Black Isle Studios' directory to the ~/.wine/drive_c/Program Files/ directory.

---

### Post by thom_raindog on 2007-04-09
How does one install and run IWD on wine?
I managed to install flawlessly, yet trying to run it...? I always get the following errormessage:
"An Assertion failed at Chitin.cpp at line number 1727. Programmer says: Error initializing key table, bad key file."

I installed Heart of winter over my main install: Fine. Same error on startup though.

Any ideas?

---

### Post by ipartola on 2007-07-22
Same error here. Any clues how to fix it? P.S.: Fiesty fawn running latest wine + IWD 1.0.6 (not heart of winter).

---

### Post by hikaricore on 2007-07-23
Although it appears that Icewind Dale works under WINE: [http://appdb.winehq.org/appview.php?iVersionId=208](http://appdb.winehq.org/appview.php?iVersionId=208)

It seems the expansion does not (or atleast not very well): [http://appdb.winehq.org/appview.php?iVersionId=5279](http://appdb.winehq.org/appview.php?iVersionId=5279)

I havn't been able to find any further info on the matter.

---

### Post by ShanghaiTeej on 2007-07-23
Yeah, never could get the game to work.  I just gave up.  I think I even tried cedega, but no luck.

---

### Post by piaskal on 2007-12-29
I had the same problem.
To start the game you have to run wine in the game folder or it wont work.

For me that was:

```

cd ~/.wine/drive_c/Program\ Files/Black\ Isle\ Studios/Icewind\ Dale\ Serce\ Zimy/
wine IDMain.exe

```

wine "C:\Program Files\Black Isle Studios\Icewind Dale Serce Zimy\idmain.exe" doesn't work.

---

