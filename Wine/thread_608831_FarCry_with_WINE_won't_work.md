---
title: "FarCry with WINE won't work"
date: 2007-11-10
forum: Wine
---

### Post by BorisK on 2007-11-10
Hello,
I got Ubuntu 7.10 and WINE 0.9.49. I got FarCry 5CD set and because I got error that CD couldn't be unmounted because it's in use, I used Loki installer, but since I was suspecting that something was wrong with the install, I copied files from Windows.After that there were few DLLs missing, which I installed, and now when I try to start the game, i get error 'CrySystem.dll Loading Failed: Module not found' . I got that .dll file, also on FarCry forums someone complained he got same error however it's associated with NVidia driver , but I got ATI Radeon 9550-RV350. I'm currently using open source driver, but FGLRX in ubuntu's repos doesn't work either. Any solution ?

---

### Post by cogadh on 2007-11-10
Did you compile 0.9.49 yourself? The DEB package isn't availalbe yet. What errors are output to the terminal when you run the game? How are you running the game (exact commands used)?

---

### Post by BorisK on 2007-11-10
No, I had WINE installed previously and I updated it today with Update Manager.I run the Farcry.exe on the CD. There are no errors in terminal, just graphical error. Here is my terminal output : 
boris@boris-desktop:~$ cd /media/cdrom0
boris@boris-desktop:/media/cdrom0$ wine FarCry.exe (after that FarCry pic shows up and I get the error)
boris@boris-desktop:/media/cdrom0$

---

### Post by aoanla on 2007-11-10
> **cogadh said:**
> Did you compile 0.9.49 yourself? The DEB package isn't availalbe yet.

Yes, it is.

Just now, on my computer:
```


   >  apt-cache showpkg wine
Package: wine
Versions: 
0.9.49~winehq0~ubuntu~7.10-1 (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_gutsy_main_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_gutsy_main_binary-amd64_Packages
                  MD5: 41c511512dffd5fac91c839619c075b8


```

---

### Post by BorisK on 2007-11-10
No one knows the solution ?

---

### Post by aoanla on 2007-11-10
Are you sure you have hardware 3d acceleration?

What's the result of

glxinfo | grep render 

?

---

### Post by jimminy_kriket on 2007-11-10
Dont copy the files from windows would be my guess. You probably dont have the registry entries.

---

### Post by BorisK on 2007-11-11
aoanly : result of grep | render:

direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX/SSE2 TCL

I got open source ATI driver which isn't yet complete but I tried with FGLRX as well and it doesn't work.

 jimminy_kriket: so I should use Loki installer's files ? And where do I have to put the files ? In WINE's C drive like C:/Program Files/Ubisoft/Crytek/FarCry/ ? I don't know where FarCry's CD will look for files after I start FarCry.

---

### Post by BorisK on 2007-11-12
Please help me !

---

### Post by aoanla on 2007-11-12
I'm a bit worried about your renderer being something MESA - I'm not an expert on the opensource ATI driver, but usually that suggests that you're not actually getting proper hardware acceleration.

What do you get with the fglrx driver?

---

### Post by weblordpepe on 2007-11-12
It works good with the normal restricted driver with a Radeon 9600 (r300).
And you need to set Far Cry to use OpenGL and not Direct3D. There's some other tweaks somewhere.

---

### Post by BorisK on 2007-11-12
aoanla :It's same with both drivers.
weblordpepe: "  r_Driver = "OpenGL"   "     (from system.cfg)    - It's been set up like this before, I think loki installed did it.

---

### Post by aoanla on 2007-11-12
> **BorisK said:**
> aoanla :It's same with both drivers.
weblordpepe: "  r_Driver = "OpenGL"   "     (from system.cfg)    - It's been set up like this before, I think loki installed did it.

If you get:
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX/SSE2 TCL

when you're using the fglrx driver, then you're not actually using the fglrx driver, I suspect. You need to investigate if there's problems with your driver installation before anything else.

---

### Post by weblordpepe on 2007-11-12
Yeah Mesa isn't the fglrx driver. You'll need to ensure the drivers are working right.

---

### Post by BorisK on 2007-11-13
No, my mesa is right, because I'm not using FGLRX !now! . But I did try using it, because it didn't work I uninstalled it and reinstalled open source radeon driver.

---

### Post by aoanla on 2007-11-13
> **BorisK said:**
> No, my mesa is right, because I'm not using FGLRX !now! . But I did try using it, because it didn't work I uninstalled it and reinstalled open source radeon driver.

