---
title: "Stuff I've learned about Wine"
date: 2007-07-10
forum: Wine
---

### Post by cogadh on 2007-07-10
[SIZE=5]**The currently updated version of this document is now part of the Ubuntu Gamers Arena and can be found**[/size] [[size=5]**here**[/size]]("http://gaming.gwos.org/doku.php/wine:winestuff")[size=5]**.**[/size]

I will continue to monitor this thread for suggestions, but rather than maintain two copies of the info, I'll only be updating the UGA version (unless someone convinces me otherwise).
:)


I've been spending a good chunk of the past few weeks working with the latest Wine and Windows games. I've had some pretty good success so far. Along the way, I picked up a few things that might not be so obvious to a new Wine user, but all Wine users should definitely be aware of. These pointers aren't in any particular order, but I did categorize them a bit. If this is useful to anyone, let me know. I'll try to keep the post updated with any new info as I encounter it.

[SIZE="4"][COLOR="DarkRed"]**General stuff**[/COLOR][/SIZE]
[list]
[*]***Wine is not an emulator*** - In fact, the name "WINE" used to be an acronym: "**W**ine **I**s **N**ot an **E**mulator". An emulator is a software program that creates a virtual environment for software to run in. That environment includes virtual representations of the hardware specifically required by the software and the operating system used to run it. That is not what Wine does. Wine is an alternate implementation of the Windows API. It is a compatibility layer that allows Linux to understand Windows executables and allows the Windows executable to understand  Linux. 
[*]***Use the latest Wine version...*** - but be aware that the latest version sometimes includes bugs that were not part of previous working versions. Ubuntu Feisty includes Wine 0.9.33 in the repositories, while the current Wine version is 0.9.40 (as of this writing). Wine 0.9.33 is pretty stable, but later versions of Wine include significant DirectX improvements. I have several games that won't work with 0.9.33, but work great with 0.9.40. However, somewhere between 0.9.37 and 0.9.40, sound in KotOR 2 broke on my system. That is the perfect example of the risk involved in using the latest version.
[*]***Don't compile Wine from source*** - Unless you absolutely have to or you are doing it for the challenge. Every time a new version is released, an Ubuntu .deb of that version is also released on Wine's own Ubuntu repository. See WineHQ's [announcement page]("http://winehq.org/?announce=latest") for download details. WineHQ also has a download page for previous versions of Wine, in case you need to downgrade your Wine version.
[*]***Use the terminal*** - If installed correctly, Wine does associate itself with the .exe file type, so in most cases you can double click on an executable to run it. This, however, is not the recommended way to use Wine. It is better to use Wine from the terminal so that the application paths can be set appropriately (see "Always cd to the game's install path" the the "Regular use stuff" below) otherwise applications will often complain that they can't find needed files. Additionally, running the application from the terminal allows any error messages from Wine to be output to the terminal, which is very useful for troubleshooting purposes.
[*]***Be prepared to work for it*** - Wine is not perfect. Heck, it's not even complete. Not everything will work correctly at first and you may need to spend some time figuring it out on your own. But you're a Linux user now, you should already be prepared to do that on occasion.
[/list]

[SIZE="4"][COLOR="DarkRed"]**Stuff in "winecfg"**[/COLOR][/SIZE]
[list]
[*]***Run "winecfg"*** - You have to run "winecfg" at least once to set up the base Wine directories and devices. Wine won't really work until you do that.
[*]***Emulate Virtual Desktop*** - using this option makes installations run so much smoother. I found instances where attempting to run an installation without this option checked caused some dialog boxes, such as CD key entry or disk swap confirmation, to not come to the front when activated. This led me to believe that the install had become "stuck" and I would end up killing the process. This can also help when troubleshooting a problem game as it won't lock up your desktop or alter your screen resolution to an unusable state when the game fails.
[*]***Use the Applications Settings*** - The Application Settings dialog on the winecfg Applications tab allows you to create some custom configurations for particular executables. At the moment, those configurations are limited to the OS version, some graphics settings and library settings (i.e. DLL overrides). Using the Application Settings allows you to do things like "override this DLL, but only when using blah.exe". This is very useful when a game requires a particular native DLL, but that DLL override is not required by or is bad for other games. I use this for every DLL override I do, just in case an override is potentially bad for Wine. Rather than screw up Wine as a whole, I just screw up that executable's profile. I can just delete that profile without hurting Wine.
[*]***Windows version*** - Try different Windows versions for different applications. Just because a game was made for Windows XP doesn't mean that Wine's Windows 98 support won't work better for the game. I once had an old Windows 3.1/Windows 95 game run best if I set the Windows version to Windows NT 4.0. When you find a Windows version that works, make sure you add an application entry in winecfg for the executable.
[*]***Use the ALSA driver*** -  Some games do require OSS to work, but unless absolutely required, always use ALSA. The OSS driver is no longer being developed and Wine's Alsa support is currently under very active development. Each new release of Wine includes significant sound improvements for ALSA.
[*]***Don't allow the window manager to control the windows*** - Letting the Window manager control the windows will sometimes cause problems with running games in full screen, among other problems. I have found it best to leave it disabled.
NOTE - Current Wine versions (0.9.39+) have corrected the full screen problems for most games and have introduced a new bug that prevents the keyboard from getting focus in the game when the window manager is not controlling the windows. This can be worked around by running the game in its own X session (see example in the "Regular use stuff" section).
[*]***Be careful with library overrides*** -  winecfg gives you the ability to override Wine's built-in DLL files with Windows native DLL files. There are some DLLs that should never be overridden: kernel32.dll, gdi32.dll, user32.dll, and ntdll.dll. If you override those DLLs, Wine will not work at all. Some other DLLs, especially the DirectX DLLs, will not work with games, but they don't prevent Wine itself from working. Just be careful if you override a DLL and make sure you never over-write a Wine DLL, just in case you need to go back to it.
[/list]

