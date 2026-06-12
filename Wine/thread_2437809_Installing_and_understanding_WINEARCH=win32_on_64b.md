---
title: "Installing and understanding WINEARCH=win32 on 64bit system"
date: 2020-02-29
forum: Wine
---

### Post by mark bower on 2020-02-29
I have installed Wine-3.6 on my 64bit Ubuntu 18.04.  It works with Irfanview 64bit.  

I have ACAD2000, 32 bit.  I have read a number of posts and understand to use it in Wine I must invoke WINEARCH=win32, but I do not under stand how it all goes together.  I have of course, the ~/.wine directory.  What I want to know is how to properly implement the WINEARCH=32 thing, and not mess up what I have.

So, I understand I would enter on the cmd line WINEARCH=win32 PREFIX=~/utility/apps_wine/ACAD2000/setup.exe.  And from what I gather this will place an ACAD2000 icon on the Desktop that can be clicked to execute ACAD2000?  An Irfanview icon is on the desktop that I click to execute 64bit Irfanview.  

Is that all there is to it, or do I have to do something that will guard the existing ~./wine?  I believe I read somewhere that the ./wine directory should be renamed?  If true, if I do that, what does that mean for execution, ie, the need to execute one program in 64bit and the other in 32bit?

This is all kinda wordy, but hopefully characterizes what I do not understand.  (this was all so easy back in 16.04, both apps 32bit, and Wine showed in the gnome-classic pull down menu)

---

### Post by mastablasta on 2020-03-02
if you have a prefix and then change it to 32 bit it will become 32 bit. you can run multiple prefixes at the same time. i use Play on linux for easier management of prefixes. each game or program is installed in separate prefix. most i have are 32 bit ones. 

this is showing how it looks like:
[https://askubuntu.com/questions/500069/how-to-check-if-my-wine-prefix-is-32-bit-or-64-bit](https://askubuntu.com/questions/500069/how-to-check-if-my-wine-prefix-is-32-bit-or-64-bit)

you can also easily change the prefix onto 32 bit one or vice versa.

edit: this of prefix as being a pretend windows C:\ drive or a separate windows install. it's not that really, but it will help you imagine how things work. so if you put various stuff in the same prefix this would be like loading it all into same c: drive in windows. 

so if you separate the prefixes, then it's like having separate virtual machines (they are not really emulators), separate windows PCs each with one app loaded.

---

### Post by mark bower on 2020-03-02
I appreciate your response, but I really need lots more hand holding (and I did look at the link you provided) - like maybe step by step after making the WINEARCH entry.

So I have Irfanview icon on the Desktop(actually not sure how I got it there as had a lot of difficulty getting WINE to install), and I can execute it.  If I enter for my PC "WINEARCH=win32 PREFIX=~/utility/apps_wine/ACAD2000/setup.exe", where/how do I execute ACAD2000?  And after closing ACAD2000, how do I execute Irfanview, same as before with Desktop icon?

In 16.04 my gnome Applications drop down menu had wine listed, and I could execute either program there.  Alternately, I could click on the Desktop icons and execute them.  I did look at the link below which indicates establishing .wine32 and .wine64 directories?  Then one would launch programs thru the appropriate "bit" directory?  If so, I am a long way from understanding how to set this up and launch each of the programs by this method.

[https://askubuntu.com/questions/177192/how-do-i-create-a-32-bit-wine-prefix](https://askubuntu.com/questions/177192/how-do-i-create-a-32-bit-wine-prefix)


mark

---

### Post by mastablasta on 2020-03-03
> **mark bower said:**
> I did look at the link below which indicates establishing .wine32 and .wine64 directories?  Then one would launch programs thru the appropriate "bit" directory?

that is correct. but you would launch it from the shortcut you created where you would tell which wine prefix to use and where to launch form. and to manage all these in a more easy way i prefer the GUI interface that play on Linux (available in software center) provides. just their scripts don't seem to always work so i install programs using a link to install nonlisted program. it worked really well so far.

Play on Linux is in repositories (Ubuntu software center)
Crossover is paid for solution with a GUI. more stuff works here and is preconfigured. pricey, but it makes sense for professional users. 
Lutris is a launcher that comes with preconfigured scripts.
Steam Proton - well, more made for games, but it still offers interface for easy install of other things.

---

### Post by mark bower on 2020-03-03
I made a clean install of WINE 5.0.  I renamed ~/.wine to ~./winesave. I can launch 64bit Irfanview from desktop .exe file.  I then cmd line entered the following which a post says will create separate win32 and win64 environments:
1) WINEARCH=win32 WINEPREFIX=~/win32 wine cfg, and
2) WINEPREFIX=~/win64 winecfg

