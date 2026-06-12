---
title: "Installing Fallout"
date: 2007-08-03
forum: Wine
---

### Post by MikeStone on 2007-08-03
I just managed to aquire a copy of the Loki port of Fallout to Linux.  But the setup script fails with the following error...

setup.sh: 9: function: not found
x86_64

I'm fairly new to Linux and still finding my way around.  And since Loki no longer exists, I can't go to them for help.  Any assistance would be greatly appreciated.  I've copied the script below...

#!/bin/sh
#
# Product setup script - Loki Entertainment Software

# Go to the proper setup directory (if not already there)
cd `dirname $0`

# Return the appropriate architecture string
function DetectARCH {
	status=1
	case `uname -m` in
		i?86)  echo "x86"
			status=0;;
		*)     echo "`uname -m`"
			status=0;;
	esac
	return $status
}

# Return the appropriate version string
function DetectLIBC {
      status=1
      if [ -f `echo /lib/libc.so.6* | tail -1` ]; then
	      if fgrep GLIBC_2.1 /lib/libc.so.6* 2>&1 >/dev/null; then
	              echo "glibc-2.1"
	              status=0
	      else    
	              echo "glibc-2.0"
	              status=0
	      fi        
      elif [ -f /lib/libc.so.5 ]; then
	      echo "libc5"
	      status=0
      else
	      echo "unknown"
      fi
      return $status
}

# Detect the Linux environment
arch=`DetectARCH`
libc=`DetectLIBC`

# Find the installation program
function try_run
{
    setup=$1
    shift
    fatal=$1
    if [ "$1" != "" ]; then
        shift
    fi

    # First find the binary we want to run
    failed=0
    setup_bin="setup.data/bin/$arch/$libc/$setup"
    if [ ! -f "$setup_bin" ]; then
        setup_bin="setup.data/bin/$arch/$setup"
        if [ ! -f "$setup_bin" ]; then
            failed=1
        fi
    fi
    if [ "$failed" -eq 1 ]; then
        if [ "$fatal" != "" ]; then
            cat <<__EOF__
This installation doesn't support $libc on $arch

Please contact Loki Technical Support at [email]support@lokigames.com[/email]
__EOF__
            exit 1
        fi
        return $failed
    fi

    # Try to run the binary
    # The executable is here but we can't execute it from CD
    setup="$HOME/.setup$$"
    cp "$setup_bin" "$setup"
    chmod 700 "$setup"
    if [ "$fatal" != "" ]; then
        "$setup" $*
        failed=$?
    else
        "$setup" $* 2>/dev/null
        failed=$?
    fi
    rm -f "$setup"
    return $failed
}


# Try to run the setup program
status=0
rm -f "$setup"
if ! try_run setup.gtk && ! try_run setup -fatal; then
    echo "The setup program seems to have failed on $arch/$libc"
    echo
    echo "Please contact Loki Technical Support at [email]support@lokigames.com[/email]"
    status=1
fi
exit $status

---

### Post by lintoolman on 2007-08-03
I'm no expert, but it seems your attempting to install on a 64 bit OS and the script is expecting a 32bit OS.

---

### Post by cogadh on 2007-08-03
lintoolman may be right, but try using bash when running the script, not sh or ./:
```
sudo bash setup.sh
```

---

### Post by MikeStone on 2007-08-03
Thanks for your help.  Like I said, I'm a newcomer to Linux.  Ran it with Bash as you suggested and got this...

This installation doesn't support glibc-2.0 on x86_64

Please contact Loki Technical Support at [email]support@lokigames.com[/email]

I'm running Ubuntu on a PC with a AMD FX-55 64 bit chip.

---

### Post by cogadh on 2007-08-03
lintoolman was right, the game (or at least the installer) won't work on a 64-bit system.

---

### Post by cor2y on 2007-08-03
when i installed fallout i simply used the tutorial at the winehq site.
> 
[LIST=1]
[*]Use *winecfg* to set the Windows version to *Windows 98* for the setup.exe program located on the Fallout CD.
[*]Run the setup.exe program with Wine.
[*]Fallout doesn't correctly detect disk sizes, this problem also occurs when you try to install Fallout while running Dosbox or Windows, se~lect the *small installation* for now.
[*][Download the 1.1 patch]("http://www.carpetsmoker.net/distfiles_wine/fallout_patch_1.1.tar.gz"), and extract it to your Fallout ~directory, for example:
  *$ tar xf fallout_patch_1.1.tar.gz -C ~/.wine/drive_c/Fallout/*
[*]Use *winecfg* to set the Windows version to *Windows 98* for the Fallout executable, *falloutw.exe*.
[*]Optional:
If you don't want to insert the Fallout CD every time you want to play the game, you can copy the game files to your hard disk:
  *$ cp -r /mnt/cdrom/master.dat /mnt/cdrom/critter.dat /mnt/cdrom/data  ~/.wine/drive_c/fallout/*
  Be sure to overwrite *master.dat* and *critter.dat*, Fallout generates smaller versions of these files when running as a cache.   
  Edit *fallout.cfg*, and change the paths specified by the *music_path1*, *critter_dat*, and *master_dat* options ~from your CD-ROM to your harddisk, for example:
  *master_dat=D:\master.dat* should be changed to *master_dat=C:\fallout\master.dat*.[/LIST]


Also in the winecfg do not set a virtual desktop if you do this will cause the game to be displayed in a very small box unless you set your screen resolution to 640x480.
Instead leave it unchecked you then go into fullscreen for the game.
If the audio stutters or is scratchy switch from ESD to either OSS or ALSA.
And if that doesn't work then try the fix at the wine database
> 
**The sound stutters, movies stutter, game is generally slow.**Setting the nice level for Fallout can seriously increase performance:
*$ /usr/bin/nice -n 18 wine falloutw.exe*
You may want to try fiddeling with the exact nice level.

---

### Post by MikeStone on 2007-08-04
Thanks.  Guess I'm just out of luck.

Cor2y.  Thanks for the assist, but this is a Linux distribution of the game.

---

### Post by cor2y on 2007-08-07
i didn't even know they had made a linux verison of fallout.

---

### Post by Duncan_Idaho on 2007-08-07
its not
its a loki installer that install fallout on wine and make the shortcuts for you :lolflag:

---

### Post by cor2y on 2007-08-09
well then he can try th two verison's of install.
I couldn't get the dosbox version to run (installing fallout via dos)
But the wine install worked for me.
I didn't know about the loki installer.

---

### Post by Zxaos on 2007-09-19
> **cor2y said:**
> Also in the winecfg do not set a virtual desktop if you do this will cause the game to be displayed in a very small box unless you set your screen resolution to 640x480.

I've found that unless I put it in a virtual desktop it crashes the X Server and dumps me back at the login screen.  Maybe a widescreen issue?  As soon as I put it in the virtual desktop, it started running perfectly.

---

### Post by marcel3003 on 2007-11-10
Hi guys, I'm having problem with running the game, when I try to run, "Error initializing video mode 640x480" appears, and I have to set up system resolution to 640x480 to make the game working, How I can fix that to start the game without changing the resolution?

---

### Post by citi on 2007-12-14
Ok, so I have the Windows version of the game, but when I tried following cor2y's installation guide, at stage 2 when I'm supposed to run setup.exe my screen just fades to black and nothing happens. Is there anything I can do?

---

