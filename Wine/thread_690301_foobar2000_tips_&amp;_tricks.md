---
title: "foobar2000 tips &amp; tricks"
date: 2008-02-07
forum: Wine
---

### Post by chochem on 2008-02-07
Since I didn't find much on running foobar2000 under wine, I thought I'd share some ideas (in the selfish hope of having others share their experiences too ;-) What versions have what problems, how best to avoid skipping and glitches, etc.?

This is a wine forum, so please no "why don't you just use [insert Gnome native player of choice] instead?" posts, please. Shoo, go away.

Enough said. Here's the fruit of my efforts:

**Global hotkey functionality**
To achieve the equivalent of the media global shortcuts in GNOME (play, pause, stop, next etc.) you can use the fact that the foobar executable accepts parameters (and that Wine will pass them along). With foobar running and playing, try opening a terminal and enter:
```
wine [foobar2000 path]/foobar2000.exe /next
```
and foobar should skip to the next song in the playlist.
This can be systematised by [adding such commands to your window manager's custom commands list and assigning it a hotkey combination]("http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/").
Here's a few more selfexplanatory commands that should work:
```

wine [foobar2000 path]/foobar2000.exe /play
wine [foobar2000 path]/foobar2000.exe /pause
wine [foobar2000 path]/foobar2000.exe /stop
wine [foobar2000 path]/foobar2000.exe /next
wine [foobar2000 path]/foobar2000.exe /prev
wine [foobar2000 path]/foobar2000.exe /show
wine [foobar2000 path]/foobar2000.exe /hide

```

**Version 9.5**
'Minimize to tray icon' results in an empty outline when you focus the window. Use 'Always show notification area icon' instead.

The 9.5 version has an integrated album list (as opposed to a separate freefloating window) which tends to work better with regards to switching focus. On the downside is that adding files to the playlist by means of double-clicking or pressing Enter doesn't seem to work - you have to right-click and choose 'send to playlist'.

When switching workspaces and foobar2000 is not maximised, it will shrink to a small cramped window size. Either keep it maunally maximised or use [Devil's pie]("http://live.gnome.org/DevilsPie").

---

### Post by portach king on 2008-02-09
This thread is a really great idea. I hope some people can contribute, I've just installed foobar myself (gotta have that gapless playback).

---

### Post by robenroute on 2008-04-05
Have a look [here]("http://www.hydrogenaudio.org/forums/index.php?showtopic=54933"). There's loads of info and a very good guide to installing foobar2000 on the linux platform.

---

### Post by Lolicon on 2008-04-06
I can never map my keys to it, but foo_joystick works fine in wine.

---

### Post by Holt on 2008-08-03
Does anyone know how to use the number pad for global shortcuts? <Control>5 doesn't seem to do it, with or without Number Lock.

---

### Post by quazi on 2008-08-06
> **Holt said:**
> Does anyone know how to use the number pad for global shortcuts? <Control>5 doesn't seem to do it, with or without Number Lock.

If you're using compiz this is pretty easy to do.  Open the settings manager (if you don't have it, sudo apt-get install compizconfig-settings-manager) and go to General Options.  Click on the commands tab, set your command under commands and choose the appropriate key binding.  Enable it and then have it grab your key combination.

If you don't feel like doing that and prefer to use gconf-editor, without numlock on the keys are:
Directions - KB_Left, KB_Up, etc.
5 - KB_Begin
0,1,3,7,9,. - KB_Insert, KB_End, etc.
Enter,+,-,*,/ - KB_Enter, KB_Add, etc.

With numlock on, it's just KB_#.

One thing I'd like to add is that the component foo_runcmd.dll is very useful.  You're not simply limited to the standard playback commands, but you can do anything you'd normally be able to do with a shortcut in windows. 

For example, I have:
```
wine ~/.foobar2000/foobar2000.exe /runcmd="Playback/Stop After Current"
```

---

### Post by quazi on 2008-08-06
Sorry for the double post, but I was adding files to Foobar (didn't feel like building a database yet) and I missed the enqueue context menu in windows, so I made up this script:

```

#!/bin/bash
#
# Enqueue in Foobar
wine ~/.foobar2000/foobar2000.exe /add "$@"

```
Replace ~/.foobar2000/ with the location of your foobar2000 executable.
 
Stick her in ~/.gnome2/nautilus-scripts/ and make it executable. Now whenever you right click on a file and select that script in the right click menu, it'll add it to the current playlist.  I'm sure more advanced commands could be done (send to specific playlist etc.), but it was enough for my purposes.

---

### Post by NESFreak on 2008-08-31
Since I didn't like foobar opening every time i pressed one of my multimediakeys, (like while watching a video,) I decided to write a script that started and stopped running with foobar2000. I've based it upon a script for amarok [http://www.kde-apps.org/content/show.php?content=60910](http://www.kde-apps.org/content/show.php?content=60910). Anyway any time you run foobar2000 you can now also start this script, It detects start/pause, pause, stop, next and previous. If you've already made a shell script to start foobar2000 you could simply change the line "wine <path to foobar>" to "wine <path to foobar> & <path to foobar-gnome.py>

included with this post is the script.
Hope someone else finds this useful. NESFreak

---

### Post by rotwang888 on 2008-11-01
Hey folks.  After using the default IU with wine for a while and finally running across instructions to get art to display in a non-hideous way, I'm finally trying to reconstruct my old columns UI setup.  It's mostly working out, other than some things like 16x16 buttons not working and whatnot.  But I no longer have "send items to playlist" in the right-click context menu from the columns playlist view.  I probably just forgot to install a component, but I can't figure out which one.  Anybody know what the problem is, or an alternate way to send individual tracks from one playlist to another?

---

### Post by NESFreak on 2008-11-11
> **rotwang888 said:**
> Hey folks.  After using the default IU with wine for a while and finally running across instructions to get art to display in a non-hideous way, I'm finally trying to reconstruct my old columns UI setup.  It's mostly working out, other than some things like 16x16 buttons not working and whatnot.  But I no longer have "send items to playlist" in the right-click context menu from the columns playlist view.  I probably just forgot to install a component, but I can't figure out which one.  Anybody know what the problem is, or an alternate way to send individual tracks from one playlist to another?

drag n drop?

---

### Post by rotwang888 on 2008-11-15
> **NESFreak said:**
> drag n drop?

 Nope.  That works with the default UI but not columns UI.

---

### Post by quazi on 2008-11-17
> **rotwang888 said:**
> Hey folks.  After using the default IU with wine for a while and finally running across instructions to get art to display in a non-hideous way, I'm finally trying to reconstruct my old columns UI setup.  It's mostly working out, other than some things like 16x16 buttons not working and whatnot.  But I no longer have "send items to playlist" in the right-click context menu from the columns playlist view.  I probably just forgot to install a component, but I can't figure out which one.  Anybody know what the problem is, or an alternate way to send individual tracks from one playlist to another?

I can't manage to get my album art to not look horrible.  Mind sharing your secret:)?

---

### Post by rotwang888 on 2008-11-18
> **quazi said:**
> I can't manage to get my album art to not look horrible.  Mind sharing your secret:)?

 Sure, if I'm remembering this right.  To be honest I don't have fb2k set up right now.  Wine seemed to be messing up the sound in Intrepid in a way I don't understand.  Anyway, you need to put a few .dll files in your foobar directory.  Same one as the .exe.  I believe having them in .wine is not good enough.  You need gdiplus, libpng12, and zlib1.  Let me know if that works for you.  If not, I can try to dig up the link where I got the info in the first place.

---

### Post by quazi on 2008-11-19
> **rotwang888 said:**
> Sure, if I'm remembering this right.  To be honest I don't have fb2k set up right now.  Wine seemed to be messing up the sound in Intrepid in a way I don't understand.  Anyway, you need to put a few .dll files in your foobar directory.  Same one as the .exe.  I believe having them in .wine is not good enough.  You need gdiplus, libpng12, and zlib1.  Let me know if that works for you.  If not, I can try to dig up the link where I got the info in the first place.

Thanks, gdiplus.dll did it for me.  Now the images look great.

---

### Post by pravinbravi on 2008-11-20
Here's a screenshot of my fb2k in Ubuntu 8.10 Intrepid Ibex.

Ubuntu likes foobar2000 "my favorite music player" with all the capabilities / features very much like in windows xp. Even the great winamp dsp Izotope Ozone via foo_dsp_winamp.dll works great.

Enjoy!

---

### Post by moncojhr on 2008-12-13
> **rotwang888 said:**
> Nope.  That works with the default UI but not columns UI.

Drag and drop really works in the default ui? How did you do that? Its not working for me? Did you do anything in particular ?

---

### Post by rotwang888 on 2009-08-06
Wow..this thread sure got ancient.  Anyway, I didn't do anything special.  And by drag and drop I mean dragging a track from the main playlist to a playlist on the left.  And to answer my own old question in case anyone is interested, one can add a new command to the "utils" section of context menu.  I have no idea how I missed that.
  In the interest of raising this thread from the dead, I have a tip to share.  If your spectrum analyzer (or "analyser") panel is slow, try removing foo_uie_trackinfo.dll if you have it.  It worked for me.
  Has anybody managed to get custom buttons to display properly?  I've resorted to using "text only" for new buttons I want, but I'd rather not.
  Also, does anyone know why "open containing folder" crashes my foobar?  Deleting files from the playlist works fine for me, which for some reason I thought was related.

---

### Post by kaptenalex on 2009-08-16
Custom buttons works fine for me. Try to change one button at a time.

---

### Post by rotwang888 on 2009-08-17
I have.  I get a blank square.  What format are those in?  The images I've been trying are .png.

---

### Post by kaptenalex on 2009-08-17
My images is also png. Do you have the libgpng and zlib libraries from columns uis homepage in your foobar directory? My images is in Program/foobar2000/images, I don´t know if that has to do with something?

---

### Post by rotwang888 on 2009-08-20
> **kaptenalex said:**
> Do you have the libgpng and zlib libraries from columns uis homepage in your foobar directory?

Well, I do now.  I don't think I ever installed those in my Windows foobar2k.  Anyway, still nothing.

---

### Post by Gen2ly on 2009-08-20
Good someone posted this.  foobar is still my fav music player.

---

### Post by kaptenalex on 2009-08-20
Hm ok. When I try to change buttons the new ones doesn´t seems to work. I have no idea why just some icons are working.

---

### Post by rotwang888 on 2009-10-31
Alright, I have a tip for anyone who has a problem with horrible static coming from fb2k after upgrading to 9.10.  Try installing wine2.1 with a pulse audio patch.  Worked wonders for me, although one of the fonts I've been using in my config now looks like *****.  Check this thread — [http://www.uluga.ubuntuforums.org/showthread.php?p=8184364](http://www.uluga.ubuntuforums.org/showthread.php?p=8184364) for the link to the PPA you'll need.  Good luck!

---

### Post by rotwang888 on 2009-11-01
Aaaand I just got rid of the ugly fonts with the handy script on the following page. [http://ubuntuforums.org/showthread.php?t=1050920](http://ubuntuforums.org/showthread.php?t=1050920)

---

### Post by jacobbrett on 2010-01-14
> **rotwang888 said:**
> Aaaand I just got rid of the ugly fonts with the handy script on the following page. [http://ubuntuforums.org/showthread.php?t=1050920](http://ubuntuforums.org/showthread.php?t=1050920)

The AA fix didn't completely work for me (you can do it via winetricks too btw). Only dialogue boxes had AA text. I had to install [these replacement Tahoma fonts]("http://ubuntudoitall.blogspot.com/2009/09/wine-with-full-antialiasing.html") to make everything in foobar2000 AA.

EDIT: Check [my new blog]("http://jacobbrett.loserx.com/2010/01/14/foobar2000-in-wine/") for a foobar2000 installation guide in Linux/Ubuntu. :)

---

### Post by quazi on 2010-01-14
> **jacobbrett said:**
> The AA fix didn't completely work for me (you can do it via winetricks too btw). Only dialogue boxes had AA text. I had to install [these replacement Tahoma fonts]("http://ubuntudoitall.blogspot.com/2009/09/wine-with-full-antialiasing.html") to make everything in foobar2000 AA.

EDIT: Check [my new blog]("http://jacobbrett.loserx.com/2010/01/14/foobar2000-in-wine/") for a foobar2000 installation guide in Linux/Ubuntu. :)

I know this is somewhat offtopic in a foobar thread, but gmusicbrowser (not the repository version, that's way old) is a pretty good replacement for just playing music.  It can't replace all the foobar functions, but it's a great supplemental music player.

EDIT: The last link in your blog directs you to font smoothing rather than a "now playing" panel.

---

### Post by jacobbrett on 2010-01-15
> **quazi said:**
> I know this is somewhat offtopic in a foobar thread, but gmusicbrowser (not the repository version, that's way old) is a pretty good replacement for just playing music.  It can't replace all the foobar functions, but it's a great supplemental music player.

EDIT: The last link in your blog directs you to font smoothing rather than a "now playing" panel.
Yeah, gmusicbrowser was the last Linux player I tried (and liked the most) before deciding to give foobar2000 another shot. foobar does/can do *everything* I want.

Cheers, fixed!

---

### Post by Woegjiub on 2010-05-04
I'm wondering if any of you had the annoying problem of the audio not working after parsing through any command-line hotkey commands to foobar.
It works at first, then if I pause, and play, the media player will seem to be playing, but it will actually not be outputting audio.
I had a console error message under alsa that the main audio wasn't configured, but that went away after I decided to use OSS instead for wine.

Any ideas as to what could be causing this problem?

---

### Post by gunwald on 2011-03-26
Dear Foobar2000 users,

trying to integrate my Foobar2000 installation better in Ubuntu, I wrote a little script, that pro-vides following features:

[LIST]
[*]Multimedia key support: The script provides support for X86fAudioNext, X86fAudioPrev and X86fAudioplaypause (more can be added) for Foobar2000 if it is started. If not it triggers the action to the normal D-Bus-Command
[*]Play media in Foobar2000 (queue them) by double click in file manager
[*]Shows notify messages when using multimedia keys
[/LIST]
The script has the following dependencies:

[LIST]
[*]Wine installation of foobar2000 with the &#8220;now playing simple&#8221; component enabled (this component saves now playing information in a file, configure it in foobar2000 configuration to use the file &#8220;npnotify.txt&#8221; in foobar2000 installation folder (that means, the wine path, for example &#8220;C:\Program Files\foobar2000\npnotify.txt&#8221;)
[*]Copy the script to /usr/bin/foobar2000 and make it executable.
[*]Following Ubuntu packages are required:  libnotify-bin and xdotool  (sudo aptitude install libnotify-bin xdotool)
[*]Normally, to catch a multimedia key event you have to catch the D-Bus-Signal. I was at this far too lazy to program this, therefore I worked around:  So to use the script you have to change your shortkeys: Change standard shortkeys (System->Preferences->Shortkeys) for Play, next and Previous to ctrl+X86fAudioplaypause, ctrl+X86fAudioNext and ctrl+X86fAudioPrev.
[*]Add following new global hotkeys (as described [here]("http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/")):
[LIST]
[*]foobar2000 --playbackControl=playpause (X86fAudioplaypause)
[*]foobar2000 --playbackControl=next (X86fAudioNext)
[*]foobar2000 --playbackControl=prev (X86fAudioPrev)
[/LIST]
 
[/LIST]
You have to adjust the scripts first four variables with your system paths

```

#!/bin/bash

### BEGIN LICENSE
# Copyright (C) 2011 Gunwald Neuhausen <gunwald@gmx.de>
# This program is free software: you can redistribute it and/or modify it 
# under the terms of the GNU General Public License version 3, as published 
# by the Free Software Foundation.
# 
# This program is distributed in the hope that it will be useful, but 
# WITHOUT ANY WARRANTY; without even the implied warranties of 
# MERCHANTABILITY, SATISFACTORY QUALITY, or FITNESS FOR A PARTICULAR 
# PURPOSE.  See the GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License along 
# with this program.  If not, see <http://www.gnu.org/licenses/>.
## END LICENSE

# Parameter: $1 = playbackControl=(next|prev|playpause)  $2 = start=start; 

#######################################################################
# ----- Variable                                                      #
#######################################################################
# ----- Variable setzen ----------------------------------------------
winePrefix="/home/user/.wine/foobar2000"     # Den Ordner angeben, in dem die Wine-Dateien liegen
foobarPath="C:/Program Files/foobar2000/foobar2000.exe"  # Wine internen Pfad zu foobar2000.exe
iconPath="/usr/share/pixmaps/foobar2000.xpm"             # Pfad zum Foobar2000 Symbol
# Pfad zu der Datei, in der die Foobarerweiterung "Now Palying Simple" die Titelinformationen speichert.
# Das Plugin muß zuvor in Foobar integiert werden und unter "File->Preferences" Tools->Now Playing simple
# konfiguriert werden.
npnotifyPath="/home/user/.wine/foobar2000/drive_c/Program Files/foobar2000/npnotify.txt"

# Aktion die Foobar standartmäßig ausführt.
playbackControl='play' 


# Pfad zu der Datei, in welcher das Foobar2000-Plugin "now playing simple" 
# die Informationen zu dem gerade gespielten Titel speichert
nowPlaying=`while read line; do echo "$line" ;done < "$npnotifyPath"`
path=""

# Werte der Variablen werden geändert, wenn dem Skript Parameter
# übergeben wurden
numberOfParam=$#
for (( I=1; $I <= $numberOfParam; I++ )); do

    # Überprüfen, ob es sich um einen gültigen Dateipfad handelt. Ist dies der Fall
    # muß er in einen Windowspfad umgewandelt werden und soll nicht in Name und Wert
    # aufgeteilt werden.
    if test -f "$1"
      then
      path=`echo "z:$1" | sed 's/\\//\\\\/g'`
      # Ist ein Pfad übergeben, kann davon ausgegangen werden, daß
      # läuft Foobar2000 nicht, er gestartet werden soll
      start=start
       
      else
      
          path=""
          # Der Parameter ist kein Dateipfad 
          # Überprüfen, Ob Variabel leer ist, wenn nicht, nach Name und Wert aufteilen
          if [ "`echo "$1" | awk 'BEGIN { FS = "=|&" } { print $2 }'`" != "" ]; then 
            # In der Variablen 'temp' wird der Bezeichner des Parameters 
            # gespeichert also im Beipspiel "--paramtersName=paramtersValue"
            # hätte temp den Wert --paramtersName
            temp=`echo "$1" | awk 'BEGIN { FS = "=|&" } { print $1 }'`

            # Nun wird aus temp der Name einer Variablen gewonnen und
            # aus dem zweiten Teil des Parameters ihr Wert
            eval "`echo $temp | awk 'BEGIN { FS = "--|-" } { print $2 }'`=`echo $1 | awk 'BEGIN { FS = "=|&" } { print $2 }'`"
          fi
    fi
    
    shift
done


echo $path

# Testen, ob foobar2000 schon läuft

    foobar2000Pid=`ps -fe|grep "[f]oobar2000.exe"|awk '{print $2}'`
    
   
    if [ $foobar2000Pid ]
       then
       echo "Foobar2000 läuft, die PID ist: " $foobar2000Pid
       env WINEPREFIX="$winePrefix" wine "$foobarPath" "$path"  "/"$playbackControl

            # Nachrichten ausgeben
            test=$playbackControl
            case "$test" in
                next ) 
                   # Aktuelle Titelinformationen neu einlesen. Vorher muß einen Moment gewartet werden, bis Foobar2000
                   # die aktuellen Informationen in die entsprechende Datei geschrieben hat. Allerdings ist das
                   # eine unsaubere Lösung, besser wäre es, die Änderung an der Datei durch eine Schleife zu überwachen.
                   sleep 1
                   nowPlaying=`while read line; do echo "$line" ;done < "$npnotifyPath"`
                   # Aktuelle Aktion und Titelinformationen ausgeben
                   notify-send --icon="$iconPath" "Nächster Titel wird gespielt:" "$nowPlaying" 
                     echo "Nächster Titel wird gespielt:" "$nowPlaying"
                   ;;
                prev ) 
                   # Aktuelle Titelinformationen neu einlesen. Vorher muß einen Moment gewartet werden, bis Foobar2000
                   # die aktuellen Informationen in die entsprechende Datei geschrieben hat. Allerdings ist das
                   # eine unsaubere Lösung, besser wäre es, die Änderung an der Datei durch eine Schleife zu überwachen.
                   sleep 1
                   nowPlaying=`while read line; do echo "$line" ;done < "$npnotifyPath"`
                   # Aktuelle Aktion und Titelinformationen ausgeben
                   notify-send --icon="$iconPath" "Vorheriger Titel wird gespielt:" "$nowPlaying"
                   echo "Vorheriger Titel wird gespielt:" "$nowPlaying"
                   ;;
                playpause ) 
                   # Aktuelle Titelinformationen neu einlesen
                   nowPlaying=`while read line; do echo "$line" ;done < "$npnotifyPath"`
                   # Aktuelle Aktion und Titelinformationen ausgeben                
                   notify-send --icon="$iconPath" "Weidergabe anhalten/fortfahren:" "$nowPlaying" 
                   echo "Weidergabe anhalten/fortfahren:" "$nowPlaying"       
                   ;;
                *) 
                   echo "Sorry, wrong option" 
                   ;;
            esac



      else
        echo "Foobar2000 läuft nicht..."
      
        if [ $start ]  
           then
           padsp env WINEPREFIX="$winePrefix" wine "$foobarPath" "$path" "/playpause" &
           echo "Foobar2000 wird nun gestartet"
           else
           
            # Trigger multimedia keys: Die Standartfunktion der Multimeidatasten wurde auf ctrl+XF86AudioXXX gelegt und soll 
            # aber auch ohne ctrl ausgeführt werden. Allerdings nur, wenn foobar2000 nicht läuft und nicht gestartet wird.
            test=$playbackControl
            case "$test" in
                next ) 
                   xdotool key ctrl+XF86AudioNext 
                     echo "Simuliere XF86AudioNext"
                   ;;
                prev ) 
                   xdotool key ctrl+XF86AudioPrev
                   echo "Simuliere XF86AudioPrev"
                   ;;
                playpause ) 
                   xdotool key ctrl+XF86AudioPlay 
                   echo "Simuliere XF86AudioPlay"       
                   ;;
                *) 
                   echo "Sorry, wrong option" 
                   ;;
            esac
           
        fi
   fi


exit 0;

```

---

### Post by flemur13013 on 2011-04-08
"Playback Queue" visibility frustrations?  IOW, you add songs to the "Playback Queue", via search, say, and you can't see the "Playback" queue.  Also, with a search, if you select any tracks, they what was already there, with no ability to just add them.

Playback Queue Viewer (foo-pqview) didn't work for me - no songs were added to any visible queue.

I got around these problems by putting the Search right above the Playlist Mgr, and dragging from the search results to the "Default" queue on top.  NO more missing "Playlist Queue".

But DON'T select "Add to Playback Queue" as shown in the picture - just drag the selected search results onto the queue in the list below.

---

### Post by paradajz on 2012-03-01
> **gunwald said:**
> Dear Foobar2000 users,

trying to integrate my Foobar2000 installation better in Ubuntu, I wrote a little script, that pro-vides following features:

...




How exactly did you make it default player in Linux? I've ran the script but still can't open files from Nautilus with f2k. Maybe because I'm using Mint (it shouldn't matter tho)?

Also, couple of issues here:

Right click on any track in foobar playlist, open containing folder - > result: foobar crashes

Quicksearch icon is just black square, anyone knows how to fix it?

---

### Post by gunwald on 2012-03-01
To make foobar2000 become your default player you have to create a desktop file pointing to the script. Unfortunately since version 3 Nautilus does not do this for you anymore, since the »open with« dialogue does not provide the possibility to open files with your own scripts.
So:

[LIST=1]
[*]Go to the folder ~/.local/share/applications
[*]Create a empty text file named foobar2000.desktop there
[*]copy following content to this file and edit it safe it:
```
[Desktop Entry]
Type=Application
Name=foobar2000
GenericName=Plays music
Version=1.0
Encoding=UTF-8
Terminal=false

# Put path to your script here
Exec=/usr/bin/foobar2000
Comment=Plays music and looks swell

#Put the path to a foobar icon here 
Icon=/usr/share/foobar2000.xpm
Categories=GNOME;GTK;AudioVideo;Audio;Player;
```
[*]Safe the file
[*]Now you can browse your music files with Nautilus click them right and choose »Preferences« ->»Open with«
[*]Choose »Show other application«. you should now find foobar2000 in this list. Choose it add it and make it default.
[*]That was it. It became that complicated because of the fact that Gnome 3 is funking crazy ****!
[*]
[/LIST]

---

### Post by pravinbravi on 2012-09-07
[ATTACH]223852[/ATTACH]

[ATTACH]223853[/ATTACH]> **kaptenalex said:**
> Custom buttons works fine for me. Try to change one button at a time.


here's one with custom buttons fb2k v1.1.15 beta1 DUI portable install in wine under lubuntu 12.04 AMD64 on Acer Aspire AO722 AMD c60, 4GB RAM, btrfs root fs & home setup. 

Enjoy guys. fb2k rocks and kicks azz as hell.

Also attached herewith, buttons, the theme (.fth in zip file), but will need to install droid Sans and Deja Vu sans font families.

---

