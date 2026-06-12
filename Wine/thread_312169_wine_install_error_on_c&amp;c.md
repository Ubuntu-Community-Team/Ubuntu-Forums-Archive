---
title: "wine install error on c&amp;c"
date: 2006-12-04
forum: Wine
---

### Post by broekskw on 2006-12-04
ok it's been 2 day that i have been trying to install c&c on 2 ubunto systems and both give me the same install and terminal error. have been looking and reading and posting all over others and this forum site(everyone so freindly here:mrgreen: 8) )but have everyone stumped on this one.so lets see if someone in the game forums has the solution to my problem. other sites [http://www.frankscorner.org/index.php?p=webdesign](http://www.frankscorner.org/index.php?p=webdesign) have this game as ok to run on linux base systems but both my systems have the same error. :-? 

pleaseeeeeeeeeeeeeeeeeeee someone come forward to help, or is it just that some games will never run on this system linux

thanks:) :KS :mrgreen: :-D

---

### Post by hikaricore on 2006-12-04
[http://appdb.winehq.org/appview.php?iVersionId=727](http://appdb.winehq.org/appview.php?iVersionId=727)

I know nothing about the game, just pointing you in the right direction.

---

### Post by broekskw on 2006-12-04
thanks for your reply but looking at this i do not see a fix. must be me but looks like french to me, do not understand what he is saying that fixed his problem

nstaller fails in current CVS (2006/04/08)
by Bernhard Rosenkraenzer on Saturday April 8th 2006, 6:09
wine autorun.exe works and gives the setup splash screen. Clicking "Install red alert" results in "Unable to locate necessary files. Please run Setup.exe from the CD-ROM disc." (the disc is mounted at /mnt/cdrom, which is also pointed to by ~/.dosdevices/d: - wine d:\\autorun.exe behaves identically).

Launching setup.exe (and the various setup.exes in subdirectories) results in this output on the console:

$ wine SETUP.EXE
Usage: winevdm.exe [--app-name app.exe] command line

can you explain this fix if it is a fix to me. thanks again:mrgreen:

---

### Post by edemark on 2006-12-04
Hi
I play red alert without any problem using dosbox
you may give it a try
Or you might try freera which is a linux port to play C&C RA

good luck

---

### Post by m3741 on 2008-09-05
What eventually worked for me was to make sure that the CD that I burned had the correct CD label. The labels MUST be EXACTLY...
Allied Disc -> CD1
Soviet Disc -> CD2
Counterstrike -> CD3
Aftermath -> CD4

Hope this helps someone...

---