[SIZE="4"][COLOR="DarkRed"]**Special configuration stuff**[/COLOR][/SIZE]
[list]
[*]***Create a symbolic link to CD drive*** - Wine creates a symbolic link to the mount directory for your CD drive, but it sometimes helps to also create a symbolic link to the actual /dev entry. I found that if I didn't do this, Wine would create its own symbolic device link and would use it for the E: drive, while my mount directory was linked to the D: drive. I believe this caused issues with some CD-based installs, since two different drives in Wine were now showing identical content. Change the /dev entry on the below code to match your system:
```
$ ln -s /dev/hdc ~/.wine/dosdevices/d\:\: 
```
[*]**[COLOR="Blue"]PERFORMANCE TWEAK[/COLOR]** [***Useful Registry Keys***](http://wiki.winehq.org/UsefulRegistryKeys) - Some features and/or configurations aren't accessible through winecfg, but they can be accessed through Wine's registry. The Wine Wiki maintains a list of those keys and updates it with every new Wine update. Two keys I have found very useful are the Alsa Driver "UseDirectHW" option, which can correct some sound stuttering problems; and the Direct3D "VideoMemorySize" key, which allows you to enter your video card's correct memory amount. Without this key, Wine will automatically report a video memory size of 64MB. Check through the other keys to see what you can use.
[*]***WINEPREFIXCREATE*** - When you first run "winecfg", it runs WINEPREFIXCREATE to create a default .wine directory, but you can use it to create a separate directory for running custom Wine configurations. I have found this useful for running games that require OSS for sound when I prefer to use ALSA. Having a separate directory for those games allows me to run them without having to run "winecfg" first to change my sound settings.
```
wineprefixcreate --prefix .ossgames
```
When running games that are in this directory, I need to modify the launch parameters with the "env WINEPREFIX=" option:
```
env WINEPREFIX="/home/cogadh/.ossgames" wine "C:\Program Files\Game\Game.exe"
```
This environment option needs to be applied when running anything, including "winecfg", on the custom directory.
[*]***Install the Wine Gecko IE engine*** - Some programs require Internet Explorer to be installed in order to run. However, installing Internet Explorer can severely break Wine. Instead, you should install the Wine Gecko IE engine. To install the Geko engine, do this:
[list=1]
[*]Run the following in the terminal: 
```
wine iexplore http://www.winehq.org
```
[*]Answer yes to the install prompt
[*]Go to the [Useful Registry Keys](http://wiki.winehq.org/UsefulRegistryKeys) page and scroll down to the HKEY_LOCAL_MACHINE section. 
[*]Add all of the Internet Explorer keys by using regedit.

**ALTERNATE INSTRUCTIONS**
Occasionally, the Gecko engine may fail to download or install properly. If this happens, do the following:
[list=1]
[*]Open a terminal and manually download/extract the Gecko package by running the following:
NOTE - You will need to install the cabextract package from the repositories to do this
```
wget http://downloads.sourceforge.net/wine/wine_gecko-0.1.0.cab && cabextract wine_gecko-0.1.0.cab
```
[*]Next, run the following to create the directories needed for Gecko:
```
mkdir -p ~/.wine/drive_c/windows/gecko/0.1.0/
```
[*]Place the extracted Gecko files into the newly created directory:
```
mv wine_gecko ~/.wine/drive_c/windows/gecko/0.1.0/
```
[*]Run regedit in the terminal. Go to HKEY_Current_User/Software/Wine/MSHTML and create a new key labelled "0.1.0"
[*]In the new "0.1.0" key, create a new string value labelled "GeckoPath" and set the string value to "c:\windows\gecko\0.1.0\wine_gecko"
[*]Go to the [Useful Registry Keys](http://wiki.winehq.org/UsefulRegistryKeys) page and scroll down to the HKEY_LOCAL_MACHINE section. Add all of the Internet Explorer keys/strings to the registry.
[/list]

Gecko should now be installed properly. To test the Gecko installation, run the following in the terminal: 
```
wine iexplore http://www.winehq.org
```
[/list]
[/list]

[SIZE="4"][COLOR="DarkRed"]**Install stuff**[/COLOR][/SIZE]
[list]
[*]***Use Windows ini files for info*** - Every install CD has an autorun.ini files and will sometimes have a setup.ini file. Checking these files out can help you troubleshoot an installation problem. Sometimes the setup.ini will give you info on what executables are being launched during the install. Knowing this can help you determine where a problem is actually occurring. For example, when trying to install a Windows 95 game, the install kept nearly completing, but would crash before I got the chance to finish. I checked the setup.ini file and found that the setup finished by calling the DirectX install executable and that executable was actually causing the problem. I created a modified setup.ini and removed the DirectX setup entry and the install completed normally (the game ended up not running though).
[*]***Never run an install from the CD directory*** - Don't change directories to the CD drive in order to launch a setup executable. Doing so can sometimes prevent your CD drive from properly ejecting when you need to swap install CDs. Instead launch the install by running this from your home directory: 
```
wine /media/cdrom0/setup.exe
```
[*]***"wine eject" is your friend*** - If an install needs you to switch CDs and the OS complains that you can't eject the CD, then open a new terminal window and run:
```
wine eject d:
```
This will usually eject the current CD and allow the new CD to be automatically mounted. Sometimes the auto mount doesn't work, but the mount can still be performed manually.
[*]***Don't install DirectX*** - Wine has its own DirectX libraries, installing Microsoft's DX will screw up those libraries and Wine in general. Just don't do it.
[*]***Install the InstallShield bugfix*** - There is a [bugfix for InstallShield](http://support.installshield.com/kb/files/Q108322/IkernelUpdate.exe) that can correct some CD install problems. Use it, it will help you.
[*]***Always use the uninstaller*** - Use the terminal command "uninstaller" to launch the Wine uninstaller tool when you want to uninstall games. Don't try using the uninstall shortcuts that a game will sometimes place in the menu during the install. Those shortcuts often don't work right, but the Wine uninstaller tool usually will work.
[*]***.MSI files _can_ be installed*** - Usually Windows applications use an .exe file to install the application. However, occasionally there are applications that use a Windows Installer File with an .msi extension instead (the current version of Steam, for example). There are two ways you can run this type of file in Wine:
```
wine msiexec /i install.msi
```
OR
```
wine start install.msi
```
[/list]

[SIZE="4"][COLOR="DarkRed"]**Regular use stuff**[/COLOR][/SIZE]
[list]
[*]***Use the Wine documentation*** - By that I don't mean "RTFM". Wine has pretty good [Wiki](http://wiki.winehq.org/) now. It is a very dry and boring read, but it does have plenty of useful info.
[*]***Use Wine's*** [***Application Database (AppDB)***](http://appdb.winehq.org/) - Thousands of people are testing Wine on a daily basis and many of us add our experiences to the Wine Application Database in the hopes that it will benefit other users and assist with the further development of Wine. Often AppDB entries will include installation and configuration solutions that other users have come up with. Other times, it may help you identify which games are not worth trying (yet).
[*]***Always cd to the game's install path*** - If you have ever looked at the shortcut properties in Windows, you've probably noticed there are two path fields. One path is the path to actual executable. The other is a path labeled "Run in...". Most Windows executables want to "Run in" the directory they were installed in, changing directories to the executable's install path accomplishes that.
[*]**[COLOR="Blue"]PERFORMANCE TWEAK[/COLOR]** ***Turn off WINEDEBUG*** - When run normally, Wine is constantly producing debug messages (all those "fixme" things). Most of that info is not really needed if you already have a functional game. So to free up those resources, launch the game using the "WINEDEBUG=-all" option. No messages will be generated at all. If you are troubleshooting a game, use the "WINEDEBUG=fixme-all" to remove only the "fixme" messages, which are just developer messages and mean nothing to the normal user.
[*]***Get used to cracks*** - Without completely functional copy protection support, sometimes the only way to get a game to work in Wine is to use a cracked executable. Either get over any apprehension you may have about using cracks, or dual boot Windows and use it for the games that won't work without a crack. Someday we will hopefully have functional copy protection support in Wine and cracks will no longer be an issue.
[*]***NEVER run Wine as root or with sudo*** - Wine is still beta software. Allowing it unrestricted access to the system through the use of a root account or the sudo command can and will cause problems. Just don't do it.
[*]***Other Wine commands*** - Wine has a few commands other than "wine", "winecfg", "wineprefixcreate" and "uninstaller". These commands can prove very useful:
[list=1]
[*]*wineboot* - Simulates a Windows reboot, useful for when an install requires a reboot before it can be used.
[*]*wine control* - Launches the Control Panel. If you install any Windows applications that make use of a Control Panel shortcut, then this is how you access it
[*]*wineserver* - wineserver is automatically launched by the wine command, but it can also be run from a terminal with different switches to different effect:
[list]
[*]-d# - Sets the debug level in the terminal output. You might find a use for that, I never have
[*]-h - Display the wineserver help file
[*]-k - Kill the current wineserver. Useful if an application has locked up and you need to break out of it.
[*]-p - Makes the wineserver persistent, meaning it will continue to run even after the application has closed. Useful if you intend to run several consecutive wine apps, as it can decrease wine load time
[*]-w - Makes wineserver wait until the currently active wineserver exits. Again, you might find a use for that, I never have.
[/list]
[/list]
[*]**[COLOR="Blue"]PERFORMANCE TWEAK[/COLOR]** ***Wine doesn't always like to play nice*** - If you are experiencing slow or choppy performance in a game, it can sometimes be fixed by giving the process a higher scheduling priority. This is done by using the "renice" command after launching a Wine game. The "renice" command allows you to change the priority of a currently running process, i.e. how "nice" a process is to other users on the system (higher priority = less nice, lower priority = more nice). The command has a range of -20 (highest priority) to 19 (lowest priority) and the default priority is 0. In order to use renice, you will need to open a separate terminal and run a command like this, after you have already launched your game/application:
```
sudo renice -10 -n game.exe
```
I don't recommend jumping right to using -20 to run Wine games, start with -10 and if it doesn't improve performance enough, try working up in small increments. You will likely find that most games don't require more than -10 to get the best performance. Also, it goes without saying (I think), that you must be able to ALT-TAB out of the game to run the renice command.

**ALTERNATE INSTRUCTIONS**
For those of you that prefer the GUI method, you can do this instead to renice an app:
[list=1]
[*]Launch the game from a terminal, then ALT-TAB to get back to the desktop
[*]Launch System Monitor (System > Administration > System Monitor) and switch to the Processes tab
[*]Right-click on the running executable and select "Change Priority..."
[*]Move the slider to your desired prority and click "Change Priority"
[*]Enter your user password when prompted
[*]Close System Monitor and ALT-TAB back into the game
[/list]
[/list]

[SIZE="4"][COLOR="DarkRed"]**Third party stuff**[/COLOR][/SIZE]
[list]
[*][***Wine-Doors***]("http://www.wine-doors.org/wordpress/") - Wine-Doors is a graphical application that assists with the installation of many Windows applications, including games. It is currently in alpha development, but does have an initial release available for download. The application itself does look very promising.
[indent]NOTE - Since Wine-Doors is alpha software, it should go without saying, use at your own risk.[/indent]
[*][***Cedega***]("http://www.cedega.com/") - Cedega is technically a fork of Wine, with a specific focus on gaming. Cedega does include a GUI for running installations and launching games, plus it includes some support for copy protection software (you might not need to use a crack with Cedega). Cedega is not free, however. It has a $5 US monthly fee with a three month minimum. A small discount is offered for purchasing a full year in advance.
[indent]NOTE - Cedega was originally called WineX and branched off of the Wine tree when Wine was still under the old MIT license and not the LGPL. Because of this, Cedega does not contribute back to the Wine source tree, as it would if it was covered by the LGPL. It also does not benefit from future updates to Wine. This combined with less than spectacular support leads many people away from Cedega as a Linux gaming solution.[/indent]
[*][***CrossOver***]("http://www.codeweavers.com/") - Technically, CrossOver is not a third party product, as it is the primary financial backer for Wine. CrossOver originally started as a means of running Microsoft Office applications in Linux, but has recently begun adding support for games. CrossOver is based on older, more stable versions of Wine, but as Wine improves and updates, so does CrossOver. It costs $39.95 US to purchase the standard edition.
[*][***ReactOS***]("http://www.reactos.org/en/index.html") - Also a Wine backer like CrossOver, ReactOS is an attempt to create a fully Windows compatible operating system based on much of the work already done in Wine. The ReactOS system, when complete, will be able to use the same drivers and applications that Windows uses, completely natively. The project is currently in alpha stages of development, but there are install CDs, live CDs, QEMU and VMware virtual machine images available for download.
[indent]NOTE - Again, since ReactOS is alpha software, it goes without saying, use at your own risk[/indent]
[/list]

[SIZE="4"][COLOR="DarkRed"]**Advanced stuff**[/COLOR][/SIZE]
[list]
[*]**[COLOR="Blue"]PERFORMANCE TWEAK[/COLOR]** ***Use launch scripts*** - Wine games will often perform their best when they are launched in a separate X server. Wine doesn't require a window manager (Gnome or KDE) to run properly, so if you launch a game in a separate X server, you can get a significant performance boost. You can get an even bigger boost by stopping the GDM/KDM before you launch the game (only to be done from the console).
[list=1]
[*]First you need to create the script. From the terminal, do the following:
```
nano launcher.sh
```
[*]Copy the text below and paste it into the terminal with either the middle mouse button or by clicking on Edit->Paste. Take out the nVidia settings portion if you don't have an nVidia card and modify the application paths to match your game.
```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd "$HOME/.wine/drive_c/Program Files/Game/Directory/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/Game/Directory/game.exe"
```
[*]Save the file in your home directory by pressing CTRL-O, hit enter then CTRL-X to exit. 
[*]Next, make your script executable with this command:
```
chmod +x ~/launcher.sh
```

[*]Launch the game by doing this from a terminal:
```
sh launcher.sh
```
OR
```
./ launcher.sh
```
[*]When you are done playing, do a CTRL-ALT-BACKSPACE to get back to the desktop.
[/list]

**ALTERNATE INSTRUCTIONS**
If your game doesn't work, or if you want to try and squeeze some additional performance out of the game, follows these additional steps to try running it without your default X session still running:
[list=1]
[*]Uncomment the "sudo /etc/init.d/gdm stop" line (remove the "#") in the script and save it. If you use KDE, uncomment the "sudo /etc/init.d/kdm stop" and save the script. 
[*]Close all open applications and switch to the console by pressing CTRL-ALT-F1. 
[*]Log into the console and run the script:
```
sh launcher.sh
```
OR
```
./ launcher.sh
```
You will be prompted for your password and your game will launch in its own X session, without the Gnome or KDE window manager getting in the way. 
[*]If the script complains that you don't have permission to start the X session do this:
```
nano launcher.sh
```
Then modify the X server launch line of the script to read:
```
sudo X :3 -ac & nvidia-settings --load-config-only
```
[INDENT]NOTE - You can avoid having to modify the script by editing the Xwrapper.config file to allow normal users X access. Open the /etc/X11/Xwrapper.config file in a text editor using sudo, then change the "allowed_users=console" entry to "allowed_users=anybody".[/INDENT]

[*]Once you are finished playing, either reboot or do a CTRL-ALT-BACKSPACE to get back to the console and restart your X server and desktop by doing this:
```
sudo /etc/init.d/gdm start
```
If you use KDE, do this instead:
```
sudo /etc/init.d/kdm start
```
The desktop should come right back up immediately, if it doesn't just type "startx".
[/list]
NOTES
[list=1]
[*]If you launch a game in it's own X session, make sure that Wine's virtual desktop has been disabled.
[*]Running a game in its own X server will often correct the problem with a non-functional keyboard in Wine games.
[*]There are additional command line switches that could be applied when launching the new X session see the [Xserver manual]("http://www.x.org/archive/X11R6.9.0/doc/html/Xserver.1.html#sect4") and [Xorg manual]("http://www.x.org/archive/X11R6.9.0/doc/html/Xorg.1.html#sect6") for details.
[/list]
[/list]

---

### Post by Doctoxic on 2007-07-10
thanks for this - some very useful info

cheers

doc

---

### Post by hikaricore on 2007-07-10
Stickied.  ^_^

Attention folks, keep replies on topic or they will be hidden.
I don't want to have to lock cogadh's thread as this makes it a pain to update.

Example (This post has no place here):

[QUOTE=*******]all that has never work for me...[/QUOTE]

---

### Post by merlyn on 2007-07-10
> **hikaricore said:**
> Stickied.  ^_^
^ Legendary move.

---

### Post by jcankrom on 2007-07-10
hey, this is great. this is much more helpful than the wine wiki, IMO.

could you add some tips on what to do if your game runs too slow?
i'm running Starcraft, in case you're wondering, and have seen all kinds of tips from "wine starcraft.exe -gl" to "wine nice -n 20 starcraft.exe" or editing the registry to use opengl instead of direct 3d or using winecfg to emulate hardware acceleration for audio and using winecfg to run it in a virtual desktop. i haven't got a clue what these things do, so i'll just try them all to find out which one works for me. some explanation of the options would be really helpful.
Thanks!

---

### Post by cogadh on 2007-07-10
Those kinds of tweaks are specific to Starcraft only and would not be useful for other games. They are beyond the intended scope of this doc. I wanted this to be a general Wine usage doc, which is why I put the "Use Wine's Application Database (AppDB)" statement in it. The info on AppDB covers most of the game-specific stuff you would need. 

However, I am not opposed to adding a game-specific section, if there is a demand for it. My only concern is that I would just be duplicating information that is already presented in a better fashion somewhere else. Perhaps adding links to good Wine How-Tos instead? Of course, AI has already done that with his "Looking for a game howto?" sticky post.

As for performance tweaks, I did post a few mixed in there, such as turning off debug channels, running in a seperate X server, the useful registry keys. I have flagged those now and as I encounter more, I will add them. If you have any suggestions that aren't game-specific, I'd be happy to add them.

---

### Post by hikaricore on 2007-07-10
If you havn't already (didn't have a chance to recheck) you may want to add a note about the info you discovered [here]("http://ubuntuforums.org/showthread.php?t=493025") for launching new X sessions without root to the part about launcher scripts.  ^_^

---

### Post by cogadh on 2007-07-10
Good call, just added it to the NOTES under the script section.

---

### Post by Cappy on 2007-07-10
I have to use wineprefixcreate to make Ventrilo work properly for me.

---

### Post by dorath on 2007-07-11
I'd love to get some of those launch scripts working, but I can never remember the command to make a script executable.  :(  Any chance you could add a couple extra steps along the lines of:
-This KotOR launch script is saved as wine.kotor (or whatever)
-[command that makes wine.kotor (or whatever) executable]

I'm sure that I'm not the only one who'd appriciate it! :)

Great work , cogadh :)

---

### Post by cogadh on 2007-07-11
**Cappy**, I don't feel comfortable adding a tool that is not recommended by the Wine developers to the document. Do you know what Sidenet did that allowed it to fix your problem, i.e. what Wine config changes did it make that seemed to work? Maybe we can figure out how Sidenet did what it did and we can add that info to the doc.

**dorath**, I added a link into the "NOTES" section to a post I wrote a while back that explains the full script. I also updated that post a bit to include a little more detail. It should have all the info you need to use one of these scripts.

---

### Post by dfreer on 2007-07-12
OMFG greatest thread ever. Especially the script to run games in seperate X session. One question, would you need to change ttyl's in order to use this? Example: <Ctrl>+<Alt>+<F9>?

---

### Post by hikaricore on 2007-07-12
> **dfreer said:**
> OMFG greatest thread ever. Especially the script to run games in seperate X session. One question, would you need to change ttyl's in order to use this? Example: <Ctrl>+<Alt>+<F9>?

When you launch a new X session (as in the script) it should take focus without user input.  So unless something
else steals the focus back it should work every time.  ^_^  You can still switch manually back and forth if needed.

---

### Post by Cappy on 2007-07-13
> **cogadh said:**
> **Cappy**, I don't feel comfortable adding a tool that is not recommended by the Wine developers to the document. Do you know what Sidenet did that allowed it to fix your problem, i.e. what Wine config changes did it make that seemed to work? Maybe we can figure out how Sidenet did what it did and we can add that info to the doc.

Yes that is logical, it doesn't really belong in the document. I just thought someone else might find the tip useful. I don't know what sidenet does that makes ventrilo work for me. It must be something registry related or all of the fake libraries it makes.

I don't have enough time to go through the changes and try to figure out what exactly makes the difference; sorry.

---

### Post by cogadh on 2007-07-13
> **dfreer said:**
> OMFG greatest thread ever. Especially the script to run games in seperate X session. One question, would you need to change ttyl's in order to use this? Example: <Ctrl>+<Alt>+<F9>?
The only time you would need to change tty is if you intend to kill you current X session before launching the new X session for the game, that is explained in detail in the instruction link that I put in the notes section under the script. As hikaricore said, when used as is, the script itself will change to display 3 for you when it launches the new X session. You get back to your original X session by hitting CTRL-ALT-BACKSPACE after you have quit out of the game.

Just for the sake of honesty, I can't claim credit for the simple brilliance of this script, I "borrowed" it from a World of Warcraft how-to I stumbled across while looking for help with a different Wine problem. Unfortunately, I don't know who was the originator of the how-to (can't remember what site I found it on), so I can't give him/her the credit they deserve.

**Cappy** I know what you mean about not having the time, I'll try to mess around with Sidenet a little this weekend, maybe I'll get lucky and find the answer real quick.

EDIT - I decided that having the full script instructions in the post would be more helpful than having a link to a separate post. I added an "Advanced stuff" section that now contains the full details on using the launch script.

---

### Post by Infinity-al on 2007-07-17
i hope you dont mind if i posted this on my newly opened forum [www.ubuntux.info.tm](www.ubuntux.info.tm) over here [http://www.ubuntux.info.tm/viewtopic.php?t=5](http://www.ubuntux.info.tm/viewtopic.php?t=5)...

---

### Post by cogadh on 2007-07-17
I don't mind, just be aware that I do update/edit the orignal post on a semi-regular basis to add new stuff as I encounter it.

---

### Post by hobieone on 2007-07-18
what would be an excellent idea  is to make a data base  where people can contribute  how to get various games running at the best performance and what wine settings thaey are using  some where on the forums. that people will have quick access too. but over allthe information posted here is excellent. and like to say having ussing cedega myself in the past i do fond my self use wine alot more and rarly using cedega and i believe wine has surpassed cedega  when it comes to running games

---

### Post by frodon on 2007-07-18
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by cogadh on 2007-07-18
Like frodon posted, Wine's AppDB already does all that. Its also in the original post, under the "Regular use stuff" section.

---

### Post by dfreer on 2007-07-19
> **hobieone said:**
> what would be an excellent idea  is to make a data base  where people can contribute  how to get various games running at the best performance and what wine settings thaey are using...

0.o was this supposed to be sarcastic?

---

### Post by weblordpepe on 2007-07-19
I know. Someone should make a forum where Ubuntu users can talk about getting games working in Ubuntu.

---

### Post by Infinity-al on 2007-07-20
> **weblordpepe said:**
> I know. Someone should make a forum where Ubuntu users can talk about getting games working in Ubuntu.

I can make one... just need to be sure i will not be the only active member... :(

---

### Post by cogadh on 2007-07-20
Um, you do know he was kidding, right? After all, this is a forum where Ubuntu users can talk about getting games working in Ubuntu.

---

### Post by weblordpepe on 2007-07-21
We can't all be the sharpest tool in the shed :)

---

### Post by gothelin on 2007-07-21
Brilliant!  This information couldn't be more timely as I try to coax a very militant system (I'm sure this laptop has never forgiven me for dropping it that one time...) into running some irreplacable Windows-based programs without leaving the comfort of Linux.  Thanks so much, Cogadh.  :)

---

### Post by vexorian on 2007-07-21
I also learned that sometimes what prevents WINE from running a program is a cyptic and lame CD protection, so getting a no-cd crack makes it easier to run (please don't do this if you don't own the game...)

---

### Post by weblordpepe on 2007-07-22
Nice signature, vexorian. It reminds me of why people run Windows XP on the mac: All the reliability of XP with the cost effectiveness of Apple hardware.

---

### Post by hobieone on 2007-07-22
no my post wasn't ment to be sarcastic. iwas thinking a better databse thane on wine site which  seemes limited to certian games like cedega theres just a lot that is not listed on  ther site plus some of the one that are i noticed  the information is a bit dated plus haveing a ubuntu database  could but  more focused i was thinking due to i have noticed  certian wine functions function slightly different from distro to distro. and  not updated at to how well they function witth the new releases .  but then again  suppose trying to keep any type date  cureent with newer games and setting for a particly release can be a pain to up keep

---

### Post by weblordpepe on 2007-07-22
Its really about Wine, though. Not Ubuntu.
And the Wine App DB already caters for different OSes. Even though really Wine should behave the same.

---

### Post by Cappy on 2007-07-23
-omitted sarcasm-

---

### Post by frodon on 2007-07-23
I think this is not useful since there isn't any ubuntu specific wine settings but just wine setting so commiting to the appdb is really the way to go IMO.
Those who make this kind of request are in general not use to the appdb, it is really a great ressource and really up to date so if we should put a sticky that would be one to point users to the appdb if they want to share tips and so on.

It is just my opinion however.

---

### Post by cogadh on 2007-07-23
I agree, there is nothing Ubuntu-specific about using or configuring Wine effectively; it's the same across all distributions, so why bother with an Ubuntu-specific duplication of AppDB or Wine discussion thread? Instead, everyone who wants to share information on how they did or did not get games working should sign up and become contributors to AppDB. Anyone can do it and the more people contributing to AppDB, the better it will be.

---

### Post by hobieone on 2007-07-28
> **frodon said:**
> I think this is not useful since there isn't any ubuntu specific wine settings but just wine setting so commiting to the appdb is really the way to go IMO.
Those who make this kind of request are in general not use to the appdb, it is really a great ressource and really up to date so if we should put a sticky that would be one to point users to the appdb if they want to share tips and so on.

It is just my opinion however.
the up to date part is not entirely true. yes it a great source but there are a number of apps there that hasn't been updated in over a year  or last updated  with version .9.33  for example  so one doesn't know if the app or game will work with the newer version when it previously didn't plus it only lists the popular apps out there alot of them arn't listed.

---

### Post by cogadh on 2007-07-28
Games that are old or unpopular are really not maintained, true, but if a game worked with a previous version of Wine, the odds are good that it will still work with the current version, plus it doesn't hurt anything to try it anyway. If you are concerned about a particular game that is not updated, then do what I did; become a member and submit your own test results. 

As for only listing "popular apps", that is just not true. If you only look at the main page, then yes, you are only going to see the popular apps. If you use the browse or search functions you will find there are over 4600 different applications listed and almost 2000 of them are games. If the game you are wondering about is not listed, then submit it to the AppDB for inclusion. The only way the AppDB will continue to be useful is if the community that uses Wine contributes to the database.

I guess my point is, if you don't like something about a community project like AppDB, then do something about it by participating in it.

---

### Post by weblordpepe on 2007-07-29
Maybe Wine should put some splash screens hinting about contributing to the App DB.

Perhaps even a message put into the console saying 'Is this app working? Let us know !' And give the URL to the AppDB.

---

### Post by cogadh on 2007-08-03
Minor update, added a section in the "Regular use stuff" on the subject of being "nice". :)

---

### Post by Pioneer5000 on 2007-08-14
Thanks for this.

---

### Post by applegrew on 2007-08-16
Thanks for this stuff. This is an awesome piece of work. I would like to add something to it. The method for manual install of Gecko given here didn't work for me, but anyway I found a working method because it is really manual (it doesn't depend on wine to make the installation). The steps are as below:-

[LIST=1]
[*]First find out the folder where WINE expects your gecko engine should be. To do that type ```
regedit
``` in console. Now navigate to *HKEY_CURRENT_USER\Software\Wine\MSHTML\(It will be some no.)*. Now in the right pane check the value of *GeckoPath*; it could be generally *c:\windows\gecko\0.1.0\wine_gecko*. This is where wine expects to find gecko engine. You can edit value to something else too if you want, but note that the path must be in Windows style as emulated by wine and not the actual Linux path. To find out the actual location of the drive in the path (e.g. C) type```
 ls -l ~/.wine/dosdevices
``` in your console. Now check where the drive links to.
[*]Now [**_download the Gecko engine from here_**]("http://gerwazy.lo3.wroc.pl/~jcaban/wine/wine_gecko.tar.bz2"), or if you face some problem with the former engine then [**_download the old but stable engine from here_**]("http://source.winehq.org/winegecko.php"). You can also get latest stable engine [**_from here_**]("http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=195269"). (**Remark:** Get more info about the first engine [**_from here_**]("http://www.winehq.org/?issue=332#Gecko%20Package%20Update").)
[*]Extract the contents of the previously downloaded to location found in step 1. Note all the dll, etc. must be in the exact location as given in the registry entry.
[/LIST]

Now you are all done. To test that if it has been installed properly type ```
wine iexplore http://applegrew.blogspot.com
``` in your console.

**[COLOR="Red"]UPDATE:[/COLOR]**
I would like to add to point 1.
Note: If you do not find any key (i.e. sub-section) under MSHTML key, then simply add the key. To do that click on MSHTML and then Edit>New>Key from the menu of regedit. Type 0.1.0 for the name of the new key. Now click on this 0.1.0 key and then right click in the right pane>Choose New>String Value. Type GeckoPath for Name and the Windows-style path to your wine_gecko folder.

Please also note that if you use the gecko engine specified as stable in the above post and also the gecko engine hosted on sourceforge.net (version 0.1.0) then even after following all the steps as above, wine will still try to install the gecko engine. A closer inspection of the debug messages in console reveals that wine was expecting gecko versioned as "WIine Gecko 0.1.0" but it gets "Wine Gecko 0.0.1\n". Changing 0.0.1 to 0.1.0 in file VERSION doesn't help because wine from somewhere still reads in the '\n', hence, to correct that please replace file VERSION from the one with the same name in the tar file of the gecko engine specified as latest but unstable in point no. 2.

---

### Post by dfreer on 2007-08-17
@applegrew
Thanks for the gecko install tip! It seems like I always get a 50/50 chance whenever I install a new wine version, on whether or not gecko will install correctly. Next time it doesn't, I'm going to try this tip. 

@cogadh
If the above tip works, it would certainly be worth putting on the front page ;) Gecko support in wine is a bit too buggy IMO.