1) opens the wine GUI configure menu, but does not allow me to select win98, which I need
2) opens and shows the same options as 1)

So what do I do to launch either 32 or 64bit, or what needs to be done differently?

---

### Post by mastablasta on 2020-03-04
```
[COLOR=#242729][FONT=Consolas]WINEPREFIX=~/.wine32 WINEARCH=win32 wineboot[/FONT][/COLOR]
```

then run

```
WINEPREFIX=~/.wine32 WINEARCH=win32 your_32bit_executable.exe
```
q: do you have 2 prefixes made?

1. you can run winecfg after install.
2. check if you need winetricks and any additional libraries installed.
3. OMG windows 98!!!!


i love irfanview! nomacs is a very good alternative. : [https://nomacs.org/](https://nomacs.org/)


> [h=3]Ubuntu and Linux Mint[/h]
[LIST]
[*]nomacs is available in the “universe” repository of Ubuntu. Just install it using your favorite package manager.
[*]translations can be added with sudo apt-get install nomacs-l10n
[/LIST]


if you need newer version or beta, there is a snap available. : [https://snapcraft.io/nomacs](https://snapcraft.io/nomacs)


[SIZE=3]**ACAD2000**[/SIZE]
[COLOR=#333333][FONT=&quot][COLOR=green]**HOWTO**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Â*Â*by NSLW on (March 26th 2009)
[SIZE=4]Installing[/SIZE]

    1. Use recent version of Wine(tested on Wine-1.3.9)

    2. Download winetricks by following command
[SIZE=2][FONT=monospace] wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)[/FONT][/SIZE]

    3. Install required components by following command
[SIZE=3][FONT=monospace]sh winetricks corefonts mdac25 tahoma win2k[/FONT][/SIZE]

    It will take some time because winetricks will download all above components
    4. Change Screen Resolution in Wine configuration by typing

[SIZE=3][FONT=monospace]winecfg[/FONT][/SIZE]

    Then go to Graphics tab and change Screen Resolution from 96 to 108
     (workaround given by [EMAIL="andysheaff@gmail.com"]Sheaff[/EMAIL])
    5. navigate to your AutoCAD 2000 CD and run
[SIZE=3][FONT=monospace]wine setup.exe[/FONT][/SIZE]

[SIZE=4][/SIZE]
[SIZE=4]PlayOnLinux[/SIZE][SIZE=3] way[/SIZE]

You can install your AutoCAD 2000 using PlayOnLinux (some kind of gui for Wine). I think it's the easiest and cleanest method because script will install AutoCAD with service packs in separate prefix automatically. To do so you'll need:

    1. [PlayOnLinux]("http://www.playonlinux.com/en/download.html")
[/FONT][/COLOR]

---

### Post by mark bower on 2020-03-04
O.K., more to try.  ACAD2000 is of the 1998 era, but works great on WINE with Win98.  I like Irfanview because it is intuitive.  Eventually I may try PlayonLinux, obviously you are very comfortable with it.  But really, I only have just the two programs I use on WINE.

---

### Post by mark bower on 2020-03-04
I now have two prefixes:  .wine32 and .wine64.  But WINEPREFIX combined with WINEARCH errors as follows:

mark@mark:/$ WINEPREFIX=~/.wine32 WINEARCH=win32 ~/Desktop/ACAD2000/setup.exe
bash: /home/mark/Desktop/ACAD2000/setup.exe: No such file or directory

I have also tried using /home/mark/Desktop/ACAD2000/setup.exe, and same error.  I do not know what the problem is?

---

### Post by mastablasta on 2020-03-05
nomac is really very similar to irfanview and me and my wife had no issues in switching to it. but yes, irfanview is a really good app and has some awesome plugins.


no, winearch will just assign the architecture to specific prefix. then to run setup it's just ```
wine  [COLOR=#000000]WINEPREFIX=~/.wine32 ~/Desktop/ACAD2000/setup.exe
[/COLOR]
```[COLOR=#000000]
can you check wine instructions i posted above. you need to have fonts etc installed (thorough winetricks) as well as change the resolution before you run the setup.  in PoL this is done through install wizard (install additional libraries, configure wine, select the file to run, create shortcut in the end...) if the script that PoL provides is not working or is not provided.

i would also check if win98 option is actually still needed. well you never know. but unlike old windows wine continues with development. so for exmaple Call of Duty 2 used to need directx7 (not default winXP version 9, but the old version 7), but now all works out of the box and uses DirectX9 libraries. oblivion needed this and that, now you just install , add 1 original library (maybe could also be set done via wineconfig) and it all works.

edit: make sure your path is correct. it will be case sensitive. if you type wine in terminal and then just click, grab and drop the file from file manager to terminal it will give the path to file. at least it used to be like that (i am on Kubuntu now). so this should give you the correct path to file, then you press enter and hopefully it will work.[/COLOR]

---

### Post by mark bower on 2020-03-05
Well, you led me to a big dumb on my part, that which I know better - case sensitivity.  But a new problem is introduced with correct command line, please see following:

mark@mark:~$ WINEPREFIX=~/.wine32 WINEARCH=win32 ~/Desktop/ACAD2000/SETUP.EXE
bash: /home/mark/Desktop/ACAD2000/SETUP.EXE: cannot execute binary file: Exec format error

I wonder if this indicates some needed file is missing?  The SETUP.EXE is located in a folder with all the other files, and the same that has always worked when only dealing with 32bit.

ACAD2000 demands Win98, NT4.0 or NT5.0 when attempting to load with wine installer (clicking on SETUP.EXE in the ACAD2000 folder.  I have always run it under Win98.  You mention fonts, but do realize I launch Irfanview without problem; I would assume that the fonts should be o.k., same fonts for whatever emulation is used?  Incidentally, this whole problem occurs because of moving off of 16.04LTS 32bit to 18.04LTS 64bit.

Addendum:
At Home I now have 4 wine prefixes:  .winesave (the original prefix renamed), .wine32 and .wine64, and .wine for which I do not know what generated it.  My guess is that the extra prefixes do no harm for what we are trying to accomplish, or do they?

I appreciate your looking into the specific installation of ACAD2000.  However, I have installed it many times on all 32bit PCs and found the steps below had no affect on performance as I use it.  Also, I have never used winetricks nor missed anything that I know of.  Just plain old wine has efficiently done all that I have needed.  I do miss however that the wine install on one of the two PCs I have does not show wine in the gnome drop down menu.  But even that is not needed as I like to launch the two programs from the Desktop.  And also missing and the crux of this problem is that winecfg GUI is not making Win98 on Ubuntu 18.04.  However, on my other PC, 16.04LTS 64bit, wine does make Win98 available, and thus, thank goodness, I can use ACAD on that PC. (and it is Irfanview is 64 bit on that PC).  Seems odd that Win98 is not available on the 18.04LTS PC, the one with which I am communicating to you.
> 
2. Download winetricks by following command
wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

3. Install required components by following command
sh winetricks corefonts mdac25 tahoma win2k

---

### Post by mastablasta on 2020-03-06
wine is the command to launch wine:

```
mark@mark:~$ **[COLOR=#ff0000]wine[/COLOR] **WINEPREFIX=~/.wine32 WINEARCH=win32 ~/Desktop/ACAD2000/SETUP.EXE
bash: /home/mark/Desktop/ACAD2000/SETUP.EXE: cannot execute binary file: Exec format error
```

> Addendum:
At Home I now have 4 wine prefixes:  .winesave (the original prefix renamed), .wine32 and .wine64, and .wine for which I do not know what generated it.  My guess is that the extra prefixes do no harm for what we are trying to accomplish, or do they?

nah, they are separated between each other. i have about 9 of them so far.

> 
I appreciate your looking into the specific installation of ACAD2000.  However, I have installed it many times on all 32bit PCs and found the steps below had no affect on performance as I use it.  Also, I have never used winetricks nor missed anything that I know of.  Just plain old wine has efficiently done all that I have needed.  I do miss however that the wine install on one of the two PCs I have does not show wine in the gnome drop down menu.  But even that is not needed as I like to launch the two programs from the Desktop.  And also missing and the crux of this problem is that winecfg GUI is not making Win98 on Ubuntu 18.04.  However, on my other PC, 16.04LTS 64bit, wine does make Win98 available, and thus, thank goodness, I can use ACAD on that PC. (and it is Irfanview is 64 bit on that PC).  Seems odd that Win98 is not available on the 18.04LTS PC, the one with which I am communicating to you.

ah yes, are 32 bit libraries installed on linux? if you install those than 64 bit OS can run 32bit apps and you won't (shouldn't) notice it's a 64bit OS.
[https://linuxhint.com/run_32_bit_windows_64_bit_unbuntu/](https://linuxhint.com/run_32_bit_windows_64_bit_unbuntu/)

also and especially wine:i386

the fonts are in wine appdb description. i do not know the app you are trying to install myself. however you should know that these fonts are installed inside the prefix and are nto much related to any system fonts or libraries.

---

### Post by mark bower on 2020-03-06
Indeed, some of the support pkgs were not loaded.  Selecting wine32-preloader:i386 in synaptic loaded: fonts-wine, libwine:i386, wine32:i386.  Unfortunately I got the same binary msg problem when running WINEPREFIX=~/.wine32 WINEARCH=win32 your_32bit_executable.exe. 

 Interestingly, if I enter the below, I can invoke winecfg GUI and see all the 32 bit OSes that are supported.  However, selecting win98, then trying to launch ACAD2000 via its SETUP.EXE, I get the same message that it needs win98.  So obviously the 32bit support is not there.

```
WINEARCH=win32 WINEPREFIX=~/win32 winecfg
```

Short of "throwing in the towel", I yield and will try to get PlayOnLinux to work for me.  So allow me some time and I will return in a few days or so.  The WINE problem has been overly frustrating, but I have appreciated your attempts to steer me to get it to work.  I am hoping PlayOnLinux will be simpler.

---

### Post by mastablasta on 2020-03-09
plenty of work there. not sure why it would not be supported as most old games are 32 bit applications and many work well in wine.

you need to separate 32 bit libraries issue. 
1. there are linux 32 bit libraries needed to run 32bit applications that are in wine 
2. and there are also windows 32bit libraries which sometimes have to be added or installed in the wine prefix. 

to add them to the prefix you can just download them from MS libraries website or copy them from windows install; to install them in the wine prefix winetricks can be used. 

there is also a 3rd option that is sometimes needed - to select them to load - this is done in winecfg where you can select to load native or default version of the library.
more on win98 applications and libraries here: 
[https://wiki.winehq.org/Wine_User%27s_Guide](https://wiki.winehq.org/Wine_User%27s_Guide)
> [h=4]4.1.1 Application Settings[/h][COLOR=#000000][FONT=&quot]Wine has the ability to mimic the behavior of different versions of Windows. In general, the biggest difference is whether Wine behaves as a Win9x version or an NT version. Some applications require a specific behavior in order to function and changing this setting may cause a buggy app to work. Wine default Windows version is Windows XP. Some newer applications may refuse to start unless you set the Windows version to Vista or higher, while some older applications may perform better if you choose Windows 98. (Note: versions of Windows prior to XP are only available for selection in winecfg in 32 bit wineprefixes. If you are on a 64 bit system, see [FAQ#How do I create a 32 bit wineprefix on a 64 bit system?]("https://wiki.winehq.org/FAQ#How_do_I_create_a_32_bit_wineprefix_on_a_64_bit_system.3F")).[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Within the tab you'll notice there is a *Default Settings entry. If you select that you'll see the current default [I]Windows Version for all applications. A troublesome application is best configured separately from the Default Settings. To do that:*[/I][/FONT][/COLOR]

[LIST=1]
[*]*[I]Click on the Add application button.*[/I]
[*]*[I]Browse until you locate the executable.*[/I]
[*]*[I]After it's been added you can choose the specific Windows version Wine will emulate for that application*[/I]
[/LIST]


-------------------------------

finally and if all fails, since this app is likely over 20 years old it might work well in virtualbox (you just need to find win98 and install it in there).

---

### Post by mark bower on 2020-03-25
@ mastablasta
I apologize for taking so long to get back.  Again, I appreciate your extensive effort to try and get me through this.  Before I continue I must stress again that there is little I understand about WINE and its environment.  Also, I simply got frustrated.  Even when I went to the WINE.wiki to install per instructions there, the 1st option there talked re deprecated process.  Oh great, for a guy who in the past simply went with "sudo apt-get install WINE" or some stuff after WINE and all worked just fine.  From what I read, WINE is kinda messed up now and in transition or something.  I also attempted Playonlinux per your suggestion, but did not seem to make things happen there either, ie, never got it "off the ground".

In summary, I have now basically have full capability/normal operation.  Both ACAD2000 and Irfanview launch just fine, again, on one PC, and switching between them is a matter of invoking winecfg and setting OS to either win98 or win7.  On my 2nd PC, ACAD2000 runs normally and is seen in pull down as well as Desktop icon, but I have to launch Irfanview I have to use the command line, go to Desktop where icon has installed, input "wine i_view.exe", and it launches.  So on the 2nd PC, ACAD2000 is in the App pull down menu and icon on Desktop, but Irfanview is only presented in the Desktop icon. (I should say, if not already, I use the Gnome Classic Desktop with pull down menus.

Now here is what I did - -

Totally frustrated with trying to get WINE installed via PPAs, so I simply did a synaptic WINE install and selected only one item:  wine-stable, which installed WINE 3.0.

For 1st PC ACAD install, where Irfanview was already working via Desktop icon, I entered:
     WINEARCH=win32 WINEPREFIX=win32 winecfg
     WINEPREFIX=~/win32 WINEARCH=win32 wine ~/path/SETUP.exe   (this got ACAD2000 going, it installed in pull down plus Desktop icon)

For 2nd PC ACAD2000 install, I believe I did the following:
     WINEARCH=win32 WINEPREFIX=win32 winecfg
     WINEPREFIX=~/win32 WINEARCH=win32 wine ~/path/SETUP.exe  (this got ACAD2000 going, it installed in pull down plus Desktop icon)
     
     and for attempted Irfanview install
     WINEARCH=win64 WINEPREFIX=win64 winecfg
     WINEPREFIX=~/win64 WINEARCH=win64 wine ~/path/i_view.exe (this put the Irfanview icon on the Desktop, but pop-up "archive msg" occurs when clicking it.

     Irfanview will launch from Desktop command line with "wine i_view64.exe", where i_view64.exe is on the Desktop; it does not appear to be installed.

This works ok for Irfanview, not that much trouble, but would it would be nice to simply click on the Irfanview Desktop Icon like I can do with ACAD2000.  This is very long winded, but gives a flavor for what I have been doing and the one remaining problem?

mark

---

### Post by mastablasta on 2020-03-26
well you now installed the app. now your issue is actually not wine one but desktop shortcut or launcher as they call it. you can create these yourself. or you can copy the existing one and then modify it.

option 1.
look here: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
under title: To start/run Windows programs using Wine
option 2:
or here: [https://ubuntuforums.org/showthread.php?t=2356273](https://ubuntuforums.org/showthread.php?t=2356273)

option 3:
[https://askubuntu.com/questions/1119771/add-wine-application-to-gnome-application-list](https://askubuntu.com/questions/1119771/add-wine-application-to-gnome-application-list)

there was also a tool wine launcher creator (not sure if it still works) and there is also Arronax ( [https://www.florian-diesch.de/software/arronax/](https://www.florian-diesch.de/software/arronax/))

in KDE i just right click on dekstop and then create launcher. if i want it in menu i go to where one would add launchers to menu and then create new launcher there.

i think you need png icons not .ico. there are tools that will convert them but you can get free nice pgn icons on line if app doesn't come with them.

---

### Post by mark bower on 2020-03-26
Thanks, I'll be working on your suggestions, and be back.
mark

---

### Post by mark bower on 2020-03-26
o.k., your advice was good.  I went with the option to make a .Desktop executable and after some struggle to get it right, it worked nicely and I used one of my .jpg's for the icon.  If I understand what is happening, running Irfanview this way (via .Desktop) is essentially the same as when I go to the folder with the executable and run wine /path/file.exe on the command line.

What I do not understand is why Irfanview does not install in the win64 prefix created?  That is, to repeat from my previous post, I ran the following, but Irfanview does not install in the prefix:  

[HTML]and for attempted Irfanview install
WINEARCH=win64 WINEPREFIX=win64 winecfg
WINEPREFIX=~/win64 WINEARCH=win64 wine ~/path/i_view.exe (this put the Irfanview icon on the Desktop, but pop-up "archive msg" occurs when clicking it.[/HTML] 

Bottom line, everything works great!  It does not matter to me whether Irfanview is launched via a .Desktop or an Irfanview installed Desktop icon.

mark

---

### Post by mark bower on 2021-01-06
Back for more help please.  Focus is on getting 32bit ACAD to run on WINE, which I have done in the past, but now a bit of trouble getting ACAD installed in Mate 20.04 64bit.  I installed WINE from synaptic pkg mgr, and have verified that i386 architecture is on board via "dpkg --print-foreign-architecture"

Steps and results:
1)WINEARCH=win32 WINEPREFIX=/home/mark/win32  winecfg   
        [win32 prefix is established at home/mark, winecfg produces winecfg pop-up, list of all OSes is provided, I select Win98 (which is what I need) on the pop-up, click apply, click o.k., close pop-up

2)WINEPREFIX=/home/mark/win32 wine ~Desktop/ACAD2000/SETUP.EXE
        [installation is initiated but bombs with msg "Wrong OS.  ACAD supports . . . Win98"

3)winecfg 
        [pop-up now reverts to showing Win7 versus the needed Win98]

So for clarity, it would seem that winecfg sets the prefix to Win98, gives the appearance it is in 32bit mode, but then for some reason it jumps out of the Win98 mode when running wine.  The WINE I have installed is functional and I am running 64bit Irfanview under it.  

I must be missing a simple step?  Could it be that some libraries are needed to support 32bit emulation?

---

### Post by #&amp;thj^% on 2021-01-06
I have used:
To create a 32-bit WINE prefix on a 64-bit Ubuntu system, you need to open a terminal and run the following command:
```

WINEPREFIX="$HOME/prefix32" WINEARCH=win32 wine wineboot
```
[list]
    [*]Where WINEPREFIX is the directory for the prefix
    [*]This directory must not already exist or you will get an error! Please do not manually create it in Nautilus or with mkdir./[/list]

---

### Post by mark bower on 2021-01-06
Please note, I was showing terminal entries in 1), 2) and 3).  I tried your suggested code line and it did not kick winecfg into the "98" mode.  That is, I ran the line then did a winecfg, and Win98 was not listed.  The default of WinXP is what showed with about 6 other options, but Win98 is not one of them.  My first code line in 1) shows a default  of Win7, but on the list is Win98.

---

### Post by mark bower on 2021-01-21
I tried 1fallen suggestion, but no luck.  I will return tomorrow to reiterate what is not working for me, really nothing new.  
[This WINE section does not seem to be very active, at least not a lot of support contributors, so I am thinking of making a fresh post at Games & Leisure.]  I am really bothered by the fact that what worked on one computer does not work with the other, both the same OS.

---

### Post by mastablasta on 2021-01-22
use play on linux. you can install older version of wine and that should hopefully have libraries you need to run win98

---

### Post by mark bower on 2021-01-22
I tried PlayOnLinux in the past, may have even been your suggestion, but I could not get it to work.  It did not seem intuitive, actually somewhat complicated - my problem in understanding it.  I only need to run just _one program in 32bit mode_, so would like to stick with WINE.

I do see where the WINE version on the PC where I get to Win98 is a 5.x version, while on the PC that I am having trouble with is a 6.x version.  BUT as far as I know, WINE is all about running older software so I would think the 6.x version should be even more robust and not cause problems?  And i386 architecture is onboard.  But if that is true that 6.x does no longer supports that architecture, then I suppose I would consider going back to the 5.x version given some help to modify the install method I used.

[edit]
o.k., today I gained some control over the process.  With WINE ver 6.0 onboard, I can enter WINEARCH=win32  WINEPREFIX=~/win32 winecfg .  This results in the WINEcfg pop-up and it offers all the selections including Win98!  It seems that using WINEPREFIX requires that every use of it be immediately preceded by the command WINEARCH=win32. 
 
So seeing the pattern, I now entered  "WINEPREFIX=~/win32   wine ~/path . . ./ACAD2000/SETUP.EXE", and ACAD installed!  Unfortunately, ACAD would not boot.  I suspect that something is fouled and were it a fresh install, it would have worked.  So maybe some more fiddling, but removing /win32, /.wine, and uninstalling wine-stable and wine-stable-amd64 with SynPkgMgr, then reinstalling, did not do the trick.  But at least I got close to achieving the ACAD install and believe I have a handle on the WINEARCH and WINEPREFIX thing.

---

### Post by mark bower on 2021-01-23
I tried PlayOnLinux in the past, may have even been your suggestion, but I could not get it to work.  It did not seem intuitive, actually somewhat complicated - my problem in understanding it.  I only need to run just _one program in 32bit mode_, so would like to stick with WINE.  As far as I know, WINE is all about running older software so I would think the 6.x version should be even more robust and not cause problems?  And i386 architecture is onboard.  But if that is true that 6.x does no longer supports that architecture, then I suppose I would consider going back to the 5.x version given some help to modify the install method I used.

[edit]

The problem is solved as I missed one key step of 3 steps, step #2 as seen below.  Also I show an image of where Win98 is selected

Step1  WINEARCH=win32  WINEPREFIX=~/win32 winecfg   [this results in the WINEPREFIX setup, and the WINE CONFIGURATION pop-up which shows all available Windows OSes.  
Step2  select Win98 on the winecfg pop-up > Apply > O.K.
Step3  WINEPREFIX=~/win32   wine ~/path . . ./ACAD2000/SETUP.EXE

With the above 3 simple steps my ACAD2000 is up and running.  And please note that I started this thread with WINE 3.6, Ubuntu 18.04 and finish with WINE 6.0, Ubuntu MATE 20.04.

---

### Post by mastablasta on 2021-01-23
right. and in PoL you would just click install "non-listed program", then select 32bit version on install and then you can configure it before (during) install or afterwards. click "configure wine" button and it will show up the winecfg screen.
[http://www.linuxandubuntu.com/home/install-windows-games-and-software-in-linux-with-playonlinux](http://www.linuxandubuntu.com/home/install-windows-games-and-software-in-linux-with-playonlinux)

well if you have only one app, the CLI method is OK, but if you want to install multiple apps using different versions of wine - this is where GUI launcher make things easier and more manageable. 

i mean at leats to me it is much easier to just click on prefix marked with the app icon, then click configure and i have various options available. it's easier to understand if you see "wine version" with drop down menu where you can just select the version that works best or install & select a different one etc.

---

### Post by mark bower on 2021-01-23
I probably should have come back for your help with PoL when I tried to get it to work for me, but I just got frustrated at the time I tried to do so.  I do fully accept that the GUI would be more pleasing and easy to use.

In parallel, sort of, I have just installed a GUI boot manager called ReFind which graphically looks at my 3 HDs, two of them 64bit, one 32bit(Win7 HD).  The GUI works very nicely and I have ACAD2000 installed on the Win7 HD.  Had I had this going, I may have given up on the WINEPREFIX path.  However, as it turns out, I like the display of ACAD2000 better under WINE than when run under Win7.  And in the future, I might not have a PC that could accommodate the additional HD, thus again to have WINE (or PoL) working for me.

---

