---
title: "Continuum on wine doesn't work, even though it should"
date: 2006-09-17
forum: Wine
---

### Post by Starlight on 2006-09-17
Hello!

I downloaded the Linux version of Continuum here: [http://wine.getcontinuum.com/](http://wine.getcontinuum.com/)

I installed it acording to the instructions, but when I try to run Continuum, I get this error:

wine: failed to initialize: /usr/local/lib/wine/ntdll.dll.so: cannot open shared object file: No such file or directory

It seems that wine is looking for it in the wrong directory... because that file is in the ~/Continuum-wine/bin directory, together with the special wine version which is used to run Continuum... Does anyone know how to make it look for files in the right directory?

---

### Post by Starlight on 2006-09-17
I'll try to give some more details :)

Continuum is installed in the Continuum-wine directory in my home directory. There are two subdirectories inside it... one is called bin, and it's a directory with a special version of wine which is required to run the game (it doesn't work with normal wine), and the second one is called Continuum, and it contains the actual game. There are also two scripts in the Continuum-wine directory. The first one is used to run the game, and here it is:

continuum.sh
```
#!/bin/sh
~/Continuum-wine/wine ~/Continuum-wine/Continuum/Continuum.exe
```

And here's the second one... it seems that it's supposed to set the right paths and then run the game using the special wine version:

wine
```
#!/bin/sh
#
# Wrapper script to run Wine and Winelib apps from inside the source tree
#
# Copyright (C) 2002 Alexandre Julliard
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA
#

# first determine the directory that contains the app itself

appdir=""
case "$0" in
  */*)
    # $0 contains a path, use it
    appdir=`dirname "$0"`
    ;;
  *)
    # no directory in $0, search in PATH
    saved_ifs=$IFS
    IFS=:
    for d in $PATH
    do
      IFS=$saved_ifs
      if [ -x "$d/$0" ]
      then
        appdir="$d"
        break
      fi
    done
    ;;
esac

# now find the top-level directory of the source tree

if [ -x "$appdir/bin/wineserver" ]
then topdir="$appdir"
elif [ -x "$appdir/../bin/wineserver" ]
then topdir="$appdir/.."
elif [ -x "$appdir/../../bin/wineserver" ]
then topdir="$appdir/../.."
elif [ -x "$appdir/../../../bin/wineserver" ]
then topdir="$appdir/../../.."
else
  echo "$0: could not locate Wine source tree"
  exit 1
fi

# setup the environment

topdir=`cd "$topdir" && pwd`

if [ "`uname -s`" = "Darwin" ]
then
  if [ -n "$DYLD_LIBRARY_PATH" ]
  then
    DYLD_LIBRARY_PATH="$topdir/bin:$DYLD_LIBRARY_PATH"
  else
    DYLD_LIBRARY_PATH="$topdir/bin"
  fi
  export DYLD_LIBRARY_PATH
else
  if [ -n "$LD_LIBRARY_PATH" ]
  then
    LD_LIBRARY_PATH="$topdir/bin:$LD_LIBRARY_PATH"
  else
    LD_LIBRARY_PATH="$topdir/bin"
  fi
  export LD_LIBRARY_PATH
fi

if [ -n "$WINEDLLPATH" ]
then
  WINEDLLPATH="$topdir/bin:$topdir/bin:$WINEDLLPATH"
else
  WINEDLLPATH="$topdir/bin:$topdir/bin"
fi
WINESERVER="$topdir/bin/wineserver"
WINELOADER="$topdir/bin/wine"
export WINEDLLPATH WINESERVER WINELOADER

# any local settings ?
if [ -f "$topdir/.winewrapper" ]
then
    . $topdir/.winewrapper
fi

# create prefix directory if needed

if [ -z "$WINEPREFIX" -a ! -d "$HOME/.wine" ]
then
    "$topdir/bin/wineprefixcreate" --use-wine-tree "$topdir"
fi

# and run the application

case "$0" in
  wine|*/wine)
    exec "$WINELOADER" "$@"
    ;;
  */*)
    [ -f "$0.exe.so" ] && exec "$WINELOADER" "$0.exe.so" "$@"
    echo "$0: cannot find corresponding application"
    exit 1
    ;;
  *)
    [ -f "$appdir/$0.exe.so" ] && exec "$WINELOADER" "$appdir/$0.exe.so" "$@"
    echo "$0: cannot find corresponding application"
    exit 1
    ;;
esac
```

---

### Post by Starlight on 2006-09-18
just bumping the thread...

---

### Post by tht00 on 2006-09-20
Sweet!  Linux version of Subspace/Continuum??