...yes, and you probably won't get FarCry to work with Mesa based OpenGL. Indeed, I'm fairly sure, as I said before, that even the Open Source ATI driver shouldn't be using Mesa...

What you haven't told us, therefore, is what you got when you install fglrx... ("It didn't work" isn't a response to that.)

---

### Post by BorisK on 2007-11-14
aoanla : With FGLRX driver I got the same error as with OpenSource driver (CrySystem.dll Failed loading...)

---

### Post by aoanla on 2007-11-14
I don't think you're understanding the point we're trying to make.

The error you got seems, on Windows machines, to most commonly occur when there are issues with the graphics drivers.

It is also the case that your system is giving odd results for glxinfo - we're not sure that you should get Mesa as a renderer, even with the Open Source ATI driver.

Hence!
It is likely that there is something wrong with your driver install - both with the Open Source driver, and with the fglrx driver when it was installed.

You might also try different versions of these drivers (for example, there are many changes just between the fglrx versions 8.40 to 8.42...)

---

### Post by BorisK on 2007-11-14
Well, I tried installing ATI FGLRX driver v. 8.42.3, and it didn't work(3D effects didn't work, not FarCry, I didn't try it with 8.42.3) , so I tried to delete it, but I believe certain parts of it might be still active, althrough I can run 3D effects with compiz just fine, and when I tried to start compiz with 8.42.3, a white screen came out.

---

### Post by aoanla on 2007-11-14
> **BorisK said:**
> Well, I tried installing ATI FGLRX driver v. 8.42.3, and it didn't work(3D effects didn't work, not FarCry, I didn't try it with 8.42.3) , so I tried to delete it, but I believe certain parts of it might be still active, althrough I can run 3D effects with compiz just fine, and when I tried to start compiz with 8.42.3, a white screen came out.

You whitelisted the fglrx driver with compiz first, right?

(Also, getting the fglrx driver working can be a bit tricky - it's quite possible that it wasn't quite installed right when you did it, through no fault of your own.)

---

### Post by BorisK on 2007-11-15
I installed the driver using this guide : [http://ubuntuforums.org/showthread.php?t=575843](http://ubuntuforums.org/showthread.php?t=575843)

But it didn't work

---

### Post by aoanla on 2007-11-15
> **BorisK said:**
> I installed the driver using this guide : [http://ubuntuforums.org/showthread.php?t=575843](http://ubuntuforums.org/showthread.php?t=575843)

But it didn't work

**What** didn't work? fglrx? compiz? FarCry?

Did you try checking the output of fglrxinfo as well as glxinfo when you installed? Did you check the contents of /var/log/Xorg.0.log to make sure that the fglrx driver was actually being loaded properly?

In addition, note that the guide you linked to notes, at the top, that it is not valid for the newest fglrx release (8.42.3) which is what you were installing. It also doesn't include instructions on how to get Compiz to work - you need to perform additional tasks after the pure driver install to make it work.

---

### Post by weblordpepe on 2007-11-15
What a royal pain. Can't we just have easily downloadable kernel modules that you can install in linux? I seem to recall this being solved in Windows 3.1

---

### Post by aoanla on 2007-11-15
> **weblordpepe said:**
> What a royal pain. Can't we just have easily downloadable kernel modules that you can install in linux? I seem to recall this being solved in Windows 3.1

Open-source kernel modules compile and install fine in Linux, for example. And, indeed, installing the current Ubuntu repository version of the ATI driver works pretty well with Synaptic.

For most people, even, most binary blob installers work fine - it's just that ATI seem to have difficulties in writing installers that work (as a defense of this statement, I note that to get the ATI 8.42.3 driver to install on 64bit Ubuntu, you have to download an additional script which ATI forgot to include...). Most of the guide to installing 8.42.3 involves procedures which fix common bugs in ATI's installer...

---

### Post by BorisK on 2007-11-15
Compiz didn't work. I didn't test FarCry with it. After I saw that Compiz doesn't work, I visited Compiz-Fusion's IRC channel and someone asked me for my xorg.0.log , however he wasn't able to diagnose the problem. And at the time I installed this driver, the guide wasn't outdated. It seems I messed up driver versions a bit, sorry. No, I didn't check outputs of glxinfo and fglrxinfo, but I think someone one the IRC asked me about that.
Now - should I install latest ATI fglrx driver ? I currently use Opensource driver - how can I uninstall it and get everything back to normal ?
Oh I forgot to mention : I think 3D games didn't work with newest ATI driver (I forgot so I'm not sure)
*when I say Compiz I mean Compiz-Fusion

---

