---
title: "Wine deskbar launcher creation via shell scripts (files attached)."
date: 2008-01-14
forum: Wine
---

### Post by Praadur on 2008-01-14
When I started using wine, one of the first things I did was disable the 'wine' section of my menus, as I found it made things a little too cluttered.  As I didn't particularly want to run everything from the CLI every time though, this left me with a dilemna.  I had to manually create deskbar launchers for each application I ran with wine, either that or menu launchers (.desktop files, either way).  This goes without saying of course that I had to create them for apps that came in zips too that didn't have any form of installer.

I got tired of that, so I decided to create a couple of shell scripts to automate that process for me.  I've attached them to this post just in case anyone wants to use them, but I thought I'd share for two reasons.  First of all, they might just be useful to someone else despite the fact that they're shoddily thrown together shell scripts, and secondly I might get suggestions as to how to make them better, which is also always nice.

There are two scripts included, exe2ico and winelaunchmaker (the main thing).  I will note two things though for anyone who wishes to start quickly with this, and that's that they require the icoutils package (grab it via synaptic, apt-get, or whatever you like using) and they expect to be in /usr/sbin (I always put my scripts there as it's the cleanest thing to do).

- exe2ico

This is basically a simplified frontend for wrestool, because I got tired of having to remember the commands for wrestool.  After all, a menu item/deskbar launcher needs an icon, so I tend to just extract it from the executable using wrestool.

This script expects one argument definitely and another optionally, if it doesn't get any arguments or it receives '--help', there is help built in.

exe2ico [/path/to/]infile.exe [/path/to/]outfile

You can provide paths if you want, otherwise it works in the directory you ran the script from.  Providing a name for the outfile (the icon that'll be produced) is optional and you can do that if you like.  If you don't provide a name for the icon then it'll share the same prefix as the executable.  For example: ShinyIM.exe will output ShinyIM.ico.

- winelaunchmaker

This calls exe2ico by default, so you don't even have to use the above script unless you really want to.  What this does is it creates a .desktop file, this file can then be dragged into a menu or onto a deskbar.  All you have to do is open the folder where you created said file and drag it over, then things should simply just work.

It also creates a script file which the .desktop launcher calls, the script file changes to the directory of the application in question (so that it'll run properly, as some apps prefer that and get iffy if one calls them in the manner of 'wine /path/to/application.exe') and then runs it with wine.

The process of creating both the desktop and the shell script is made visible so that you can see the contents of thw two files as they're being created, that way you'll know if anything needs to be edited without even needing to open the files (but things shouldn't need editing if it works as intended).

This script expects three arguments definitely and if it gets less or '--help' is sent to it, it should show its help info.

winelaunchmaker [/path/to/]appname.exe "Application Name" "Application Description"

The first is the executable that wine will run, if no path is supplied then the script assumes the executable is in the current directory and creates things that way.  The 'Name' is the name of the application that'll appear in the tooltip or underneath the icon when viewed by nautilus, the 'Description' is the text that shows directly beneath the name in the tooltip.

As an example...

winelaunchmaker ShinyIM.exe "Shiny IM!" "A multiple-service messenger client." would create the following files in the directory it was ran from:

[list]
[*]ShinyIM.ico: This is the icon file used by the launcher, it's the output of exe2ico as winelaunchmaker calls that automatically.
[*]ShinyIM-sh: This is the script file which changes to the appropriate directory and then runs the application with wine.
[*]ShinyIM.desktop: This is the launcher, it'll show up as 'Shiny IM!' when viewed in Nautilus.[/list]
Once those files are created, one can simply open that directory in Nautilus and either drop the launcher in the deskbar or a menu.

- All that said...

I realise that these shell scripts are fairly horrible but they're just something I threw together to make my life a little easier.  It's more than possible that something out there like this exists (perhaps even for the CLI too) but I couldn't find anything after a good deal of searching... so I did the only thing I knew how to do, I created something to fill the gap myself.  I'm sharing these because anyone who's encountered the same situation that I did might find them useful, and because I might get to improve them thanks to suggestions.

I'm personally hoping that these won't cause anyone or their computer to blow up in a fireball of illogic, but one can never be sure, so I'd say that running these will be at yer own risk.

I can't really think of anything to add other than that but I hope that others might find them useful.  It's certainly given me less headaches with all the indy games that I play!

---

