---
title: "Wine - Half life 2 - Ubuntu Menu Showing"
date: 2007-09-16
forum: Wine
---

### Post by mikeym on 2007-09-16
HI,

I have Half Life 2 running under wine but whenever it starts the ubuntu menu is on top of it (I am running it in fullscreen mode) and I can't get it to go away! I've tried every setting in winecfg but with no luck.

Any advice would be appreciated.

---

### Post by peabody on 2007-09-16
Have you tried making a launcher script for it so that it runs in its own X session?  There's instructions in a thread around this forum somewhere that describes how to do that, it's called something like "what I've learned about wine" or some such.

---

### Post by salamba on 2007-09-16
Are you running with desktop effects/compiz/beryl ?.   I find that the gnome bars will stay on top of any full screen apps - wine / mythtv / compiz / virtualbox, if compiz is running.

If that's the problem then either switch back to metacity by hand, or use a script to stop then restart compiz when you run these apps.

---

### Post by mikeym on 2007-09-16
Yes I am running Compiz Fusion. 

How can I trun off Compiz before running it and then restart it?

---

### Post by deadlydeathcone on 2007-09-16
You might want to take a look at my wrapper script [here]("http://ubuntuforums.org/showthread.php?t=533257") - it does exactly what salamba describes.

Start it like this:
```
winefix -w metacity /path/to/HL2.exe
```

---

### Post by mikeym on 2007-09-16
Thanks, that's got the menu working!

However, one of the times it crashed when I was trying to exit wine and it messed up my desktop resolution or font or something (see picture).

[[IMG]http://img118.imageshack.us/img118/9963/screenshotae9.th.png[/IMG]](http://img118.imageshack.us/my.php?image=screenshotae9.png)

Now I can't get it to change back! I have restarted and tried changing resolution. Do oyu know how to put it back?

---

### Post by mikeym on 2007-09-16
OK my resolution must have been 12809x1024 not 1024x768. I don't know why it looks so awful but the higher resolution look OK.

---

### Post by mikeym on 2007-09-16
OK. While I can get into Half Life 2 with Wine now and it runs fairly well whenever I exit it throws me out in 1024x786 mode. 

Is there any way to avoid or counteract this?

---

### Post by deadlydeathcone on 2007-09-16
Hold on, I should be able to fix that...

edit:
I just uploaded a new version of the script that makes sure the correct resolution gets restored when a game exits. Let me know if it clears things up.

---

### Post by mikeym on 2007-09-16
Not working I'm afraid.

The script isn't finding a resolution for the old and new resolutions.

I tried breaking it down to see what it was doing and the output of this bit seemed a little weird.


```

$ echo `xrandr` | tr " " "\n"
SZ:
Pixels
Physical
Refresh
*0
1280
x
1024
(
342mm
x
270mm
)
50
*54
1
1024
x
768
(
273mm
x
203mm
)
51
59
60
....

```

And this gives you:

```

$ echo `xrandr` | tr " " "\n" | grep -B 1 ".*\*" 
Refresh
*0
--
50
*54

```

So the next bit can't find an 'x'.

---

### Post by deadlydeathcone on 2007-09-16
I completely forgot about the new version of xrandr in Gutsy. I'll come up with something that works for Feisty as well. 

Until then, you can quickly change your resolution with:
xrandr -s  1280x1024

edit:
Does the following command return a 0?
```
echo `xrandr` | tr " " "\n" | grep -m 1 "\*." | sed 's/*//'
```

---

### Post by mikeym on 2007-09-17
Yes that returns a 0

---

### Post by mikeym on 2007-09-17
OK,

I've got the script working on my computer. It took a few modifications to get it to switch properly. See what you think (the bits I've edited have "Modified Mikey" writen s a coment).

