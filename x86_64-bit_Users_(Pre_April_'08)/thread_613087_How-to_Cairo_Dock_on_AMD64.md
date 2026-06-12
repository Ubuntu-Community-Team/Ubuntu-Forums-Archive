---
title: "How-to: Cairo Dock on AMD64"
date: 2007-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by RavanH on 2007-11-14
So here is a **short and easy** (the installation part anyway) How-To for **Cairo-Dock on Ubuntu Gutsy AMD64**.

[CENTER][COLOR="DarkRed"][FONT="Palatino Linotype"][SIZE="5"]
How to get Cairo Dock running on AMD64[/SIZE][/FONT][/COLOR][/CENTER]


[COLOR="DimGray"][FONT="Palatino Linotype"][SIZE="4"]INDEX[/SIZE][/FONT][/COLOR]

[B]About Cairo Dock
About this How-To
Prerequisites [/B](what you need to make it all work -- start here if you are too eager to first read the about sections ;) )
[B]Installation
- Method 1, from repo [/B](NEW and recommended! Now stable 64bit packages and completely the 'Ubuntu way')
**- Method 2, manually installing deb packages** 
**- Method 3, compiling from SVN source **(get the latest development with script to make things easier)
[B]Error Messages
Usage [/B](to get you on your way)
[B]Notes & Tips
Remove Cairo Dock
References[/B]



[COLOR="DimGray"][FONT="Palatino Linotype"][SIZE="4"]ABOUT CAIRO-DOCK[/SIZE][/FONT][/COLOR]

Cairo Dock (also referred to as CD in this how-to) is a brilliant, highly configurable, light-weight but effective and useful piece of eye-candy. It sort of resembles the well known OS-X dock that looks so smooth. Well... this one not only looks smooth, it IS smooth!

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=57160&stc=1&d=1200956562[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=50253&stc=1&d=1195119889[/IMG]

Video's on YouTube featuring Cairo Dock: [http://www.youtube.com/watch?v=G4bNdznE0qc](http://www.youtube.com/watch?v=G4bNdznE0qc)

For questions about [_Cairo Dock_]("http://developer.berlios.de/projects/cairo-dock/"), I would suggest posting them on the main [_Cairo Dock Forums_]("http://developer.berlios.de/forum/?group_id=8724") because the project needs some fire from the international community. Currently, the buzz on cairo-dock is fragmented on these forums but mainly heard in French forums. 
[NEWS:] The dock has recently been upgraded to support internationalization. Fabounet, the current main developer, says: > hop, hop, the 1.4.6 is now fully internationnalized through gettext. [ ... ] the language is detected automatically so no more need to select it. The launchers are also internationnalized if you drag'n'dropped them from the gnome menu. So if anyone feels the need to contribute... get your dictionaries out! :) 



[COLOR="DimGray"][FONT="Palatino Linotype"][SIZE="4"]ABOUT THIS HOW-TO[/SIZE][/FONT][/COLOR]

It is my first how-to on these forums. I have done the following a while back on a Gusty Gibbon AMD64 install. Please post any suggestions to improve this how-to to the thread. 

The info on this page is collected from several other wiki-pages, forum-threads and my own experience as a newbie, so please be lenient with me ;) and help improve this how-to!



[COLOR="DimGray"][FONT="Palatino Linotype"][SIZE="4"]PREREQUISITES[/SIZE][/FONT][/COLOR]

Before anything else, you (user) must be in the sudoers list. This means you must be logged in as user with admin privileges (but not root) so you can install programs.

**Transparency** 
Your desktop should be capable of and using transparency (compositing). 
**Gnome:** This can be achieved by either **running Desktop Effects** or (if you do not like the extra system load of Desktop Effects) get **xcompmgr** by following the instructions at the end of this paragraph. Without transparency, Cairo Dock works but doesn't look as good as it should. If you have a NVidea or ATI graphics card, you might have to take a few more steps to get Desktop Effects working. There are a lot of threads and How-to's on that topic on these forums. For good instructions on installing the latest ATI drivers using AIGLX on *Gutsy and Hardy*, see Method 2 on _[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Installation](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Installation)_.
[INDENT]**TIP:** To get transparency (and window shading!) without Desktop Effects and the additional system load that CompizFusion brings along, do the following. Get **xcompmgr** by entering in a terminal screen the command ```
sudo apt-get install xcompmgr
``` Then add a new entry to your start-up list containing the command **xcompmgr -c -f -n** so transparency will load on each login. Easy! [/INDENT]
**XFCE:** You can perfectly use the native/built-in composite manager (instead of installing anything bulky like compiz-fusion) if you are happy with only transparency and drop shadows. To activate it, open the Configuration Manager from your Settings menu. Open **Window Manager Tweaks** and click the tab Compositor. Activate at least the first option 'Enable Compositing' for transparency to become available. Other options can be activated at will.
**KDE:** To enable KDE's built-in compositor, go to System Settings -> Desktop -> Window Behavior -> Transparency.

**Getlibs** 
[COLOR="Red"]**Since 64bit is supported, Getlibs is no longer needed. However, you might still consider installing Getlibs on your system. It is useful for many of those applications that still only come in 32bit packages. Just browse through the getlibs forum thread to see all the success stories...**[/COLOR]
For ***installation Method 2*** (below) you will need to have the excellent 32bit library dependency tool that should be on EVERY 64bit system called **Getlibs** installed on your system. If you did not do so already, follow the simple installation instructions on _[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)_ (basically just one click to download the latest version as a Debian package and install it). After using it on this installation process, just leave it on your system. It will be useful for ***every 32bit application*** you will be installing later!




[COLOR="DimGray"][FONT="Palatino Linotype"][SIZE="4"]INSTALLATION[/SIZE][/FONT][/COLOR]