---

### Post by applegrew on 2007-08-17
I have added a few more tips in my same last post. Pls have a look.

---

### Post by cogadh on 2007-08-17
I will add that info (thanks much for bringing it up), but first, which version of Wine are you using? The problem you describe existed in earlier versions of Wine but is supposedly corrected in the more current versions. 

Also, if you don't mind, I will probably put my own spin on the instructions, there is actually a slightly quicker and cleaner way to do most of what you did from the terminal.

EDIT -  I was doing some checking while working on the update and the version of the Gecko engine that you can get from the default Wine page ([http://source.winehq.org/winegecko.php](http://source.winehq.org/winegecko.php)) is actually slightly newer than the one you get from Jacek's page. I dug a little further and found that Jacek has a zip file on his site that contains the same package as the default Wine Gecko installation. It looks like the tar you can get from Jacek's site is really only for testing and is not stable, but I might be wrong. I don't feel comfortable directing people to potentially unstable code, so I modified things a little more and made the instructions only describe how to manually install the default package.

@dfreer - 
Almost forgot, you shouldn't have to reinstall Gecko when you update Wine. You should only need to reinstall if you delete your .wine directory.

---

### Post by GFree678 on 2007-08-18
I have to say, I'm utterly amazing at how good Wine is these days.

A while back I tried playing the Tomb Raider Anniversary demo and although the graphical effects were fine, the sounds was full of static and, well, unplayable. Now I decided to give the game a shot again, and hey, the sound finally works!

Having said that, it turns out to fix the sound I have to run Wine using ALSA instead of OSS. Last time I tried the demo, it was an older version of Wine and ALSA didn't actually play sound at all. Looks like ALSA's the engine they're devoting all their time in nowadays, am I correct?

Either way, I'm happy! I still advocate native games over the Wine method, but compromises have to be made sometimes I suppose.

EDIT: Eh, spoke/typed too soon. Yes the sound works perfectly now, but for some reason whenever the screen is rendering water, the colours become yellow-tinted, then if you look away to an area where there's no water, the coloring goes back to normal. Weird. Ah well, just a rendering bug. Once they fix this all I'll be able to get the full version properly.

---

### Post by cogadh on 2007-08-18
> **GFree678 said:**
> Looks like ALSA's the engine they're devoting all their time in nowadays, am I correct?
Correct, Maarten Lankhorst proposed making ALSA driver improvement part of the Google summer of code back in March and he has been very busy making that happen starting with Wine 0.9.36. ALSA support is now 90% complete and generally works better than OSS for most games. There are still some games that require OSS to work properly (I think WoW is one), but we are getting much closer to a fully functional ALSA sound system in Wine.

---

### Post by dfreer on 2007-08-18
> **cogadh said:**
> 
@dfreer - 
Almost forgot, you shouldn't have to reinstall Gecko when you update Wine. You should only need to reinstall if you delete your .wine directory.

That's exactly what I'm doing :D
Wasn't there a way to use separate environments for each installed program in older versions of wine, similar to the "Bottles" of Crossover Office? I'm pretty sure IE4Linux used a method like this, to keep it's files in a separate location...

---

### Post by cogadh on 2007-08-18
If you use WINEPREFIXCREATE you can create seperate Wine directories for different applications. That's essentially what "bottles" do. Look under the "Special configuration stuff" in the original post, it explains how to use it there.

---

### Post by applegrew on 2007-08-19
@cogadh
I am using the version 0.9.43 of wine.
Also as I posted the cab file that u get from [http://source.winehq.org/winegecko.php](http://source.winehq.org/winegecko.php) has a problem. The VESRION file of that cab gives incorrect version no. because of that wine will still try to install gecko. I have mentioned its fix.

[quote=cogadh]Also, if you don't mind, I will probably put my own spin on the instructions, there is actually a slightly quicker and cleaner way to do most of what you did from the terminal.[/quote]
Sure. :)

---

### Post by cogadh on 2007-08-19
Hmm, that doesn't make any sense, because when Wine tries to auto install Gecko, it should be reading the Gecko download URL from the registry ([http://source.winehq.org/winegecko.php](http://source.winehq.org/winegecko.php)), but it doesn't seem to get the correct file when you manually download it from that URL. I did find that the correct package is actually the one here: [http://downloads.sourceforge.net/wine/wine_gecko-0.1.0.cab](http://downloads.sourceforge.net/wine/wine_gecko-0.1.0.cab), so I've changed the instructions to reflect that. That way, there is no workaround needed.

---

### Post by vlkoslak on 2007-08-20
I am a big N00B to Ubuntu.  I have followed the directions, but when my x-server session launches I get a "Timidity is not yet configured" error.  I checked my restricted drivers and my Nvidia driver is listed.  
I also ran the command

sudo dpkg-reconfigure xserver-xorg

Have no idea what option to pick.  Did not see Nvdia listed.  I did not want to muck with it because I have no idea what the repercussions are to me making an incorrect change.

Any assistance would be great.  Thanks.
V

---

### Post by cogadh on 2007-08-20
Timidity is a midi software synthesizer and has nothing to do with graphics. I would guess that the game/application you are trying to run uses midi sound and you need to either install or configure Timidity correctly for sound to work and for that error to go away. 

What are you trying to run with Wine?

---

### Post by vlkoslak on 2007-08-20
I am trying to run a game by Bigfish Games: Virtual Villagers 2.  I can run the game in WINE.  The issue is that the keyboard does not respond while in the game.  Sound, mouse and video are all working.

---

### Post by cogadh on 2007-08-20
Have you tried enabling the "Allow window manager to control the windows" option in winecfg? That usually corrects the keyboard issue and if you are using the latest version of Wine it won't introduce the problem where the panels still appear in full screen games.

---

### Post by vlkoslak on 2007-08-21
Ok, I have set "Allow window manager to control the windows" option in winecfg.  I get the following  out put when I save:

err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet

I am running version -- wine-0.9.43

Guild Wars runs fine (But dropps internet connection and I have to reconnect constantly)

SIMS Runs

Virtual Villagers 2 runs, but the keyboard does not respond and when I kill the app I have a frame window that has the text I was trying to type.

Am I at the point of uninstalling WINE and re-install?  How do I make sure that all my WINE packages (gcc, glibc, X libraries, OpenGL (!), ...) E.g. 

Are uptodate.

Thanks

V

---

### Post by cogadh on 2007-08-21
You can ignore all of those error and fixme messages, everyone gets them. The fixme's are just developer messages and mean nothing to users anyway. 

You might have one of those games that just doesn't work fully in Wine yet. I tried to find the game on Wine's AppDB and there doesn't appear to be an entry for it yet, which usually indicates no one has tried it with Wine yet. That also means that the Wine developers have never received a bug report on it and may not have encountered whatever bug you are encountering. You do need to understand that Wine is just beta software, is no where near complete and until it gets to a final release, it will have bugs that prevent some Windows apps from working fully.

Uninstalling/reinstalling Wine probably won't change anything and as long as you haven't been ignoring the Ubuntu Update Manager, everything on your system is already up to date.

Just to clarify, have you tried to run the game using a launch script like I describe in the original post? If so, does the game launch at all?

In the meantime, I'm going to try downloading the demo and see if I can do anything with it.
EDIT - Well that was a waste of time, the demo is a download installer that crashes when run.

---

### Post by vlkoslak on 2007-08-21
When I run your launch script I get the error

 "Timidity is not yet configured" 

That is what started my post :)

Thanks.

V

---

### Post by cogadh on 2007-08-21
Post the launch script you created, maybe there is a minor error in it that we are missing. Make sure you use the forum code tags when you post it, it makes things a lot easier to read.

---

### Post by vlkoslak on 2007-08-21
Ok.

Here is the script

#!/bin/sh
#uncomment if launching from console session
sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia
card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd $HOME/chloe/.wine/drive_c/Program Files/Virtual Villagers - The Lost
Children

# Forces the system to have a break for 2 seconds, X doesn't launch
instantly
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:\Program Files\Virtual Villagers -
The Lost Children\Virtual Villagers - The Lost Children.exe"

---

### Post by cogadh on 2007-08-21
Hmmm, there are some minor errors in it, but some of them may just be because of how the forum formats your post. Try this:
```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia
card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd $HOME/chloe/.wine/drive_c/Program\ Files/Virtual\ Villagers\ -\ The\ Lost\ Children

# Forces the system to have a break for 2 seconds, X doesn't launch instantly
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:\Program Files\Virtual Villagers - The Lost Children\Virtual Villagers - The Lost Children.exe"
```
The "\" character is required on the "cd" command because Linux can't see the spaces in the directory/file names. 

I noticed you have the GDM stop command uncommented. Were you doing the whole "CTRL-ALT-F1, log back in, blah, blah, blah" part of the instructions, or was uncommenting that just an error?

---

### Post by hikaricore on 2007-08-21
> **vlkoslak said:**
> When I run your launch script I get the error

 "Timidity is not yet configured" 

That is what started my post :)

Thanks.

V

This thread really isn't the place for asking alot of questions.
I'll be moving the posts in question to a new thread soon.

Next time I suggest PMing the OP questions about this thread.

_I'm keeping it unlocked so that cogadh and others can updated it._

---

### Post by cogadh on 2007-08-21
Thanks h, this looked like a simple one post problem at first, but it is obviously not.

---

### Post by hikaricore on 2007-08-21
No worries I'm just letting it be known.

---

### Post by gundumfx on 2007-08-30
dam very nice job i knew a lot about wine but after this post i learned a lot thanks an this was useful 
an this 
code 
sudo renice -10 -n game.exe

---

### Post by deadlydeathcone on 2007-09-03
I created a [wrapper script for Wine]("http://ubuntuforums.org/showthread.php?t=533257"), that among other things automatically renices the application being run to -10, as it was getting tiresome doing such fixes manually.

---

### Post by cogadh on 2007-09-03
If I read the script correctly, the command you use *lowers* the running Wine app's scheduling priority to 19 and does not raise it's priority at all. I'm not sure that will actually accomplish what you are trying to do with it.

---

### Post by deadlydeathcone on 2007-09-04
> **cogadh said:**
> If I read the script correctly, the command you use *lowers* the running Wine app's scheduling priority to 19 and does not raise it's priority at all. I'm not sure that will actually accomplish what you are trying to do with it.

For some dumb reason I said -10 when I meant 19, doh.

I've been using 19 as, for me at least, it makes Wine apps run a lot smoother and nearly eliminates sound stuttering. The value I use is from two Con Colivas posts about Cedega in a  [Wine newsletter from 2004]("http://www.kerneltraffic.org/wine/wn20040820_236_print.html#5"):

"See if it's a priority issue on the part of wine*. Be absolutely certain that wineserver, wine and the game are all run the _same_ priority and not a better priority than X. Send me the output of 'top -b -n 1' during the sound being choppy. Then try running _all_ the wine things at nice +19. This is a simple sanity check to see where the problem lies. "
...
 "You do not have different nice levels; that is PRI that is different, which is the "dynamic" priority that constantly changes by the scheduler. It is as I suspected, though - if you renice everything +19 and the problem goes away it is bad programming on the wine developers' part that use what's called sched_yield instead of proper locking between their threads. Don't concern yourself over the details, but at least you have a simple workaround... sigh "

It seems to work best for me, while -10, which comes up a lot, makes things nearly unusable. Still, I just updated the script to allow for custom nice values since others seem to work better for some people.

---

### Post by sleepyjon on 2007-09-14
Thank you, this was very helpful.

---

### Post by Sockerdrickan on 2007-09-22
Stuff I've learned about WINE:
1.It rocks the crap out of what it's goal is to replace.
2.64bit deb compile-guys are lazy :)

