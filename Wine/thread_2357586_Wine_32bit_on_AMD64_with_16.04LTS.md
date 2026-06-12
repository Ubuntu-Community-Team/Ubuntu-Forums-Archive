---
title: "Wine 32bit on AMD64 with 16.04LTS"
date: 2017-04-03
forum: Wine
---

### Post by mark bower on 2017-04-03
**Run 32bit ACAD2000 with WINE on 16.04LTS AMD64** - a better title

I am not successful in understanding how to install a 32bit version of WINE on my 64bit system.  (I have a 32bit program, ACAD2000 which works just fine on my 32bit CPU computer, but I have another program that is available as either 32 or 64bit)  

Can someone please provide fairly detailed instructions on how to do this?  Or is there a way to use "sudo apt install wine-stable" and force it to install the 32 bit version?

I have tried to install 32bit capability via "sudo dpkg --add-architecture i386 && sudo apt update" which was suggested to do before a WINE install.  But when I run "dpkg --print-architecture" all I get is amd64.  Perhaps this suggested change is not relevant. I also attempted to try and get PlayOnLinux to work, but could not get the hang of it.  I would prefer to have just a WINE installation, no PlayOnLinux

What I would ideally like to have is a 32bit WINE.deb that would install on my 64amd system and run 32bit programs for sure, and maybe run both 32 and 64bit.

But if I need to do much more the cmd line code on line 2 above, then please provide explicit detail based on my limited level of understanding.

---

### Post by Dennis N on 2017-04-04
Too see the architecture, there are two options that you use:

```
dmn@Sydney ~ $ dpkg --print-architecture
amd64

```tells you the native architecture
and 

```
dmn@Sydney ~ $ dpkg --print-foreign-architectures
i386
```
any other architecture enabled.

There are two wine programs: **wine** is 32 bit and **wine64** is 64 bit. I just installed 'wine' from the Ubuntu repository and found that both of these are in /usr/bin. I have always just used the command **wine** to start or install programs (not wine64).


PlayOnLinux, I have only limited experience with. I installed it from the Ubuntu repos. It installs a custom(?) version of wine to use with the program you select to install from their inventory.

---

### Post by mark bower on 2017-04-04
o.k., sure enough, "dpkg --print-foreign-architectures" shows that "i386" is installed - thanks for this.

1) Now, is the step to install an i383 architecture necessary to get WINE 32bit to install on a 64bit system?

2) And are you suggesting that if I now run "sudo apt install wine-stable" that 32bit WINE will be installed?

I will return tomorrow

---

### Post by Dennis N on 2017-04-04
After enabling i386, Installing **wine** should install the necessary 32-bit libraries as dependencies. All automatic. I installed the package **wine** from the repository and got both 32-bit wine and 64-bit wine, plus a couple of extra packages got installed, like winetricks. I don't see any **wine-stable**.

---

### Post by mark bower on 2017-04-04
I am gaining optimism, especially since what you have done accommodates both 32 & 64bit.

Could you please supply me the actual cmd lines you used to install from the repository? (I realize I should be able to figure this out, but if it involves the ppa thing then I am never quite sure of what I am doing; I would like to steer clear of mucking up my system).  

Also, what version is working for you or what version gets installed? I read somewhere that there were problems with 1.8 so persons went back to 1.6.

---

### Post by Dennis N on 2017-04-04
> **mark bower said:**
> I am gaining optimism, especially since what you have done accommodates both 32 & 64bit.

Could you please supply me the actual cmd lines you used to install from the repository? (I realize I should be able to figure this out, but if it involves the ppa thing then I am never quite sure of what I am doing; I would like to steer clear of mucking up my system).  

Also, what version is working for you or what version gets installed? I read somewhere that there were problems with 1.8 so persons went back to 1.6.

I looked at the command history (type 'history' in the terminal), and this was the actual command used:
```
sudo apt install wine --install-recommends
```
wine is actually a metapackage that installs the 32-bit and 64-bit versions of wine, and the --install-recommends installs a couple of extra packages like winetricks. The version in 16.04 Ubuntu repository is 1.6.2.

(PlayOnLinux (if you ever try it) is likely to install other versions known to work with the programs in its catalog. These other versions are kept separate in another folder from the regular installation of wine from the Ubuntu repository, so no conflict.)

