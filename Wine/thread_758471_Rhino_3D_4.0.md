---
title: "Rhino 3D 4.0"
date: 2008-04-18
forum: Wine
---

### Post by MrDoug on 2008-04-18
I'm wondering if anyone has been able to run Rhino 3D 4.0 on Ubuntu with Wine.  In the database it said it hadnt been tested yet, and all the related posts regarding Rhino were unanswered.  Will it work?

---

### Post by rocketship on 2008-05-19
I just tried to install it with Wine, and was not successful.

This piece of software is the holy grail for me... sadly, they're not very Linux friendly at McNeel.  My hope is that when they finish the port to OSX it will make the software more portable as a whole.  I'm found that other CAD apps like Vectorworks, which is cross-platform, seem to Wine a bit better.  I'm guessing its because they're using less of the Windows built-in libraries...

RS

ps - you should politely request a Linux port on the McNeel forum.  I think they believe that Linux users are people who aren't willing to pay for software.

---

### Post by jrharvey on 2008-07-30
I have been asking for this from McNeal for a while now. A linux version is not even being considered at the moment and although an OSX version is being developed i believe it is from a 3rd party. From what i understand it is not a matter of porting to OSX then porting to Linux. If any progress is to be made then we (the users) are going to have to do it ourselves probably through wine. The biggest problem is being able to run the license manager.

---

### Post by zivotinja on 2009-02-02
I think this is an old method of coercive authoring. MC Neel like most companies that produce softwares for Windows is in bed with Microsoft. They, MS, are not allowing them to add the LInux version. MC Need is not alone there. Just think of Adobe. Same thing happened with the XSI. As soon as they were bought by Autodesk (another monopoly in CAD/3D world) the Linux version was sacked. Need more proof just look into kernel and C libraries and you will see that developing rhino on Linux is far easier than on the OS X. Yet there is no project out there. 
What free market? What is a globalism - monopoly over three continents. Thanks to EU Microsoft could not pull the same nasty game in Europe.

---

### Post by nikkkko on 2009-09-22
This is an old thread but maybe not a dead thread...

I'm a linux user of six years but stuck when it comes to 3D. I do more and more 3D design - mostly for a range of cabins built out of steel and wood - and currently use SketchUp running under wine. It's OK, (arcs are terrible), but we're now looking to send our output directly to industrial machinists for computer numerical controlled, (CNC), cutting and I've pretty much hit the wall. I have a CNC sub contractor who recommends Rhino3D and from a recent search it appears that it [might work under wine]("http://frankscorner.org/index.php?p=rhino3d").  

Anyone have any first hand experience?

---

### Post by razor7 on 2009-09-24
Any success with rhino in wine?

Thanks in advise

---

### Post by nikkkko on 2009-09-25
Nah.  Stuck with an error message asking for Windows Installer ver 3.0 or higher.  A search for this on WineHQ reveals that Wine doesn't yet support 3.0 but maybe there's a patch but I can't find it and even if I could I'm not sure I'd go there.

On the other hand there is a ruby script for outputing what I want from SketchUp so I'm going to pursue that route for a bit and then, unless there's a long term solution, I'm going to have to go back to [..draws deep breath..] Windows.

3D is really the achilles heel for Linux.

---

### Post by razor7 on 2009-09-25
Oh man...what a shame!.

I have done some research and found this softwares to be useful for cad and 3D design.