---

### Post by cogadh on 2007-10-10
Not everyone can handle Linux or Wine, but just because you are not capable of handling it, does not make it ****. The rest of us have no problems working with either, perhaps if you practiced a little more patience you could learn to use them as well.

---

### Post by brennydoogles on 2007-10-10
> **dark-insignia said:**
> i've learned that wine and ubuntu, not to mention, are both a piece of ****! we should all just use windows instead. life is too short and this is just too ******* complicated!

Translation- We should all let microsoft and AOL think for us, because they know better than we do....

---

### Post by Sockerdrickan on 2007-10-11
Hahaha his post count proves the time spent for trying to learn

---

### Post by nekosama on 2007-10-11
im having some problems getting Unreal Anthology to run in its own X server.  the unreal anthology.exe file is located at /home/callisto/.wine/drive_c/Unreal Anthology/Unreal Anthology.exe.  i typed "nano launcher.sh" in terminal and copy/pasted the text as instructed and modified it as follows:

#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia
card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd "$HOME/.wine/drive_c/Unreal Anthology/"

# Forces the system to have a break for 2 seconds, X doesn't launch
instantly
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Unreal
Anthology/Unreal Anthology.exe"

after saving and exiting i typed "sh launcher.sh" into the terminal and got the following:

callisto@Binah:~$ sh launcher.sh
launcher.sh: 8: card: not found
X: user not authorized to run the X server, aborting.
launcher.sh: 16: instantly: not found
wine: cannot find 'C:/Unreal 
Anthology/Unreal Anthology.exe'
callisto@Binah:~$ 