You can choose between three methods. The ***first method*** is the easiest (let's call this the 'Ubuntu way') and uses the brand new Cairo Dock repository. The ***second method*** will be using the precompiled Debain packages. The ***third method*** will involve compiling from the latest development source. This means that you will be getting the latest (but possibly/sometimes unstable) version. It sounds more complicated than it is, because the difficult stuff is handled by a neat little script provided by one of the CD developers.

Do you want my suggestion? If you are curious, want the latest features, not afraid of possibly periodically running an unstable dock ánd you have the time, go for Method 3 straight away. Else go for Method 1... If you feel up to it, you can always try method 3 later (simply overwriting the first installation) to get the latest development version with all the shiny new features like the new plugins Stacks, Netspeed, Mailchecker, Switcher, Slider, CPUsage, Wifi and more...


[COLOR="DimGray"][FONT="Palatino Linotype"][SIZE="3"]METHOD 1, using the 64bit Debian packages[/SIZE][/FONT][/COLOR]

Short and sweet, the ***Ubuntu way***. The 64bit packages are provided by user paradoxxx_zero. > **paradoxxx_zero said:**
> 64bit repo is out !
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock


Add the official repositories to your sources list and install though your favourite package manager like apt-get or synaptic...

[INDENT]**1.** Do in terminal ```
wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -
``` and add the line **deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock** (replace *hardy* with *gutsy* or any other version if you have not moved to the latest and greatest yet) to your sources list either by [INDENT]**A.** Start the Software Sources Manager from the System menu and open the Third Party Software tab. Hit the Add... button and copy the line in the dialog. Hit Close and then Refresh to let the sources update. 
**B.** Edit the sources list manually with ```
sudo gedit /etc/apt/sources.list
``` (or use your favourite editor like vim, nano, mousepad or kate) and put the line at the bottom, then save and close. After that, do in terminal ```
sudo apt-get update
``` to refresh all sources.[/INDENT]

**2.** Then enter ```
sudo apt-get install cairo-dock cairo-dock-plug-ins
``` to get CD installed.

**3.** Try to fire up Cairo-Dock by giving the command ```
cairo-dock
``` in a terminal screen and see if cairo dock starts up with the first time Theme Manager dialog. If not, check for error messages in terminal and report them here.

**4.** If all works well and is configured to your liking, close the terminal again (CD closes too). Then make CD part of your daily working environment (starting up every session) by one of these methods
[INDENT]**A.** Hit the Alt+F2 keys and enter **cairo-dock** in the Run dialog. Now be sure to save your session upon the next logout/shutdown by checking the Save Session box in the Exit dialog.
**B.** If you do not like to save each session upon logout/shutdown, add a new entry with the command **cairo-dock** to the Sessions list (Ubuntu menu: System>Preferences>Sessions)[/INDENT] to make it start up at login... Choose one, or you will have two instances of CD running on top of each other.[/INDENT]


[COLOR="DimGray"][FONT="Palatino Linotype"][SIZE="3"]METHOD 2, using Debian packages[/SIZE][/FONT][/COLOR]

I recommend using the latest version of CD since 64bit is now supported, but you might want to use one of the older 32bit-only packages on your 64bit system. This is not a problem as long as all dependencies are taken care off manually, because Apt (the debian package manager) will not be able to do it for us. Lucky for us, there is user Cappy, who wrote the outstanding tool Getlibs for precisely this purpose!

[INDENT]**1.** Make sure you have met all prerequisites above.

**2.** Download the latest cairo-dock package files: You need *two* deb files, one called **cairo-dock_vX.X.X.X_i686.deb** and the other **cairo-dock-plug-ins_vX.X.X.X_i686.deb** (where the X's represent the latest version number, 1.5.0.1 at the time of writing this) from _[http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)_. Download them *both* to your home folder.

**3.** Open a terminal screen and run ```
sudo dpkg -i cairo-dock*.deb
``` or, if you have chosen one of the older 32bit versions, run ```
sudo dpkg -i --force-all cairo-dock*.deb
``` and follow with ```
getlibs /usr/bin/cairo-dock
``` (see help on usage of Getlibs on _[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)_)
```
for i in /usr/share/cairo-dock/plug-in/*.so; do echo "$i"; getlibs -b "$i"; done;
```

**4.** Try to fire up Cairo-Dock by giving the command ```
cairo-dock
``` in a terminal screen. If you installed an older 32bit version, see if there are any dependency errors left. If so, use the 'manual 32bit libs installation' described on the getlibs page above to get them: ```
getlibs -l full_library_name_here
```

**If no dependencies are left open, cairo-dock should run and present you it's first-time Theme Manager dialog. See chapter BASIC USAGE for help.**

**5.** If all works well and is configured to your liking, add a new entry with the command **cairo-dock** to the Sessions list (Ubuntu menu: System>Preferences>Sessions) to make it start up at login *OR* hit Alt+F2 and enter **cairo-dock** to make it start up without terminal and save your session upon the next logout/shutdown...[/INDENT]


[COLOR="DimGray"][FONT="Palatino Linotype"][SIZE="3"]METHOD 3, straight from SVN source[/SIZE][/FONT][/COLOR]

This method was reported to run successfully on a Hardy installation by user neymac:
> **neymac said:**
> I used the script cairo-dock_svn.sh from M@v (the author) and did follow the instructions from 

[http://www.cairo-dock.org/ww_page.php?p=From SVN&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From SVN&lang=en")

and got cairo-dock working compiled from SVN without major problems and quite stable until now.
When compiling it asked if I wanted "glitz", I said no because I was not shure if "glitz" would work on my system (8.04).

I have tested it on my machine and found the following procedure took quite some time but worked fine in the end. Giving me all the goodies that are under development straight away!

[INDENT]**1.** Make sure you have met all prerequisites above (most importantly 2, while 1 can be postponed until you are sure you will be keeping CD) 

**2.** We need a location to put the source files. Open a terminal window and use ```
mkdir ~/svn
mkdir ~/svn/cairo-dock
``` to make a new directory in your home folder. Here we will be downloading the source files later.

**3.** Now we want the prefab script that will be handling the download and compilation for us. Download it and make it executable by running the commands ```
cd ~/svn/cairo-dock
wget http://www.cairo-dock.org/cairo-dock_svn.sh
chmod u+x cairo-dock_svn.sh
``` (leave the terminal screen open)

**4.** Let the script do all the downloading and compilation for you by running in that same terminal screen ```
./cairo-dock_svn.sh
```
You will see that the script gives you dialog in French (this might change in newer versions), but that should not be a problem. We will be going through it step-by-step. Enter your password whenever needed so installation can continue.

The script will be doing the following on your system:

[INDENT]**A.** Check for and download the latest version of itself. If there is a new version, the script will close and want you to relaunch it. > Vérification de la disponibilité d'un nouveau script

[COLOR="Red"]Veuillez relancer le script, une mise à jour a été téléchargée[/COLOR] Just hit the UP arrow and Enter to do so... 

**B.** Check for, download from the Ubuntu repo's and install all debian packages that are needed for compiling cairo-dock from source. If needed, provide your password to continue the process. > [COLOR="SeaGreen"]Vous possédez la dernière version du script de M@v[/COLOR]
[COLOR="RoyalBlue"]
Détection de l'environnement graphique[/COLOR]
[COLOR="SeaGreen"]Votre environnement est GNOME[/COLOR]

[COLOR="RoyalBlue"]Vérification des paquets nécéssaires à la compilation[/COLOR] If you have not done anything like this before, it might take a while asking you for confirmation each time a bunch of packages are about to be installed. After this (possibly LOOOONG) process, it will report > [COLOR="SeaGreen"]Vérification OK[/COLOR] and continue with the next step.

**C.** Recompile the Cairo libraries with Glitz enabled if you want it to (warning: NOT advisable on slow/average systems, on systems with ATI graphics card nor on laptops.) > [COLOR="RoyalBlue"]Voulez-vous installer la librairie Cairo avec l'option GLITZ d'activée ?

Cette option permet une plus grande réactivité de votre dock en utilisant votre carte graphique et non votre processeur pour effectuer les calculs mais peut ralentir votre système ou occasionner des dysfonctionnements[/COLOR]
[COLOR="Red"]Attention ! Des erreurs semblent apparaitre avec les cartes ATI, notamment avec les chipsets de portable

Etes-vous sûr de vouloir effectuer cette opération ? (y/n)[/COLOR] This basically means that Cairo Dock can use an option called Glitz which could improve performance of CD. But it will be a major drag on the average or slower system and is best reserved for a speedy machine with newer graphics card. When on a system with an ATI card or on a laptop, be sure to NOT go for Cairo with Glitz enabled. Also, when in doubt about what to do here, just enter '[COLOR="Red"]n[/COLOR]' (for NO) and continue.

**D.** Download the latest Cairo Dock source files from SVN. > [COLOR="RoyalBlue"]C'est la première fois que vous installez le SVN de Cairo-Dock

Téléchargement des données. Ceci peut prendre quelques minutes

Téléchargement de cairo-dock[/COLOR]
... After which you will see a long list of file downloads being processed. Just be patient and let it run.

**E.** Compile/install Cairo Dock on your system. > [COLOR="RoyalBlue"]Checked out revision XXX.

Données téléchargées. L'installation va débuter
Cette opération peut prendre plusieurs minutes et ralentir votre système

Installation de cairo-dock[/COLOR] Enter your password again if it asks for it and wait for the first > [COLOR="SeaGreen"]Réalisé avec succès[/COLOR] Now sit back or just go and have some coffee or something because this might take a long time and make your system somewhat sluggish during the process.

**F.** If all goes well, you will see for each installed plugin that same success message. Like > [COLOR="RoyalBlue"]Installation du plug-in alsaMixer[/COLOR]

[COLOR="SeaGreen"]Réalisé avec succès[/COLOR] Finally closing with > Vérification de l'intégrité de l'installation

[COLOR="SeaGreen"]L'installation s'est terminée correctement.[/COLOR][/INDENT]

**5.** Try to fire up Cairo-Dock by giving the command ```
cairo-dock
``` in the same terminal screen and see if there are any dependency errors left. If so, install them manually using ```
sudo apt-get install full_package_name_here
``` If you do not know which packages you need, please post a message on this forum thread.

**If no dependencies are left open, cairo-dock should run and present you it's first-time Theme Manager dialog. See chapter BASIC USAGE for help.**

**6.** If all works well and is configured to your liking, add a new entry with the command **cairo-dock** to the Sessions list (Ubuntu menu: System>Preferences>Sessions) to make it start up at login...

[COLOR="Red"]TIP:[/COLOR] To keep CD updated to the latest version you need to re-run the script again from time to time. It will automatically check for a new revision and download/install it when needed. To make this as easy as possible, create a new launcher in CD that will initiate the command **gnome-terminal --working-directory=~/svn/cairo-dock/ -e "./cairo-dock_svn.sh"** (note: that command will not work when cairo dock itself is launched from terminal; change 'gnome-terminal' to 'terminal' for XFCE/Xubuntu or 'konsole' for KDE/Kubuntu). See chapter NOTES & TIPS point H for a small how-to.

[COLOR="Red"]TIP 2:[/COLOR] If there are problems after first time install or later after updating you can force the re-installation with **./cairo-dock_svn.sh --force-install**. Type **./cairo-dock_svn.sh --help** for more options (like ***uninstall***!)
[/INDENT]



[COLOR="DimGray"][FONT="Palatino Linotype"][SIZE="4"]POSSIBLE ERROR MESSAGES[/SIZE][/FONT][/COLOR]

**Installation**
If you run into any error messages during the installation process that are not related to unfulfilled dependencies (see step 4 above) please go to the [_Cairo Dock forum_]("http://developer.berlios.de/forum/?group_id=8724") for help. I am not involved with CD development and have not run into any installation errors myself. Sorry...

When ***method 3*** ends in the following message > Vérification de l'intégrité de l'installation
[COLOR="Red"]Des erreurs ont été détectés pendant l'installation mais il est impossible de les identifier. Veuillez consulter le fichier log.txt pour plus d'informations et vous rendre sur le forum de cairo-dock pour reporter l'erreur dans la section "Version SVN"[/COLOR] it means that there were errors during the process. This does not necessarily mean CD will not run. Just try with the command cairo-dock in terminal and see. If you run into serious problems with the dock, you can use the error output in the ~/svn/cairo-dock/log.txt file to get help on the [Cairo Dock help forum]("http://developer.berlios.de/forum/forum.php?forum_id=26288"). As soon as the problems are fixed in the new SVN version, you can force complete re-installation by pasting the following in terminal ```
cd ~/svn/cairo-dock
./cairo-dock_svn.sh --force-install
``` and going through all the steps again.

**Usage**
Not liking the systray module, you might find it won't be removed and make the dock close. For me, it turned out that only after changing some config options of that applet and using it a few times (making it capture the systray icons), I finally could remove the icon... Strange, èh?

For more advanced startup options (e.g. in case of problems) type **cairo-dock --help** in terminal. A few basic ones that might get you further are:
```
  -l, --log                 log verbosity (debug,message,warning,critical,error) default is warning
  -a, --keep-above          keep the dock above other windows whatever
  -p, --no-skip-pager       show the dock in pager
  -b, --no-skip-taskbar     show the dock in taskbar
  -t, --toolbar-hint        force the window manager to consider cairo-dock as a toolbar instead of a dock
  -n, --normal-hint         force the window manager to consider cairo-dock as a normal appli instead of a dock
  -m, --maintenance         allow to edit the config before the dock is started and show the config panel on start
  -f, --safe-mode           don't load any plug-ins and show the theme manager on start
```



[COLOR="DimGray"][FONT="Palatino Linotype"][SIZE="4"]BASIC USAGE[/SIZE][/FONT][/COLOR]

**1.** After successfully getting through the last step (4) and selecting a theme in the first-time theme manager dialog, Cairo Dock should be running and visible on your screen. If not, please retrace your steps and see if you skipped a part of the installation procedure. Are the prerequisites all fulfilled? And all dependencies? Open Nautilus (or your preferred system browser) and go to** /usr/bin/** and look for the file **cairo-dock**. Does it exist? Post questions on this thread or on the [_Cairo Dock forum_]("http://developer.berlios.de/forum/?group_id=8724").

**2.** Start configuring Cairo Dock by right-click anywhere on the dock (even an icon - it doesn't matter) and choosing from the menu **Cairo Dock>Manage themes**. In the theme manager, find a theme (see *Note C* below) that fist your taste and the rest of your Desktop -- might I suggest the EXCELLENT new **_MacOSX_** theme? 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=57160&stc=1&d=1200956562[/IMG]

**3.** Then via right click **Cairo Dock>Configure** you can start changing the *behavior* of the dock. If you feel up to it, click the button *'Do you want more?'* in the bottom left corner of the Configuration window to get more than the basic configuration options. 

**4.** To add your own program launchers (icons) to the dock, the easiest way is simply drag launchers from your current panel or dock to Cairo Dock. You can also use the right-click menu item **Add a launcher**. LOTS more info on configuring Cairo Dock you can find on _[https://help.ubuntu.com/community/CairoDock#head-034ba9c79b4f2cea6de5ad282f27e58890ad380d](https://help.ubuntu.com/community/CairoDock#head-034ba9c79b4f2cea6de5ad282f27e58890ad380d)_

**5.** If all works well and is configured to your liking, add a new entry with the command **cairo-dock** to the Sessions list (Ubuntu menu: System>Preferences>Sessions) to make it start up at login...



[COLOR="DimGray"][FONT="Palatino Linotype"][SIZE="4"]NOTES & TIPS[/SIZE][/FONT][/COLOR]

**A.** When you have reached a nice setup (theme, active plugins and behavior), it is best to** save it as a new theme**. Go to the Theme manager (right-click **Cairo Dock>Manage themes**) and select the tab Save. Here you can enter a new name and place check marks at all options, then hit Save. The saved setup will show in the themes list as a new entry.

**B.** Some themes might not play nicely. It might be related to the auto-hide feature, I am not sure. But if you find that after changing the theme and Cairo Dock doesn't show anymore, you have two options. The first 'friendly' one is to start cairo dock in safe mode by running the following in terminal ```
cairo-dock -f
``` If that does not get you out of trouble you can always reset CD the 'hard' way by deleting the directory /home/<YOUR_USER_NAME>/.cairo-dock/current_theme. Open a terminal screen and run ```
rm -R .cairo-dock/current_theme
```After that, running cairo-dock in terminal (or on new session startup, if you already placed cairo-dock in the session list) will invoke the theme manager and you can select your previously saved setup (see note B) or just another theme.

**C.** On my system, the new modules **shortcuts** (missing dependencies still or architecture issue?) and **X-gamma** (due to my ATI card / fglrx driver, I guess) do not work as they should. There are two different methods to remove an applet/module: 1. right click the icon and selecting the 'remove this module' option; 2. right-click anywhere on the dock and select 'Cairo Dock > Configure' and open the System tab (or the Applets tab if it shows) and uncheck  the modules under Applets. 

If a module/applet is giving so much trouble that you do not even get to open the Configuration screen, you can start CD in maintenance mode by giving the following command in terminal ```
cairo-dock -m
``` and config will open before the dock loads.

**D.** If you do not like/want (too high system load / performance drag) or are not able (using open ATI/NVidia drivers) to run Desktop Effects / Compiz Fusion, you can get basic eye-candy like transparency and shading following these steps:
[INDENT]**[COLOR="Red"]TIP:[/COLOR]** To get transparency (and window shading) without Desktop Effects and the additional system load that CompizFusion brings along, do the following. Get **xcompmgr** by entering in a terminal screen the command ```
sudo apt-get install xcompmgr
``` Then add a new entry to your start-up list containing the command **xcompmgr -c -f -n** so transparency will load on each login. Type **xcompmgr --help** for instructions on fine-tuning some basic settings and adapt the start-up command to your liking if need be. Easy! :)[/INDENT]

[B]E.[B] By default, Cairo Dock will be displayed 'always on top'. There is no setting in the config options to change this, because it is your window manager (Gnome, XFce) that is responsible for that. It treats CD as any other dock/panel: always on top.

If you would like CD to behave differently, you have several options.
[INDENT]1. Use the 'Auto-hide' feature in the config options of Cairo Dock;
2. Force your window manager to consider CD as something other than a regular dock/panel. Try and start cairo dock with **cairo-dock -n**one of these options and see if it gets the behaviour you are looking for:
```
  -p, --no-skip-pager       show the dock in pager
  -b, --no-skip-taskbar     show the dock in taskbar
  -s, --no-sticky           don't make the dock appear on all desktops
  -t, --toolbar-hint        force the window manager to consider cairo-dock as a toolbar instead of a dock
  -n, --normal-hint         force the window manager to consider cairo-dock as a normal appli instead of a dock
```[/INDENT]

**F.** If you have installed Cairo Dock using Method 3 (from SVN source), you can keep the dock easily up-to-date by adding a new update launcher to the dock.
[INDENT]1. Right click on any launcher on the dock (so not a plugin/module) and select "Add a launcher". 
2. Click the 'New' button at the bottom of the dialog window.
3. Enter in the new Modify Launcher window **Cairo Dock SVN update** (or anything you like) for Launcher's name, **gnome-terminal --working-directory=~/svn/cairo-dock/ -e "./cairo-dock_svn.sh"** (change 'gnome-terminal' to 'terminal' for XFCE/Xubuntu or 'konsole' for KDE/Kubuntu) for Command and **/usr/share/cairo-dock/cairo-dock.svg** for Image (or any better image you like).[/INDENT]
Test the launcher by clicking it (note: this will result in an error when CD itself has been launched from terminal but when launched from Session startup or Alt+F2 it should work). This should re-initiate the script which will check for a new version. Do this from time to time and you will have all the latest at your fingertips!



[COLOR="DimGray"][FONT="Palatino Linotype"][SIZE="4"]REMOVE CAIRO DOCK[/SIZE][/FONT][/COLOR]

You really do not like what you see? Wow... Well, okay, here you are then:

**Uninstalling from Method 1 & 2**
Remove the deb packages as you would remove any other. If you prefer, you can use your regular package manager like Synaptic (in Gnome and XFCE) and use the search feature with 'cairo-dock' and mark the two packages for uninstallation. Or you can simply enter in terminal ```
sudo apt-get remove cairo-dock
``` 

**Uninstalling from Method 3**
Just use the same script as you used during the installation process but this time with the --uninstall option.
```
cd ~/svn/cairo-dock
./cairo-dock_svn.sh --uninstall
```
Enter your password and Cairo Dock will be removed promptly.



[COLOR="DimGray"][FONT="Palatino Linotype"][SIZE="4"]REFERENCES[/SIZE][/FONT][/COLOR]

Cairo Dock:
- [http://www.cairo-dock.org/ww_page.php?lang=en](http://www.cairo-dock.org/ww_page.php?lang=en) (main website) and [http://www.cairo-dock.org/ww_page.php?p=From%20SVN&lang=en](http://www.cairo-dock.org/ww_page.php?p=From%20SVN&lang=en) (svn installation script) 
- [http://developer.berlios.de/projects/cairo-dock/](http://developer.berlios.de/projects/cairo-dock/) and [http://developer.berlios.de/forum/?group_id=8724](http://developer.berlios.de/forum/?group_id=8724) (english help forum)
- [http://ubuntuforums.org/showthread.php?t=302570](http://ubuntuforums.org/showthread.php?t=302570)
- [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)
Getlibs:
- [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)



**That's it!**


Please post your results (maybe with screen dump image of your dock?), improvement suggestions or questions about this how-to here. Questions, bug reports an feature requests for Cairo Dock, please do them on the main [_Cairo Dock Project pages_]("http://developer.berlios.de/forum/?group_id=8724") ...

--ravan

---

### Post by Cappy on 2007-11-14
You should change the apt-get line to ```
sudo apt-get install libcairo2 librsvg2-2 libglitz1 libglitz-glx1
```
(for the addition of the words "install" and "libglitz-glx1")
and then you won't need that line ```

sudo apt-get -f install
```
because all required libraries will have been installed from the sudo apt-get install already.

Also, you probably want to include what kind of errors/messages users might get when they run ```
cairo-dock
```
because that's going to be a common question.

---

### Post by RavanH on 2007-11-15
> **Cappy said:**
> You should change the apt-get line to ```
sudo apt-get install libcairo2 librsvg2-2 libglitz1 libglitz-glx1
```
(for the addition of the words "install" and "libglitz-glx1")
and then you won't need that line ```

sudo apt-get -f install
```
because all required libraries will have been installed from the sudo apt-get install already.

Also, you probably want to include what kind of errors/messages users might get when they run ```
cairo-dock
```
because that's going to be a common question.
Thanks Cappy, done that... only on the error messages, I cannot oblige. I am not involved in Cairo Dock development in any way and have no clue what errors might be encountered.

Using your excellent Getlibs, I did not run in to any :) So I will have to wait until others get error messages and then see what could be done... The current developer of CD, fabounet, cannot help here. He is strictly 32bit (ok, ok, his systems ;) ) and was not even aware that there exists '--force-architecture' for 64bit users.

Maybe some 64bit guru out there willing to take on CairoDock64 conversion/development?

---

### Post by tuwe on 2008-01-15
hi there,

the installation worked like a charm. the only issue i had was 

```
~$: sudo getlibs /usr/bin/cairo-dock
libGL is installed from video drivers, please install or reinstall your video drivers
```

i resolved this by placing a symbolic link into /usr/lib32:

```
cd /usr/lib32
sudo ln -s libGL.so.1.2 libGL.so.1
```

I'm on a Macbook Pro with Ati Graphics Card and Gutsy 64bit install.
Hope this helps.

---

### Post by montechristos on 2008-01-15
Thanks. It works. But i have no 3d view on cairo-dock.
Can somebody help me?

---

### Post by Cappy on 2008-01-15
I'll make getlibs create the correct link to the library if the file exists.

---

### Post by Mark76 on 2008-01-20
I managed to get cairo dock installed and working in mere minutes thanks to Ravan's clear and concise instructions :)

It rocks :guitar:

---

### Post by RavanH on 2008-01-21
> **montechristos said:**
> Thanks. It works. But i have no 3d view on cairo-dock.
Can somebody help me?

Have you selected the _MacOSX_ theme? And have you tried the tab **Views** under **Cairo Dock>Confgure**? You might have to hit the button 'Do you want more?' before that tab is shown in the config menu.

Please go to the [Cairo Dock forum]("http://developer.berlios.de/forum/?group_id=8724") for any questions on CD usage. It will help other CD users too if you take the extra time :)

---

### Post by montechristos on 2008-01-26
I have only the default view. No other choice

---

### Post by RavanH on 2008-01-28
> **montechristos said:**
> I have only the default view. No other choice

Sorry I cannot help with this. Only one thought: Did you install **2 packages** during the process? You need the cairo-dock*.deb file as well as the cairo-dock-plugins*.deb file... 

Anyway, in the Cairo Dock forums ( [http://developer.berlios.de/forum/?group_id=8724](http://developer.berlios.de/forum/?group_id=8724) ) you will receive excellent support (in english *and* french) on this -- I am sure :)

---

### Post by RavanH on 2008-01-28
> **montechristos said:**
> I have only the default view. No other choice

What do you see when you browse to /usr/share/cairo-dock/themes ? Only a folder called _default_ or more than that? If the latter, what are the permissions of those other folders?

---

### Post by romac on 2008-01-31
well the themes are all there, and easily switched between, but what he's talking about is the 'view' tab where there's normally 3 options i think - 'default'   '2d'  and  '3d'  the only one listed there is _default_

i've had this happen to me on two occasions and under 2 different OS installs

the first time i reinstalled cairo dock after completely removing it a couple times - tried deleting the config file, and nothing would work - then one day i just looked at the 'view' tab on a whim and the 3d option was there again

this just happened to me again today in a completely different OS install (32 bit vs 64) and a completely new cairo install.   What happened this time was i was playing a fps game (cube-sauerbraten) that crashed and then froze my system  so i hit the restart button on the front of my case rather than use the normal ubuntu 'restart'.  When my system came back up my dock was 2d and the option for 3d is gone from the dropdown under the 'view' tab.

i can still play the game in 3d, and all my 3d desktop effects work so far as i can tell.

i want my sexy cairo reflections back!  :(

---

### Post by RavanH on 2008-02-02
montechristos & romac, this really sounds like something to be discussed on the Cairo Dock forums... there, you *and* others will benefit from the solution that will be found. 

Please take the time to register and submit a forum post about this issue on [http://developer.berlios.de/forum/?group_id=8724](http://developer.berlios.de/forum/?group_id=8724) and help improve Cairo Dock :)

Thanks!

---

### Post by rune0077 on 2008-02-03
Hey, thanks a bunch for this. Instructions where easy to follow, install went smoothly and the dock runs like a charm.

One question: how do the file-manager plugin work? It seems to be working (I can enable/disable it and configure it), but nothing shows up in the dock. I really need to have my folders accessible through the dock before I'll use this over AWN, so if you (or anyone) knows how this works, help would be much appreciated.

---

### Post by RavanH on 2008-02-04
> **rune0077 said:**
> One question: how do the file-manager plugin work? It seems to be working (I can enable/disable it and configure it), but nothing shows up in the dock. I really need to have my folders accessible through the dock before I'll use this over AWN, so if you (or anyone) knows how this works, help would be much appreciated.

I was wondering about that applet too a while back so I posted a question on the CD forum and got a very short reply: [https://developer.berlios.de/forum/message.php?msg_id=41495](https://developer.berlios.de/forum/message.php?msg_id=41495)

Might be all too obvious for 32bit users but not really working for 64bit? Not sure...

I reposted the question so maybe we get a full answer now ;)

---

### Post by NilsHG on 2008-02-04
thanks for the howto. cairo-dock installed fine. however it does not run well. it is somewhat unresponsive, the animations lagg and it uses over 40% of both cores of my cpu. (pentium dualcore @3GHZ).

for some reason i am not (yet) able to center the dock on my screen. it is attached to the right corner on the bottom of the screen. but thats probably just a matter of configuration.
*edit* i fixed the location of the dock! from what i understood from the french cairo-dock website you have to press and hold ctrl key and then click and drag the doch to where you want it. */edit*

however, if i cannot fix the high cpu usage and the laggs the dock is pretty much unusable. eyecandy that looks like you are running a p2 333 mhz machine :(

---

### Post by RavanH on 2008-02-04
> **romac said:**
> well the themes are all there, and easily switched between, but what he's talking about is the 'view' tab where there's normally 3 options i think - 'default'   '2d'  and  '3d'  the only one listed there is _default_

i've had this happen to me on two occasions and under 2 different OS installs

the first time i reinstalled cairo dock after completely removing it a couple times - tried deleting the config file, and nothing would work - then one day i just looked at the 'view' tab on a whim and the 3d option was there again

this just happened to me again today in a completely different OS install (32 bit vs 64) and a completely new cairo install.   What happened this time was i was playing a fps game (cube-sauerbraten) that crashed and then froze my system  so i hit the restart button on the front of my case rather than use the normal ubuntu 'restart'.  When my system came back up my dock was 2d and the option for 3d is gone from the dropdown under the 'view' tab.

i can still play the game in 3d, and all my 3d desktop effects work so far as i can tell.

i want my sexy cairo reflections back!  :(

> **montechristos said:**
> Thanks. It works. But i have no 3d view on cairo-dock.
Can somebody help me?

A thought: Did you guys have the applet called **'rendering'** turned on? It seems to have something to do with the 3D views...

---

### Post by rune0077 on 2008-02-04
> **RavanH said:**
> I was wondering about that applet too a while back so I posted a question on the CD forum and got a very short reply: [https://developer.berlios.de/forum/message.php?msg_id=41495](https://developer.berlios.de/forum/message.php?msg_id=41495)

Might be all too obvious for 32bit users but not really working for 64bit? Not sure...

I reposted the question so maybe we get a full answer now ;)

Yeah, I saw your original question on the forum, but the answer didn't seem to offer me any solution. Let's hope the second time around will yield some information, and drop us a line if it does.

---

### Post by fatbuttlarry on 2008-02-04
If you skip the first step you might get:
```
cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory
```

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Unfortunately, after getting "getlibs", it hangs on that command.

So I tried to register the .so's manually:
```
getlibs -l libglitz-glx.so.1(works)
getlibs -l libXcomposite.so.1(hangs!!!!)
```

I'm stuck!



-Tres

---

### Post by Cappy on 2008-02-05
Sounds like it couldn't contact the packages web interface for some reason.

Another way is to use the package name ```
getlibs -p libxcomposite1
```

---

### Post by cwgannon on 2008-02-05
Thank you very much, RavanH.  I was able to get this up and running in no time.

There are a few aspects of AWN I liked a bit more, but the extra configuration options of Cairo Dock have won me over.  (I mean, for instance,, AWN needs to get with the program and let us put a dock at the top, something which Cairo Dock allows.)

---

### Post by ahuman on 2008-02-25
[CENTER][COLOR="Green"][FONT="Palatino Linotype"][SIZE="4"]Would any of you be patient enough to please help me & others who don't quite understand exactly how to install the Cario Dock on our computers. In my case, I'm using a Dell Inspiron 531s which is installed with Ubuntu 7.10 (Gusty Gibbons) it has a built-in NVidia video card (drivers included) and it's running on the AMD64 (64Bits) system?

I'll start by highlighting the problems I've been having with the installation-instructions (which I have listed 1-7):

Instruction #1:[/SIZE][/FONT][/COLOR][/CENTER]
**1.** Your system should be capable of and **running Desktop Effects**. Without it, Cairo Dock works but doesn't look as good as it can (no transparency for instance). If you have a NVidea or ATI graphics card, you might have to take a few more steps to get at this point. There are a lot of threads and How-to's on that on these forums. For good instructions on installing the latest ATI drivers using AIGLX on *Gutsy*, see _[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually)_.

[COLOR="DarkBlue"][FONT="Palatino Linotype"][SIZE="4"]Problem 1: I don't know if I need the AIGLX thing. Would you tell me if the NVidia video card needs to be using AIGLX (to make the Cario Dock appear transparent for instance)?[/SIZE][/FONT][/COLOR]

[SIZE="4"][COLOR="Green"][CENTER][FONT="Palatino Linotype"]Instruction #2:[/SIZE][/FONT][/COLOR][/CENTER]
**2.** Also, the **Cairo libraries** should be installed. It is not called Cairo Dock for nothing ;)
```
sudo apt-get install libcairo2 librsvg2-2 libglitz1 libglitz-glx1 dbus libdbus-1-3 libdbus-glib-1-2 libvte9 libxxf86vm1
```
NOTE: Since version 1.5.0.1, there are separate dependencies for the Cairo Dock Plug-ins package. The above command should take care of those dependencies...

[COLOR="Green"][FONT="Palatino Linotype"][SIZE="4"]*No Problem:* Those instructions made perfect sense to me, and that code seemed to work.:[/SIZE][/FONT][/COLOR]

[SIZE="4"][COLOR="Green"][CENTER][FONT="Palatino Linotype"]Instruction #3:[/SIZE][/FONT][/COLOR][/CENTER]
**3.** You will need to have the excellent 32bit library dependency tool that should be on EVERY 64bit system called **Getlibs** installed on your system. If you did not do so already, follow instructions on _[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)_.

[COLOR="DarkBlue"][FONT="Palatino Linotype"][SIZE="4"]Problem 2: I don't know if all of the instructions on that [forum-thread](http://ubuntuforums.org/showthread.php?t=474790) are necessary to follow, in my case. Would you tell me which of those examples on that [webpage](http://ubuntuforums.org/showthread.php?t=474790) are necessary to follow, in order to make the Cario Dock work on my computer?[/SIZE][/FONT][/COLOR]

[SIZE="4"][COLOR="Green"][CENTER][FONT="Palatino Linotype"]Instruction #4:[/SIZE][/FONT][/COLOR][/CENTER]
**4.** Download the latest cairo-dock 32bit deb files.

[COLOR="Green"][FONT="Palatino Linotype"][SIZE="4"]*No Problem:* I went to the previously mentioned [webpage](http://developer.berlios.de/project/showfiles.php?group_id=8724), and downloaded all 4 of those files:

Here's a screenshot from the files I found on that  [webpage](http://developer.berlios.de/project/showfiles.php?group_id=8724):
[IMG]http://img141.imageshack.us/img141/4687/0wenttoberliosdeveloperer1.png[/IMG]

I successfully installed those 2 .deb-files: cairo-dock-plug-ins_v1.5.1_i686-32bits.deb &  cairo-dock_v1.5.1_i686-32bits.deb (as seen in the 2 following screenshots):
[img]http://img84.imageshack.us/img84/377/2gdebigtkunstalledpart3gn5.png[/img]

[img]http://img206.imageshack.us/img206/7/4installedcariodockplugtr7.png[/img][/SIZE][/FONT][/COLOR]

[SIZE="4"][COLOR="Green"][CENTER][FONT="Palatino Linotype"]Instruction #5:[/SIZE][/FONT][/COLOR][/CENTER]
**5.**...You need two deb files, one called **cairo-dock_vX.X.X.X_i686-32bits.deb** and the other **cairo-dock-plug-ins_vX.X.X.X_i686-32bits.deb** (where the X's represent the latest version number, 1.5.0.1 at the time of writing this) from _[http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)_ to your home folder.

[COLOR="DarkBlue"][FONT="Palatino Linotype"][SIZE="4"]Problem 3: I don't know exactly what this part of instruction #5 means: "...from _[http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)_ to your home folder."

Two questions about *problem 3*:
 Would any of you please tell what that means?To get the *Cairo Dock* to install correctly, would I have to drag & drop those .deb files to my home folder or "Extract" them in that same folder?

Problem 4: I don't know what to do with cairo-dock-sources-20080219.tar.bz2. 

One question about *problem 4*:
Please give me step-by-step instructions about what I should do with this package/file: cairo-dock-sources-20080219.tar.bz2[/SIZE][/FONT][/COLOR]

[SIZE="4"][COLOR="Green"][CENTER][FONT="Palatino Linotype"]Instruction #6:[/SIZE][/FONT][/COLOR][/CENTER]
**6.** Open a terminal screen and run
```
sudo dpkg -i --force-all cairo-dock*.deb
```
```
sudo getlibs /usr/bin/cairo-dock
``` (see prerequisite 3 above if this results in an error)

[COLOR="DarkBlue"][FONT="Palatino Linotype"][SIZE="4"]I haven't tried any of those commands  in instruction #7, yet, but I will do so, after problem 1-3 are solved. Please help me.[/SIZE][/FONT][/COLOR]

[SIZE="4"][COLOR="Green"][CENTER][FONT="Palatino Linotype"]Instruction #7:[/SIZE][/FONT][/COLOR][/CENTER]
**7.** Try to fire up Cairo-Dock by giving the command ```
cairo-dock
``` in the same terminal screen and see if there are any dependency errors left. If so, use the 'manual 32bit libs installation' described on the getlibs page above to get them. **If no dependencies are left open, cairo-dock should run and present you it's first-time theme manager dialog**.

[COLOR="DarkBlue"][FONT="Palatino Linotype"][SIZE="4"]Like I mentioned before, I haven't tried any of those commands in instruction #7, yet, but I will do so, after problem 1-4 are solved.  I'd appreciate any future-help given to me, in this case.[/SIZE][/FONT][/COLOR]

---

### Post by ahuman on 2008-02-25
[SIZE="4"][FONT="Georgia"][COLOR="Purple"]My problems #1-3 were solved. I've installed all of the package/files (and libraries) that were mentioned in instructions #1-7, except for this package/file: cairo-dock-sources-20080219.tar.bz2.

I still need help solving this problem:
I don't know what to do with cairo-dock-sources-20080219.tar.bz2.

Please give me step-by-step instructions about what I should do with this package/file: cairo-dock-sources-20080219.tar.bz2[/COLOR][/FONT][/SIZE]

---

### Post by rune0077 on 2008-02-25
> **ahuman said:**
> [SIZE="4"][FONT="Georgia"][COLOR="Purple"]My problems #1-3 were solved. I've installed all of the package/files (and libraries) that were mentioned in instructions #1-7, except for this package/file: cairo-dock-sources-20080219.tar.bz2.

I still need help solving this problem:
I don't know what to do with cairo-dock-sources-20080219.tar.bz2.

Please give me step-by-step instructions about what I should do with this package/file: cairo-dock-sources-20080219.tar.bz2[/COLOR][/FONT][/SIZE]

You don't need the sources. You only need the two deb packages (the dock and the plugins). The source is only if you want to install the thing manually. Just get the two debs, then install the dock-deb through a terminal, using the command from the instructions.

---

### Post by rickrob on 2008-02-28
Cairo-dock only opens threw terminal and once i close the terminal cairo disapears.Cannot find on my desktop either.

---

### Post by Mark76 on 2008-02-28
Add it to your autostarted applications (the command is cairo-dock)

---

### Post by rickrob on 2008-02-28
Thanks for the reply but i keep geting this in the terminal when i start up cairo-dock in the terminel

---

### Post by Mark76 on 2008-02-28
Did you try what I suggested?

Note: If you're using Ubuntu it's under System/Preferences/Sessions.  I've no idea what autostarted applications is listed under in KUbuntu

---

### Post by sanga_sanga on 2008-03-01
Thanks RavanH for the detailed Instructions. Cairo Dock is awesome! :)

i couldnt get awn to work (thank g*d for that), now i wouldnt want to replace cairo with anything else. :twisted

---

### Post by KhaaL on 2008-03-01
> **Mark76 said:**
> Did you try what I suggested?

Note: If you're using Ubuntu it's under System/Preferences/Sessions.  I've no idea what autostarted applications is listed under in KUbuntu

By placing links under ~/.kde/Autostart you'll have things autostarted.

On a diffrent issue, I just followed the instructions here and the icons for the settings etc. are missing for my cairo dock (for instance, the menu when you right click to configure it has missing icons and so does the configure panel). Anyone have an idea what package I might be missing?

---

### Post by RavanH on 2008-03-03
> **KhaaL said:**
> On a diffrent issue, I just followed the instructions here and the icons for the settings etc. are missing for my cairo dock (for instance, the menu when you right click to configure it has missing icons and so does the configure panel). Anyone have an idea what package I might be missing?

I noticed that the icons in the right-click (context) menu change when the User Interface Theme is changed. Could you try to switch to another user interface theme to see what happens? No idea how thatis done in KDE though...

---

### Post by RavanH on 2008-03-03
> **rickrob said:**
> Thanks for the reply but i keep geting this in the terminal when i start up cairo-dock in the terminel

I get the same weather plugin error in the latest version (when running from terminal) but it seems the plugin itself works fine :)

Maybe you can post a question about it on the Cairo Dock  developers forum? Seems the plugin is looking for something in the wrong location -- ../trunk/.. suggest a development location

---

### Post by Leech333 on 2008-03-07
Hi there!

has anyone the same problem as I always have? cairo-dock disappears once SHOW THE DESKTOP is pressed . it is still alive as a process but doesn't appear on desktop anymore.
Ubuntu 7.10 64bit, AutoHide option enabled

:confused:

---

### Post by RavanH on 2008-03-07
> **Leech333 said:**
> Hi there!

has anyone the same problem as I always have? cairo-dock disappears once SHOW THE DESKTOP is pressed . it is still alive as a process but doesn't appear on desktop anymore.
Ubuntu 7.10 64bit, AutoHide option enabled

:confused:
You mean the Show desktop button in your regular panel? No, that does not happen with my dock, also with autohide enabled... What happens if you switch autohide off?

---

### Post by Leech333 on 2008-03-08
> **RavanH said:**
> You mean the Show desktop button in your regular panel? No, that does not happen with my dock, also with autohide enabled... What happens if you switch autohide off?

Yes, this button.
moreover, cairo-dock disappears when I switch programs through the regular panel (both cairo and panel are on the buttom of desktop).
it works fine when autohide disabled since cairo is on top of the panel so I cant switch windows.  :(

---

### Post by RavanH on 2008-03-08
> **Leech333 said:**
> Yes, this button.
moreover, cairo-dock disappears when I switch programs through the regular panel (both cairo and panel are on the buttom of desktop).
it works fine when autohide disabled since cairo is on top of the panel so I cant switch windows.  :(

OK, I normally have the dock at the bottom and one regular panel at the top... Testing your setup with both at the bottom -- pressing the desktop button, did indeed result in cairo dock not coming out off autohide anymore. My guess this is because when clicking anywhere on the regular panel, it is immediately placed in front of the activation zone that should make cairo dock pop up... 

This theory is supported by the fact that when cairo dock does not seem to 'come out' anymore and I move the regular panel to  the top (or any other position), cairo-dock will react upon mouse movement at the bottom of the screen -- the area which is called the "Call-Back Zone" in cairo dock config.

Several options to work around this spring to mind:
1. Move either the panel or the dock to another position (cairo dock position can be managed in config)
2. I remember there used to be a setting to make cairo dock stay 'always on top' but cannot seem to find it in the current version, if you find it, it might make a difference
3. Report this problem on the Cairo Dock forum on [http://developer.berlios.de/forum/?group_id=8724](http://developer.berlios.de/forum/?group_id=8724) and ask that the Call-Back zone should be 'always on top' ...

---

### Post by Leech333 on 2008-03-09
> **RavanH said:**
> 
Several options to work around this spring to mind:
1. Move either the panel or the dock to another position (cairo dock position can be managed in config)
2. I remember there used to be a setting to make cairo dock stay 'always on top' but cannot seem to find it in the current version, if you find it, it might make a difference
3. Report this problem on the Cairo Dock forum on [http://developer.berlios.de/forum/?group_id=8724](http://developer.berlios.de/forum/?group_id=8724) and ask that the Call-Back zone should be 'always on top' ...

can not find 'always on top' also.
anyway, thank you for the suggestions. hope developer's forum will help me. guess I'm not alone in such problem.

---

### Post by rune0077 on 2008-03-09
> **Leech333 said:**
> can not find 'always on top' also.
anyway, thank you for the suggestions. hope developer's forum will help me. guess I'm not alone in such problem.

Hey, try launching Cairo-dock with this command:

```
cairo-dock -a
```

This should ensure that cairo-dock always stays on top of other windows (like the "always on top" command).

---

### Post by Leech333 on 2008-03-10
> **rune0077 said:**
> Hey, try launching Cairo-dock with this command:

```
cairo-dock -a
```

This should ensure that cairo-dock always stays on top of other windows (like the "always on top" command).

Thanks a lot!!! it realy solves the problem!!!! :guitar:

---

### Post by timbellomo on 2008-03-21
The dock runs for me, but some icons of the UI are missing (small x's).  On executing "cairo-dock", I get the error:
```
/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

```

And upon accessing the menus, I get a whole host of errors like this:

```
Error loading theme icon 'gtk-missing-image' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
```

I am running Hardy beta.  I downloaded the i386 gtk-2.0 libs and put them in /usr/lib32/ but cairo-dock is still looking for them in /usr/lib/.

Any ideas?

---

### Post by Cappy on 2008-03-21
Your problem with Hardy is filed here:
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/162993](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/162993)
and
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/202448](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/202448)

The only solutions it mentions are downgrading ia32-libs or moving/removing the 64-bit gtk

---

### Post by RavanH on 2008-03-22
Cappy,

So you are saying that Cairo Dock does not work on Hardy at this point? And it is a bug in GTK 2.2 but downgrading to 2.1 should work? 

Thanks for the tip :)

---

### Post by Huss on 2008-04-01
Great.

It worked for me.

It's better than the Ubuntu supported AWN

Thank you!

---

### Post by Cappy on 2008-04-01
> **RavanH said:**
> Cappy,

So you are saying that Cairo Dock does not work on Hardy at this point? And it is a bug in GTK 2.2 but downgrading to 2.1 should work? 

Thanks for the tip :)

Right, Hardy users have to downgrade ia32-libs from 2.2 to 2.1

---

### Post by RavanH on 2008-04-06
> **Cappy said:**
> Right, Hardy users have to downgrade ia32-libs from 2.2 to 2.1

Ok, made a note about it in the How-to... Thanks again :)

---

### Post by Cappy on 2008-04-06
> **RavanH said:**
> Ok, made a note about it in the How-to... Thanks again :)

Found a better solution:
[http://ubuntuforums.org/showpost.php?p=4660832&postcount=7](http://ubuntuforums.org/showpost.php?p=4660832&postcount=7)

---

### Post by RavanH on 2008-04-06
> **Cappy said:**
> Found a better solution:
[http://ubuntuforums.org/showpost.php?p=4660832&postcount=7](http://ubuntuforums.org/showpost.php?p=4660832&postcount=7)

Excellent!

---

### Post by Keith_Beef on 2008-04-14
Congratulations, Ravan, on writing a pretty good cookbook method on getting this to work.

For me, it almost works... but I get an irritating message when I try to start cairo-dock:
```

$ cairo-dock
cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory
$ ls -al /usr/lib | grep glitz
lrwxrwxrwx   1 root root       21 2008-04-14 21:22 libglitz-glx.so.1 -> libglitz-glx.so.1.0.0
-rw-r--r--   1 root root    25704 2006-07-10 14:27 libglitz-glx.so.1.0.0
lrwxrwxrwx   1 root root       17 2008-04-14 21:22 libglitz.so.1 -> libglitz.so.1.0.0
-rw-r--r--   1 root root   170800 2006-07-10 14:27 libglitz.so.1.0.0
```

So if the libraries are there, What's that message mean?


K.

---

### Post by RavanH on 2008-04-15
> **Keith_Beef said:**
> Congratulations, Ravan, on writing a pretty good cookbook method on getting this to work.

For me, it almost works... but I get an irritating message when I try to start cairo-dock:
```

$ cairo-dock
cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory
$ ls -al /usr/lib | grep glitz
lrwxrwxrwx   1 root root       21 2008-04-14 21:22 libglitz-glx.so.1 -> libglitz-glx.so.1.0.0
-rw-r--r--   1 root root    25704 2006-07-10 14:27 libglitz-glx.so.1.0.0
lrwxrwxrwx   1 root root       17 2008-04-14 21:22 libglitz.so.1 -> libglitz.so.1.0.0
-rw-r--r--   1 root root   170800 2006-07-10 14:27 libglitz.so.1.0.0
```

So if the libraries are there, What's that message mean?


K.

Guessing here: To me it sounds like the 32bit lib versions are not installed properly... Does ```
sudo getlibs /usr/bin/cairo-dock
``` return nothing anymore? 

Earlier in this thread there is a similar issue [http://ubuntuforums.org/showthread.php?p=4271167#post4271167](http://ubuntuforums.org/showthread.php?p=4271167#post4271167) followed by Cappy suggesting to install the libs manually using **getlibs -p ... **.

--ravan

---

### Post by t4ggs on 2008-04-15
hi 
i have a question, when i put a windows ovet the dock, the dock is still over the window, and i want it to be under and just when i move the mouse to the dock it will come to the front

any idea how do i do that?
and i still want it to be shown on top of the desktop

---

### Post by RavanH on 2008-04-15
> **t4ggs said:**
> hi 
i have a question, when i put a windows ovet the dock, the dock is still over the window, and i want it to be under and just when i move the mouse to the dock it will come to the front

any idea how do i do that?
and i still want it to be shown on top of the desktop

The main dev, fabounet, suggested on the Cairo Dock forums to use the option **--normal-hint** when starting the dock. This should prevent your window-manager (Gnome?) to treat cairo-dock as a dock. You see, It is the window manager that makes Cairo Dock stay 'in front' of other windows like any other dock. 

Only I think with this option it will stay on the desktop and never come to the front. So maybe you want to be using the autohide feature? Although it is not exactly what you are asking, it might fill your needs... Look for the option 'Activate autohide?' in the Cairo Dock settings on the Position tab.

Hope it works for ya :)

---

### Post by Keith_Beef on 2008-04-15
> **RavanH said:**
> Guessing here: To me it sounds like the 32bit lib versions are not installed properly... Does ```
sudo getlibs /usr/bin/cairo-dock
``` return nothing anymore? 

Earlier in this thread there is a similar issue [http://ubuntuforums.org/showthread.php?p=4271167#post4271167](http://ubuntuforums.org/showthread.php?p=4271167#post4271167) followed by Cappy suggesting to install the libs manually using **getlibs -p ... **.

--ravan

Excellent. That worked a treat.

---

### Post by IanW on 2008-04-16
Already answered above. Ignore this.

---

### Post by Neilguy on 2008-04-18
Great instructions, simple tutorial. Thanks a lot. Was looking for instructions to install Cairo-Dock on my AMD 64 laptop. None were as simple as these. You rock :guitar: (and Cairo-Dock too)

---

### Post by martin saint martin on 2008-04-19
cairo-dock rules!  flawless install thank!  only one problem though, i'm having trouble doing a drag/drop into the trash/dustbin.  i figured out how to get to open the trash(like the default trash on the gnome-panel) but i can't figure out how to enable a drag/drop into the trash bin on the dock.

---

### Post by josel777 on 2008-04-22
Great tutorial! Is there a way to set it up so that only icons show up with a 
transparent background? Right now I have a black rectangular box behind the icons.

---

### Post by josel777 on 2008-04-22
It was working fine yesterday, but today I am getting the following:

warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:251)  
  Attention : Attention : while opening module '/usr/share/cairo-dock/plug-in/libcd-gnome-integration.so' : (libgnomeui-2.so.0: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:251)  
  Attention : Attention : while opening module '/usr/share/cairo-dock/plug-in/libcd-terminal.so' : (libvte.so.9: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:251)  
  Attention : Attention : while opening module '/usr/share/cairo-dock/plug-in/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:288)  
  Attention : Failed to open file 'ccsm': No such file or directory


Any suggestions? I am running V1.5.4.2

---

### Post by martin saint martin on 2008-04-23
i think that i may have stumbled upon a bug.  the dock will disappear from the desktop.  i have auto-hide off, i like having the dock there at all times.  to get it back, all i have to do is: applications->system tools->cairo dock and it comes back right away, but i would prefer that i wouldn't have to do that(it defeats the reason for having a dock).  i don't know exactly all the ways to make it disappear but i've noticed that if i do a check updates the dock the terminal will open then after a few seconds close and the same time the dock will remove itself.  is anyone else having this problem?  if so share your story so we all maybe able to learn from each other. if this is a bug, how would i report it to those who should/need know about it?

---

### Post by IanW on 2008-04-23
> **josel777 said:**
> Great tutorial! Is there a way to set it up so that only icons show up with a 
transparent background? Right now I have a black rectangular box behind the icons.

You either need Compiz running, or you can```
sudo aptitude install xcompmgr
```

---

### Post by Cappy on 2008-04-23
> **josel777 said:**
> It was working fine yesterday, but today I am getting the following:

warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:251)  
  Attention : Attention : while opening module '/usr/share/cairo-dock/plug-in/libcd-gnome-integration.so' : (libgnomeui-2.so.0: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:251)  
  Attention : Attention : while opening module '/usr/share/cairo-dock/plug-in/libcd-terminal.so' : (libvte.so.9: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:251)  
  Attention : Attention : while opening module '/usr/share/cairo-dock/plug-in/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:288)  
  Attention : Failed to open file 'ccsm': No such file or directory


Any suggestions? I am running V1.5.4.2

Try ```
getlibs -l libgnomeui-2.so.0 libvte.so.9 libthunar-vfs-1.so.2
```

---

### Post by josel777 on 2008-04-24
I am now getting the following:

Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libfile.so' (/usr/lib/gnome-vfs-2.0/modules/libfile.so: wrong ELF class: ELFCLASS64)
Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libfile.so' (/usr/lib/gnome-vfs-2.0/modules/libfile.so: wrong ELF class: ELFCLASS64)
Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libfile.so' (/usr/lib/gnome-vfs-2.0/modules/libfile.so: wrong ELF class: ELFCLASS64)
Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libfile.so' (/usr/lib/gnome-vfs-2.0/modules/libfile.so: wrong ELF class: ELFCLASS64)
file gnome-vfs-cancellable-ops.c: line 309 (gnome_vfs_find_directory_cancellable): assertion failed: (near_uri != NULL)
Aborted (core dumped)


This is after I installed V1.5.5.1.

---

### Post by josel777 on 2008-04-24
Bump

---

### Post by Cappy on 2008-04-25
```
getlibs -p libgnomevfs2-0
```

---

### Post by josel777 on 2008-04-25
Tried code:
getlibs -p libgnomevfs2-0

But I'm still getting the message below.

Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libfile.so' (/usr/lib/gnome-vfs-2.0/modules/libfile.so: wrong ELF class: ELFCLASS64)
Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libfile.so' (/usr/lib/gnome-vfs-2.0/modules/libfile.so: wrong ELF class: ELFCLASS64)
Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libfile.so' (/usr/lib/gnome-vfs-2.0/modules/libfile.so: wrong ELF class: ELFCLASS64)
Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libfile.so' (/usr/lib/gnome-vfs-2.0/modules/libfile.so: wrong ELF class: ELFCLASS64)
file gnome-vfs-cancellable-ops.c: line 309 (gnome_vfs_find_directory_cancellable): assertion failed: (near_uri != NULL)
Aborted (core dumped)

---

### Post by oviciadao on 2008-04-30
Hi, I'm new in Ubuntu and don't get a lot of things quite well

The solution found here seems to be related to vmware. I don't understand how it will apply in Cairo Dock.
Could someone help me trough this? Step by step, please...

Thanks

---

### Post by RavanH on 2008-05-02
> **oviciadao said:**
> Hi, I'm new in Ubuntu and don't get a lot of things quite well

The solution found here seems to be related to vmware. I don't understand how it will apply in Cairo Dock.
Could someone help me trough this? Step by step, please...

Thanks
What solution? Are you having trouble with Cairo Dock? Or with this step-by-step 'how to install it on AMD64' ? 

Please explain.

---

### Post by RavanH on 2008-05-02
> **josel777 said:**
> Tried code:
getlibs -p libgnomevfs2-0

But I'm still getting the message below.

Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libfile.so' (/usr/lib/gnome-vfs-2.0/modules/libfile.so: wrong ELF class: ELFCLASS64)
Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libfile.so' (/usr/lib/gnome-vfs-2.0/modules/libfile.so: wrong ELF class: ELFCLASS64)
Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libfile.so' (/usr/lib/gnome-vfs-2.0/modules/libfile.so: wrong ELF class: ELFCLASS64)
Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libfile.so' (/usr/lib/gnome-vfs-2.0/modules/libfile.so: wrong ELF class: ELFCLASS64)
file gnome-vfs-cancellable-ops.c: line 309 (gnome_vfs_find_directory_cancellable): assertion failed: (near_uri != NULL)
Aborted (core dumped)

Did you ask in the Help forum over at [http://developer.berlios.de/forum/?group_id=8724](http://developer.berlios.de/forum/?group_id=8724) already? The tech dev of CD might be able to shed some light on this. 

I can only guess it has to do with the Shortcuts Applet and you might be able to switch it off by removing your selected theme by ```
rm -R .cairo-dock/current_theme
``` and then (after starting cairo-dock once more) selecting another simpler theme. Be sure to place check-marks at 'Use new theme's behavior' and 'Use new theme's launchers' and see what happens...

---

### Post by RavanH on 2008-05-02
> **Neilguy said:**
> Great instructions, simple tutorial. Thanks a lot. Was looking for instructions to install Cairo-Dock on my AMD 64 laptop. None were as simple as these. You rock :guitar: (and Cairo-Dock too)

Hey, thanks man :)

---

### Post by oviciadao on 2008-05-02
> **Cappy said:**
> Found a better solution:
[http://ubuntuforums.org/showpost.php?p=4660832&postcount=7](http://ubuntuforums.org/showpost.php?p=4660832&postcount=7)

Sorry, that's the solution I was talking about. It seems to be about vmware, what is it? How do I apply it for Cairo installation? Should I do it before or after install Cairo? 

I'm very newby.

I have hardy heron, the amd64 version.

Thanks

---

### Post by RavanH on 2008-05-04
> **oviciadao said:**
> Sorry, that's the solution I was talking about. It seems to be about vmware, what is it? How do I apply it for Cairo installation? Should I do it before or after install Cairo? 

I'm very newby.

I have hardy heron, the amd64 version.

Thanks
OK, I see... Well, I have just installed Hardy and Cairo-Dock without that solution and it seems to work fine. Only I am missing some of the newer plugins like the mail notifier (and i had just gotten used to it :( ) but hey, "don't try 'n fix what ain't broke (much)" ;)

Is cairo-dock not working for you on hardy?

---

### Post by Cappy on 2008-05-04
> **RavanH said:**
> OK, I see... Well, I have just installed Hardy and Cairo-Dock without that solution and it seems to work fine. 

It was fixed in Hardy before the final release.

---

### Post by oviciadao on 2008-05-04
> **RavanH said:**
> OK, I see... Well, I have just installed Hardy and Cairo-Dock without that solution and it seems to work fine. Only I am missing some of the newer plugins like the mail notifier (and i had just gotten used to it :( ) but hey, "don't try 'n fix what ain't broke (much)" ;)

Is cairo-dock not working for you on hardy?

Ok, thanks for your patience. As I said, step by step...

root@denis-desktop:/home/denis# dpkg -i --force-all cairo-dock*.deb
dpkg-deb: `cairo-dock-plug-ins_v1.5.3.2_i686-32bits.deb' não é um formato de arquivo debian
dpkg: erro processando cairo-dock-plug-ins_v1.5.3.2_i686-32bits.deb (--install):
 subprocesso dpkg-deb --control retornou código de saída de error 2
dpkg-deb: `cairo-dock_v1.5.3.2_i686-32bits.deb' não é um formato de arquivo debian
dpkg: erro processando cairo-dock_v1.5.3.2_i686-32bits.deb (--install):
 subprocesso dpkg-deb --control retornou código de saída de error 2
Erros foram encontrados durante processamento de:
 cairo-dock-plug-ins_v1.5.3.2_i686-32bits.deb
 cairo-dock_v1.5.3.2_i686-32bits.deb

Well, I know it's in Portuguese, but it means its not a debian format file. I tried other versions too, got the same messenges.

Again, thank you.

---

### Post by RavanH on 2008-05-05
> **oviciadao said:**
> ...dpkg-deb: `cairo-dock-plug-ins_v1.5.3.2_i686-32bits.deb' não é um formato de arquivo debian
...
Wow, not a debain package?? That is weird. My first guess would be that the file got corrupted during download but you have tried other/older versions too with the same result? Even weirder...

Try this: delete all the previously used cairo-dock deb files from your home folder and download the two latest deb files again with the following command in a terminal window (so not via you browser!) and use them following the instructions on the how-to:
```
wget http://download.berlios.de/cairo-dock/cairo-dock_v1.5.5.3_i686-32bits.deb http://download.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.5.3_i686-32bits.deb
```

The first download should be reported by wget as **Size: 7,090,828 (6.8M) [application/x-download]** and the second as **Size: 13,395,824 (13M) [application/x-download]** with a total of **Fetched: 20,486,652 bytes in 2 files** (or similar in portuguese ofcource). Just to give you an indication whether the files are correctly downloaded...

Hope this helps :)

---

### Post by RavanH on 2008-05-05
> **Cappy said:**
> It was fixed in Hardy before the final release.

OK, thanks Cappy. I'll adapt the how-to again :)

---

### Post by engstrom on 2008-05-06
I've got Cairo installed on 8.04 and working after one or two minor issues but it doesn't show any other themes apart from _Default_ under Theme Manager and Views tab only has basic 2d views for the Main and Sub Docks listed...
Also the Applets tab has nothing but "Preferences" listed under all three sections (Accessories. functionalaties and Control your PC). Clicking on the prefs box does nothing.

---

### Post by oviciadao on 2008-05-06
> **RavanH said:**
> Wow, not a debain package?? That is weird. My first guess would be that the file got corrupted during download but you have tried other/older versions too with the same result? Even weirder...

Try this: delete all the previously used cairo-dock deb files from your home folder and download the two latest deb files again with the following command in a terminal window (so not via you browser!) and use them following the instructions on the how-to:
```
wget http://download.berlios.de/cairo-dock/cairo-dock_v1.5.5.3_i686-32bits.deb http://download.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.5.3_i686-32bits.deb
```

The first download should be reported by wget as **Size: 7,090,828 (6.8M) [application/x-download]** and the second as **Size: 13,395,824 (13M) [application/x-download]** with a total of **Fetched: 20,486,652 bytes in 2 files** (or similar in portuguese ofcource). Just to give you an indication whether the files are correctly downloaded...

Hope this helps :)

Weird, weird! I've downloaded the 'not found' html page...
If there's anything in Portuguese you need me to translate, please tell me:


root@denis-desktop:/# wget [http://download.berlios.de/cairo-dock/cairo-dock_v1.5.5.3_i686-32bits.deb](http://download.berlios.de/cairo-dock/cairo-dock_v1.5.5.3_i686-32bits.deb) [http://download.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.5.3_i686-32bits.deb](http://download.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.5.3_i686-32bits.deb)
--21:14:52--  [http://download.berlios.de/cairo-dock/cairo-dock_v1.5.5.3_i686-32bits.deb](http://download.berlios.de/cairo-dock/cairo-dock_v1.5.5.3_i686-32bits.deb)
           => `cairo-dock_v1.5.5.3_i686-32bits.deb'
Resolvendo download.berlios.de... 195.37.77.141
Conectando a download.berlios.de|195.37.77.141|:80... conectado.
HTTP requisição enviada, aguardando resposta... 302 Found
Localização: [http://download.berlios.de/error/HTTP_NOT_FOUND.html.var](http://download.berlios.de/error/HTTP_NOT_FOUND.html.var) [seguinte]
--21:14:53--  [http://download.berlios.de/error/HTTP_NOT_FOUND.html.var](http://download.berlios.de/error/HTTP_NOT_FOUND.html.var)
           => `HTTP_NOT_FOUND.html.var.2'
Conectando a download.berlios.de|195.37.77.141|:80... conectado.
HTTP requisição enviada, aguardando resposta... 200 OK
Tamanho: nao especificado [text/html]

    [ <=>                                 ] 1,031         --.--K/s             

21:14:53 (105.78 MB/s) - `HTTP_NOT_FOUND.html.var.2' salvo [1031]

--21:14:53--  [http://download.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.5.3_i686-32bits.deb](http://download.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.5.3_i686-32bits.deb)
           => `cairo-dock-plug-ins_v1.5.5.3_i686-32bits.deb'
Conectando a download.berlios.de|195.37.77.141|:80... conectado.
HTTP requisição enviada, aguardando resposta... 302 Found
Localização: [http://download.berlios.de/error/HTTP_NOT_FOUND.html.var](http://download.berlios.de/error/HTTP_NOT_FOUND.html.var) [seguinte]
--21:14:54--  [http://download.berlios.de/error/HTTP_NOT_FOUND.html.var](http://download.berlios.de/error/HTTP_NOT_FOUND.html.var)
           => `HTTP_NOT_FOUND.html.var.3'
Conectando a download.berlios.de|195.37.77.141|:80... conectado.
HTTP requisição enviada, aguardando resposta... 200 OK
Tamanho: nao especificado [text/html]

    [ <=>                                 ] 1,031         --.--K/s             

21:14:55 (188.32 MB/s) - `HTTP_NOT_FOUND.html.var.3' salvo [1031]


FINALIZADO --21:14:55--
Baixados: 2,062 bytes em 2 arquivos
root@denis-desktop:/# 

Thanks

---

### Post by RyderSTorm on 2008-05-11
Hi there, I'm still somewhat new to linux, and installing packages from the console still gives problems. I followed the instructions:
[B]
-downloaded the latest packages from the website[/B]
- worked fine
**-sudo dpkg -i --force-all cairo-dock*.de**b 
- worked fine
**-sudo getlibs /usr/bin/cairo-dock**
-just gives a blinking cursor, doesn't output any info, have to ctrl-c to get back to a prompt

when i try to run **cairo-dock** it spits out:
"cairo-dock: error while loading shared libraries: libdbus-glib-1.so.2: cannot open shared object file: No such file or directory"

At first it was giving me an error about libglitz-glx.so.1 , but I managed to get that one installed. I can't find a way to get libdbus-glib-1.so.2 installed. Any help you could offer would be much appreciated!

---

### Post by RavanH on 2008-05-11
> **RyderSTorm said:**
> ...
**-sudo getlibs /usr/bin/cairo-dock**
-just gives a blinking cursor, doesn't output any info, have to ctrl-c to get back to a prompt
...

Can you try and re-install getlibs?

---

### Post by Cappy on 2008-05-11
It means getlibs can't contact the ubuntu package search. Are you using a proxy?

---

### Post by RavanH on 2008-05-11
> **oviciadao said:**
> Weird, weird! I've downloaded the 'not found' html page...
If there's anything in Portuguese you need me to translate, please tell me:


root@denis-desktop:/# wget [http://download.berlios.de/cairo-dock/cairo-dock_v1.5.5.3_i686-32bits.deb](http://download.berlios.de/cairo-dock/cairo-dock_v1.5.5.3_i686-32bits.deb) [http://download.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.5.3_i686-32bits.deb](http://download.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.5.3_i686-32bits.deb)
--21:14:52--  [http://download.berlios.de/cairo-dock/cairo-dock_v1.5.5.3_i686-32bits.deb](http://download.berlios.de/cairo-dock/cairo-dock_v1.5.5.3_i686-32bits.deb)
           => `cairo-dock_v1.5.5.3_i686-32bits.deb'
Resolvendo download.berlios.de... 195.37.77.141
Conectando a download.berlios.de|195.37.77.141|:80... conectado.
HTTP requisição enviada, aguardando resposta... 302 Found
Localização: [http://download.berlios.de/error/HTTP_NOT_FOUND.html.var](http://download.berlios.de/error/HTTP_NOT_FOUND.html.var) [seguinte]
--21:14:53--  [http://download.berlios.de/error/HTTP_NOT_FOUND.html.var](http://download.berlios.de/error/HTTP_NOT_FOUND.html.var)
           => `HTTP_NOT_FOUND.html.var.2'
Conectando a download.berlios.de|195.37.77.141|:80... conectado.
HTTP requisição enviada, aguardando resposta... 200 OK
Tamanho: nao especificado [text/html]

    [ <=>                                 ] 1,031         --.--K/s             

21:14:53 (105.78 MB/s) - `HTTP_NOT_FOUND.html.var.2' salvo [1031]

--21:14:53--  [http://download.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.5.3_i686-32bits.deb](http://download.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.5.3_i686-32bits.deb)
           => `cairo-dock-plug-ins_v1.5.5.3_i686-32bits.deb'
Conectando a download.berlios.de|195.37.77.141|:80... conectado.
HTTP requisição enviada, aguardando resposta... 302 Found
Localização: [http://download.berlios.de/error/HTTP_NOT_FOUND.html.var](http://download.berlios.de/error/HTTP_NOT_FOUND.html.var) [seguinte]
--21:14:54--  [http://download.berlios.de/error/HTTP_NOT_FOUND.html.var](http://download.berlios.de/error/HTTP_NOT_FOUND.html.var)
           => `HTTP_NOT_FOUND.html.var.3'
Conectando a download.berlios.de|195.37.77.141|:80... conectado.
HTTP requisição enviada, aguardando resposta... 200 OK
Tamanho: nao especificado [text/html]

    [ <=>                                 ] 1,031         --.--K/s             

21:14:55 (188.32 MB/s) - `HTTP_NOT_FOUND.html.var.3' salvo [1031]


FINALIZADO --21:14:55--
Baixados: 2,062 bytes em 2 arquivos
root@denis-desktop:/# 

Thanks
Hmmm, seems that version was just replaced by one digit up. Instead use: 
```
wget http://download.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.5.4_i686-32bits.deb http://download.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.5.4_i686-32bits.deb
``` and follow the step-by step again.

You could also use ```
sudo getlibs -w http://download.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.5.4_i686-32bits.deb http://download.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.5.4_i686-32bits.deb
``` and make getlibs do the work for you ;) . I have not tested this methode on a clean system, so if you are willing to test it out, let me know the result! :)

---

### Post by RavanH on 2008-05-11
> **engstrom said:**
> I've got Cairo installed on 8.04 and working after one or two minor issues but it doesn't show any other themes apart from _Default_ under Theme Manager and Views tab only has basic 2d views for the Main and Sub Docks listed...
Also the Applets tab has nothing but "Preferences" listed under all three sections (Accessories. functionalaties and Control your PC). Clicking on the prefs box does nothing.

Can you see if there are themes (folders) installed under /usr/share/cairo-dock/themes ? If not, the package was not installed completely. You might have to download and install again.

Otherwise, are you sure you have met all the prerequisites in the how-to? To make sure all is in place, do in terminal ```
sudo apt-get install libcairo2 librsvg2-2 libglitz1 libglitz-glx1 dbus libdbus-1-3 libdbus-glib-1-2 libvte9 libxxf86vm1 libgnome2-0 gvfs libgnomevfs2-0 libgnome-keyring0 libavahi-glib1 libavahi-common3 libavahi-client3 libgnomeui-0 libbonoboui2-0
```

Also, to get the latest plugins up and running, do ```
sudo getlibs -p libgnome2-0 gvfs libgnomevfs2-0 libgnome-keyring0 libavahi-glib1 libavahi-common3 libavahi-client3 libgnomeui-0 libvte9 libbonoboui2-0
``` and if you are using XFce also ```
sudo getlibs -p libgamin0 libstartup-notification0 libthunar-vfs-1-2 libexo-0.3-0 libxfce4util4 libhal-storage1
``` (this info will be in the how-to soon, when i have verified it works correctly)

Let me know if it works for you (or not)

---

### Post by RavanH on 2008-05-11
> **josel777 said:**
> Tried code:
getlibs -p libgnomevfs2-0

But I'm still getting the message below.

Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libfile.so' (/usr/lib/gnome-vfs-2.0/modules/libfile.so: wrong ELF class: ELFCLASS64)
Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libfile.so' (/usr/lib/gnome-vfs-2.0/modules/libfile.so: wrong ELF class: ELFCLASS64)
Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libfile.so' (/usr/lib/gnome-vfs-2.0/modules/libfile.so: wrong ELF class: ELFCLASS64)
Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libfile.so' (/usr/lib/gnome-vfs-2.0/modules/libfile.so: wrong ELF class: ELFCLASS64)
file gnome-vfs-cancellable-ops.c: line 309 (gnome_vfs_find_directory_cancellable): assertion failed: (near_uri != NULL)
Aborted (core dumped)

Josel777, can you try to start cairo-dock in safe-mode or maintenance mode? 

Do **cairo-dock -f** and select any theme in the dialog. The dock should now be loaded without any plugins/applets available. Does that work?

You can also try **cairo-dock -m** which makes the config screen come up before starting the dock. That too switches off all applets and can see if it works without any of them active. Then restart cairo-dock without the -m option and activate the applets again, one by one (and only the ones you want, ofcource)...

Else, please report this error on [http://developer.berlios.de/forum/forum.php?forum_id=26288](http://developer.berlios.de/forum/forum.php?forum_id=26288)

Let me know. Thanks,
Ravan

---

### Post by engstrom on 2008-05-11
> **RavanH said:**
> Can you see if there are themes (folders) installed under /usr/share/cairo-dock/themes ? If not, the package was not installed completely. You might have to download and install again.

Let me know if it works for you (or not)

Yes the themes are there in the folder you specified.

I tried the 3 things listed and still no joy...the only difference is now booting up is a 10-15 hdd thrash-fest :confused:

---

### Post by RavanH on 2008-05-12
> **engstrom said:**
> Yes the themes are there in the folder you specified.

I tried the 3 things listed and still no joy...the only difference is now booting up is a 10-15 hdd thrash-fest :confused:

Hmm, I do not see how the hdd checking (that is what you are talking about, i think?) would be related. Has that not happened before? And now on every boot? Is file or disk corruption being reported? If so, it would sound like your hdd is falling apart...

About the missing themes and plugins: can you see if there are a whole bunch of plugins (.so files and their subfolders) in /usr/share/cairo-dock/plug-in/ ? If so, can you remove the user cairo-dock settings by ```
rm -R ~/.cairo-dock
``` and start cairo-dock again from terminal and see what messages you get?

---

### Post by neymac on 2008-05-12
I used the script cairo-dock_svn.sh from M@v (the author) and did follow the instructions from 

[http://www.cairo-dock.org/ww_page.php?p=From SVN&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From SVN&lang=en")

and got cairo-dock working compiled from SVN without major problems and quite stable until now.
When compiling it asked if I wanted "glitz", I said no because I was not shure if "glitz" would work on my system (8.04).

---

### Post by RavanH on 2008-05-13
> **neymac said:**
> I used the script cairo-dock_svn.sh from M@v (the author) and did follow the instructions from 

[http://www.cairo-dock.org/ww_page.php?p=From SVN&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From SVN&lang=en")

and got cairo-dock working compiled from SVN without major problems and quite stable until now.
When compiling it asked if I wanted "glitz", I said no because I was not shure if "glitz" would work on my system (8.04).

Ok, thanks for the tip. I will consider making it part of the how-to as an alternative. 

I am also considering another alternative: converting the available 64bit RPM packages for OpenSUSE with alien and installing them. I have tested and it works fine but it might be a somewhat too cumbersome route for most users.

EDIT: just trying it out, I see the glitz question you are talking about... > Voulez-vous installer la librairie Cairo avec l'option GLITZ d'activée ?
Cette option permet une plus grande réactivité de votre dock en utilisant votre carte graphique et non votre processeur pour effectuer les calculs mais peut ralentir votre système ou occasionner des dysfonctionnements
Attention ! Des erreurs semblent apparaitre avec les cartes ATI, notamment avec les chipsets de portable and since I am running it on a laptop with ATI card, it seems wise for me to answer "no" here too ;)

---

### Post by neymac on 2008-05-14
> 6. If all works well and is configured to your liking, add a new entry with the command cairo-dock to the Sessions list (Ubuntu menu: System>Preferences>Sessions) to make it start up at login...

TIP: To keep CD updated to the latest version you need re-run the script again from time to time. It will automatically check for a new revision and download/install it when needed. To make this as easy as possible, create a new launcher in CD that will initiate the command gnome-terminal --working-directory=/[COLOR="Red"]opt[/COLOR]/cairo-dock_svn/ -e "./cairo-dock_svn.sh" (note: that command will not work when cairo dock itself is launched from terminal). See chapter NOTES & TIPS point H for a small how-to.

There is a little mistake in this TIP, as you change the working directory to /svn/cairo-dock_svn/ , for this tip work you need exchange "opt" by "svn".
Great how-to!

---

### Post by RavanH on 2008-05-14
> **neymac said:**
> There is a little mistake in this TIP, as you change the working directory to /svn/cairo-dock_svn/ , for this tip work you need exchange "opt" by "svn".
Great how-to!
Wow, thanks! You have a sharp eye ;)

---

### Post by josel777 on 2008-05-18
> **RavanH said:**
> Josel777, can you try to start cairo-dock in safe-mode or maintenance mode? 

Do **cairo-dock -f** and select any theme in the dialog. The dock should now be loaded without any plugins/applets available. Does that work?

You can also try **cairo-dock -m** which makes the config screen come up before starting the dock. That too switches off all applets and can see if it works without any of them active. Then restart cairo-dock without the -m option and activate the applets again, one by one (and only the ones you want, ofcource)...

Else, please report this error on [http://developer.berlios.de/forum/forum.php?forum_id=26288](http://developer.berlios.de/forum/forum.php?forum_id=26288)

Let me know. Thanks,
Ravan

Thanks for the info. CD runs when I type cairo-dock -f.

---

### Post by paradoxxx_zero on 2008-05-18
Just to let you know that the next release will have amd64 packages...
See you at [www.cairo-dock.org](www.cairo-dock.org) ;)

---

### Post by engstrom on 2008-05-18
I used synaptic to remove cairo in order to start again.

Using method 1 I get as far as the getlibs command and it just sits in the terminal with;
"libglitz-glx.so.1: libglitz-glx1
libglitz.so.1: libglitz1"
until I ctrl-c. There's no hdd access or anything.

---

### Post by Banny706 on 2008-05-18
Doesn't work on Hardy for me.

the getlibs command hangs up.

---

### Post by jem222 on 2008-05-19
> **RyderSTorm said:**
> Hi there, I'm still somewhat new to linux, and installing packages from the console still gives problems. I followed the instructions:
[B]
-downloaded the latest packages from the website[/B]
- worked fine
**-sudo dpkg -i --force-all cairo-dock*.de**b 
- worked fine
**-sudo getlibs /usr/bin/cairo-dock**
-just gives a blinking cursor, doesn't output any info, have to ctrl-c to get back to a prompt

when i try to run **cairo-dock** it spits out:
"cairo-dock: error while loading shared libraries: libdbus-glib-1.so.2: cannot open shared object file: No such file or directory"

At first it was giving me an error about libglitz-glx.so.1 , but I managed to get that one installed. I can't find a way to get libdbus-glib-1.so.2 installed. Any help you could offer would be much appreciated!

[PHP][/PHP]

Hi-
I had the same problem initially. After waiting 24 hours, getlibs picked up one of the libraries I needed, but not another. Incidentally, if you want to find out which libraries you are missing, try "ldd /usr/bin/cairo-dock" Instead, getlibs returned an error like "No Match for libdbus-glib-1.so.2." I fixed the problem by finding the debian package (I used the libdbus-glib-1-2 found at [http://packages.debian.org/lenny/libdbus-glib-1-2](http://packages.debian.org/lenny/libdbus-glib-1-2)) and installing it with "getlibs -i /home/your_directory/libdbus-glib-1-2_0.74-2_i386.deb"
Good luck!
Jem

---

### Post by theumang on 2008-05-22
some one check this out n let us know on how to do THAT stacks thing within the dock...

[http://www.youtube.com/watch?v=_F2tAMeTKqI](http://www.youtube.com/watch?v=_F2tAMeTKqI)

---

### Post by paradoxxx_zero on 2008-05-22
You need to have the rendering plugin and to activate it !

---

### Post by RavanH on 2008-05-25
> **Banny706 said:**
> Doesn't work on Hardy for me.

the getlibs command hangs up.

You might want to check out the new Method 2 in the how-to... It will install the latest development version straight from SVN :)

---

### Post by RavanH on 2008-05-25
> **paradoxxx_zero said:**
> Just to let you know that the next release will have amd64 packages...
See you at [www.cairo-dock.org](www.cairo-dock.org) ;)

That is GREAT news ! :) Let me know ASAP as they are in the repo and I will change the How-to

:guitar:

---

### Post by paradoxxx_zero on 2008-05-25
ok no problem !
There's already unstable rc packages but it seems to have problems with themes.
If you want to help me : feel free to test it and tell me how it works : they're available at [http://www.cairo-dock.org/bg_topic.php?t=700&pos=91](http://www.cairo-dock.org/bg_topic.php?t=700&pos=91). (It's in french but just open the links :) )
ps : wait about 20minutes i will update these packages to rc3...

edit : here the new package if someone woud like to test :
[http://paradoxxx.zero.free.fr/cairo-dock-deb-64bit/cairo-dock_v1.5.6-rc1_x86_64.deb](http://paradoxxx.zero.free.fr/cairo-dock-deb-64bit/cairo-dock_v1.5.6-rc1_x86_64.deb)
[http://paradoxxx.zero.free.fr/cairo-dock-deb-64bit/cairo-dock-plug-ins_v1.5.6-rc1_x86_64.deb](http://paradoxxx.zero.free.fr/cairo-dock-deb-64bit/cairo-dock-plug-ins_v1.5.6-rc1_x86_64.deb)

---

### Post by RavanH on 2008-05-25
> **paradoxxx_zero said:**
> ok no problem !
There's already unstable rc packages but it seems to have problems with themes.
If you want to help me : feel free to test it and tell me how it works : they're available at [http://www.cairo-dock.org/bg_topic.php?t=700&pos=91](http://www.cairo-dock.org/bg_topic.php?t=700&pos=91). (It's in french but just open the links :) )
ps : wait about 20minutes i will update these packages to rc3...

edit : here the new package if someone woud like to test :
[http://paradoxxx.zero.free.fr/cairo-dock-deb-64bit/cairo-dock_v1.5.6-rc1_x86_64.deb](http://paradoxxx.zero.free.fr/cairo-dock-deb-64bit/cairo-dock_v1.5.6-rc1_x86_64.deb)
[http://paradoxxx.zero.free.fr/cairo-dock-deb-64bit/cairo-dock-plug-ins_v1.5.6-rc1_x86_64.deb](http://paradoxxx.zero.free.fr/cairo-dock-deb-64bit/cairo-dock-plug-ins_v1.5.6-rc1_x86_64.deb)

Thanks, Fabounet already pointed the thread out to me but I read that there is no XFCE integration in these packages yet? Since I am running Xubuntu, I will stick to the SVN scriptbuild and wait for that last part to become available in the 64bit debs.

---

### Post by paradoxxx_zero on 2008-05-25
my last packaging contains xfce-integration now :)
can you test it please ?

---

### Post by RavanH on 2008-05-25
> **paradoxxx_zero said:**
> my last packaging contains xfce-integration now :)
can you test it please ?

GREAT! I will... I suppose I should uninstall the SVN version first? Anyway, will let you know.

---

### Post by RavanH on 2008-05-25
> **paradoxxx_zero said:**
> ok no problem !
There's already unstable rc packages but it seems to have problems with themes.
If you want to help me : feel free to test it and tell me how it works : they're available at [http://www.cairo-dock.org/bg_topic.php?t=700&pos=91](http://www.cairo-dock.org/bg_topic.php?t=700&pos=91). (It's in french but just open the links :) )
ps : wait about 20minutes i will update these packages to rc3...

edit : here the new package if someone woud like to test :
[http://paradoxxx.zero.free.fr/cairo-dock-deb-64bit/cairo-dock_v1.5.6-rc1_x86_64.deb](http://paradoxxx.zero.free.fr/cairo-dock-deb-64bit/cairo-dock_v1.5.6-rc1_x86_64.deb)
[http://paradoxxx.zero.free.fr/cairo-dock-deb-64bit/cairo-dock-plug-ins_v1.5.6-rc1_x86_64.deb](http://paradoxxx.zero.free.fr/cairo-dock-deb-64bit/cairo-dock-plug-ins_v1.5.6-rc1_x86_64.deb)

OK, after uninstalling the SVN version, I downloaded and installed these debs. I got no message about missing dependencies which seems logical since I was running the SVN version already.

Entering the command cairo-dock started the dock just fine and the first thing I notice is that the Shortcuts applet is finally working now :) ... only the Stacks and Mail applets I am sorry to see missing. Hope they will be coming soon too?

Extra info: The terminal screen retuned ```
$ cairo-dock
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
cairo_dock_create_surface_from_image: assertion `rsvg_handle != NULL' failed
cairo_dock_create_surface_from_image: assertion `rsvg_handle != NULL' failed
```

---

### Post by paradoxxx_zero on 2008-05-25
Thanks for testing :)

These plugins are not in stable category yet. More developpement and more tests are needed... But it will come :)
I'm glad it works, i'm more confident now about packaging a stable version !
Another testers ?

---

### Post by jason50146 on 2008-05-25
I have a problem with Cairo-Dock that showed up after a fresh install of Hardy.  It only works properly when I run it as a super user from the terminal.  This also means adding it to my sessions list fails to load it properly on startup.  If I do not run it as a super user I get the "Manage Themes" window and clicking "OK" or "Quit" does nothing and the dock does not appear.  As stated above, when running from the terminal as a super user everything works great.

This didn't occur under Gutsy, so I'm assuming I'm missing something.  I am running Hardy AMD64 and compiz-fusion.  Any thoughts?  Both 32 and 64 bit versions of C-D behave this way.

Thanks
Jason

---

### Post by RavanH on 2008-05-26
> **jason50146 said:**
> I have a problem with Cairo-Dock that showed up after a fresh install of Hardy.  It only works properly when I run it as a super user from the terminal.  This also means adding it to my sessions list fails to load it properly on startup.  If I do not run it as a super user I get the "Manage Themes" window and clicking "OK" or "Quit" does nothing and the dock does not appear.  As stated above, when running from the terminal as a super user everything works great.

This didn't occur under Gutsy, so I'm assuming I'm missing something.  I am running Hardy AMD64 and compiz-fusion.  Any thoughts?  Both 32 and 64 bit versions of C-D behave this way.

Thanks
Jason

I would guess there is something wrong with the owner/permissions of the folder where all your Cairo Dock user settings are stored. Try ```
sudo chown YOUR_USERNAME:YOUR_USERGROUP -R ~/.cairo-dock
``` (fill in your username == *login name* and then most likely your username again since Ubuntu creates a new group for every user by default, or any other group if you have set your user to any other group like *users* for example)

Then if that does not do the trick check in nautilus (press Ctrl+H to make it show hidden files and folders) by right clicking on the **.cairo-dock** folder in your home folder and open the tab 'Rights' to see what your access rights to files and folders are. They should be create/delete access for folders + read/write access for files.

---

### Post by jason50146 on 2008-05-26
> **RavanH said:**
> I would guess there is something wrong with the owner/permissions of the folder where all your Cairo Dock user settings are stored. Try ```
sudo chown YOUR_USERNAME:YOUR_USERGROUP -R ~/.cairo-dock
``` (fill in your username == *login name* and then most likely your username again since Ubuntu creates a new group for every user by default, or any other group if you have set your user to any other group like *users* for example)

Then if that does not do the trick check in nautilus (press Ctrl+H to make it show hidden files and folders) by right clicking on the **.cairo-dock** folder in your home folder and open the tab 'Rights' to see what your access rights to files and folders are. They should be create/delete access for folders + read/write access for files.

I tried your suggestion but am still having the same trouble.  I used both the command line and checked the permissions in Nautilus.  Everything appears as you indicated it should be.  There are no errors indicated when I run cairo dock from the terminal, so I'm not sure what is happening.

Thanks again!

---

### Post by RavanH on 2008-05-26
> **jason50146 said:**
> I tried your suggestion but am still having the same trouble.  I used both the command line and checked the permissions in Nautilus.  Everything appears as you indicated it should be.  There are no errors indicated when I run cairo dock from the terminal, so I'm not sure what is happening.

Thanks again!

First try ans start from terminal with **cairo-dock -f** (as normal user), save your current setup with a new name and then pick one of the standard themes. Now see if that works. If so, try to switch back to your old theme/setup and then try and activate each plugin one by one...

IF that doesn get you anywhere, can you remove (or rename) the /.cairo-dock folder and restart CD from terminal as normal user? You should get the theme manager dialog and be able to pick a new theme. Can you tell me whether CD runs correctly after that? If not, does a new /.cairo-dock folder even get created or not?

Last suggestion: remove Cairo Dock again (see the how-to for the new 'remove' chapter, also remove any ~/.cairo-dock folder so CD will start fresh) and try the new **Method 0** in the how-to. It simply involves installing the alpha testing 64bit deb packages but should result in a proper working installation.

---

### Post by jason50146 on 2008-05-28
> **RavanH said:**
> First try ans start from terminal with **cairo-dock -f** (as normal user), save your current setup with a new name and then pick one of the standard themes. Now see if that works. If so, try to switch back to your old theme/setup and then try and activate each plugin one by one...


Cairo-dock -f did the trick.  I hadn't altered it much from the default, so setting it up again should not be a problem.

Thanks!

---

### Post by RavanH on 2008-05-30
> **paradoxxx_zero said:**
> Thanks for testing :)

