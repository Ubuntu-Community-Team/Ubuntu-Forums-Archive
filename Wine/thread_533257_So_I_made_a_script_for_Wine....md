---
title: "So I made a script for Wine..."
date: 2007-08-23
forum: Wine
---

### Post by deadlydeathcone on 2007-08-23
...a script called winefix. In short, it allows Wine applications to be run just as easily as those native to Linux, meaning that they can be linked to or run from any directory, whether from a terminal or even a file manager like nautilus. It also handles some of the more awkward Wine extensions like .lnk and .msi, akkowing them to be run with a double click.

It also offers a good number of enhancements and fixes over "vanilla" Wine, especially in regards to Compiz and Beryl. If either of the two are running when a Wine application requiring DirectX or OpenGL is run, you'll be asked if they should be temporarily disabled, and reinstated immediately after the application exits. it also allows for the "Legacy Apps" workaround in Compiz Fusion to be similarly enabled and disabled, as always leaving it on is a disaster - while it can fix the fullscreen modes of Wine apps, it actually breaks those of most native ones. The other enhancements allow the option for each application to have it's own dedicated virtual Windows desktop (basically whether a program should be started  "windowed" ), be reniced, ensure that fullscreen applications restore the desktop resolution properly, or, for 64 bit machines, run in 32-bit compatability mode (thanks to mikey for suggesting the last two!)

The script also changes Wine's error reporting behavior. Wine normally reports every error and fixme message that is encountered when an application is running, meaning that running programs via terminal results in a deluge of error messages that can greatly hurt performance, and that running them via script or file manager results in losing the ability to see any error messages at all. This script, by default, only reports critical system and Wine error messages, and only displays them if a Wine program actually crashes, in which case you'll then see a dialog much like this:

If it's the first time a particular application has crashed, you'll also be given the option to view its Winehq.org Application Database page, or if not found, asked if you'd like to create one.