any ideas?

it may be worth mentioning that it launches just fine from either winefile or the "wine Unreal Anthology.exe" command in the terminal.  however when playing UT 2004 the mouse will stop at the edge of the screen and i can only turn in about a 120 degree arc, thus making the game virtually unplayable.  ive messed around with all the graphic settings in winecfg as well as in UT itself and nothing so far has worked.  it occurred to me that if the game ran in its own X server it might work, but i honestly dont know it will or not.

---

### Post by cogadh on 2007-10-12
If you don't have an Nvidia graphics card and the Nvidia drivers installed, you need to take out the "& nvidia-settings --load-config-only". That could be why it is saying "card: not found".

As for the permissions thing, there are two ways to get around it:
[LIST=1]
[*]Add a "sudo" to the X launch line:
```
sudo X :3 -ac & nvidia-settings --load-config-only
```
[*]Modify your Xwrapper.config file to allow anyone permission to launch the X server:
```
sudo gedit /etc/X11/Xwrapper.config
```
Change the line that says "allowed_users=console" to "allowed_users=anybody"
[/LIST]

---

### Post by jso2897 on 2007-10-13
> **dark-insignia said:**
> i've learned that wine and ubuntu, not to mention, are both a piece of ****! we should all just use windows instead. life is too short and this is just too ******* complicated!

Mom?

---

### Post by hikaricore on 2007-10-14
> **jso2897 said:**
> Mom?

The next person who feels the need to quote this crap comment will get infracted.

KEEP THIS THREAD CLEAN.

---

### Post by deadlydeathcone on 2007-10-14
I forgot to say this the first time around, but ... thanks for this thread! It's been insanely useful.

I just want to add a few (somewhat) useful things I figured out while foraging through Wine's documentation for things to add to my script:

In all cases $WINECOMMAND = name of Windows executable.

Run a Windows Link ( .lnk )
```
strings "$WINECOMMAND" | grep ".:\.*"
```

Add it to the Gnome menu
```
wine winemenubuilder "$WINECOMMAND"
```

Open a Windows Url ( .url )
```
url=`grep -o -m 1 "URL.*" "$WINECOMMAND" | sed 's/URL=//'` && xdg-open "$url"
```

Convert a Dos path to Unix, and vice-versa
```
man winepath
```

Run an application in it's own virtual Windows desktop:
```
wine explorer /desktop=wine,1024x768 "$WINECOMMAND"
```

---

### Post by TheThinker on 2007-10-15
Thanks Codagh for your info; now I can try to swap CDs during game installations without fear of failing! Yay!

---

### Post by cogadh on 2007-10-15
You're welcome. :)

Ack! It's Co**gad**h, not Co**dag**h, totally changes the meaning of the word.

---

### Post by balthamaisteri on 2007-10-16
Very nice list :)

---

### Post by bereanone on 2007-10-16
Well here is a few things I ]have learned about wine:
On my hp laptop it runs one of my Windows program better/faster than native...but...On my Compaq Presario with Athlon Chip  desktop? As of today Oct 16,2007 with the latest Gutsy download it does not run AT ALL.  On my laptop running the uninstall causes total screen corruption.  The screen goes black and in order to see anything, you have to move the cursor around and whatever it crosses over gets redrawn (sometimes) and finally most of it (not all) comes back.  Total recovery requires reboot.  I mistakenly deleted some files trying to uninstall a failed iTunes install and now cannot get wine to fix it.  I have tried looking for support in Winehq chat rooms, but that is a tedious fruitless waste of time.  Anyone wanting to email me with a better support fix is welcome.  I have tried Crossover but can't get ANYTHING to run with it.

---

### Post by cogadh on 2007-10-16
Sounds like your .wine directory is corrupted. I'd try deleting or renaming it, then run winecfg to create a new one and see if the problem continues.

---

### Post by YokoZar on 2007-10-16
cogadh, can you please remove Winetools from the initial post?  It's quite useless now, and I've seen way too many threads by confused users still trying to get Winetools to do something.

---

### Post by cogadh on 2007-10-16
Done. I noticed that WineHQ has also moved Winetools into the "Obsolete" section of their third party applications list.

Hey, has anyone tried out PlayOnLinux and if so, how good is it? Would it be worth adding to the list of third party apps?

---

### Post by YokoZar on 2007-10-16
You might also want to make a note that when a user upgrades from Feisty to Gutsy they will need to install the newer, Gutsy repository by refollowing the instructions here:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

(that page should be updated within the next day, by the way).

---

### Post by bsmith1051 on 2007-10-16
Have any of these 'tricks' been added to the base Wine product yet, or can they become default settings, or activate automatically?  (Did I already ask this?)

---

### Post by cogadh on 2007-10-16
Technically they are all part of the product already, they just aren't necessarily default settings or accessible through a GUI. Wine is still a beta product so I would expect to see some of these things to become less obscure (or even unecessary) once it gets to a "final" release.

---

### Post by Yeeha on 2007-11-05
Do anyone knows how to get old 16 bit graphic games to work, i have googled around but... cant find any solutions to: fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
This problem seems to creep every 16 bit graphic game i have tryed :/ .

---

### Post by cogadh on 2007-11-05
As long as you have 16 BPP enabled in your xorg.conf, they _should_ work.

---

### Post by Peter6218 on 2007-11-05
Gutsy's version of Wine does not support Eudora while Feisty's does.

As a result I'm back to Feisty!!

---

### Post by frodon on 2007-11-05
I think it would have been easier to just remove the wine gutsy package and install the version that worked for you, all the packages can be found here (feisty packages should work with gutsy):
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by Peter6218 on 2007-11-05
> **frodon said:**
> I think it would have been easier to just remove the wine gutsy package and install the version that worked for you, all the packages can be found here (feisty packages should work with gutsy):
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Thanks, will try that next time I install Gutsy

---

