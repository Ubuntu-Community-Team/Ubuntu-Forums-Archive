---
title: "[SOLVED] How do I go about installngWineCVS.sh (and dx9wine)"
date: 2008-06-30
forum: Wine
---

### Post by slothbotkiller on 2008-06-30
Hello, I am hoping to get a decent solution to my problem, I keep on getting an error when trying to install the WineCVS.sh script. Is there anyone skilled enough to answer what seems to me, a challenging situation? 

thanks. I hope to recieve answers soon.

brian@brian:~$ sudo '/home/brian/WineCVS.sh' 

===============================================================================

Profile menu

Here you can download new profiles, upgrade existing
or run existing


  g) Get a profile from [http://winecvs.linux-gamers.net/WineCVS](http://winecvs.linux-gamers.net/WineCVS)
  c) Change command line action
  r) Run existing profile


=================WineCVS helpsystem (q will quit, b go back)=================

 Make your choice:
r







===============================================================================

List of profiles (b to go back):

0 ) dx9wine
Enter choice:
0


Running Profile : dx9wine
    Unpacking sourcetree...
/home/brian/.WineCVS/sources/dx9wine/wine












WineCVS.sh - Progress(u) : Green is current

   0 = Uninstall
   1 = Cleanup
   2 = CVS checkout
   3 = Configure
   4 = Make depend
   5 = Make
   6 = Make install
   7 = Finish up

-------------------------------------------

Configuring ...
/home/brian/.WineCVS/Functions/RunWineCVS: line 785: cd: /home/brian/.WineCVS/sources/dx9wine/wine/: No such file or directory



--------- Error log - file /home/brian/.WineCVS/sources/dx9wine/ErrorLog : ---------

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now


Error in Configure

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


brian@brian:~$

---

### Post by p_quarles on 2008-06-30
Moved to the Wine section.

---

### Post by cogadh on 2008-06-30
Is there a particular reason you trying to use an outdated script to try and compile Wine yourself, rather than use the precompiled current version from the WineHQ repositories? Or compile it using the actual WineHQ scripts?
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by slothbotkiller on 2008-06-30
> **cogadh said:**
> Is there a particular reason you trying to use an outdated script to try and compile Wine yourself, rather than use the precompiled current version from the WineHQ repositories? Or compile it using the actual WineHQ scripts?
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Thank you for your speedy reply, I had never realized it was an outdated script until you questioned my motive. Well for some reason I thought that there was a possible connection as to why my network speed in gameplay was (and still is) so slow. Perhaps there is a way around that, the unfortunate thing about this is that I am a beginner in the Ubuntu Universe

Brian

---

