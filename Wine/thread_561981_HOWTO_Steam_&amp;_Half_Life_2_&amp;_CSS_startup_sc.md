---
title: "HOWTO: Steam &amp; Half Life 2 &amp; CSS startup scripts for Compiz"
date: 2007-09-28
forum: Wine
---

### Post by mikeym on 2007-09-28
Hi, 

Just thought I would post my startup scripts for Steam, Half Life 2 and Counter Strike Source. They are primarily for starting the games when using the Compiz  window manager without causing problems, but there's no reason that they shouldn't be used with other setups (they would still fix things like screen resolution changes). 

They all use *deadlydeathcone*'s excellent script for fixing issues that arise from using wine applications. (Thanks again for the script and putting in the few additional things I requested). 

This assumes that you have half life 2, steam and CSS installed on your computer. It's also worth noting that the method I use for launching half life 2 and css has been depreciated you're supposed to just launch steam now with an application code but that is no use for us when we have to resize the display and switch window managers after we've stopped playing the game. However this method is still available and works well.

[COLOR="Red"][SIZE="4"]Getting the scripts[/SIZE][/COLOR]

So first download [*deadlydeathcone*'s script (winefix)]("http://www.box.net/shared/9zbop0or6u") and save it to your home directory.

[Please note that I'm only using the terminal launcher bit of this script to see how to integrate it with nautilus see [here]("http://ubuntuforums.org/showthread.php?t=533257").]

Then open a text editor and paste the following into it:

```

#!/bin/bash

# OPTIONS:

# Window manager: metacity for GNOME / kwin for KDE / xfwm4 for XFCE
WINDOWMANAGER="metacity"

# Windows Path to hl2.exe
WINPATH="C:/Program Files/Steam/steamapps/***[COLOR="Red"]yourprofilename[/COLOR]***/half-life 2"

# Game - options hl2 (for half life 2) or cstrike for (counter strike source)
GAME="hl2"

# Graphics mode for hl2: 'dxlevel XX' where XX is the Direct X level * 10 (e.g. dxlevel 81) / 'gl' for OpenGL
GRAPHICSMODE="dxlevel 80"

# Game Resolution
WIDTH=1024
HEIGHT=768

# Extras
# Uncomment to show console on startup
# EXTRAS="$EXTRAS -console"
# Uncomment to hide valve logo on startup
# EXTRAS="$EXTRAS -novid"

# Uncoment for 64 bit users to run Wine under Linux32
# Better performance - just remember to have 32 bit graphics drivers 
# installed under "/usr/lib32". [COLOR="Red"](edit) I'm not so sure about this now[/COLOR]
# LINUX32="-b 1"

WINEDEBUG=fixme-all winefix $LINUX32 -w $WINDOWMANAGER "$WINPATH/hl2.exe" -$GRAPHICSMODE -steamlocal -game $GAME  -fullscreen  -width $WIDTH -height $HEIGHT $EXTRAS -heapsize 512000 +map_background none "$@"

```

Go through the script and uncomment or change the values to suit your system as directed by the comments.

Save in your home directory as 'hl2'.

[COLOR="Red"]**(edit) New Script for launching CSS through steam (as required by VAC servers) and polling of hl2.exe to see when it closes.**
[/COLOR]

Open a new text file and paste the following into it:

```

#!/bin/bash

# OPTIONS:

# Steam Application ID Half-Life 2 Deathmatch (320) Counter-Strike Source (240)
APPID=240

# Window manager: metacity for GNOME / kwin for KDE / xfwm4 for XFCE
WINDOWMANAGER="metacity"

# Windows Path to steam
WINPATH="C:/Program Files/Steam"

# Graphics mode for hl2: 'dxlevel XX' where XX is the Direct X level * 10 (e.g. dxlevel 81) / 'gl' for OpenGL
GRAPHICSMODE="dxlevel 80"

# Game Resolution
WIDTH=1024
HEIGHT=768

# Extras
CONSOLE="-console"

#Mode
MODE="-fullscreen  -width $WIDTH -height $HEIGHT"

# Uncoment for 64 bit users to run Wine under Linux32
# Better performance - just remember to have 32 bit graphics drivers 
# installed under "/usr/lib32". [COLOR="Red"](edit) I'm not so sure about this now[/COLOR]
# LINUX32="-b 1"

# How often to check if the game has closed, and how long to wait 
# for hl2.exe to be launched by steam
SUMMARYFREQ=1s
PROCESSTIMEOUT=10
 
function WaitProcess {
PROCESSID=$1
	# Wait for process to finish
	if [ ! -z $PROCESSID ]; then
		echo "Waiting on $PROCESSID"
		while ps -p $PROCESSID > /dev/null; do 
			# Check to see if process has finished
			sleep $SUMMARYFREQ 
		done
		echo "$PROCESSID has finished"
	else
		echo "No process ID given!"
	fi
}

function CallProcess {
WAITON=$1; shift
PROCESSNAME=$*
	echo $PROCESSNAME
	#Clear the old process info
	LASTPROCESS=0
	PROCESS=""
	# get PID of script.
	echo "$PROCESSNAME & LASTPROCESS=$!"
	$PROCESSNAME & LASTPROCESS=$! 
	echo "Launched $LASTPROCESS"
	CNT=0
	while [ -z $PROCESS ]; do
		sleep 1s
		CNT=$((CNT+1))
		echo "pidof -s -x $WAITON"
		PROCESS=`pidof -s -x $WAITON`
		echo "Process: $PROCESS"
		if [ CNT == $PROCESSTIMEOUT ]; then
			echo "Error finding process."
			exit 1
		fi	
	done
	# Wait for the process
	WaitProcess $PROCESS
}

REPLACE()
# Execute Window Managers, and suppress output
{
	$1 --replace 2>/dev/null &
	sleep 2
}

function WineFixCodeOn {
	# Determine if either Compiz or Beryl are in use
	if [ "`pidof compiz.real`" ]
	then
		WINDOWMANAGER2="compiz"
	elif [ "`pidof beryl`" ]
	then
		WINDOWMANAGER2="beryl"
	fi
	# Save the original desktop resolution
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
}

function WineFixCodeOff {
	# If Wine changed the desktop resolution, change back
	sleep 2
	RESCHECK=`echo \`xrandr\` | tr " " "\n" | grep "\*." | sed 's/*//' | sed -n -e '1p'`
	REFCHECK=`echo \`xrandr\` | tr " " "\n" | grep "\*." | sed 's/*//' | sed -n -e '2p'`
	NEWRES=$RESCHECK
	NEWREF=$REFCHECK
	if [ "$NEWRES" != "$ORIGRES" ] | [ "$NEWREF" != "$ORIGREF" ]
	then
		xrandr -s $ORIGRES -r $ORIGREF
	fi
	if [ $WINDOWMANAGER ] && [ $WINDOWMANAGER2 ]
	then
		REPLACE $WINDOWMANAGER2 &
		wait
	fi
}

WineFixCodeOn

export WINEDEBUG=fixme-all
CallProcess hl2.exe winefix $LINUX32 "$WINPATH/Steam.exe" -$GRAPHICSMODE -applaunch $APPID $MODE $CONSOLE -heapsize 512000 +map_background none $EXTRAS "$@"

WineFixCodeOff

```

Change the parameters in the script to suit your system and then save the file in your home directory as 'css'.

Close this text file and open a new one and save the following:

```

#!/bin/bash
winefix C:/Program\ Files/Steam/Steam.exe "$@"

```

and save the file in your home directory as 'steam'.

[COLOR="Red"][SIZE="4"]Installing the scripts[/SIZE][/COLOR]

type the following into the terminal to install the scripts and enter passwords where required:

```

cd ~
tar -zxvf winefix-*.tar.gz
chmod 755 winefix hl2 css
sudo mv winefix /usr/local/bin
sudo mv hl2 /usr/local/bin
sudo mv css /usr/local/bin

```

[COLOR="Red"][SIZE="4"]Adding Menu Items and Sessions[/SIZE][/COLOR]

Right click on your menu and select edit menu to add items for steam, hl2 and css. For the command just put in 'steam', 'hl2, and 'css' for each one (without quotes.

You can get icons for half life and css in your "Program Files/Steam/steam/games" folder on your wine C: drive (normally "~/.wine/drive_c/") and find one for steam in your steam folder, or downlaod them from here [here ]("http://halflife2.filefront.com/file/Valve_World_Icon_Pack;46231#Download"). [COLOR="Red"]**(edit)**[/COLOR]

To add steam as a startup application so that it's always running in the background (and you don't have to launch it by hand before you start a game), go to System->Preferences->Sessions and click on New. Put in the name 'Steam' and the command as:

```

steam -silent

```

That should be you! Restart or launch steam by hand and try running Half Life 2 or Counter Strike. I hope you enjoy it as much as I have.

---

### Post by exile on 2007-09-28
Thank you mikeym you rock!

---

### Post by mikeym on 2007-09-28
You can do the same for any hl2 game by following the steps for css and replacing the GAME="cstrike" bit for the name of the mod directory in it's install folder (of course changing the WINPATH to the folder for the new game).

If you are installing via steam then you need to launch it from steam first to set up the files. If you're running Compiz disable it before launching the game from the terminal:

```
metacity --replace

```

(for gnome -see the script for the names of the other window managers) and do "compiz --replace" to restore compiz.

---

### Post by mikeym on 2007-10-14
There is now a script for Counter Strike Source and other VAC secured online games as part of the HowTo which will launch the games through Steam but find the running hl2.exe and poll it to find out when it finishes to restore the graphical environment.

---

### Post by dboot on 2008-03-17
Doesn't wine-doors work for installing Steam and HL2? I'm about to install them both on gutsy with compiz and want to know the best way to go about doing it.

---

### Post by mikeym on 2008-03-26
I've posted another HOWTO on running games with compiz after a lot of messing about. The link is on my signature below. It gets rid of the polling this script has, works with any window manager as it start it's own xsession and gets a performance boost to boot. 

The only thing is that I've not rewritten the launch script for half life yet. Wine is more stable these days than when I wrote this script so something like should work with the new script (or on it's own without compiz running):

```

#!/bin/bash

# OPTIONS:

# Steam Application ID Half-Life 2 Deathmatch (320) Counter-Strike Source (240)
APPID=240

# Windows Path to steam
WINPATH="C:/Program Files/Steam"

# Graphics mode for hl2: 'dxlevel XX' where XX is the Direct X level * 10 (e.g. dxlevel 81) / 'gl' for OpenGL
GRAPHICSMODE="dxlevel 80"

# Game Resolution
WIDTH=1024
HEIGHT=768

# Extras
#CONSOLE="-console"

#Mode
MODE="-fullscreen  -width $WIDTH -height $HEIGHT"

export WINEDEBUG=fixme-all
hl2.exe "$WINPATH/Steam.exe" -$GRAPHICSMODE -applaunch $APPID $MODE $CONSOLE -heapsize 512000 +map_background none $EXTRAS "$@"

```

you can then run with *[x.game]("http://ubuntuforums.org/showthread.php?t=699332")* with:

```

x.game start hl2script.sh

```

---