### Post by Celeb on 2007-11-05
There is one on line game i would like to play on Ubuntu and that is Lineage 2 ( Chronicle 5 ). And i would like to know if any user would help me with mi Q about using wine to help me in it.

---

### Post by cogadh on 2007-11-05
Just to remind everyone, this thread is not for asking for help with specific applications, it is only for requesting/adding content to the OP. If you need help with a specific application, either find a thread that already deals with that app and add to it or start a new thread. I don't want to have to ask the mods to close the thread to further posting, it has proved way too useful in updating the original document.

---

### Post by HalloweenB on 2007-11-08
I have a question on the performance tweaks listed in the original post.

To turn off the Wine Debug function, it mentions to launch your game using "winedebug=-all".  How exactly is that entered in the terminal?

In my case, I use Wine for WoW and I launch the game using:

wine "WoW.exe" (once I am in the WoW directory already)

So my question is how do I insert the windebug code?


thanks

---

### Post by cogadh on 2007-11-08
Like this:
```
WINEDEBUG=-all wine WoW.exe
```
I didn't notice until just now that I had an error in that section that left out the wine command in the sample. It's fixed now.

---

### Post by HalloweenB on 2007-11-08
That solved it.  Thanks for the quick reply.

Regarding video memory size, on the Wine homepage I believe it says Wine defaults to recognizing 64MB of video memory.  Do we need to input the correct video size in Winecfg or in the WTF file somewhere?

I have an older PC with a GeForce AGP FX5500 with 256MB of memory, and was wondering if 256 MB was automatically detected somewhere.  My framerate is about the same with Windoughs and Ubuntu, but the keyboard response and character movements in WoW feel more faster or 'immediate'  with Ubuntu.

:guitar:

---

### Post by cogadh on 2007-11-08
VRAM is not automatically detected, but you can manually set it using a registry edit. Check the "Special configuration stuff" section for details.

---

### Post by FG123 on 2007-11-08
/offtopic

cogadh, you never seem to post in anything other that the gaming forums. I'm sure you're very useful for providing info and advice related to Ubuntu/Linux gaming, but come on man, take a trip down Community Cafe once in a while. I'll be fun! :)

---

### Post by cogadh on 2007-11-08
Ha! I do poke my head in there every now and then, usually just to start trouble. :twisted:

I just tend to spend much more time here and in the UGA forums, this my Ubuntu forums "comfort zone".8-)

---

### Post by FG123 on 2007-11-08
Hehe, oh then. ;)

---

### Post by baqai on 2007-11-21
Excellent thread, i would request few additions to the write up

If one is using a physical CD than wine eject will work but what should one do if we are using virtual drives / images mounted? i tried to eject the virtual drive but had no success maybe i am doing something wrong, using AcetoneISO2 

```

wine eject /home/me/virtual-drives/1

```

which of course is not going to work since wine eject is going to understand the windows sentex (if i am not wrong?) 

Any work around besides installing Daemon Tools in Wine?

---

### Post by burt_57 on 2007-11-24
> **baqai said:**
> Excellent thread, i would request few additions to the write up

If one is using a physical CD than wine eject will work but what should one do if we are using virtual drives / images mounted? i tried to eject the virtual drive but had no success maybe i am doing something wrong, using AcetoneISO2 

```

wine eject /home/me/virtual-drives/1

```

which of course is not going to work since wine eject is going to understand the windows sentex (if i am not wrong?) 

Any work around besides installing Daemon Tools in Wine?

Wine ......Wine ....oh my I believe it should just be made has a drink "wine " than having is as an simulator :lolflag:

---

### Post by cogadh on 2007-11-24
> **baqai said:**
> Excellent thread, i would request few additions to the write up

If one is using a physical CD than wine eject will work but what should one do if we are using virtual drives / images mounted? i tried to eject the virtual drive but had no success maybe i am doing something wrong, using AcetoneISO2 

```

wine eject /home/me/virtual-drives/1

```

which of course is not going to work since wine eject is going to understand the windows sentex (if i am not wrong?) 

Any work around besides installing Daemon Tools in Wine?
Keep in mind that I have never tried this but...

In theory, if you mount the image in Linux then set up a fake CD-ROM drive in winecfg that uses the image's mount point as the Linux path of the CD-ROM drive, then running the "wine eject X:" command should just unmount the image (where "X:" is the drive letter you chose for the fake CD-ROM drive). Then you could mount a different image to the same point and Wine should detect it as if you swapped CDs in a normal drive.

Like I said, I've never tried it myself, but I see no reason it shouldn't work.

---

### Post by baqai on 2007-11-25
Well i tried adding a drive in wine and gave the path to the virtual drive, than went to advance and set the drive as CDROM but when i try to eject it wine gives me an error 

will see if i can figure out some way to fix this problem

---

### Post by ericesque on 2007-11-29
I'll add my thanks!  I managed to get BF2 installed.  The ground is blue and the sky is black... but like you said, be prepared to work for it :)

One suggestion that may help others, the command to eject cds:
wine eject x:     (where 'x' is your cd-rom drive letter)

didn't work for me.  BUT

wine eject -a

will eject all cd-rom devices that Wine finds-- which DID work for me.

---

### Post by cogadh on 2007-11-29
Interesting that specifying your CD-ROM drive letter didn't work, I've never run into that before (hence why the "-a" option wasn't in the doc before). I just learned something new, updated the doc. Thanks!

---

### Post by manuthomas on 2007-12-03
hi,
i am only a 'new bie' and is trying to install my PVR in ubuntu linux 7.04
as i was unsuccessful with installing it as a native linux, i tried installing it thru wine(when i failed to run the already installed program in windowsXP). but is getting the following errors.

> 
root@doriz:~# wine /home/manu/EasyTV/EasyTV\ MPEG.exe 
err:module:import_dll Library ksuser.dll (which is needed by L"Z:\\home\\manu\\EasyTV\\ksproxy.ax") not found
err:module:import_dll Library ksproxy.ax (which is needed by L"Z:\\home\\manu\\EasyTV\\EasyTV MPEG.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\manu\\EasyTV\\EasyTV MPEG.exe" failed, status c0000135

is there a possibility of running the windows PVR software in linux like this?
how do i tell wine to check up the mentioned DLLs at the right location?

by using the command "lspci"i the details of my TV tuner card is shown as 

> 05:05.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

this would be of great help as i am longing to see my TV in linux!
...thanx in advance
...manu

---

### Post by cogadh on 2007-12-03
This thread is not supposed to be for asking for help with specific applications, even though we have answered a few quick questions in it already. This problem sounds like an issue that is going to take much more than just a quick answer. Please create a new thread in the forums asking for assistance with this.

---

### Post by hikaricore on 2007-12-04
Removed his post.  It was a dup of his thread anyway.  Stop being greedy people.

---

### Post by AndrewRiedi on 2007-12-22
Nice information.  A few things though.

1) Wine is now LGPL, not GPL.

2) Adding it to the [Wine Wiki]("http://wiki.winehq.org") might be of use.  This way it can be updated and overlooked by the main Wine developers and testers.

3) Related to (2), what license is this guide released under?  Public domain?  LGPLv2.1+?

Public domain and LGPL are the only two above that would be compatible with the [Wine Wiki License]("http://wiki.winehq.org/WikiLicense").  Of course, whether you want it in the Wiki is up to you.

---

### Post by cogadh on 2007-12-22
1. Whoops, fixed

2. Most of the info from it is taken from the Wine Wiki and other related sources. Adding it to the Wiki would be kind of redundant.

3. License? It's a forum post that has been duplicated on a gaming wiki website. I don't own either site and I'm pretty sure there would be no licensing attached.

---

### Post by hOmerscousin on 2007-12-23
Hey Everyone,

I've been reading all of these posts and attempting to follow along... I am a Noob. Its been interesting trying all of this out. I can't seem to get the launch script to perform correctly. When I run it I get a grey screen with an "X" as my mouse pointer. 

this is my script:

#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac
#nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd $HOME/rdaltreche/.wine/drive_c/Program\ Files/Starcraft

# Forces the system to have a break for 2 seconds, X doesn't launch instantly
sleep 2
 
# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine StarCraft.exe

Also, when I ctrl+alt+backspace back to my desktop i checked my terminal and it gave me this error:

t your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

Any ideas? I have no idea which driver it referring to. Thank you!

---

### Post by hOmerscousin on 2007-12-23
Also, I'm running 0.0.46-0ubuntu1 version of wine. The game without the script except that its really slow even with nice set to -17. Cool, thanks

---

### Post by cogadh on 2007-12-23
This thread is not for asking for help, it is only for making suggested additions to the original doc. You would be better of creating your own post and asking this question.

---

### Post by AndrewRiedi on 2007-12-28
Cool.  Thanks for the information.

---

### Post by mongoose_za on 2008-01-02
wow nice post. Bookmarked for sure. Followed pretty much everything that i can understand and got my warcraft running. it's just that it runs so slow still :( like 6fps.

---

### Post by akurashy on 2008-01-06
alright I got to be sure I'm doing this right