```

#!/bin/bash -x

# winefix - Wrapper script for Wine with fixes for several bugs and annoyances.
#
# Partly based on:
#    podencoder
#    winelauncher  

# Copyright (C) 2007, John Simpkins
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA
# 02110-1301  USA
VERSION="0.8"

# The nice level at which Wine applications and the Wineserver are run.
# Reccommended values are from -10 to 19.
# nice 19 - increases application smoothness, especially for sound, and provides a
# moderate performance increase in applications that rely mainly on GPU processing.
# nice -10 - decreases application smoothness, but can slightly increase the performance
# of programs that rely mainly on CPU processing.
NICE=""

# Set the below value to "1" if using Compiz Fusion and wish to use the "legacy
# apps" workaround. The workaroud is enabled and then immediately disabled, as it's 
# known to break the fullcreen modes of many applications.
# Only the gconf backend is supported.
COMPIZFIX=""

# If the above workaround is not sufficient, Compiz or Beryl can be automatically replaced
# with another Window Manage whenever a Wine application is executed.
# Default Window Managers:
#	Gnome - metacity
# 	KDE - kwin
# 	XFCE - xfwm4
WINDOWMANAGER=""

# Set the below value to "1" if error logging is desired.
ERRORLOGGING=""

# The line that is matched in a path to determine if it is DOS formatted.
MATCH=:\

# Parse command-line options
while getopts ":c:d:n:w:u:" options; do
	case $options in
	c) COMPIZFIX=1;;
	d) ERRORLOGGING=1;;
	n) NICE=$OPTARG;;
	w) WINDOWMANAGER=$OPTARG;;
	u) cat <<EOF
winefix $VERSION
Copyright (C) 2007, Jack Simpkins
This program is free software.  You can redistribute it and/or modify it under
the terms the GNU General Public License version 2 or, at your option,
any later version published by the Free Software Foundation.  There is
NO WARRANTY, to the extent permitted by law.
EOF
	exit 1;;
	*) cat <<EOF
Usage: winefix [OPTIONS] [WINECOMMAND] [WINEOPTIONS]

WINECOMMAND can be in either DOS or UNIX format.

All flags are optional
  -c    Set to "1" to enable the Wine workaround for the gconf backend
	in Compiz Fusion.
  -d	Set to "1" to enable error reporting, as well as logging.
	Set to "2" to enable full reporting of ALL error messages. This is
	mainly used for error reports.
  -n    The "nice" value that Wine applications and Wineserver are set to.
  -u	Display this usage message.
  -w    Window Manager to use when a Wine application is running.

Report bugs to <jack.simpkins@gmail.com>.
EOF
	exit 1;;
	esac
done
shift $(($OPTIND - 1))

# Renice both application and wineserver.
RENICE()
{
        sleep 3s;
if [ "$NICE" -lt 0 ]
then
	for a in `pgrep $1`; do sudo renice $NICE -p $a > /dev/null; done
        for a in `pgrep wineserver`; do sudo renice $NICE -p $a > /dev/null; done
else
	for a in `pgrep $1`; do renice $NICE -p $a > /dev/null; done
        for a in `pgrep wineserver`; do renice $NICE -p $a > /dev/null; done
fi
}

REPLACE()
# Execute Window Managers, and suppress output
{
	$1 --replace 2>/dev/null &
	sleep 2
}

LOWERCASE()
# Lowercase DOS drive letters. Needed for DOS to UNIX path conversion.
# TODO: Implement this in a way that avoids breaking abnormal drive letters.
{
	echo "$*" | sed -e "s/A:/a:/" -e "s/B:/b:/" -e "s/C:/c:/" -e "s/D:/d:/" \
	-e "s/E:/e:/" -e "s/F:/f:/" -e "s/G:/g:/" -e "s/H:/h:/" -e "s/I:/i:/" \
	-e "s/J:/j:/" -e "s/K:/k:/" -e "s/L:/l:/" -e "s/M:/m:/" -e "s/N:/n:/" \
	-e "s/O:/o:/" -e "s/P:/p:/" -e "s/Q:/q:/" -e "s/R:/r:/" -e "s/S:/s:/" \
	-e "s/T:/t:/" -e "s/U:/u:/" -e "s/V:/v:/" -e "s/W:/w:/" -e "s/X:/X:/" \
	-e "s/Y:/y:/" -e "s/Z:/z:/"
}

# If using a GUI, display only ten lines of errors. If there are more, display an option to
# view the log file.
DIE () 
{
	if [ $GUI ]
	then
		zenity --error --title="$NAME" --text="Wine has crashed! \n\n$@"
		if [ `less $WINEPREFIX/log/$NAME.log | grep -c .` -gt "10" ]
		then
			zenity --question --text "There were too many errors to display. Would you like to view the error log?"
			if [ $? == 0 ]
			then
				zenity --text-info --width 600 --height 600 --title="$WINEPREFIX/log/$NAME.log" --filename="$WINEPREFIX/log/$NAME.log"
			fi
		fi
	else
		echo "Wine has crashed! $@" >/dev/stderr
	fi
}

WARNING()
{
	if [ $GUI ]
	then
		zenity --warning --title="$NAME" --text="Warning: \n\n$1"
	else
		echo "Warning: $1" >/dev/stderr
	fi
	exit 1
}

# Check to see if we were started without arguments
if [ $# -eq 1 -a "$1" = "" ] || [ $# -eq 0 ]
then
echo "Winefix called without arguments. For usage information, run winefix -u"
exit 1
fi

# Are we being run from a terminal?
if tty -s
then :
else GUI=1
fi

# Is zenity installed?
if [ $GUI ]
then
	[ -z "$(which zenity)" ] && GUI=""
#	echo "Warning: \"zenity\" is not installed. Error dialogs will not be displayed"
fi

# Check to see if the WINEPREFIX points to exists. If not specified, set it to the default.
if [ ! $WINEPREFIX ]
then
	WINEPREFIX=$HOME/.wine
fi

if [ ! -e "$WINEPREFIX" ]
then
	WARNING "WINEPREFIX: \"$WINEPREFIX\" doesn't exist!"
fi

# Unless error logging is enabled or a custom value has been specified, disable the display of error messages.
if [ ! $WINEDEBUG ] && [ ! $ERRORLOGGING ]
then
	WINEDEBUG="-all"
elif [ ! $WINEDEBUG ] && [ "$ERRORLOGGING" == "1" ]
then
	WINEDEBUG=""
elif [ ! $WINEDEBUG ] && [ "$ERRORLOGGING" == "2" ]
then
	WINEDEBUG="+all"
fi

# Isolate Wine application command line arguments.
WINEARGS=`echo "$@" | grep -o -i '\( -.*\| www.*\| http:*\)' | tr "\n" " "`
WINECOMMAND=`echo "$@" | grep -o -i ".*\(exe\|bin\|msi\)"`

# Test if a path is symlinked, and if so, convert it into something Wine can use.
# Wine likes symlinks little, if at all.
if [ -L "$*" ]
then
	SYMLINK=`readlink "$WINECOMMAND"`
	LOCATION=`dirname "$SYMLINK"`
	NAME=`basename "$SYMLINK"`

# Test if a path is DOS formatted, and if not in concatenated "~" format, convert to the UNIX
# equivalent. "~" formatted paths are passed directly to Wine.
elif echo "$*" | grep -q "$MATCH";
then
	if echo "$*" | grep -q "~"
	then
		LOCATION=`.`
		NAME="$*"
	else
		DOSPATH=$(echo "$WINECOMMAND" | sed "s/\\\/\//g")
		DOSDIR=`dirname "$DOSPATH"`
		CASE=`LOWERCASE "$DOSDIR"`
		LOCATION=""$WINEPREFIX"/dosdevices/$CASE"
		NAME=`basename "$DOSPATH"`
	fi
		if echo "$NAME" | grep -q ".msi"
		then
			NAME="start $NAME"
		fi

# If none of the above are true, the path is assumed to be formatted correctly.
else
	LOCATION=`dirname "$WINECOMMAND"`
	NAME=`basename "$WINECOMMAND"`
fi

# Change to an application's directory and then run Wine; many programs look for assets in
# the folder that they were executed from, and break outright if this is not done.
cd "$LOCATION" 2>/dev/null || WARNING "The path \"$LOCATION\" doesn't seem to exist!"

# If a program is being reniced to less than zero, prompt for a password.
if [ $NICE ] && [ $NICE -lt 0 ]
then
	if [ $GUI ]
	then
		gksudo -D "renice $NICE" "sudo -v"
		wait
	else
		`sudo -v`
		wait
	fi	
fi

# Determine if either Compiz or Beryl are in use so that they can be reinstated later.
if [ "`pidof compiz.real`" ]
then
	WINDOWMANAGER2="compiz"
elif [ "`pidof beryl`" ]
then
	WINDOWMANAGER2="beryl"
fi


# Enable Window Manager workarounds
[ $COMPIZFIX ] && ( gconftool-2 -t bool -s /apps/compiz/plugins/workarounds/allscreens/options/legacy_fullscreen true )

# Modified Mikey 17/09/06
# Save the original desktop resolution so that we can restore it if Wine screws it up.
RESCHECK=`echo \`xrandr\` | tr " " "\n" | grep "\*." | sed 's/*//' | sed -n -e '1p'`
REFCHECK=`echo \`xrandr\` | tr " " "\n" | grep "\*." | sed 's/*//' | sed -n -e '2p'`
ORIGRES=$RESCHECK
ORIGREF=$REFCHECK