---

### Post by mark bower on 2017-04-04
I installed per your suggestion, and indeed I get two folders:  Program Files and Program Files (x86).  I installed the 32bit version of IrfanView; it installs under Program Files (x86) and it runs fine.  I installed ACAD2000; it also installs under Program Files (x86), it appears to be a good installation based on folder locations, tries to but does not boot, either from acad.exe in its folder, or from WINE as an installed application.  I think the system may be buggered up, at least with respect to ACAD.

So, I want to purge, and do all anew, new WINE, ACAD and Irfanview install.  However, when I remove programs via WINE [I may have directly deleted their folders in Program Files (x86)], use purge and remove cmds, WINE still remains in the Applications drop down and scrolling to right still list applications as available.  So how do I completely remove WINE (where is the file that is retaining previously installed applications), and remove it from the Applications drop down menu.  IE, in gnome classic, Applications>WINE.

---

### Post by mark bower on 2017-04-05
o.k.  found were the "offending files" are located:  ~/.local/share/applications and /share/desktop-directories.  hopefully then WINE will disappear from the Applications drop down?  And then I will start the install steps again

---

### Post by Dennis N on 2017-04-05
Installs but does not run can happen. Wine will not run all Windows programs, just some. And the version of Wine used can be a factor.

I would try starting the offending program from the terminal and see if any useful error messages show up. 

terminal usage:
```
wine <path to program executable>
```
example:
```
wine "/home/dmn/.wine/drive_c/Program Files/Internet Explorer/iexplore.exe"
```
quotes used because of space in path.

I would not remove wine since the installation is probably o.k. (the other program works). Try adjusting settings instead. To remove, you would have to specifically remove the packages wine installs as dependencies - these include several executables. **sudo apt remove wine** won't remove them - removing a metapackage like wine never removes the stuff it installs.

I see these containing "wine" in the name as being installed:
 wine-gecko2.21 (2.21-0ubuntu1 Ubuntu:16.04/xenial [amd64])
 wine-gecko2.21:i386 (2.21-0ubuntu1 Ubuntu:16.04/xenial [i386])
 wine-mono0.0.8 (0.0.8-0ubuntu1 Ubuntu:16.04/xenial [all])
 wine1.6-amd64 (1:1.6.2-0ubuntu14 Ubuntu:16.04/xenial [amd64])
 wine1.6-i386:i386 (1:1.6.2-0ubuntu14 Ubuntu:16.04/xenial [i386])
 wine1.6 (1:1.6.2-0ubuntu14 Ubuntu:16.04/xenial [amd64])
 winetricks (0.0+20141009+svn1208-2ubuntu1 Ubuntu:16.04/xenial [all])

then there are many 32-bit libraries installed as well - but probably no good reason to remove those.

_Additional Thoughts:_

Did you explore settings in winecfg? A program can have custom settings and Windows dlls specified for it. Winetricks can modify lots of wine settings too. You can also investigate PlayOnLinux as it may allow you to specify a different Wine version to use.

---