These plugins are not in stable category yet. More developpement and more tests are needed... But it will come :)
I'm glad it works, i'm more confident now about packaging a stable version !
Another testers ?

Hi paradoxxx, I notice new deb files on [http://paradoxxx.zero.free.fr/cairo-dock-deb-64bit/](http://paradoxxx.zero.free.fr/cairo-dock-deb-64bit/) seemingly marked as stable ... will they be in the main cairo-dock repo soon?

---

### Post by paradoxxx_zero on 2008-05-31
yes as soon as the repo manager will be back ;)
if you can, please test it, i'd like someone do this before putting in repo...
thanks ;)

---

### Post by RavanH on 2008-05-31
> **paradoxxx_zero said:**
> yes as soon as the repo manager will be back ;)
if you can, please test it, i'd like someone do this before putting in repo...
thanks ;)

Installed it yesterday and all seems better then it has ever been (compared to 32bit stable). Starting from terminal I get > _cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
Binding '<Ctrl>F2' failed!
warning :  (cairo-dock-keybinder.c:cd_keybinder_bind:301)  
  couldnt bind <Ctrl>F2
Binding '<Ctrl>F2' failed! and when I do hit Ctrl+F2, the tray icon shows the tray but at the same time hides (minimizes) all open apps. That does not seem like it is supposed to happen so I disabled the systray plugin again.