# Don't run a Window Manager if it's already in use
if [ $WINDOWMANAGER ]
then
	if [ "`pidof $WINDOWMANAGER`" ]
	then
		echo "$WINDOWMANAGER is already running, skipping"
	else
		REPLACE $WINDOWMANAGER
	fi
fi

# Create the log directory if it doesn't already exist.
if [ ! -e "$WINEPREFIX/log" ]
then
	mkdir "$WINEPREFIX/log"
fi
	
# Create an application log if one doesn't already exist.
if [ ! -e "$WINEPREFIX/log/$NAME.log" ]
then
	touch "$WINEPREFIX/log/$NAME.log"
fi

if [ $NICE ]
then
	RENICE $NAME &
fi

# Execute Wine.
env WINEPREFIX=$WINEPREFIX WINEDEBUG="$WINEDEBUG" wine "$NAME"$WINEARGS 2>"$WINEPREFIX/log/$NAME.log" wait ||
if [ $ERRORLOGGING ]
then
	DIE "Errors: `tail "$WINEPREFIX"/log/"$NAME".log`"
else
	DIE "To enable debugging and error logging, please run winefix with the flag \"-d 1\""
fi

if [ $ERRORLOGGING ]
then
	# If log file is empty, remove it
	if [ ! -s "$WINEPREFIX/log/$NAME.log" ]
	then
		rm -f "$WINEPREFIX/log/$NAME.log"
	fi
