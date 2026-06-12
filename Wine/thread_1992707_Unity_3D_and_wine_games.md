---
title: "Unity 3D and wine games"
date: 2012-05-31
forum: Wine
---

### Post by pdvrosado on 2012-05-31
Yo I have a small issues, i've been playing diablo 2 + lod on my vaio with ubuntu 12, but sometimes when i hit alt and touch the touchpad, the window closes and it shows me the desktop, with everything bugged... Gnome 3 does the same after I quit diablo 2 on wine, the desktop gets distorted and the fonts can't be read and stuff. The stupid thing is that none of that happens on gnome 2 or ubuntu uniti 2d... Is this normal or something? I prefer to use ubuntu 3d since it's quicker and looks pretty, and the memory usage is lower than unity 2d (idk how...), but every damn time i hit alt or alt and shift, the desktop crashes. On unity 2d, i just press alt again, and click on the wine icon, and I'm back into the game, and everything works fine after i quit. but not on unity 3d or gnome 3.

help plz

---

### Post by cogadh on 2012-06-01
Just grasping at straws here, but it might have something to do with the keyboard shortcuts associated with Unity, or some other plugin of Compiz. I know a few of the Unity ones are ALT or SHIFT plus some other key, but that normally shouldn't cause this kind of problem. You could try installing CompizConfig Settings Manager and checking out the enabled shortcuts, maybe see if changing them helps.

---

### Post by pdvrosado on 2012-06-01
yeah, i've tried that but is was no good. just by pressing alt for x time, ubuntu opens the start panel and i can't return to diablo 2 anymore. It's kind of stupid, coz on unity 2d, i press alt again and a micro icon appears on the screen, and as i touch it, i can enter the game screen again. wth is wrong with this? ._.

---

### Post by teique on 2012-09-10
EDIT: lockable with xscreensaver super+L

I have created this script that creates a new X session and runs a command or open a terminal so you can run it there.

**openNewX.sh**
```
#!/bin/bash

function FUNCisX1running {
  ps -A -o command |grep -v "grep" |grep -q -x "X :1"
}

useJWM=true
useKbd=true
while [[ ${1:0:2} == "--" ]]; do
  if [[ "$1" == "--no-wm" ]]; then #opt SKIP WINDOW MANAGER (run pure X alone)
    useJWM=false
    shift
  elif [[ "$1" == "--no-kbd" ]]; then #opt SKIP Keyboard setup
    useKbd=false
    shift
  elif [[ "$1" == "--isRunning" ]]; then #opt check if new X :1 is already running
    if FUNCisX1running; then
      exit 0
    else
      exit 1
    fi
  elif [[ "$1" == "--help" ]]; then #opt show help info
    echo "usage: options runCommand"
    
    # this sed only cleans lines that have extended options with "--" prefixed
    sedCleanHelpLine='s"\(.*\"\)\(--.*\)\".*#opt" \2"' #helpskip
    grep "#opt" $0 |grep -v "#helpskip" |sed "$sedCleanHelpLine"
    
    exit 0
  else
    #echoc -p "invalid option $1"
    echo "PROBLEM: invalid option $1"
    $0 --help
    exit 1
  fi
done
#echo "going to execute: $@"
#runCmd="$1" #this command must be simple, if need complex put on a script file and call it!
runCmd="$@" #this command must be simple, if need complex put on a script file and call it!

#if ! echoc -q -t 2 "use JWM window manager@Dy"; then
#  useJWM=false
#fi

# run in a thread, prevents I from ctrl+c here what breaks THIS X instace and locks keyb
if ! FUNCisX1running; then
  xterm -e "\
  echo \"INFO: hit CTRL+C to exit the other X session and close this window\";\
  echo \"INFO: running in a thread (child proccess) to prevent ctrl+c from freezing this X session and the machine!\";\
  echo \"INFO: hit ctrl+alt+f7 to get back to this X session (f7, f8 etc, may vary..)\";\
  echo ;\
  echo \"Going to execute on another X session: $runCmd\";\
  sudo X :1"&
fi
#sudo chvt 8 # this line to force go to X :1 terminal

# wait for X to start
while ! FUNCisX1running; do
  sleep 1
done

# run in a thread, prevents I from ctrl+c here what breaks THIS X instace and locks keyb
if $useJWM; then
  if [[ ! -f "$HOME/.jwmrc" ]]; then
    echo '<?xml version="1.0"?><JWM><Key mask="4" key="L">exec:xscreensaver-command --lock</Key></JWM>' \
      >$HOME/.jwmrc
    #if ! jwm -p; then
    #  rm $HOME/.jwmrc
    #  echo ".jwmrc is invalid"
    #else
      echo "see http://joewing.net/programs/jwm/config.shtml#keys"
      echo "with Super+L you can lock the screen now"
    #fi
  fi
  
  jwm -display :1&
fi

kbdSetup="echo \"SKIP: kbd setup\""
if $useKbd; then
  kbdSetup="setxkbmap -layout us"
fi

sleep 2

xscreensaver -display :1&

# setxkbmap is good for games that have console access!; bash is to keep console open!

# nothing
#xterm -display :1&

# dead keys
#xterm -display :1 -e "setxkbmap -layout us -variant intl; bash"&

# good for games!
xterm -display :1 -e "$kbdSetup; bash -c \"$runCmd\"; bash"&
#xterm -display :1 -e "$kbdSetup; bash -c \"$@\"; bash"&

```