The script also allows for more thorough error reporting by the use of command line options. Adding the flag "-d 1" causes all errors normally reported by Wine to be displayed, and saves application to the "log" folder in your Wine directory. There's also a "-d 2" option that causes ALL errors and system relays to be reported, but it's really only useful for debugging (it's insanely slow).

Using the script is pretty easy - it's used in exactly the same manner as wine itself, ie 'winefix drive_c/Program Files/dwarfort.exe' or 'winefix "C:\Program Files\dwarfort.exe"', and accepts all of wine's environment varables. It adds many command line options as well - run "winefix -?" in a terminal for a complete list.

The easiest way to use the script is to install the [attached deb]("http://ubuntuforums.org/attachment.php?attachmentid=46247&stc=1&d=1192321512") - the script will be automatically integrated with Gnome, allowing Wine apps to be run with a double click - something that can't be reliably done with Wine alone (see Bug #1, below). It does the same with Wine files of the .msi, and .lnk extensions, and adds Tango icons to the Wine menu as well:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=43801&d=1190162935[/IMG]

Don't want a .deb?

If you want the script by itself, grab it from [here]("http://ubuntuforums.org/attachment.php?attachmentid=46248&d=1192321526"), save it to your home directory, and install winefix with the command: ```
sudo tar -xvvzf winefix.tar.gz -C /usr/bin/
``` You'll also need to have zenity installed, and optionally lynx for AppDB integration, so if you don't:```
 sudo apt-get install zenity lynx
```

If there are any bugs, problems, or suggested improvements, please let me know.

If you want to run Wine apps in another xserver, you should take a look at my [other script]("http://ubuntuforums.org/showthread.php?t=552805").

##########################
# Bugs and annoyances fixed #
##########################

#1 -  Applications breaking when not run from their base directory.
The usual fix is to change to the base directory of an applications before it is run. The script does this automatically, saving you the trouble and allowing the ability to double click Wine executables in a file manager instead of having to run them via terminal or launchscript.

#2 - Wine's finicky handling of links (symlinks) to executables.
If you've ever tried right-clicking on an executable and creating a shortcut to place on your desktop, you know full well this. This script acts as a symlink interpreter of sorts for Wine, allowing symlinks to be used without error.

#3 - Desktop panels overlapping the screen of fullscreen applications when Wine is used with Compiz or Beryl, and other weirdness. 
The script allows for another window manager, like Metacity, to be started whenever a Wine application is in use, and automatically starts Compiz or Beryl again after said application exits. As of version 9.9 of this script, you'll be automatically prompted if a program uses either OpenGL or DirectX, and the backup Window Manager is automatically detected.

In the same fashion, the script can also enable and immediately disable the "Legacy Apps" Workaround for Compiz Fusion, as it's known to break the fullscreen modes of regular apps.

#4 - Choppy performance, or stuttering sound.
The best workaround for the above is to change the nice value of both the wineserver and program being run to either "19" or "-10", which can get very annoying.
Fortunately, this script can do it for you; just use the "-n" command-line option to specify whatever nice value is desired. For nice values less than 0, though, you'll be prompted for a password, but it's only used for the "renice" command - nothing else in the script is ever run as root.

#5 - Applications changing the desktop resolution - and not changing it back. << thanks to Mikey for this one!

#6 - The mysterious .lnk shortcuts and .msi extensions
Wine is already able to handle these - it's just not very easy to figure out how. The script handles them automatically, and in the case of .lnk shortcuts, also asks if you'd like a proper menu entry to be created from it.

#7 - If a program crashes, and wasn't executed from a terminal, no indication is given as to why.
This script will show a window containing the last ten Wine errors if an application crashes: 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=43802&stc=1&d=1190163141[/IMG]

If there were more, it also gives an option to view the entire log file. The script also warns of other common things, like bad paths and missing Wine drives.
Extended error reporting is also available by using the "-d 1" option, which saves error logs to the "log" folder of your Wine directory and shows all of the errors normally output by Wine - when this flag isn't set, only critical and system errors are shown. "-d 2" is also available, but it's mainly useful for Bug reports as it shows ALL errors and system calls.

#8 - AppDB integration!
When an application crashes, you'll be asked if you want to view it's Winehq Application Database entry, or if it doesn't exist, whether you want to create one. You'll only be asked once, but if you want to view the page again just run the particular app with the "-a" flag set. Unfortunately, this feature is currently limited to applications in the Wine menu.  

If you want to test these out, [Dwarf Fortress]("http://www.bay12games.com/dwarves/") is a good choice as it's a small download and suffers from most of the bugs I listed above above - plus, it's pretty fun.

############
# Other Stuff #
############

Command line options:
```
All flags are optional
  -a	Displays a program's Application Database page if it has been added
	to the main menu.
  -c    Enable the "Legacy Apps" workaround in Compiz Fusion.
	Only available for the gconf backend.
  -d	Set to "1" to enable error reporting, as well as logging.
	Set to "2" to enable reporting of ALL error messages - This option
	mainly useful for error reports, as the peformance penalty is severe.
  -f	Force the Window Manager specified with the "-w" flag to be used.
  -l	Enables "Linux 32" compatability mode for 64 bit operating systems. 
  -n    The "nice" value that Wine applications are set to.
	"19" generally decreases application and sound stuttering, while "-10"
	can increase the performance of CPU intensive applications.
  -v	Set this to "1", or a specific resolution such as "1024x768", to create
	a virtual desktop. This is equivalent to checking the "Emulate a virtual
	desktop" option in winecfg, only on an application specific basis.
  -w    Specifies a backup Window Manager.
  -i	Prints version and copyright information about Winefix.
  -?	Displays this lovely usage message.

```

For example - `winefix -w metacity -n "-10" -c 1 Anacreon2.exe -e` would have winefix use Metacity, nice values of "-10", enable extended error reporting and logging, and start Anacreon with the "-e" option. 

These options can also be permanently set as after the script is run for the first time, a file called ".winefixrc" will be created in your Wine directory - add whatever you like between the quotes. You can have one .winefixrc for every WINEPREFIX, or "bottle".

Changelog:

v 1.02: Disabled DRI and AppDB checks for setup files, fixed renicing via command line, fixed the deb package for Feisty users (sorry, that was terrible),.
v 1.0:   AppDB integration, improved logic.
v 0.92: Added a .desktop file for better desktop integration, and Tango icons.
v 0.91: Added support for .msi and .lnk extensions, improved some logic, added the "-v" option to run apps in a virtual desktop, report "err" class Wine errors by default.
v 0.9:    Make sure that if Wine changes the desktop resolution it gets changed back afterwords.
v 0.8:    Added GUI error reporting and logging, and converted the script to /bin/bash.
v 0.7:    Added command line options and usage information, and implemented proper passing of the WINEPREFIX variable.
v 0.6:    For Compiz/Beryl users, added an option for another Window Manager to be run when a Wine program is in use.
v 0.5:    Added support for Wine command line variables, and allowed for the nice value at which programs are run to be changed
v 0.4:    Initial Release

---

### Post by ubuntu.daemon on 2007-08-23
hmmm interesting... did you post this on the winehq forums?  Im still kind of up in the air with this but yeah good job!

---

### Post by dfreer on 2007-09-03
To pass arguments in a bash script:
[http://ubuntuforums.org/showpost.php?p=3028849&postcount=82](http://ubuntuforums.org/showpost.php?p=3028849&postcount=82)
Is this what you were looking for? Hope it helps!

---

### Post by deadlydeathcone on 2007-09-04
> **dfreer said:**
> To pass arguments in a bash script:
[http://ubuntuforums.org/showpost.php?p=3028849&postcount=82](http://ubuntuforums.org/showpost.php?p=3028849&postcount=82)
Is this what you were looking for? Hope it helps!

Pretty close, but no :( . Thanks, though.

$@ spits out every command line variable given to both the script and Wine, while what was needed was a way to separate the two from each other.

I gave it a shot, and ended up using two grep commands, which work for most things:
```
arguments=`echo "$*" | grep -o ' -.*' | tr "\n" " "`
command=`echo "$*"| grep -o ".*\(exe\|bin\|msi\)"`

```

---

### Post by graigsmith on 2007-09-04
> 1 - Automatically renices both the wineserver and the app being run to 19. It seems odd, but Wine apps have serious trouble with the Linux scheduler, and lowering their priority is the only way to circumvent this.

heh, wow this does fix my sound in wow. not only that, but i think my fps is improved.

---

### Post by deadlydeathcone on 2007-09-12
> **graigsmith said:**
> heh, wow this does fix my sound in wow. not only that, but i think my fps is improved.

You know, I think you're right. Since the script now supports custom nice values, I did three tests using values of 19, 0, and -10, along with a control test that ran Wine without using the script at all. I used[ 3DMark2000]("http://www.futuremark.com/download/3dmark2000/") for the tests, and did three different rounds of testing on an up to date (~Tribe 6) install of Gutsy.

Here are the results as a graph...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=43421&stc=1&d=1189735623[/IMG]

and table, which also shows the average difference in performance over the control test:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=43422&stc=1&d=1189735623[/IMG]

This matches what I've experienced with other Wine programs, so it look like nice 19 really is the magic value, for both performance and increase in sound smoothness. Still, I'm planning to do a few more tests sometime soon on something more cpu than gpu or input intensive to see if the results hold, as nice -10 might have the edge in those instances.

Also: I updated the script again. I'll update the original post in a few minutes.

---

### Post by deadlydeathcone on 2007-09-13
As promised, as few more tests - this time with Dwarf Fortress, a game surely able to bring the mightiest of CPUs to its knees (so to speak). I didn't use a frame capturing utility with this, so I recorded the maximum and minimum frame rates recorded during the intro movie.

The results are quite different from those of the last test:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=43425&stc=1&d=1189735914[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=43426&stc=1&d=1189735914[/IMG]

A seen, nice 19 nearly halved performance, while nice -10 gave a slight (5%) boost. If these two tests apply elsewhere, it looks like positive nice values are beneficial to GPU heavy apps ( or those with sound skipping issues) while negative ones benefit CPU heavy ones.

If anyone else has been toying around with nice values, does this conform fairly well to what you've experienced? My system is pretty unbalanced in terms of performance ( a pretty decent dual-core AMD Turion 64 X2 TL-50 coupled with a weak Geforce 6100 ), so these results could be somewhat skewed.

---

### Post by Vadi on 2007-09-14
Is it possible to have some sort of a configuration file that the script checks when launching an app, and picks the best values for it appropriately?

---

### Post by deadlydeathcone on 2007-09-14
It would take some testing to figure out what the best value is in the first place, but If there's agreement as to what is best for a popular app it's definitely possible. It could be toggled with a command line switch, too, so at least it couldn't hurt.

---

### Post by Vadi on 2007-09-15
That would be great. I'll try getting the script later and test on my machine :)

---

### Post by AmandaKerik on 2007-09-17
I tried this script after having some stuttering problems while trying to play Nox... Unfortuanately, this just made it worse.
Note: I'm a relative newbie.
Any suggested tweaks?

It stutters in this way (without your script):
I'll move my mouse too fast or too often and it'll freeze up for about 2 - 3 seconds, repeating the bit of music exactly three times. This chan happen 4 times in a row, or go for 30 seconds without a stutter.

I've tried adjusting the version of WIndows, I've tried adjusting the sound drivers, the sampling rate... 

With yours it seems fine until I get in game, then it stutters very fast every time I move the mouse - also, the game (intro, anyways) seems to be playing slower.

---

### Post by Vadi on 2007-09-17
Are you using Compiz or Beryl?

Try disabling those (type metacity --replace in the terminal if you're on ubuntu).

---

### Post by deadlydeathcone on 2007-09-17
> **AmandaKerik said:**
> I tried this script after having some stuttering problems while trying to play Nox... Unfortuanately, this just made it worse.
Note: I'm a relative newbie.
Any suggested tweaks?

It stutters in this way (without your script):
I'll move my mouse too fast or too often and it'll freeze up for about 2 - 3 seconds, repeating the bit of music exactly three times. This chan happen 4 times in a row, or go for 30 seconds without a stutter.

I've tried adjusting the version of WIndows, I've tried adjusting the sound drivers, the sampling rate... 

With yours it seems fine until I get in game, then it stutters very fast every time I move the mouse - also, the game (intro, anyways) seems to be playing slower.

I downloaded the demo, and it runs perfectly for me, so I can't really help with the freezing issues. Like vadi said, if you're using Compiz/Beryl, start the game like this (replace metacity with kwin if using kde):

winefix -w metacity "C:\Westwood\NoxDemo\Nox.EXE"

Other than that, add -n "-10" or -n 19 after winefix - it'll start the game at different nice values, and one might work for you.

You might try also try downloading the script again. On older versions everything was run at nice 19 by default, but that was changed as it really hurt performance in some instances - that might be the issue here. Otherwise, performance really shouldn't be any worse with the script than without.

---

### Post by slayerboy on 2007-09-22
THANK YOU!  This coupled with settings changes I made to my nvidia driver optinos, seems to have fixed the issue for right now at least, in WoW.

I did have to switch nice to run -10 because 19 seemed to affect the system too much.  -10 seems to not even have any lag even when fps drops too low sometimes.  I was getting normal fps around 15-18, now i'm getting it around 24-27 in most areas.  Shat is another story, but even there it went from 9-10 to about 14-17.

There is HOPE yet that my computer will be able to handle the rest of outlands in 3 more levels!  I just hope WotLK doesn't screw it up again, better yet patch 2.2!

---

### Post by deadlydeathcone on 2007-10-03
1.0 is out! Many things were rewritten, and among the things added was integration with Wine's AppDB.

This is the first version that changes how the script is used to any extent - at least if you use Compiz. Having to add the "-w metacity" flag to every game seemed kind of clunky, so the script now has the ability to detect whether or not an application uses OpenGL or DirectX, and if it does asks whether or not Compiz should be temporarily disabled. Also, manually disabling Compix is now done with the "-f" flag, as the backup Window Manager is now automatically detected.

The next most significant thing is that when an application crashes for the first time you'll now be asked whether you want to view its page on AppDB, or if one one doesn't exist if you'd like to create one.

The other significant thing is that Windows ".lnk" files can now be used as actual links, instead of just added to the Wine menu -  other than that most of the changes are internal, and probably wont be noticed.

Anyways, enjoy! Let me know if the AppDB stuff and OpenGL/DX detection works as it should.

by the way, the old Window Manager behavior is still available - it's actually now one of four "policies" that can be used for dealing with Compix - the "-f" flag in fact just toggles it on. The others are "ask", the new default described above, "smart", which always disables Compiz for OpenGL/DX apps, and "always", which always leaves Compiz running.

---

### Post by Vadi on 2007-10-04
... awesome.

But the .deb link doesn't work!

---

### Post by wishyjr on 2007-10-04
good work dude, i really like this!

---

### Post by Vadi on 2007-10-04
Ah, you put an extra " at the end of the link by accident.

---

### Post by deadlydeathcone on 2007-10-05
> **Vadi said:**
> Ah, you put an extra " at the end of the link by accident.

Good catch; it's fixed now. It must confer great confidence in a bash script when it's creator can't even format a http link properly  :) 

I replaced the link with one to version 1.01, which fixes two bugs: one that caused .winefixrc to be overwritten when it shouldn't, and one for the deb package that caused the script to not be properly associated with Wine .exes.

Also: has anyone else dug through Wines utilities and discovered [winelauncher]("http://wiki.jswindle.com/index.php/Winelauncher")? I found out about it when I was about halfway done with this script, and it's basically the Wine project's aborted (in 2002) attempt at creating a similar launcher script. It's pretty interesting, to say the least :)

[QUOTE=wishyjr]good work dude, i really like this![/QUOTE]
Thanks!

---

### Post by Vadi on 2007-10-08
Okay, I installed winefix via the deb, but it didn't go through for whatever reason (I think it complained about permissions), and now I can't install anything else, it gives me this:

```
(Reading database ... 191339 files and directories currently installed.)
Unpacking multisync (from .../multisync_0.82-8build1_i386.deb) ...
Setting up winefix (1.0-0ubuntu1) ...
+ [ ! -f /etc/gnome/defaults.list.bak ]
+ grep -o -m 1 winefix /etc/gnome/defaults.list
+ match=winefix
+ [ winefix != winefix ]
+ gtk-update-icon-cache /usr/share/icons/gnome
+ update-mime-database /usr/share/mime/
+ update-mime-database /usr/local/share/mime
update-mime-database: I don't have write permission on /usr/local/share/mime.
Try rerunning me as root.

Aborted (core dumped)
dpkg: error processing winefix (--configure):
 subprocess post-installation script returned error exit status 134
Setting up multisync (0.82-8build1) ...

Errors were encountered while processing:
 winefix
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried running the command that wants to be root, but something is still wrong:

```
vadi@vadi-laptop:~$ sudo update-mime-database /usr/local/share/mime
update-mime-database: I don't have write permission on /usr/local/share/mime.
Try rerunning me as root.

Aborted (core dumped)

```

Help please?

---

### Post by MasterNetra on 2007-10-08
Hi I am unable to fully install this script. I try having its package install by double-clicking it and it gets to "updating" /usr/local/share/mime and claims it doesn't have write access. So i go into route and gice it access to that share folder sense mime isn't present when i get there (not even hidden) and afterward i try running it again (this is 3rd attempt) and now package manger saying its corrupted or i don't have access (Sense I know i have access and even checked it must be some form of corruption. 2nd attempt involed trying to run it in terminal as root but it wouldn't even get started for some reason and I did set it to be read/write/access for all.)

---

### Post by MasterNetra on 2007-10-08
Oh and yea I'm running Ubuntu: Feisty for my OS. Also I get this error when trying to run Update Manager:

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package winefix needs to be reinstalled, but I can't find an archive for it.'

---

### Post by MasterNetra on 2007-10-08
<Removed by User>

---

### Post by Vadi on 2007-10-08
That's the same problem I got!

---

### Post by MasterNetra on 2007-10-09
Aye. I get a similar error message with the package editor and it won't let me install or remove winfix... Then again it doesn't seem to let you remove anyway >.>

---

### Post by Vadi on 2007-10-09
Ahah!

My friend helped me find a solution. In uninstalling it, I'll try installing it after this problem is fixed. Anyhow, the problem, as simple as it sounds, was that it was looking for "/usr/local/share/mime", whereas mime really was in "/usr/share/mime".

So what you do, is make an empty folder to trick it there. Type alt+f2, gksudo nautlius (to give nautilus root privs, so we can make folders there). Then go to usr, local, share, and make a folder named "mime" there. Also, in that mime, folder, make a folder named "packages".

Now sudu apt-get remove winefix should work.

---

### Post by MasterNetra on 2007-10-09
> **Vadi said:**
> Ahah!

My friend helped me find a solution. In uninstalling it, I'll try installing it after this problem is fixed. Anyhow, the problem, as simple as it sounds, was that it was looking for "/usr/local/share/mime", whereas mime really was in "/usr/share/mime".

So what you do, is make an empty folder to trick it there. Type alt+f2, gksudo nautlius (to give nautilus root privs, so we can make folders there). Then go to usr, local, share, and make a folder named "mime" there. Also, in that mime, folder, make a folder named "packages".

Now sudu apt-get remove winefix should work.

you mean sudo or sudu??? apt-get is failing to remove it... I tried that later on. So i make the fake folder first before removing it?

---

### Post by Vadi on 2007-10-09
Sudo, sorry. I don't even think sudu exists.

Yeah, make that fake mime folder, and the fake packages folder inside it, then apt-get will remove it properly.

---

### Post by MasterNetra on 2007-10-09
Prehaps we can create the folders for installation OR we could attempt to remove that line from the script... That way it won't kill itself sense it wouldn't be looking to update something thats not there. It would seem after all that the line would be useless anyway wouldn't it?

---

### Post by MasterNetra on 2007-10-09
Crap it didn't work x.x It still won't uninstall winefix

---

### Post by MasterNetra on 2007-10-09
Ok I fixed. I went into dpkg's folder itself and modified the winefix entries out of status and available and removed all winefix files in the info folder. Afterward the warning thing for dpkg went away and it works  fine now. I am currently "slowly but surely" removing the remaining parts of winefix by looking at winfix.list for directories that were used.

Now i'm wondering it is ok to like the .png images and the strange extensions that accompany them in a nearby folder or will that affect the future reinstall?

---

### Post by Vadi on 2007-10-09
No idea :/.

I'm planning on reinstalling Ubuntu anyway when I get gutsy (I moved my home folder to it's own patrition, so I'll lose no stuff when I reinstall).

---

### Post by MasterNetra on 2007-10-10
I decided to reinstall Windows XP... Ubuntu nor any other distro i've used seems to reconize my CD-RW... And I don't think i can get the proper device driver so ubuntu can use my Graphics card properly. I will have to wait and see if GG will be able to better handle my hardware. Meantime I guess its a linux emulator for me...at least if i come across a linux program i want that doesn't have a Windows Version to it :p

---

### Post by doorknob60 on 2007-10-11
Sorry...but...THIS STUPID THING SCREWED UP MY PACKAGE MANAGER!!!

It says the file is corrupt when i try to reinstall and the update and package managers don't work and quit because it wants me to reinstall...any suggestions? Maybe reupload the deb file?

ooh nvm i just erased the entries of winefix from the dpkg config file, so when you fix the problem I'd be happy to download it :D

---

### Post by deadlydeathcone on 2007-10-13
I'm really sorry about the disastrous deb package, that was terrible of me. The "/usr/local/share/mime" directory exists on Gutsy, so I didn't even notice the problem.

I updated the package on the first page to only update the mime database in "/usr/share", which fixes the problem (thanks, Vadi, for figuring that out!) If you have the old, corrupted package installed it will be overwritten, so you won't have to remove all of the files manually. 

Ssorry about how late this reply is, too - a wind storm knocked out the telephone lines where I live, and I haven't had an internet connection for days.

---

### Post by Vadi on 2007-10-13
Ahh, excellent. Thanks for fixing this, I'll get it again :)

---

### Post by deadlydeathcone on 2007-10-14
> **MasterNetra said:**
> I decided to reinstall Windows XP... Ubuntu nor any other distro i've used seems to reconize my CD-RW... And I don't think i can get the proper device driver so ubuntu can use my Graphics card properly. I will have to wait and see if GG will be able to better handle my hardware. Meantime I guess its a linux emulator for me...at least if i come across a linux program i want that doesn't have a Windows Version to it :p

A Linux emulator, eh? I suppose a combination of [Update Checker]("http://www.filehippo.com/updatechecker/"), [Tango Icons]("http://vertigosity.deviantart.com/art/Tango-Patcher-2600-7-08-1-27940418") and the [Murrina theme]("http://wingnome-xp.deviantart.com/art/MurrinaFancyClearlooks-65562925") plus a bit of cygwin might be close enough to count.

Is the new deb package working okay? Hopefully this silence isn't due to everyone's computers melting to slag simultaneously ](*,)

---

### Post by Vadi on 2007-10-14
Well it installed okay, and I can install other programs too now, so I guess so. It also replaced a bunch of icons for .dll, .exe files with the xp icon, but I don't know if it's working well yet - I still can't buy a game off steam properly. Argh.

---

### Post by stewils on 2007-10-22
Error:  Wrong architecture 'i386'

Running AMD64 Ubuntu Gusty....

---

### Post by inigomontoya on 2007-10-22
Thanks for this, i will make good use of it.  One thing though.  If I use the -n flag, how do I make it so I don't have to enter a password each time?  In other words how can i make "nice" executable for users without having to sudo?

---

### Post by Super Jamie on 2007-10-22
HOLY CRAP, I CAN GET GZDOOM RUNNING WITH THIS THING, I ABSOLUTELY LOVE YOU!!!

ironically, i actually found this the other day, but never bothered to read the description and install it till it got dugg. thank you SO much for writing this script, you have vastly improved my linux experience

let's hope this gets noticed and included in wine upstream too

---

### Post by Vadi on 2007-10-22
I suppose the .deb will work on gutsy okay, right? ;)

---

### Post by alanrr_sr on 2007-10-22
Another sugestion...a parameter for wineprefix. I think that is sane to install each application in its own wine directory, so you can easily remove them (instead of uninstall).
It is something like "bootles" in crossofice.

Just a sugestion for a already great script.

PS: later I will try it by my own, so maybe I can help add another feature

---

### Post by Rykielz on 2007-10-22
> **stewils said:**
> Error:  Wrong architecture 'i386'

Running AMD64 Ubuntu Gusty....

I dont think it works on 64 bit architectures yet. Maybe in the future..

---

### Post by buu700 on 2007-10-22
Will it work in Xfce without installing any GNOME dependencies? I'm setting up Xubuntu Gutsy on her computer later, and I think this would be good for the occasional Windows program she might need.

---

### Post by KillerKiwi on 2007-10-22
+1 For the bottles... currently I create a zip file of the apps folder so I can recreate if the .wine corrupts

also a way to sync GTK color scheme / fonts with wine... I know that mono does this with .net winforms some how.....

---

### Post by UK-Wobbie on 2007-10-25
Wow nice one this fixed my DOOM sound and Image :mrgreen:

---

### Post by KillerKiwi on 2007-10-28
Ok I started a python script to sync the colors nothing fancy... im not sure why this dosnt happen by default

```
#!/usr/bin/env python
import pygtk
import gtk


def format_color_string( Color ):
	return "%s %s %s" % (Color.red /256, Color.green/256,  Color.blue/256)
	
def format_color_key( key, Color):
	return "\"%s\"=\"%s\"\n" % (key, format_color_string( Color ))
	

invisible1 = gtk.Invisible()
style1 = invisible1.style

button1 = gtk.Button()
buttonstyle = button1.style

scroll1 =  gtk.VScrollbar()
scrollbarstyle = scroll1.style

menu1 = gtk.Menu()
menuitem1 = gtk.MenuItem()
menu1.add(menuitem1)
menustyle = menuitem1.style

user_reg = """WINE REGISTRY Version 2
;; All keys relative to \\User\\S-1-5-4

[Control Panel\\\\Colors]
"""

# http://www.moeraki.com/pygtkreference/pygtk2reference/class-gtkstyle.html
# http://lists.ximian.com/pipermail/mono-winforms-list/2003-August/000469.html

user_reg += format_color_key('Scrollbar', scrollbarstyle.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('Background', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('ActiveTitle', menustyle.bg[gtk.STATE_PRELIGHT])
user_reg += format_color_key('InactiveTitle', menustyle.bg[gtk.STATE_PRELIGHT])
user_reg += format_color_key('Menu', menustyle.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('Window', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('WindowFrame', style1.fg[gtk.STATE_INSENSITIVE])
user_reg += format_color_key('MenuText', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('WindowText', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('TitleText', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('ActiveBorder', menustyle.bg[gtk.STATE_PRELIGHT])
user_reg += format_color_key('InactiveBorder', menustyle.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('AppWorkSpace', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('Hilight', menustyle.bg[gtk.STATE_PRELIGHT])
user_reg += format_color_key('HilightText', style1.bg[gtk.STATE_PRELIGHT])
user_reg += format_color_key('ButtonFace', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('ButtonShadow', style1.bg[gtk.STATE_INSENSITIVE])
user_reg += format_color_key('GrayText', style1.fg[gtk.STATE_INSENSITIVE])
user_reg += format_color_key('ButtonText', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('InactiveTitleText', style1.fg[gtk.STATE_INSENSITIVE])
user_reg += format_color_key('ButtonHilight', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('ButtonShadow', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('ButtonLight', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('InfoText', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('InfoWindow', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('ButtonAlternateFace', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('ButtonHilight', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('GradientActiveTitle', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('GradientInactiveTitle', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('MenuHilight', style1.bg[gtk.STATE_NORMAL])

print user_reg 
```

It should just be a matter of finding the correct mappings from here...

EDIT: Ok I found the mono code at 
[http://lists.ximian.com/pipermail/mono-winforms-list/2003-August/000469.html](http://lists.ximian.com/pipermail/mono-winforms-list/2003-August/000469.html)

Ill work that in

---

### Post by Super Jamie on 2007-11-03
Further to my above comment about running Doom, I've found this can run all the OpenGL apps I have been keeping a Windows partition around for.

Admittedly, this has been limited to older stuff like GZdoom, and OpenGL-equipped emulators such as ePSXe, but it's doing everything I use my computer for, and extremely well.

Thankyou deadlydeathcone, I now have absolutely no need for Windows whatsoever, you ROCK!

:guitar:

---

### Post by orduek on 2007-11-13
when try to install Statistica7 i get this msg:

Statistica7 requires Internet Explorer version 4.01 or higher

Any ideas?

BTW i have ie4linux on my computer.
I thought the script will fix it but it didn't.

---

### Post by Vadi on 2007-11-13
I think you need the wine gecko thing, but I have no idea how to get it.

---

### Post by theShaggy on 2007-12-02
I managed to forcearchitecture the deb into installing on my Gutsy-64, and it is opening Wine programs with a double-click, like it is supposed to.

However, it isn't checking for my Windows Manager, not giving me the option to disable it, and beyond the double-click, doesn't appear to be doing anything.

I took a look at the file, and apparently there is supposed to be a configuration file installed? I don't have that, nor do I know how to go about creating one.  Any suggestions?

Also, in installing the program, I now have "Winefix" in Applications -> Other, but it doesn't do anything.

---

### Post by prodigalson666 on 2007-12-02
Stupid question, should I uninstall wine or will this integrate?

---

### Post by Vadi on 2007-12-02
It'll integrate (or well it actually requires wine :))

---

### Post by prodigalson666 on 2007-12-02
WOW! what can I say but thank you! Completely improved wow for me! Congrats!:):)

---

### Post by stewils on 2007-12-12
> **theShaggy said:**
> I managed to forcearchitecture the deb into installing on my Gutsy-64, and it is opening Wine programs with a double-click, like it is supposed to.



How did you do that?  Running on an AMD 64 here...

---

### Post by twickline on 2007-12-14
> **Vadi said:**
> I think you need the wine gecko thing, but I have no idea how to get it.

Here is a guide to [install Steam in Wine]("http://wine-review.blogspot.com/2007/11/steam-on-linux-with-wine.html") and it shows how to install Gecko the easy way :D

Tom

---

### Post by finesse on 2007-12-21
Nice work on this one.

For those interested, in WoW's video options, you can set it to Windowed Mode and Maximized and it works as if it was fullscreen but you can still use all the trixy desktop stuff.

Warning, YouTube link follows!
[http://youtube.com/watch?v=LDn7cDajeM4](http://youtube.com/watch?v=LDn7cDajeM4)

---

### Post by Vadi on 2007-12-21
That's pretty cool.

---

### Post by loosetoned on 2008-01-05
I have an AMD64 processor, running Ubuntu 7.10.  Just wanted to say that I've got winefix running with no problems on this setup.

I manually extracted the file which is listed on the first post of this thread into my home directory and followed the instructions on installing it from there.


Been playing Dwarf Fortress and only DF for the last 2-3 months (it and aquaria convinced me to axe WinXP altogether, it felt damn good to do so);  with winefix it seems to be running probably 30% better for me (but I also changed some key settings in the config file for DF at the same time so it may not be that substantial of a boost), I run it with the following command in a terminal, from the DF directory:

winefix dwarfort.exe -n "-10".  

Works like a charm.

(if you run winefix from a terminal, you will be able to see why a particular program won't run, it will display error messages)

Some additional info:  I have sound turned completely off in the DF config file.  This may help with compatability but I don't know.  I accept the option to disable the desktop effects when loading it, it definitely runs better when this option is selected. I find that it runs better when not running in a virtual desktop;  F11 does nothing when I run it in a virtual desktop.  

I've run Eschelon book 1 windows edition with winefix as well, with some small problems, but I didn't try to fiddle with it much.  Aquaria has mouse problems, but I probably just need to change a setting or two.  DF has consumed me so it's been the main testbed.

Can't think of any other pointers, I think that manually installing the script was what did the trick;  also, there is the 64 vs 32 bit .lib thing which can come up (
sometimes on new Ubuntu installs, you get no 32 bit libs on 64 bit machines), which can be fixed with [getlibs]("http://ubuntuforums.org/showthread.php?t=474790"),  a really stellar utility, it saved me 8 hours of work a few months back and made linux games and a number of previously nonfunctional programs runnable for me.

I think this was everything that I did, but if anyone has any questions I can help.

Great, great utility here, maybe soon windows XP will be a total thing of the past for gamers.. probably 3-4 years down the road, but advances like this continue to make it more possible.

---

### Post by trash on 2008-01-16
Didn't work for me:(. As far as i can tell wine didn't crash either but since I couldn't login to the server it's hard to tell for sure.
I also use GLdesktop but winefix won't restore it.


Should Desktop Effects be disabled?
1) yes
2) no
#? 1
Wine has crashed! To enable full error reporting, please run winefix with the flag 
"-d 1"
The Wine Application Database (App DB) is a collection of user-submitted information about application compatibility with Wine.

Would you like to view the App DB page for "Silkroad.exe"?
1) yes
2) no
#? 2
compiz is already running, skipping


EDIT: here's the output of winefix -d 1...
Should Desktop Effects be disabled?
1) yes
2) no
#? 1
Wine has crashed! Errors:
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x171960, L"szClsidFilter", 0x34df00)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x171960, L"szName", 0x34dee0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x171960, L"dwMerit", 0x34dee0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x171960, L"dwInputs", 0x34dee0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x171960, L"dwOutputs", 0x34dee0)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x1691b0, L"DxDiag_DirectShowFilters", 0x171960)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x1691b0, L"DxDiag_SystemInfo", 0x34ea1c)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x16bfb8, L"dwDirectXVersionMajor", 0x34ea28)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x16bfb8, L"dwDirectXVersionMinor", 0x34ea28)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x16bfb8, L"szDirectXVersionLetter", 0x34ea28)
The Wine Application Database (App DB) is a collection of user-submitted information about application compatibility with Wine.

Would you like to view the App DB page for "Silkroad.exe"?
1) yes
2) no
#? 2

Wine did not crash. After installing emerald, the desktop was restored. Wasn't able to log on to server so can't say if it has improved the game play or not.

---

### Post by Hairy_Palms on 2008-03-18
this rocks :) thanks for this, cant beleive i didnt discover it earlier :D

---

### Post by Nythain on 2008-03-21
couldnt install deb...
sudo dpkg -i --force-architecture blahblahblah.deb:
Preparing to replace winefix 1.0-1ubuntu2 (using winefix_1.0-1ubuntu2_i386.deb) ...
Unpacking replacement winefix ...
Setting up winefix (1.0-1ubuntu2) ...
+ [ ! -f /etc/gnome/defaults.list.bak ]
+ [ -f /etc/gnome/defaults.list ]
+ cp /etc/gnome/defaults.list /etc/gnome/defaults.list.bak
+ grep -o -m 1 winefix /etc/gnome/defaults.list
+ match=
+ [  != winefix ]
+ echo application/x-ms-dos-executable=winefix.desktop
application/x-extension-lnk=winefix.desktop
application/x-extension-msi=winefix.desktop
+ tee -a /etc/gnome/defaults.list
application/x-ms-dos-executable=winefix.desktop
application/x-extension-lnk=winefix.desktop
application/x-extension-msi=winefix.desktop
+ gtk-update-icon-cache /usr/share/icons/gnome
/var/lib/dpkg/info/winefix.postinst: 1: gtk-update-icon-cache: not found
+ update-mime-database /usr/share/mime/
/var/lib/dpkg/info/winefix.postinst: 1: update-mime-database: not found
dpkg: error processing winefix (--install):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 winefix

---

### Post by MasterNetra on 2008-03-23
Does this intergrate will with the kde interface or just gnome??

---

### Post by MasterNetra on 2008-05-03
Whats the News on the script? Is it ready for 8.04?

---

### Post by megadeus on 2008-05-03
Awesome! I found this thread searching for help with getting Dwarf Fortress to run in Wine and your script helped it run perfectly. (By disabling my desktop effects, basically).

If I could figure out how to give your post an official forum-Thanks, I'd do it!

Gracias! ^_^

---

### Post by glacialfury on 2008-05-11
I've been looking at the script to try and make a much simpler version - I have some amateur programming experience, but am new to linux and am having some trouble extracting the important bits.

Basically, I'd like to write a script that:

1) Switches the WM from compiz to kwin
2) runs World of Warcraft on wine
3) upon exiting World of Warcraft, revert the WM to compiz.

Could you provide any help or guidance?  I realize your script would do this as-is, but it's partly for my understanding as well as the actual use. I could understand a much simpler script as a basis to start understanding your more complicated version.

---

### Post by mixmatch on 2008-05-31
The deb would not install on my amd64 system. Is there any reason for this to be architecture specific?

---

### Post by BlackDragonBE on 2008-06-01
Wow this is cool!
All my apps have increased in speed! 
Thanks a lot!

Cheers

---

### Post by jmoraleda on 2008-07-02
Great script. Thank you!

I have added option -1 (number one, not letter el) to unblock the lower 64k of memory, which is blocked in new kernels and prevented some 16-bit apps from running with message winevdm: unable to exec '--app-name': 16-bit support missing. 
See [http://ubuntuforums.org/showthread.php?p=4713701](http://ubuntuforums.org/showthread.php?p=4713701) for details. Also fixed small bug when renicing from the command line.

---

### Post by smCw6GNakQn300£ on 2008-08-06
Hi there,
I'm pretty new to Ubuntu, but following a thread on these forums, I successfully managed to install and run my Windows game "Football Manager 2008" through Wine.

To enable this to work properly, I had to alter the xorg.conf file to disable the compiz desktop effects by adding the following:

[PHP]Section "ServerFlags"
Option "AIGLX" "off"
EndSection

Section "Extensions"
Option "Composite" "Disable"
EndSection[/PHP]

Then I had to restart the XServer by pressing Ctrl+Alt+backspace.

This is all well and good, but I would really, really like an easy way of temporarily disabling the desktop effects while I run my game, and then set them back on when I'm finished.

Your script seems like the perfect answer, but it's not working for me.
When I run the command to start the game, the script asks me if I want to disable the effects, which I say yes to.
The the game starts and displays the splash screen. After that though, it crashes and I get the following output:

[PHP]Wine has crashed! Errors:
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10028 0x00000000
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  162 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  1846
  Current serial number in output stream:  1846
There isn't an entry for "fm.exe" in the Application Database.[/PHP]

This **looks** like the error I got when first trying this, before I changed the xorg.conf file.

Can anyone please help me as to how to amend the Winefix script to change the above xorg.conf settings only while playing the game?

Thanks.

---