fi

# Modified Mikey 17/09/06
# If Wine changed the desktop resolution, make sure it's properly changed back
sleep 2
RESCHECK=`echo \`xrandr\` | tr " " "\n" | grep "\*." | sed 's/*//' | sed -n -e '1p'`
REFCHECK=`echo \`xrandr\` | tr " " "\n" | grep "\*." | sed 's/*//' | sed -n -e '2p'`
NEWRES=$RESCHECK
NEWREF=$REFCHECK
if [ "$NEWRES" != "$ORIGRES" ] | [ "$NEWREF" != "$ORIGREF" ]
then
	xrandr -s $ORIGRES -r $ORIGREF
fi

# Disable Window Manager workarounds
[ $COMPIZFIX ] && ( gconftool-2 -t bool -s /apps/compiz/plugins/workarounds/allscreens/options/legacy_fullscreen false )
if [ $WINDOWMANAGER ] && [ $WINDOWMANAGER2 ]
then
	REPLACE $WINDOWMANAGER2 &
	wait
fi

```

I added a refresh rate check as well because mine was changing along with the screen size. I've also moved the resolution change to before Compiz is restarted because it crashes on me if I try to use xrandr to switch resolutions when it's running.

I hope this is helpful!

---

### Post by deadlydeathcone on 2007-09-17
> **mikeym said:**
>  added a refresh rate check as well because mine was changing along with the screen size. I've also moved the resolution change to before Compiz is restarted because it crashes on me if I try to use xrandr to switch resolutions when it's running.

I hope this is helpful! 

Very much, thanks! I have an LCD monitor with only one refresh rate, so I completely overlooked that part.

The new version 0.9 I just uploaded should work with all versions of xrandr, and also makes sure Compiz or Beryl aren't running before changing resolutions.

---