Running on XFCE, so no test of gnome integration nor compizfusion. Becouse of my ATI card the Xgamma plugin does not do much except gamma (no brightness/contrast) and Showdesktop minimizes apps only after double-click, not single click. Is that default behaviour? The wifi plugin I cannot test fully because I only connect via LAN and the Terminal icon works but only after a long time I found out that I had to middle-click the terminal icon to close the opened terminal(s). This is fine but on my laptop I have no middle click button ;)

All other plugins do the job just perfectly!

[COLOR="Red"]EDIT :[/COLOR] I found out why Ctrl+F2 behaves strangely. That key combo is used to switch to desktop #2 (in XFCE only, not GNOME ?) so that might explain the strange effect. Activated the plugin again and changed the key combo which removed the error message but then the tray icon does not show the tray when hitting those keys. Only it opens the tray on left-click, then does not close it anymore (or is that middle click again?). Also, it shows the tray only on one desktop... Not liking that behaviour, I decided to remove it again.

[COLOR="Red"]EDIT 2 :[/COLOR] Just noticed that running Evolution, the icon does not show in the opened apps list... Apps like FF and OpenOffice are shown just fine. Strange. Terminal shows error > (evolution:6839): camel-CRITICAL **: get_message_info: assertion `folder->summary != NULL' failed


---

### Post by paradoxxx_zero on 2008-05-31
Thanks for this great complete testing :)
These problems are not 64bit specific as far as i know...
So the repository will be updated soon, thanks a lot RavanH ;)

---

### Post by paradoxxx_zero on 2008-06-05
64bit repo is out !
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock
:)

---

### Post by Mark76 on 2008-06-09
How do I populate a sub-dock?

---

### Post by RavanH on 2008-06-10
> **paradoxxx_zero said:**
> 64bit repo is out !
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock
:)

GREAT! That's a reason for a small party :guitar: 

...but also a sad goodbye for this How-to :cry: since it is no longer needed ;)

---

### Post by RavanH on 2008-06-10
> **Mark76 said:**
> How do I populate a sub-dock?

Not exactly sure if you mean what I think you mean but try this:

Right-click a launcher on the main dock and select **Modify this launcher** then click **Extra parameters** and change the container option _Main Dock_ to the name that represents your second/sub-dock... Then hit Apply and the launcher should jump to the sub-dock.

---

### Post by davarse on 2008-06-11
i install it on hardy and i went alright, but i just have "default" option for the view both dock and sub-dock.
i had cairo dock on my gusty before and it was perfect..
do you know how to make another option rather than "default"?

cheers'

---

### Post by RavanH on 2008-06-11
> **davarse said:**
> i install it on hardy and i went alright, but i just have "default" option for the view both dock and sub-dock.
i had cairo dock on my gusty before and it was perfect..
do you know how to make another option rather than "default"?

cheers'

All the great view options should be there, so clearly something went wrong. 

Questions: What version of CD do you have installed? How did you install: the new repository method, the deb package method or using the SVN script? And what errors do you see when you start CD from terminal? 

Suggestion: It might be some of the plugins that is causing trouble. Start CD from terminal with ```
cairo-dock --safe-mode
``` to start with all plugins disabled. You will still not have 3D because also the Rendering plugin will be swithed off but if you restart CD normally, you will be able to switch the plugins back on one-by-one. Start with the Rendering plugin and see if you have any other view beside default...

---

### Post by davarse on 2008-06-12
> **RavanH said:**
> All the great view options should be there, so clearly something went wrong. 

Questions: What version of CD do you have installed? How did you install: the new repository method, the deb package method or using the SVN script? And what errors do you see when you start CD from terminal? 

Suggestion: It might be some of the plugins that is causing trouble. Start CD from terminal with ```
cairo-dock --safe-mode
``` to start with all plugins disabled. You will still not have 3D because also the Rendering plugin will be swithed off but if you restart CD normally, you will be able to switch the plugins back on one-by-one. Start with the Rendering plugin and see if you have any other view beside default...



hi there, thanks for reply...
anyway, i was installed cairo-dock 64bit for the testing one (the fist method on your how-to) about couple of weeks ago... and last night i remove it and and installed the 64bit stable version (method 1; the ubuntu way). it was fine, and have few option on the view option, but i have some problem still...

1. when i change the view option to 3d, cairo-dock just gone. and after that i changed again to default view and i appeared again..
2. when i changed the themes to mac os style, the the dock just disappeared again, this time i couldn't change anymore, because i couldn't find the dock

i restart my laptop few times and when i fire up cairo-dock, it still disappeared, i still couldn't find anywhere, i've check all over computer's edges, but nothing happened... but i know it still somewhere there, because everytime i minimize the windows, the window still go toward the dock, but i couldn't find where it is...

and also i tried to fire up cairo-dock --safe-mode, i does worked but only default option in view option. i've tried to used all the themes but still "default" option for view..

one more question: when you say "Rendering plugin will be swithed off but if you restart CD normally, you will be able to switch the plugins back on one-by-one" where can i find that rendering plugin, and how to which it on. and what do you mean by restart cairo-dock??

and this's the messege that i got after install and fire up cairo-dock for first time before it disappeared:


[I]warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory) 
warning :  (cairo-dock-config.c:cairo_dock_get_double_list_key_value:428)  
  Attention : Key file does not have key 'text color start' 
warning :  (cairo-dock-config.c:cairo_dock_get_double_list_key_value:428)  
  Attention : Key file does not have key 'text color stop' 
warning :  (cairo-dock-config.c:cairo_dock_get_boolean_key_value:183)  
  Attention : Key file does not have key 'vertical label pattern' 
mkdir: cannot create directory `/home/david/.cairo-dock/current_theme/plug-ins/Cairo-Penguin': Permission denied 
cp: cannot create regular file `/home/david/.cairo-dock/current_theme/plug-ins/Cairo-Penguin/Cairo-Penguin.conf': No such file or directory 
warning :  (cairo-dock-applet-facility.c:cairo_dock_check_conf_file_exists:60)  
  Attention : couldn't copy /usr/lib/cairo-dock/Cairo-Penguin/Cairo-Penguin.conf in /home/david/.cairo-dock/current_theme/plug-ins/Cairo-Penguin; check permissions and file's existence 
init: assertion `pContainer != NULL && pIcon != NULL' failed 
mkdir: cannot create directory `/home/david/.cairo-dock/current_theme/plug-ins/clock': Permission denied 
cp: cannot create regular file `/home/david/.cairo-dock/current_theme/plug-ins/clock/clock.conf': No such file or directory 
warning :  (cairo-dock-applet-facility.c:cairo_dock_check_conf_file_exists:60)  
  Attention : couldn't copy /usr/lib/cairo-dock/clock/clock.conf in /home/david/.cairo-dock/current_theme/plug-ins/clock; check permissions and file's existence 