MEDUSA4 (Free for personal use)
[LIST]
[*][http://www.cad-schroer.com/index.php?screen=1.4&ziel=Products-MEDUSA-M4Personal&land=com](http://www.cad-schroer.com/index.php?screen=1.4&ziel=Products-MEDUSA-M4Personal&land=com)
[*][http://www.cad-schroer.com/index.php?screen=1.4&ziel=Products-MEDUSA-Demos&land=com](http://www.cad-schroer.com/index.php?screen=1.4&ziel=Products-MEDUSA-Demos&land=com)
[/LIST]

Realsoft 3D (Usable Demo)
[LIST]
[*][http://www.realsoft.com/](http://www.realsoft.com/)
[/LIST]

VariCAD (Trial)
[LIST]
[*][http://www.varicad.com/en/home/](http://www.varicad.com/en/home/)
[/LIST]

Also found some tips on using Blender for precision drawings
[LIST]
[*][http://www.rab3d.com/tutorial.html](http://www.rab3d.com/tutorial.html)
[*][http://www.studiorola.com/news/blender-3d-current-situation-with-external-renderers/](http://www.studiorola.com/news/blender-3d-current-situation-with-external-renderers/)
[*][http://www.studiorola.com/tutorials/miscellaneous/bringing-rhino-files-into-blender-3d/](http://www.studiorola.com/tutorials/miscellaneous/bringing-rhino-files-into-blender-3d/)
[*][http://www.studiorola.com/tutorials/rendering-tutorials/product-rendering-using-yafray-via-blender-3d/](http://www.studiorola.com/tutorials/rendering-tutorials/product-rendering-using-yafray-via-blender-3d/)
[/LIST]

I have found lots and ots of programs that run on windows and linux, but thie are the most professional IMHO.

Hope this little research helps someone

---

### Post by nikkkko on 2009-09-25
Thanks for that.  I'll probably give Medusa, (too tech), and RealSoft, (worried about output formats), a miss but will give VariCad a shot.  It's a while since I tried Blender - at least a couple of years - so maybe I'll have another look.

---

### Post by aeon.flux on 2009-10-25
hi,

i'm looking for rhino for linux too, i need it for school, they can give me free full version (for study) but i have windows7 RC (that is working only to march 2010), so i'm looking for any way how to run rhino on ubuntu, or...
..is there any way, how do make a model in blender and than export it, so it can be opened in rhino?

---

### Post by nikkkko on 2009-10-26
> **aeon.flux said:**
> how do make a model in blender and than export it, so it can be opened in rhino?
Rhino has extensive import/export capabilities, but I don't know about Blender.  A (very) quick google shows that there are many export scripts available for Blender and that .stl is amongst them.  I've used the .stl format for importing and exporting in Rhino so that should work fine, although other formats might work better.

FYI, I have been using Rhino running it under VirtualBox/XP and it works flawlessly. There's a VirtualBox addon somewhere which allows me to share directories with Ubuntu so that swapping in and out of Windows is seamless.  I mostly use this for going from Rhino to SketchUp and back.

---

### Post by tonybeccar on 2009-11-11
Hi everyone.. I want to get this software running on Ubuntu too..

Today I decided to give it another try on Wine.. well.. here it is what I accomplished so far which is not much but it's something..

I copied the installation folder from a Windows partition.. and using Wine 1.1.30 I was able to run it BUT I get stuck with an error asking for the license.. not precisely that, but I can tell because when Rhino splash screen starts, it is unable to find any serial number or registration name.. and then Wine gives an error message and the program crashes leaving a DUMP file on the desktop.

One more thing.. when I run "RmaLicenseValidation.exe" it complains about not finding the license key at certain parameter.. I was wondering where does that parameter point so I can look for the key in the Win partition.

After this, I tried to export every 'mcneel' registry key I found on the win partition and then import it to wine registry. Still no luck.. despite everything I imported it still cannot find the damn license! Although I think I imported some keys containing license info.. I really don't know it for sure.

I still haven't searched the windows registry for 'rhino' and do the export/import process..

I found this really interesting thread:
[http://www.winehq.org/pipermail/wine-users/2007-February/024514.html](http://www.winehq.org/pipermail/wine-users/2007-February/024514.html)

The guy who answers the question says that in order to perfom the kind of procedure I am trying to.. you must do a clean windows install in a virtual machine.. and then using a file monitor provided there, you can see every file which was installed during the installation.

It's a longshot but I think it is worth the try because this is a great software and in my opinion vital to Linux.

So, in conclusion.. my suggestions would be:

Anyone knows exactly how to perform the process of 'copying the windows installation directories and then running it from wine', but doing it right? (import reg files, native dll's, etc..)

Since I'm unable to install it in wine because Windows installer v3.1 cannot be installed in wine although I used cabextract and extracted the files in it but still cannot execute the obtained .exe. Anyone knows about a patch to install win installer 3 or anything likely in wine? (maybe doing the same process described above)

I don't know if something in winetricks would help.. 


Well... this is where I got so far.. I would be deeply grateful if some user could have some kind of response to this matter. 

Thanks to everyone in advance!

---

### Post by cacycleworks on 2010-01-05
Ugh... I just hit the same wall as you guys. Today (like every other day I need to do CAD or scan something) I chose WinXP from GRUB. But what makes today special is that now suddenly there are USB errors when trying to connect to our Romer CMM arm.

I've got an SSD drive in this laptop and am to the point where I'm thinking of reinstalling windblows onto either this laptop with a conventional HD or going and getting another computer altogether to install windows to (so I can get back to where I was "yesterday"). 

Y'all were talking about the Rhino license...? If you're not running a free license server at your work (I'm about to find out how to do that) then it will sometimes ask for your key when it starts. If not connected to the internet, it asks everytime. So there must be a phone home feature.

If there's anything you guys think of that I can do to help, please let me know. (I will do that thing about sniffing the files upon the next install I do of rhino). We are almost rid of quickbooks and now Rhino is the sole program requiring windows.

Windows=FAIL

---

### Post by andrea000 on 2010-01-06
someone has made autocad 2008 work in wine so
i would say someone has made Rhino 3D work it
took me a long time to find out what he did to
make it work and i would say it will take you
a long time as well.You may want to try virtual
box and a copy of win xp it may be the only way
right now.

---

### Post by cacycleworks on 2010-01-06
> **tonybeccar said:**
> I copied the installation folder from a Windows partition.. and using Wine 1.1.30 I was able to run it BUT I get stuck with an error asking for the license.. not precisely that, but I can tell because when Rhino splash screen starts, it is unable to find any serial number or registration name.. and then Wine gives an error message and the program crashes leaving a DUMP file on the desktop.

I found this really interesting thread:
[http://www.winehq.org/pipermail/wine-users/2007-February/024514.html](http://www.winehq.org/pipermail/wine-users/2007-February/024514.html)

The guy who answers the question says that in order to perfom the kind of procedure I am trying to.. you must do a clean windows install in a virtual machine.. and then using a file monitor provided there, you can see every file which was installed during the installation.

Hi tonybeccar, I just did a fresh install of winXP on the notebook I have for using my CMM arm. When I installed Rhino professional (with the key), I ran the process monitor and saved the output as a CSV. I also ran it when I ran sr6 update, so there are 2 CSV files. The total is 6,666K, or 7M. 

[Here is the URL for the file... http://sites.google.com/site/cacycleworks/rhino_install.zip]("http://sites.google.com/site/cacycleworks/rhino_install.zip")

Now I've got to see if I can get back to work... only lost 2 days to windows so far...

:) Chris

---

### Post by oralgant2 on 2012-06-26
I am a long time linux user, and have had some trouble with programs under wine; auto cad mainly.   I have had excellent luck running virtual box with a minimal xp installation.  It is very fast and more reliable than a stand alone xp installation.  I run autocad, flight simulator, delftship, etc.  with no problems.  The only thing is that you need a valid xp installation cd.  I boot into linux in 18sec. then into xp in another 30sec, because I don't have any anti virus, only a windows firewall.  I would like to try rino, but do not have it.  I am sure you could run in vb in any case.
Happy hunting.

---

### Post by ubudog on 2012-06-27
Old thread closed.

---