also, add this at: compiz config settings manager -> window rules -> non closeable windows:
```
(class=XTerm) & (title=sudo X :1) & (name=xterm)
```
This will prevent you from closing that terminal (use ctrl+c to close the other X session and also the terminal), because if you close "the window" it will freeze your current X session!

It has the advantage that you dont have alt+enter full screen problems, also no Alt+TAB full screen problems; you can run with more stability any 3D game, from Urban Terror (linux native) to games run with Wine! Even some browsers that run 3D games like Firefox with Quake!

Obs.: you may want to install jwm package, not required but will make a difference if you need to do any window management there..

PS.: it can be improved of course, my plan is to add the keyboard setup to an option, but I do it very slowly ;), if someone improve/clean it up, post so I can update mine script :)

---

### Post by Neo40 on 2012-09-11
I tried your script to launch a game (Civ IV BTS), it works fine but I have no sound! :(

---

### Post by teique on 2012-09-11
> **Neo40 said:**
> I tried your script to launch a game (Civ IV BTS), it works fine but I have no sound! :(

the script is only intended to prevent graphics instability

when you open a new X, you have a graphics environment untouched by unity 3D (that is great and I wont uninstall it for unity 2D or any other..)

so it has the most clean graphics environment = no crashes (caused by graphics instability); you can still have sound problems, or game bugs, or graphics driver bugs tho...

so, does sound work without the script (at normal "X :0") ?
in other words, you "still have no sound" or "now you have no sound" ?

---

### Post by Neo40 on 2012-09-12
Sound is working fine without your scritpt. So, if I play the game from current X (Ubuntu 12.10 Beta-1), video is ok but a bit jerky and sound is ok. If I use your script, video is much better but I have no sound.

---

### Post by teique on 2012-09-12
> **Neo40 said:**
> Sound is working fine without your scritpt. So, if I play the game from current X (Ubuntu 12.10 Beta-1), video is ok but a bit jerky and sound is ok. If I use your script, video is much better but I have no sound.

after the game exits, the terminal at X :1 will remain opened, you can read the error log there looking for something related to sound.
EDIT: to have also a log file, do this: yourRunGameScript.sh |tee "GameName.log"

also, try this: add a delay before calling your game in your script like:
sleep 5
may be the game is starting too fast

another thing, while the other X and terminal is open but you exit the game, run it again and see what happens?

all games I run there have no sound issues!

PS.: I would wild guess also that, by having no sound you video may be playing fast, so you could try disable the sound on X :0, to see what happens?
You may have a sound issue on your system, update it also.
( I had sound issues on mine, I had to force loading kernel modules to make it work on X :0 )

---

### Post by vexorian on 2012-09-12
My method for running a terminal sesion is much less sophisticated.

sudo gedit /usr/share/xsessions/terminal.desktop 
```

[Desktop Entry]
Name=Terminal
Comment=This session logs you into Terminal
Exec=gnome-terminal
TryExec=gnome-terminal
Icon=
Type=Application

```
sudo chmod +rx+rx+rx /usr/share/xsessions/terminal.desktop 


I wonder if the results are different. (This one requires you to run the game manually from CLI)

Also, to avoid sound issues, I normally do this before calling WINE (in a script made to launch the game)

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie

The .asound* thing may be unnecessary lately.

About terminal being unlockable. My only solution is to close the game and exit the terminal. If the other people in your house are technologically or (ubuntu) illiterate then you can just press Ctrol+Alt+F1 and it will 'block' the screen as long as the person does not know that she has to press Ctrol+Alt+F7.

---

### Post by teique on 2012-09-13
> **vexorian said:**
> sudo /usr/share/xsessions/terminal.desktop
interesting, I dont like to touch much files outside the user home, I prefer to let the OS manage them, because it may "want" to change or overwrite or delete them, and I dont like surprises :), I dont know if thats the case tho...

> **vexorian said:**
> Also, to avoid sound issues, I normally do this before calling WINE (in a script made to launch the game)

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie

The .asound* thing may be unnecessary lately.
try also: pulseaudio -k 
will auto restart self also
but I admit once I had to remove ~/.pulse, one time only tho.. dont remember why tho... :)

> **vexorian said:**
> About terminal being unlockable. My only solution is to close the game and exit the terminal. If the other people in your house are technologically or (ubuntu) illiterate then you can just press Ctrol+Alt+F1 and it will 'block' the screen as long as the person does not know that she has to press Ctrol+Alt+F7.
I think its possible to run some kind of screensaver, may do the trick; I just havent tried/researched yet, but is surely a missing important feature..

EDIT: I updated the script so it now support xscreensaver lock!

---

### Post by vexorian on 2012-09-14
There's no problem in creating new files in the xsessions folder. Because it was created for that very reason. The only situation in which the system will want to overwrite it is if you install a package that for some reason creates a terminal.desktop, in that case then it means that someone in the repositories created a package that does exactly what we want and you are installing it in your PC.

---