init: assertion `pContainer != NULL && pIcon != NULL' failed 
mkdir: cannot create directory `/home/david/.cairo-dock/current_theme/plug-ins/logout': Permission denied 
cp: cannot create regular file `/home/david/.cairo-dock/current_theme/plug-ins/logout/logout.conf': No such file or directory 
warning :  (cairo-dock-applet-facility.c:cairo_dock_check_conf_file_exists:60)  
  Attention : couldn't copy /usr/lib/cairo-dock/logout/logout.conf in /home/david/.cairo-dock/current_theme/plug-ins/logout; check permissions and file's existence 
init: assertion `pContainer != NULL && pIcon != NULL' failed 
mkdir: cannot create directory `/home/david/.cairo-dock/current_theme/plug-ins/rendering': Permission denied 
cp: cannot create regular file `/home/david/.cairo-dock/current_theme/plug-ins/rendering/rendering.conf': No such file or directory 
warning :  (cairo-dock-applet-facility.c:cairo_dock_check_conf_file_exists:60)  
  Attention : couldn't copy /usr/lib/cairo-dock/rendering/rendering.conf in /home/david/.cairo-dock/current_theme/plug-ins/rendering; check permissions and file's existence 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_double_list: assertion `key_file != NULL' failed 
g_key_file_get_double: assertion `key_file != NULL' failed 
g_key_file_get_double: assertion `key_file != NULL' failed 
g_key_file_get_boolean: assertion `key_file != NULL' failed 
g_key_file_get_double: assertion `key_file != NULL' failed 
g_key_file_get_double: assertion `key_file != NULL' failed 
g_key_file_get_double: assertion `key_file != NULL' failed 
g_key_file_get_double: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_boolean: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_double: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_double: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_double: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_boolean: assertion `key_file != NULL' failed 
g_key_file_get_boolean: assertion `key_file != NULL' failed 
g_key_file_get_boolean: assertion `key_file != NULL' failed 
g_key_file_get_double_list: assertion `key_file != NULL' failed 
g_key_file_get_double_list: assertion `key_file != NULL' failed 
g_key_file_get_double_list: assertion `key_file != NULL' failed 
g_key_file_get_boolean: assertion `key_file != NULL' failed 
g_key_file_get_boolean: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_double: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_boolean: assertion `key_file != NULL' failed 
g_key_file_get_boolean: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_double: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_boolean: assertion `key_file != NULL' failed 
g_key_file_get_boolean: assertion `key_file != NULL' failed 
g_key_file_get_boolean: assertion `key_file != NULL' failed 
g_key_file_get_double_list: assertion `key_file != NULL' failed 
g_key_file_get_double_list: assertion `key_file != NULL' failed 
g_key_file_get_double_list: assertion `key_file != NULL' failed 
g_key_file_get_boolean: assertion `key_file != NULL' failed 
g_key_file_get_boolean: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_double: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_boolean: assertion `key_file != NULL' failed 
g_key_file_get_boolean: assertion `key_file != NULL' failed 
g_key_file_get_double: assertion `key_file != NULL' failed 
g_key_file_get_integer: assertion `key_file != NULL' failed 
g_key_file_get_double_list: assertion `key_file != NULL' failed 
reload: assertion `pNewContainer != NULL' failed 
reload: assertion `pNewContainer != NULL' failed 
reload: assertion `pNewContainer != NULL' failed 
reload: assertion `pNewContainer != NULL' failed 
reload: assertion `pNewContainer != NULL' failed 
reload: assertion `pNewContainer != NULL' failed 
[/I] 

thanks heap for your help

---

### Post by RavanH on 2008-06-13
> **davarse said:**
> ...mkdir: cannot create directory `/home/david/.cairo-dock/current_theme/plug-ins/rendering': Permission denied
...