### Post by mark bower on 2017-04-05
Well I apologize.  To keep things simple, or so I thot, I did not mention wherein ACAD2000 did work.  So - - - It works fine (under WINE) on my 32bit-CPU-PC, no tweaks required.  It actually did work on the AMD64 PC, but had difficulty in some functions.  And since it is a 32bit app, that led me to the "sudo dpkg --add-architecture i386" install and your comments on how I could verify that.  And then somewhere along the line, ACAD ceased to boot.  And last nite, before your comments, I again tried to remove everything wine.  However, using a Nautilus search today, I now realize that WINE files are stored in any number of locations, so a clean removal is probably not practical (and your comment is probably not advisable to do so.  I did try a WINE boot from the directory that acad.exe resides in, but that did not work.

So as much as I appreciate all of your time on presenting suggestions, I am going to install fresh essentials on another HD to see if ACAD works.  If so, then (arg!) I will redo the main HD.  This is not trivial since I have had to make a number of tweaks to get my 4K monitor (TV) to behave practically; fortunately Gnome Classic is easy for me to do.  The large 40" is worth the effort and cost a little less than $400 in a Costco deal.

I will report back when there is "meaningful clarity" - may take a couple of days thoh.

mark

---

### Post by Dennis N on 2017-04-05
> It works fine (under WINE) on my 32bit-CPU-PC, no tweaks required. It actually did work on the AMD64 PC, but had difficulty in some functions.

Aha! I thought you meant it ran using Windows on a 32-bit computer. That is a strange problem then if the executable of the 32-bit Wine version is identical on each machine. Seems like it should work the same on both machines.

A new install attempt seems like a reasonable thing to try.

---

### Post by mark bower on 2017-04-05
o.k., talking only the amd64 PC, I installed an additional hard drive with the intent to do a clean install of 64bit on that drive and use it to try and resolve the problem - leave the "main" hard drive alone.  **oops**, I confused my connects and disconnects, didn't observe when setting partitions, and made the new install on my main drive(removing all that was on the drive), not the additional drive.  I am good at doing this all the time, until today; apparently I was subjected to a brainless day. [I have USB HD backups of important stuff]

As soon as I got the classic, nvidia (needed for 4k), and some other small stuff installed, I installed WINE and then ACAD2000.  No dice.  The little wheel during attempted booting twirls for a while, no msgs.  Tried to boot from desktop icon, via WINE, and from the location of acad.exe.  I verified that i386 is present as well as amd64.

So, any suggestions on how one can trace why ACAD might be unhappy during a WINE boot on the 32bit/64bit system?  

I have a terrible work around, but doeable.  Install 32bit on the additional drive and then ACAD can run for sure(from what I experience) on the AMD64 computer.

---

### Post by bcschmerker on 2017-04-06
**As an environment, wine is designed around the Intel® Pentium Processors® and related models.**  In Synaptic, marking **wine** for installation will drag in the i386 Package dependencies for installation as well.  **wine** is a compatibility environment for executables built for Microsoft® Windows® NT&#8482; through 5.4, and some NT 6.x programs will also work.

I used wine on the Hot Rod gPC in a failed  attempt to upgrade firmware in a Mitsumi® FA404M; the Application didn't recognize the FA404M's internal Carry Computer USB 2.0 datacard interface (the same problem I ran into attempting to upgrade the same device on my ASUS® CM1630-06 under both Win 7.0.8001 and 10.0.14393.168).  Both systems run AMD processors and chipsets capable of x86 and x86-64.

---

### Post by Dennis N on 2017-04-06
> I confused my connects and disconnects, didn't observe when setting partitions, and made the new install on my main drive(removing all that was on the drive)
Ouch!
> any suggestions on how one can trace why ACAD might be unhappy during a WINE boot on the 32bit/64bit system?
Did you try the suggestion in post #9 about running in terminal to observe any system messages?
> What I would ideally like to have is a 32bit WINE.deb that would install on my 64amd system and run 32bit programs for sure
Get it with:
```
dmn@Sydney:~$ apt-get download wine:i386
Get:1 http://mirrors.cat.pdx.edu/ubuntu xenial/universe i386 wine i386 1:1.6.2-0ubuntu14 [974 B]
Fetched 974 B in 0s (4,534 B/s)

```
Also, you could install the 32-bit version of wine and leave out the 64-bit packages. Would be same result as using the deb file. 

**sudo apt-get install wine:i386**

---

### Post by mark bower on 2017-04-07
Dennis

I am now back working on the 64AMD, installed 64bit 16.04LTS, WINE installed via "sudo apt install wine --install-recommends", ACAD installed as 32bit, and IrfanView installed as 64 bit.  Irfanview launches from its installed icon on the Desktop, ACAD does not launch from its installed icon.

The following cmd line entries with WINE generated error msgs: "wine:  cannot find . . path":
      
      wine "/home/mark/.wine/drive_c/Program Files (x86)/ACAD2000/acad.exe&#8221; 
      wine "/home/mark/.wine/drive_c/Program Files/IrfanView/i_view64.exe"

I rt clicked each of the Desktop icons, then properties, and get the following paths which were established by WINE:
env WINEPREFIX="/home/mark/.wine" wine C:\\Program\ Files\\IrfanView\\i_view64.exe      
env WINEPREFIX="/home/mark/.wine" wine C:\\Program\ Files\ \(x86\)\\ACAD2000\\acad.exe 

I believe I installed Irfanview as 32bit previously, and it worked.
I set up another HD on my AMD64 system with 32bit 16.04LTS.  With WINE, ACAD does not work on it, IrfanView does.

I have discovered a problem of missing .dll files which I will work some time today, and report back, could be as late as this evening.

---

### Post by Dennis N on 2017-04-07
All three of the formulations below start my Across Lite crossword puzzle program. If I have to manually enter the path to make a menu entry, I always opt for the first, as I can just copy most of the part in quotes from the file manager address window when I browse to the program's directory and it is more readable for me.

```
wine "/home/dmn/.wine/drive_c/Program Files (x86)/Litsoft/Across Lite/ACROSSL.EXE"
env WINEPREFIX="/home/dmn/.wine" wine C:\\Program\ Files\ \(x86\)\\Litsoft\\Across\ Lite\\ACROSSL.EXE
wine C:\\Program\ Files\ \(x86\)\\Litsoft\\Across\ Lite\\ACROSSL.EXE

```
From here, no ideas why you see "cannot find path". But there is some reason, of course - can only suggest you copy path to the folder from file manager address window to avoid error.

---

### Post by mark bower on 2017-04-07
In a nutshell, the problem appears to have been due to the WINE installation (and more than once) not placing some six .dll files where they were needed.  They were identified by "cd <path>/wine acad.exe".  This spelled out the directory and five files missing from loading.  Corrected these and then another missing .dll was identified.  And finally, repeating the process for a 3rd time, got a "FATAL ERROR:  cannot find XMX file acdb???" msg.  So located that file and copied it to the directory where other files were copied - voila, ACAD2000 booted and functioned properly.

So, wish I had centered more on your suggestion #9 to figure out why "wine <path>/acad.exe" did not work, as "cd <path>/wine acad.exe" did what you intended and exposed the  problem.

I do not intend to pursue whether this problem is a 32bit CPU vs 64bit CPU, noting again I had no problems installing ACAD2000 on my 32 bit PC.

So thanks ever so much for spending quite a bit of timely hanging in with me, and guiding me to the step that worked.  Tomorrow I will play with the "wine <path>/acad.exe" syntax again to try and see what goes.  Needless to say, I have a set of notes to retain re what ACAD2000 files, after initial WINE installation, must be copied to another existing directory.

mark

---

### Post by Dennis N on 2017-04-08
I checked some old notes I made for myself about using wine (a file dated Aug 2009), and at that time wrote the following as the first steps:
> 1- Use the Ubuntu repo version. winecfg must be run  at least once (from the terminal) before installing any other programs under wine. This sets up the necessary directories.
2- Also use the terminal to start your applications - **if its an installer, always cd to the installer program's location**.

I had completely forgotten about this suggestion (in bold) until you mentioned it in you last post. Maybe that makes a difference, at least in some cases. I haven't installed anything with wine for over a year, and I don't think I followed it on most recent installs. In those days, I always used the terminal to run wine, but now I just use the menu entry.

---

### Post by mark bower on 2017-04-09
I believe you made some solid points.  As mentioned before, I did a complete reinstall of 16.04LTS on the HD.  I installed WINE and did one config WINE within the app to verify or set the windows operating system to Win98 (required by ACAD2000). I then installed ACAD2000 and got a message along the lines that a path did not exist and should ACAD create it - I answered yes.  This probably relates to your comment on running WINE config twice.

Actually, I used to install by going to the directory where I have copied the the apps' files to be installed, and specifically go to location of an app's setup.exe file.  Then in that directory/folder I executed "wine setup.exe".  But I have gotten lazy recently and just rt-clicked on setup.exe files, get a pop-up window, and choose "Open with WINE windows program"(or maybe "Open with Wine Windows program loader")"., which then installs the program.  So - more notes, and I will return to the sequence you suggest and that which I used to do, except now maybe also do a second config WINE before installing apps for more "insurance".

The really good news for me is that use of ACAD2000 is not broken!  I do not use it often enough to maintain an ease of working level.  Switching to another cad program would make things worse.

---

### Post by bcschmerker on 2017-04-10
**Concerning the "missing dll's" problem,** would it be possible to construct Applications and Application Extensions in GNU GCC?  I've a contingency for building an experimental program in Wine, using /usr/local/src/wine as the build directory prior to installing in /usr/local/wine/drive_c/progra~1; Microsoft charges quite a bit for Visual C++, J++, &c.

---

