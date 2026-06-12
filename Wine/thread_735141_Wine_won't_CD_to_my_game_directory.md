---
title: "Wine won't CD to my game directory"
date: 2008-03-25
forum: Wine
---

### Post by asdfqwert on 2008-03-25
I've tried cogadh's instructions to make a script, and when itry to run it, i get 

[email]ubuntu1@ubuntu1-desktop:~/.wine[/email]/drive_c/Program Files/LucasArts$ nano launcher.sh
[email]ubuntu1@ubuntu1-desktop:~/.wine[/email]/drive_c/Program Files/LucasArts$ chmod +x ~/launcher.sh
[email]ubuntu1@ubuntu1-desktop:~/.wine[/email]/drive_c/Program Files/LucasArts$ sh launcher.sh
cd: 12: can't cd to /home/ubuntu1/.wine/drive_c/Program\ Files/LucasArts/Star Wars Jedi Knight Jedi Academy
wine: cannot find 'C:/Program 
Files/LucasArts/Star Wars Jedi Knight Jedi 
Academy/GameData/jamp.exe'
[email]ubuntu1@ubuntu1-desktop:~/.wine[/email]/drive_c/Program Files/LucasArts$ 


Does the terminal HAVE to be in the home folder, or is it something related to the spacing in Star Wars Jedi Knight Jedi Academy?

---

### Post by prshah on 2008-03-25
> **asdfqwert said:**
> 
cd: 12: can't cd to /home/ubuntu1/.wine/drive_c/Program\ Files/LucasArts/[color=red]Star Wars Jedi Knight Jedi Academy[/color]
is ti something related to the spacing in Star Wars Jedi Knight Jedi Academy?

Your cd line is not escaped properly; in Windows you can use quotes but in linux, each space in a file/folder name must be preceded by a "\", eg:
cd ~/.wine/drive_c/Program\ Files/LucasArts/Star[color=red]\[/color] Wars[color=red]\[/color] Jedi[color=red]\[/color] Knight[color=red]\[/color] Jedi[color=red]\[/color] Academy

Also keep in mind that the case (upper, lower) is important.

---

### Post by asdfqwert on 2008-03-25
ok, well the script is 

#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia

# take out the "& nvidia-settings --load-config-only" para

# Goto game dir (modify as needed)
cd /home/ubuntu1/~.wine/drive_c/Program\ Files/LucasArts/Star\ Wars\ Jedi\ Knight\ Jedi\ Academy


# Forces the system to have a break for 2 seconds, X doesn't launch
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program\ Files/LucasArts/Star\ Wars\ Jedi\ Knight\ Jedi\ Academy/GameData/jamp.exe"


when i run it i get

cd: 12: can't cd to /home/ubuntu1/~.wine/drive_c/Program Files/LucasArts/Star Wars 
launcher.sh: 13: Jedi Knight Jedi Academy: not found
wine: cannot find 'C:/Program\ Files/LucasArts/Star\ Wars\ Jedi\ 
Knight\ Jedi\ Academy/GameData/jamp.exe'

---

### Post by FrozenFox on 2008-03-25
In     cd /home/ubuntu1/~.wine/drive_c/Program\ Files/LucasArts/Star\ Wars\ Jedi\ Knight\ Jedi\ Academy


You should not have a ~ before .wine

~ at the beginning of the location means /home/yourname. Ie, if you typed ls ~ it would show you what files and folders are in /home/yourname. I'm pretty sure it means nothing in the middle of a path, and I somehow doubt you meant to put it there. In the future you can save yourself a lot of trouble by copying and pasting the location and just putting double quotes around the whole thing. Ie:

cd /home/ubuntu1/.wine/drive_c/Program\ Files/LucasArts/Star\ Wars\ Jedi\ Knight\ Jedi\ Academy
should work the same as
cd "/home/ubuntu1/.wine/drive_c/Program Files/LucasArts/Star Wars Jedi Knight Jedi Academy"

---

### Post by asdfqwert on 2008-03-25
Now i get




> ubuntu1@ubuntu1-desktop:~$ sh launcher.sh
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.


---

### Post by happyhamster on 2008-03-25
- You'll have to get rid of the DISPLAY=:3 part. (In that case the game won't run in a separate X session.) If you do want it to run in its own X session, you'll need the line:

X :3 -ac & nvidia-settings --load-config-only

- or, for non-Nvidia owners:

X :3 -ac &

- Example:
```
#!/bin/sh
            #uncomment if launching from console session
            #sudo /etc/init.d/gdm stop

            # Launches a new X session on display 3. If you don't have an Nvidia card
            # take out the "& nvidia-settings --load-config-only" part
            X :3 -ac & nvidia-settings --load-config-only

            # Goto game dir (modify as needed)
            cd "$HOME/.wine/drive_c/Program Files/Reality Pump/KnightShift/"

            # Forces the system to have a break for 2 seconds, X doesn't launch instantly 
            sleep 2

            # Launches game (modify as needed)
            DISPLAY=:3 WINEDEBUG=-all wine KnightShift.exe
```

- For this to work, you'll also need to allow a regular user to get X access:

sudo nano /etc/X11/Xwrapper.config

- And change the line "allowed_users=console" into "allowed_users=anybody"

- After that you should be able to run the script as a regular user (you won't need to use 'sudo'). Also, to get back to your regular X session, press ctrl-alt-F7.

Good luck.

---

### Post by asdfqwert on 2008-03-25
I tried it, but i got an error about mpconfig(but i didn't have the CD in.)
So i came back to my X session,(ctrl+alt+F7) put the CD in and ran the script again, but i got


> Fatal server error:
Server is already active for display 3
        If this server is no longer running, remove /tmp/.X3-lock
        and start again.


How can i delete it(if it's safe to delete it)?

---

### Post by happyhamster on 2008-03-26
To close the X session you can always use ctrl-alt-backspace (but it will mean all other programs will be terminated and you'll need to login again)

---

### Post by asdfqwert on 2008-03-26
I get an error.


> JAmp: v1.0.1.0 win-x86 Oct 24 2003
----- FS_Startup -----
Current search path:
Z:\home\ubuntu/base

----------------------
0 files in pk3 files

Running in restricted demo mode.

----- FS_Startup -----
Current search path:
Z:\home\ubuntu/demo

----------------------
0 files in pk3 files
Couldn't load mpdefault.cfg


I actually stole that from another thread since i didn't copy the message, but it's exactly that except for the path.

---