[http://img112.imageshack.us/img112/1950/usermt4.png](http://img112.imageshack.us/img112/1950/usermt4.png)

Is it creating the folder or adding the strings ?

I'm doing the regedit since I found it interesting... need to be sure I'm implementing it right

---

### Post by negerbarn on 2008-01-17
Thansk :D

---

### Post by sonofabics on 2008-01-22
wow thanks for this. It is really great!!!
:guitar:

---

### Post by SoliDphantoM on 2008-02-12
nI was trying launch a new x session with the script and the session was working, but the game was not launching....

I found in another thread why.

Since I didn't see this when I skimmed the thread and it wasn't revised in the OP, I thought I'd share this:

```
# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac & nvidia-settings --load-config-only
```

If you don't have a Nvidia card do NOT take out the "&", if you do the game does not launch in the new session.
So the edited script without the Nvidia settings should look like this:

```
X :3 -ac &
```

---

### Post by eggbloke on 2008-02-22
thanks!
steam is now working!
although a lot of the words are missing so i have to guess what to press :S

---

### Post by vexorian on 2008-04-08
> sudo renice -10 -n game.exe
Did you know this doesn't work?

renice needs a pid.

I am currently looking for a way to use pgrep so this works.

Edit:

```
sudo renice -10 $(pgrep game.exe)
```

Edit: And now that I use the correct renice syntax, GTA:SA's performance has been improved significantly.

---

### Post by KBA3AP on 2008-04-10
"Wine supports using native DLLs when the built-in versions don't function properly. In many cases, it's possible to use native DLL versions to gain access to 100% of the functions an application requires." (taken from here [http://wiki.winehq.org/Debunking_Wine_Myths](http://wiki.winehq.org/Debunking_Wine_Myths))
I assume this means one could simply copy-paste all DLLs(except wine-critical ones like DirectX) from the owned Wndows version, where the software works 100% and that would ensure on-wine functionality(that is, excluding programs that use wine-critical DLLs). And, while this is unusable for wine development, it could be used to fix programs, that don't work with simple tweaks.
I.e. say i need to be able to run 10-15 windows-specific programs, and am not willing to tweak wine for each of those, but have access to DLLs of the windows version where they do work.

---

### Post by cogadh on 2008-04-10
You can actually override any Wine DLL *except* kernel32.dll, gdi32.dll, user32.dll, and ntdll.dll (you can override the DirectX DLLs if you want, but in many cases, the Wine versions are going to work better anyway). If you were to override any of those 4 DLLs, Wine would no longer work.

The process is not as simple as just copy/past the Windows DLLs, you also have to run winecfg and apply a library override for each DLL you copy/paste. No matter what, you will have to do some tweaking.

You should only apply a DLL override if the application you are trying to run returns a specific error related to a specific DLL. You can then try to override that particular DLL to see if that corrects the issue. You will probably find that using the new DLL will eliminate the original error, but you will then get different errors that may require additional DLL overrides to fix. 

Automatically overriding all Wine DLLs with Windows native DLLs is a really bad idea. There is absolutely no guarantee that using a Windows native DLL will make any difference whatsoever in how your program runs. Sometimes, the Windows native DLLs are actually worse than the Wine ones and you will end up with a Wine installation that is incapable of running anything.

---

### Post by KBA3AP on 2008-04-10
Well, applying a _specific_ DLL override would require knowing what exactly you need, and if it's not the case(i.e. program crashes/doesn't start for no apparent reason), you cannot do it.

Hm, I'm probably missing something, since wine is not an emulator, all it does is provide windows-specific resourses to the windows-specific software and visa verse, am I right? So, in case of a wrong/old DLL, resources required <>  provided, which = program failure, and in case of a right DLL, resources required == provided, which = program successful functionality.
Obviously it isn't always about the DLLs but I'd say most of the time for the older programs.

---

### Post by vexorian on 2008-04-10
WINE is most likely to provide all the windows' dll functionality, but a couple of functions that are instead replace with stubs.

If your program requires a non-windows third party dll, you can just place the dll in the same folder you got the .exe in (just like in windows)

---

### Post by cogadh on 2008-04-10
> **KBA3AP said:**
> Well, applying a _specific_ DLL override would require knowing what exactly you need, and if it's not the case(i.e. program crashes/doesn't start for no apparent reason), you cannot do it.

Hm, I'm probably missing something, since wine is not an emulator, all it does is provide windows-specific resourses to the windows-specific software and visa verse, am I right? So, in case of a wrong/old DLL, resources required <>  provided, which = program failure, and in case of a right DLL, resources required == provided, which = program successful functionality.
Obviously it isn't always about the DLLs but I'd say most of the time for the older programs.
It is actually relatively easy to figure out what DLLs you might need to override. If the application itself doesn't give you an error saying something like "foo.dll caused an error", then the terminal messages that Wine produces will tell you exactly what went wrong. Of course, that assumes that you are using Wine from the terminal (which you should).

If the DLL you are having a problem with is not a MS DLL, then like vexorian said, you can usually just drop it into the install directory (or system32) and it will work fine. You shouldn't even need to apply an override in winecfg for most third-party DLLs. You usually don't have to worry too much about third party DLLs, since any app that requires them will usually install them as required already.

---

### Post by dabski on 2008-04-14
I was stuffing around today and found out about the -terminate switch. I haven't seen anyone else do this so I thought I'd be the first to share it with the community :)
If you changing this line:
```
sudo X :3 -ac & nvidia-settings --load-config-only
```
to
```
sudo X :3 -ac -terminate & nvidia-settings --load-config-only
```
then you don't need to do CTRL+ALT+BACKSPACE after exiting your game. Works really well on XFCE with no login manager since I'm automatically dumped back into my original X session.

---

### Post by cogadh on 2008-04-14
Ha, learn something new every day!

Thanks! I'll mess around with it some in KDE and Gnome then add it to the doc (as long as it doesn't have any problems).

---

### Post by gsmanners on 2008-04-16
How to run Wine without the network:

- add user "highwire" (because this user works without a net):

```
sudo adduser highwire
```

- give password, other info then set up iptables:

```
sudo iptables -I OUTPUT -m owner --uid-owner highwire -j REJECT --reject-with icmp-net-unreachable
```

- log out, log back in as "highwire"
- load up Firefox (or some other web browser) and make sure that the net is unreachable
- open a terminal and type:

```
winecfg
```

- now you should be ready to use Wine without having to worry about network interference

(The line for iptables was taken from [this entry in Wine-Wiki]("http://wiki.jswindle.com/index.php/Advanced_Wine_User_Information#Blocking_Network_access_to_Software_running_on_Wine").)

---

### Post by cogadh on 2008-04-16
Just curious, but is there any reason to run Wine without the network?

---

### Post by gsmanners on 2008-04-16
I worry more about security issues with Windows programs since I don't do a good job of keeping them up to date, so this is to assure myself that I'm not making my computer more vulnerable somehow.

---

### Post by cogadh on 2008-04-16
That's reasonable, but as long as you aren't running Wine with root permissions (which you shouldn't do anyway), malicious Windows programs can't really do much more than possibly damage your .wine directory. That is easily fixed by just creating a new one.

---

### Post by victor.zamanian on 2008-04-29
This was worth its weight in gold for me. (I had troubles getting gecko installing on Ubuntu 8.04, for wine.) Thanks a lot!

---

### Post by Joshgo on 2008-05-10
I'm stuck here, I don't know how to do the following:

NOTE - You can avoid having to modify the script by editing the Xwrapper.config file to allow normal users X access. Open the /etc/X11/Xwrapper.config file in a text editor using sudo, then change the "allowed_users=console" entry to "allowed_users=anybody".

How do I open it using sudo? What is the command? Help is greatly appreciated.

---

### Post by cogadh on 2008-05-10
```
sudo nano /etc/X11/Xwrapper.config
```
Or if you prefer a graphical text edotr:
```
gksudo gedit /etc/X11/Xwrapper.config
```

---

### Post by OmniCloud on 2008-06-05
> **cogadh said:**
> That's reasonable, but as long as you aren't running Wine with root permissions (which you shouldn't do anyway), malicious Windows programs can't really do much more than possibly damage your .wine directory. That is easily fixed by just creating a new one.Good post...

I just erased my drive completely with all the partitions I had on it and now just run Xubuntu completely. 

I'm having a bit of trouble getting my watchtower application to work under Wine though. TBH--after installation, a double-click of the desktop Icon ran the program automatically so I never really played around with Wine in the terminal too much. Since that's the only Windows app I need to run. A few questions for you my fried.

My wine application ran automatically after installation on my Gnome Hardy setup, but I can't get a response in Xfce? Same version of wine, same OS, is this a desktop difference issue here?

Second question, when I click the desktop icon, there isn't an error message, it's just no response. Same with going into my /.wine folder and trying to run the .exe or any other command. In fact, the only thing I get a response from is to installing or removing the application? 

Third, how do you actually run wine in the terminal? copy and paste the command from the desktop icon file?

---

### Post by cogadh on 2008-06-05
I'm really not familiar with XFCE, I've only really used Gnome and KDE regularly. I supposed XFCE could make a difference, but I can't really say how exactly.

You often won't get error messages from application run with Wine, they usually tend to fail silently, unless...

...you run the app from the terminal, where Wine can output its own error messages. To run an application in Wine from the terminal, simly open the terminal, change directories to where the app is installed, then "wine" the executable:
```
cd ~/.wine/drive_c/Program\ Files/<install directory>
wine <executable name>.exe
```

---

### Post by OmniCloud on 2008-06-05
> **cogadh said:**
> I'm really not familiar with XFCE, I've only really used Gnome and KDE regularly. I supposed XFCE could make a difference, but I can't really say how exactly.

You often won't get error messages from application run with Wine, they usually tend to fail silently, unless...

...you run the app from the terminal, where Wine can output its own error messages. To run an application in Wine from the terminal, simly open the terminal, change directories to where the app is installed, then "wine" the executable:
```
cd ~/.wine/drive_c/Program\ Files/<install directory>
wine <executable name>.exe
```cool cool...I was reading some info on the data base and a user said I can't run Watchtower without MS core fonts installed. 

So after getting that i'll try it in the terminal. Tks for the reply!

Btw--I used to play a lot of Starcraft when I was little, I think I downloaded from Kazaa or something back in the 90's? You know where I could find an old game like that--frostwire maybe? Game was crazy fun--and I don't really like the new online-only Strategy games that's coming out now...

---

### Post by cogadh on 2008-06-05
Discussion of pirated software is frowned upon in these forums. If you want to play Starcraft, just buy it, it's still available as part of the "Starcraft Battle Chest" with all expansion packs in most stores. Last time I saw it, it was only about $20.

---

### Post by OmniCloud on 2008-06-05
> **cogadh said:**
> Discussion of pirated software is frowned upon in these forums. If you want to play Starcraft, just buy it, it's still available as part of the "Starcraft Battle Chest" with all expansion packs in most stores. Last time I saw it, it was only about $20.
I feel you..I'll probably just partition XP back on my system as well...

don't feel like going through the hassle of all the configuration just to play an old game. 

Then again, it might be years before I ever get around to having time to play PC games again. I'm happy with my Playstation/Wii for now lol...

---

### Post by OmniCloud on 2008-06-05
> **cogadh said:**
> I'm really not familiar with XFCE, I've only really used Gnome and KDE regularly. I supposed XFCE could make a difference, but I can't really say how exactly.

You often won't get error messages from application run with Wine, they usually tend to fail silently, unless...

...you run the app from the terminal, where Wine can output its own error messages. To run an application in Wine from the terminal, simly open the terminal, change directories to where the app is installed, then "wine" the executable:
```
cd ~/.wine/drive_c/Program\ Files/<install directory>
wine <executable name>.exe
```ok, here's a screenshot to help a bit...

1) I can't cd to Program files in a terminal which is where Watchtower app is installed. 



2) When trying to browse the Wine c:: drive I get an error--which maybe the cause of all this nonsense--it says "c: drive is not supported"

3) Should I try to install it to a different directory when doing the installation?

[[img]http://xs128.xs.to/xs128/08234/2008-06-05-171736_1280x1024_scrot329.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs128&d=08234&f=2008-06-05-171736_1280x1024_scrot329.png)

---

### Post by cogadh on 2008-06-05
Did you use "sudo" to run Wine at all?

BTW - Where's the screenshot?

---

### Post by OmniCloud on 2008-06-05
> **cogadh said:**
> Did you use "sudo" to run Wine at all?

BTW - Where's the screenshot?trying now...reload its up I don't really know what I need to sudo...

I'm just trying to cd into the place where the app is and can't reach it...

---

### Post by OmniCloud on 2008-06-05
btw I"m using the latest version of Wine...don't have any other apps installed besides Watchtower 07. Run a Dell Pen4 with Intel card with about a gig of memory...

Xfce manager Xubntu hardy;)

---

### Post by cogadh on 2008-06-05
That was a question, not a suggestion. You should never use sudo to run Wine, it screws up the permissions on the .wine directory and allows Windows applications, including malware, full access to the Linux system. I was only asking because it might explain why you are having problems accessing the .wine directory. If you have gone and used sudo, you now need to delete the .wine directory and start fresh with a new one:
```
sudo rm -r ~/.wine
winecfg
```