OK, first things first. Most if the output is just warnings but some messages (like quoted) I think would indicate that the permissions of your ~/.cairo-dock folder are not correct.

Try in terminal ```
sudo chown YOUR_USERNAME:YOUR_USERGROUP -R .cairo-dock
``` where you fill in your username and your user group (in most cases the same as your username with a ':' between them)

Then start CD again from terminal and see if it changed anything.

---

### Post by davarse on 2008-06-13
> **RavanH said:**
> OK, first things first. Most if the output is just warnings but some messages (like quoted) I think would indicate that the permissions of your ~/.cairo-dock folder are not correct.

Try in terminal ```
sudo chown YOUR_USERNAME:YOUR_USERGROUP -R .cairo-dock
``` where you fill in your username and your user group (in most cases the same as your username with a ':' between them)

Then start CD again from terminal and see if it changed anything.

yay, thats work well. i have 3d view, etc... but it's bit slower than mine in gusty, i used mac style... do you know how to make it faster...

thank you for your help, you are a camp!!!

---

### Post by RavanH on 2008-06-13
> **davarse said:**
> yay, thats work well. i have 3d view, etc... but it's bit slower than mine in gusty, i used mac style... do you know how to make it faster...

thank you for your help, you are a camp!!!

I have no idea how to speed up CD. I can only think of disabling any plugin that you do not really need (like penguin?) but you might drop this question to the main developer Fabounet on [http://www.cairo-dock.org/bg_forum.php?f=2](http://www.cairo-dock.org/bg_forum.php?f=2) ... do not let all those french posts scare you, you can post in english too.

---

### Post by davarse on 2008-06-14
hi RavanH, i just notice 1 thing about CD mac theme (or maybe other themes too) it doesn't say any thing about the icon, what i mean is just the icon and it doesn't have any writting on it to say what icons are they. is there any way to name the icon (do you know what i mean)?
and my other question is, i remember my CD on gusty, it has sub-dock on few icon e.g internet has mozilla, ekika, pignin, etc. something like that, and i just realize in CD i have now all the icon become main icon on the dock. how to make sub-dock for those things i.e internet, gimp, etc it's very helpful you know to save the space on the dock....

thanks heaps'

---

### Post by Pedro_Pdr on 2008-06-14
Hi ppl!
My laptot is a toshiba L300 with:
Intel processor core 2 duo T2390 1,86GHZ
2GB Ram
So not too god... I cant enable effects. Gets me error and i think its because my laptop doesnt have a dedicated graphic card.
So, is there a way to use a dock without having effects enabled???

---

### Post by RavanH on 2008-06-16
> **Pedro_Pdr said:**
> Hi ppl!
My laptot is a toshiba L300 with:
Intel processor core 2 duo T2390 1,86GHZ
2GB Ram
So not too god... I cant enable effects. Gets me error and i think its because my laptop doesnt have a dedicated graphic card.
So, is there a way to use a dock without having effects enabled???

CD will work without 'effects' (= Compositing) but will have an ugly black background instead of being transparent. So what you need is just the very basic effect called Transparency. This can be achieved via any of the different 'Compositors', each with their own pro's and cons. So if you have trouble with the built-in or by default installed compositor, switch to another, preferably one with the least system load.

Are you on Xubuntu or Ubuntu (meaning XFCE or GNOME) ?

If you have trouble with Gnome desktop effects, I can recommend installing **xubuntu-desktop** with ```
sudo apt-get install xubuntu-desktop
``` and then logout and select XFCE for your new Session at login... The integrated compositor of XFCE should be enabled by default. Also notice speed improvements over Gnome and much less memory (ab)use ;)

