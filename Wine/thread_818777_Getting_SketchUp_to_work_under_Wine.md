---
title: "Getting SketchUp to work under Wine"
date: 2008-06-04
forum: Wine
---

### Post by Zephik on 2008-06-04
**My apologies in advanced if I have not posted this into the right forum section, please move to the appropriate section if so. Thanks.**

I'm going to share with all of you my experiences with getting Google SketchUp 6 to work using Wine 1.0 rc3 in Ubuntu 8.04 aka Hardy Heron. 

**My System Specs:** (Possibly Important) 
ATI Mobility Radeon 9700
Ubuntu 8.04
Wine 1.0 rc3

When I first installed SketchUp via Wine, I would always get this error upon launching of the program. 

> Sketchup was unable to Initialize OpenGL!
Please make sure you have installed the correct
drivers for your graphics card.

Error: ChoosePixelFormat failed 

Then I installed EnvyNG and selected the option "Install the ATI Driver (Automatic)" and clicked "Apply". 

Doing this then gave me no errors on SketchUp startup, but it didn't give me a working SketchUp either. It gave me the basic outline of the SketchUp Window but didn't load anything else and then auto closed.

So to fix that I followed these instructions:

> Fix:
Open your wine menu and open the C drive (/home/user/.Wine)
Open the Windows Folder
Find Regedit.exe and run it with Wine
Find: HKEY_CURRENT_USER\Software\Google\SketchUp6\GLConf ig\Display
There are three entries - Look at the bottom one, name 'HW_OK"
Double click it and change the data from a 0 to a 1
Run Sketchup 6

Doing that gave me a non-auto closing SketchUp with a black screen where you usually draw/create your models. But the second I clicked on anything it would once again auto-close on me. 

So to fix that I opened up Terminal and entered this code.

```
sudo metacity --replace &
```

Now I had SketchUp up and running without hitch or error and no auto-closing, but the screen where you draw/create your models was still black and therefore unusable. So to fix this problem all I did was uninstall my graphics drivers using EnvyNG. Now I have SketchUp working perfectly! 

Hope this helps some of you out there! It worked for me so hopefully it will work for you too! :)

**Major thanks to "Crazy Buddhist" of TheBestCaseScenario.com! I couldn't of done this without you pal.** :)

(Note: I am however stuck in 800x600 resolution because of the uninstallation of my graphics driver. I am downloading the proper driver from ATI/AMD for Linux as we speak, will post update if I solve the screen resolution problem.)

---

### Post by naught101 on 2008-06-14
thanks for the info, Zephik.

I'm also getting the black screen issue, but I'm using the intel driver, so the envy solution won't work for me. Good to have confirmation that it's a driver issue though.

Does anyone know what exactly might cause this? Sketchup was working for me previously (a few months ago), although that might have been when I was still using the i810 driver.

---

### Post by jcr1 on 2008-07-28
I have been trying to get this to work...

I had the gecko question, said yes, then did the regedit fix.

It opens, and trys to run the initial set up window, where you pick dimension type etc...but freezes from there. 

There are no dimension options in the drop down menu, and pressing continue causes it to freeze up.

Any ideas?

---

### Post by jcr1 on 2008-08-06
Now I cant get past the opengl problem. I edit the registry but it doesn't make a difference. 

The metacity command doesn't seem very happy either

---

### Post by bhall430 on 2008-08-23
I'm actually getting suck prior to the install finishing.

Sketchup 6 - free with Wine 1.1.3

The install will quit with the following error
 "Setup is installing Google Sketchup Features"
 then "error -1. SketchupInstaller.exe failed."


Is wine too new? are there libraries missing from Wine?

---

### Post by babujbf on 2008-11-12
ho ho ho! snap yo! I followed the steps posted, uninstalled nvidia driver with envy and reinstalled it. Sketchup works just fine. 

thanks

---

### Post by dankegel on 2008-11-23
Sketchup 7 is working fine for me (I have an Nvidia 8500 graphics card, and I'm using the latest drivers on Intrepid) once I follow the tips in 
  [http://wiki.winehq.org/GoogleSketchup](http://wiki.winehq.org/GoogleSketchup)
but I'm no expert.  
If after following the tips there, you still have
problems, please report them to the wine appdb or bugzilla
and I'll try to get them fixed, if I can.
Thanks!

---

### Post by AaronDavison on 2009-02-19
Hi:KS
  
    :Dthanks for ur useful info...

its rocking..:popcorn:


[www.staffingpower.com](www.staffingpower.com)


sentersoftech

---

### Post by eggshelly on 2010-08-14
Thank you very much, nice simple fix.  Just writing back to confirm that this worked for me:

Ubuntu 10.04
Wine 1.1.42
IBM T42p, ATI FireGL T2 graphics card with default drivers
Google Sketchup Pro 7

---