---

### Post by logos34 on 2008-06-05
Every time I try to launch Exact Audio Copy I get this message:

> Unhandled exception

at WndProcs.741 ->INDEX-RANGE 

EAC never even appears.  How can I get rid of it/fix it?

EAC on wine has worked perfectly until now (Hardy).

---

### Post by cogadh on 2008-06-05
Okay, I am already breaking my own rules about this thread. I never meant for it to be used for supporting individual problems, just suggestions for future additions to the original topic. I think we should take any future issues into their own threads for now.

logos34, unfortunately, I had already looked at your original post with this problem, and I have absolutely no idea why you are getting that error. It might help if you were to run the application from the terminal and post any output from Wine itself on the issue (in your original thread, of course).

---

### Post by logos34 on 2008-06-05
Thanks for the reply.  Normally I wouldn't ask, but I'm kind of desperate.

I ran

winedebug .wine/drive_c/Program\ Files/Exact\ Audio\ Copy/EAC.exe 

but no output exept for same error popup.

I've tried just about everything I can think of.  Actually, I don't think Wine is at fault here, I just wanted to know if there was a way to clear the error message in the hopes that would unblock EAC and allow it to launch.

Is, there a winedebug (verbose) command?

thanks

---

### Post by cogadh on 2008-06-05
Don't bother with the debug channels, start with just running the app normally in Wine through the terminal. If that doesn't produce any informative errors (it will definitely give you something), *then* use the debug channels. Information on how to use the debug channels can be found here:
[http://wiki.winehq.org/DebugChannels](http://wiki.winehq.org/DebugChannels)

---

### Post by logos34 on 2008-06-05
ok, I'll check it out

---

### Post by RealG187 on 2008-07-24
> **cogadh said:**
> ***Get used to cracks*** - Without completely functional copy protection support, sometimes the only way to get a game to work in Wine is to use a cracked executable. Either get over any apprehension you may have about using cracks, or dual boot Windows and use it for the games that won't work without a crack. Someday we will hopefully have functional copy protection support in Wine and cracks will no longer be an issue.

I never thought I would hear something like that here! Can you say that?

About the copy protection support, I oppose [DRM]("http://bestwikiever.wikidot.com/DRM") entirely, compatibility being one, another being violating user's rights.

Ubisoft stole a scene crack and used it as a fix for one of their games. That's how good they are!

---

### Post by Aravindvs on 2008-07-30
Thanks Man! Your Are Awesome!

---

### Post by kidux on 2008-07-31
> **SoliDphantoM said:**
> nI was trying launch a new x session with the script and the session was working, but the game was not launching....

I found in another thread why.

Since I didn't see this when I skimmed the thread and it wasn't revised in the OP, I thought I'd share this:

```
# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac & nvidia-settings --load-config-only
```

If you don't have a Nvidia card do NOT take out the "&", if you do the game does not launch in the new session.
So the edited script without the Nvidia settings should look like this:

```
X :3 -ac &
```

Thanks for this man, it works great now!!!

---

### Post by riggity_ryan on 2008-08-01
> **cogadh said:**
> 
```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd "$HOME/.wine/drive_c/Program Files/Game/Directory/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/Game/Directory/game.exe"
```


Thanks, this script is really handy.

I was wondering if anyone knew if it's possible to also specify the resolution of the new X screen.  This would be useful for older application that are meant to run full screen but are on a fixed resolution (like 640x480).  I didn't have much luck searching any forums or google on this topic.  If it's possible it would make a good addition to this documentation.

---

### Post by riggity_ryan on 2008-08-02
Well, I finally found a way to adjust the resolution of a second X window (sort of, it's really zooming).  Thanks to sdimhoff off of this forum: [http://www.linuxforums.org/forum/wine/114017-wine-display-scaling.html#post554231](http://www.linuxforums.org/forum/wine/114017-wine-display-scaling.html#post554231)

You can use [crtl] + [alt] [+/-] to zoom an X screen (needs to be the number pad + and -).

The nice thing is it doesn't effect any other screens, so you can have your wine application zoomed in on screen 3 and your regular X screen normal on screen 0.

The down side is that because it's a zoom you will scroll around on the screen if you move to the edges.

Don't know if you think it's worth adding to your document, but I'm finding it pretty useful for some of my wine applications.

---

### Post by dfreer on 2008-08-04
> **riggity_ryan said:**
> Well, I finally found a way to adjust the resolution of a second X window (sort of, it's really zooming).  Thanks to sdimhoff off of this forum: [http://www.linuxforums.org/forum/wine/114017-wine-display-scaling.html#post554231](http://www.linuxforums.org/forum/wine/114017-wine-display-scaling.html#post554231)

You can use [crtl] + [alt] [+/-] to zoom an X screen (needs to be the number pad + and -).


I'm pretty positive that's actually changing the resolution of the X screen, it's been in X for quite some time (I think I remember flipping between resolutions in SuSE 7.0).

EDIT: Also, I do believe you can run nvidia-settings specifying a certain resolution, and then save the configuration file and load that in your script.

---

### Post by laam on 2008-08-11
If have know some information about wine if do you want to know that please click here.

[ Wine Club ](http://www.wineclubdirectory.net)

---

### Post by Eisenwinter on 2008-08-12
Thanks to the OP for sharing this valuable information, I have learned a lot.

---

### Post by simam on 2008-08-20
Stuff I've learned about Wine
If you're like me, you were probably frustrated by the state of Wine documentation when you first tried to use Wine. Sure, there are plenty of “How-to” documents out there that explain how to use it for a particular application or game, but I couldn't find any comprehensive “beginner's guide” to Wine that could give me the basic knowledge needed to begin really working with and understanding Wine. I didn't want a document that showed me how to make Half-Life 2 work, I wanted something that actually showed me how to use Wine. To that end, I began collecting all of the stuff I gathered from numerous Wikis, guides, forum posts and how-tos into a single general document. While this document does have a strong focus on running games in Wine, nearly all of the info included can be applied to running any application with Wine. Enjoy, its good stuff! 8-)
-Cogadh

    *
      General stuff
    *
      Stuff in "winecfg"
    *
      Special configuration stuff
    *
      Install stuff
    *
      Regular use stuff
    *
      Third party stuff
    *
      Advanced stuff

---

### Post by moral on 2008-08-21
n

---

### Post by Garratt on 2008-08-24
> ALTERNATE INSTRUCTIONS
Occasionally, the Gecko engine may fail to download or install properly. If this happens, do the following:

   1. Open a terminal and manually download/extract the Gecko package by running the following:
      NOTE - You will need to install the cabextract package from the repositories to do this
      Code:

      wget [http://downloads.sourceforge.net/wine/wine_gecko-0.1.0.cab](http://downloads.sourceforge.net/wine/wine_gecko-0.1.0.cab) && cabextract wine_gecko-0.1.0.cab

   2. Next, run the following to create the directories needed for Gecko:
      Code:

      mkdir -p ~/.wine/drive_c/windows/gecko/0.1.0/

   3. Place the extracted Gecko files into the newly created directory:
      Code:

      mv wine_gecko ~/.wine/drive_c/windows/gecko/0.1.0/

   4. Run regedit in the terminal. Go to HKEY_Current_User/Software/Wine/MSHTML and create a new key labelled "0.1.0"
   5. In the new "0.1.0" key, create a new string value labelled "GeckoPath" and set the string value to "c:\windows\gecko\0.1.0\wine_gecko"
   6. Go to the Useful Registry Keys page and scroll down to the HKEY_LOCAL_MACHINE section. Add all of the Internet Explorer keys/strings to the registry.


if people have to be told how to mkdir etc, then they usually need to be told how to do step 4, 5, 6....

or linked to a tutorial that explains. 

cause personally i understand what you mean by those steps... but i got NFI how to do them.

g.

---

### Post by thinhhoangdinh95 on 2008-09-04
Wow, that was great. But if Wine can run programs which was written in .NET and can play media files (such as AVI) without any supports from another programs (Just like Windows), everyone will use Ubuntu! :lolflag:

---

### Post by wisedrunkard on 2008-09-04
I'm a total newb how do i start my own thread... i have a problem i need help with, thx for the help

---

### Post by RealG187 on 2008-09-04
> **Garratt said:**
> if people have to be told how to mkdir etc, then they usually need to be told how to do step 4, 5, 6....

or linked to a tutorial that explains. 

cause personally i understand what you mean by those steps... but i got NFI how to do them.

g.

I could Upload the Gecko files in a tar.gz, zip, rar or whatever format if anyone wants...

---

### Post by YokoZar on 2008-09-29
I am unsticking this thread as it has a lot of old cruft that is scaring new users.  For example, double clicking should work for just about everything these days, so terminal use is a bad thing to recommend to first-time users.

I'm completely open to posting an updated small version though, or merging it into one of the other threads.

---

### Post by Thelasko on 2008-09-29
> **YokoZar said:**
> I am unsticking this thread as it has a lot of old cruft that is scaring new users.  For example, double clicking should work for just about everything these days, so terminal use is a bad thing to recommend to first-time users.

I'm completely open to posting an updated small version though, or merging it into one of the other threads.

Aww, I reference this thread all of the time.  Now it's going to be harder to find.

---

### Post by cogadh on 2008-09-30
Actually, I completely agree with YokoZar's decision to unsticky this. This was originally written well before the Wine 1.0 release and while much of the info included can still apply to Wine usage in rare cases, most of it is no longer necessary. I also have not had the time or inclination to keep the document up-to-date for a while now (I haven't actually been using Wine or Ubuntu for some time), so it will likely just get more and more irrelevant as time goes by.

---

### Post by aftertaf on 2009-02-06
Hi.
First: you've just been bookmarked.... far too useful for it's own good :) thanks!!!
:popcorn:
2nd: Concerning Wine, do you have any 'business' experience ?
I'm looking to migrate work PCs from XP to Kubuntu, and we use database stuff and homemade Borland C++ exes...
Before we can begin porting to linux, I want to show them that it's viable as a system, and without dev costs make things run with Wine;
I'm currently stuck with the ODBC. I can't conenct a wine-run app to a SQL server via the ODBC I configured with odbcad32.exe
I wondered if you have any tips or experience on this, or maybe a way to override the odbc to use the linux implementation unixodbc directly.??

Also, is there a way to capture or debug why a certain program is crashing at a certain point? 

Thanks again and serious bravo. If I finf in the meantime any things useful in my tests, i'll let you know, for the record :)
David

---

### Post by Thelasko on 2009-02-06
> **aftertaf said:**
> ...we use database stuff and homemade Borland C++ exes...

If you have the source code for the homemade stuff, you should theoretically be able to port it to Linux by compiling it with [Winelib]("http://www.winehq.org/winelib").

You should also start a new thread on this topic.

---

### Post by made_of_spoons on 2011-05-28
I'm trying to run a game by BigFish Games and almost everything seems to be working BUT the graphics. When I enter the game, audio is ok but I can see nothing but white squares floating. Even the pointer is a little white square. ._. What do I do? Is there something I can do in the Wine Configuration? I have wine1.2.

---

### Post by lisati on 2011-05-29
Thread closed so that it may rest in pieces.

---