I thought the day would never come... (well, last time I checked, numbers were seriously dwindling in some zones.  I haven't checked up on it in about a year).

Pray tell, is WarzoneCTF still alive and well?


I'll look into this soon.  I played it for a few years (and logged somewhere ~400 hours).  I dropped out of continuum about 1 1/2 ago (shortly before I started college), and then once I installed Ubuntu(and rarely boot Windows), I kinda gave up on the idea of ever playing it much again.

---

### Post by tht00 on 2006-09-20
Yeah, it looks like there's something broken with the wine script.  I'll try digging in later today (though, I'm not proficient with scripts).  

I'm really itching to play now. :D

---

### Post by Starlight on 2006-09-20
Well, I've never played it before, but it seems like a really cool game... that's why I'd love to play it. :) Does it work on your computer?

---

### Post by tht00 on 2006-09-20
> **Starlight said:**
> Well, I've never played it before, but it seems like a really cool game... that's why I'd love to play it. :) Does it work on your computer?

No, it doesn't work... at least not at the moment (same error).

---

### Post by tht00 on 2006-09-20
Yay.  I got it working.

Not a very solid solution, but it does seem to work fine.

Since it was looking in the wrong place for the files, I just made a symbolic link from there back to the right files:
```

sudo ln --symbolic ~/Continuum-wine/bin/ /usr/local/lib/wine/
```

From there, I got a weird error that it couldn't find 'libwine_unicode.so.1'.  I found the file in a 386 RPM, pulled out the file, and put it in '/usr/lib/'.  I've attached the file (zipped) if you need that.

Also, you'll likely need to change the sound to get it working in game:
```
winecfg
```

Under the 'sound' tab, change one of the drop-down boxes (hardware acceleration, I think) to 'emulated'.

That should get it up and running.

---

### Post by Starlight on 2006-09-21
Thanks! i can run the game now :) But it keeps putting me in the spectator mode, and I have no idea why...

---

### Post by tht00 on 2006-09-21
> **Starlight said:**
> Thanks! i can run the game now :) But it keeps putting me in the spectator mode, and I have no idea why...

That happens when you have latency (lag).  Make sure you've got no downloads going (especially if you aren't on broadband).

Sometimes there is a clogged server inbetween you and the Subspace server... but it seems the 'trace' function doesn't work in Linux.  If there is a clogged server, it doesn't matter if you have the fastest connection in the world.

As a rule of thumb, a playable ping will be under 300.  'Decent' would be under 150.  'Good' would be under 70.  Right now, I'm hitting pings of 30. :D 

Right now, I'm trying to get the fullscreen to work...

---

### Post by Starlight on 2006-09-24
It seems that it's a problem with my internet connection in general..

---

### Post by vskye on 2006-11-05
I have 0.2.1 installed here and it works well. I had to edit the file wine, which is in your $Home/Continuum-wine directory.  I commented out the following lines like so:

# else
# echo "$0: could not locate Wine source tree"
# exit 1

Now it's working fine.  I play full-screen and MATCH the resolution of my monitor. (if not, I have to restart X (ctrl-alt-backspace) to get it corrected. Also, make sure you follow the rest of the instructions here:
[http://wine.getcontinuum.com/](http://wine.getcontinuum.com/)

Dana

---

### Post by andrewroth on 2007-02-18
I had to comment out the 'else' like a few others had to.

I also had to use the dev version ([http://wine.getcontinuum.com/development.php](http://wine.getcontinuum.com/development.php)) else I got:

[andrewroth@localhost Continuum-wine]$ ./continuum.sh wine: failed to initialize: /usr/local/lib/wine/ntdll.dll.so: cannot open shared object file: No such file or directory

Like the original poster.

-Andrew Roth

---

### Post by n00bish on 2007-02-19
I got it working but I get an ugly, distorted screen whenever I try to join a server.  The server selector part works though..  any ideas?

---

### Post by Xenix on 2007-02-19
I can get Continuum running very well on Ubuntu 6.06 and 6.10 by compiling Wine from source and applying a small patch for it.  I use [_this guide_]("http://wiki.minegoboom.com/index.php/Running_Continuum_under_Wine") to install and get Contiuum running.

If using the above guide, then be sure to read the bottom of the guide first about the extra stuff you will need in order to compile Wine properly with Ubuntu.  I think the last time I ran Continnum using this method I was using Wine 0.9.29.  Not sure if it still works with later versions, but it should.

Enjoy :)

NOTE: I have issues running the pre-compiled version.

---

### Post by n00bish on 2007-02-19
I figured out my problem - I adjusted the color depth, then I changed it to "fullscreen" - it's not fullscreen, but it plays now.

---

### Post by rommie7 on 2008-02-26
Hmmm, it's actually running perfect on my Ubuntu 7.10, i had the same problem as the writer but i did the soultion given here and it works just perfecty.

i run it full screen with fps high enough to play it smoothly without needing to change color depth or turn compiz off.

plus i found how to activate the chat when u minimize (press the lower left butten on the ubuntu lower taskbar)

---