You can also stick with Gnome (or switch back at next login) and install **xcompmgr** with ```
sudo apt-get install xcompmgr
``` and add the command **xcompmgr -c -f -n** to your Session Startup list.

Hope this helps.

---

### Post by RavanH on 2008-06-16
> **davarse said:**
> hi RavanH, i just notice 1 thing about CD mac theme (or maybe other themes too) it doesn't say any thing about the icon, what i mean is just the icon and it doesn't have any writting on it to say what icons are they. is there any way to name the icon (do you know what i mean)?
No idea what you mean, sorry... Do you mean when you right-click an icon and select 'Modify this launcher', you have not got the option to give the launcher a name ?
> **davarse said:**
> and my other question is, i remember my CD on gusty, it has sub-dock on few icon e.g internet has mozilla, ekika, pignin, etc. something like that, and i just realize in CD i have now all the icon become main icon on the dock. how to make sub-dock for those things i.e internet, gimp, etc it's very helpful you know to save the space on the dock....

thanks heaps'
In the latest versions, subdocks have changed a little. You can create sub docks by right clicking anywhere on CD and selecting 'Add a subdock'. Give it a name "**Internet**" and an icon "**web**" (or browse to find an icon for example in /usr/share/cairo-dock/themes/_MacOSX_/launchers/) and select the view to be used. After that, richt-click on each icon you want to move to that sub-dock and select 'Modify this launcher' then click 'Extra parameters' and select the new sub-dock next to 'Name of the container it belongs to...'

But you might also want to create a **second dock** (not sub !). You can do this by right-click an icon that you would like to be on the second dock and select 'Modify this launcher' then click 'Extra parameters' and fill in a new name next to 'Name of the container it belongs to...' The icon will now appear on a small new dock positioned over the _Main Dock_. Richt-click it and select Cairo-Dock > Set up this Dock and you will be able to place it on another screen edge :) . After that, richt-click on each icon you want to move to that sub-dock and select 'Modify this launcher' then click 'Extra parameters' and select the new second dock next to 'Name of the container it belongs to...'

A second (or any 'nd) dock will have the same theme as the main dock. Only and some behaviour the position on the screen can be different. Another difference is that a second dock can not auto-hide.

What to get rid of that second dock again? Just move all launcher-icons on it back to the main dock (see above) and it will be gone again.

---

