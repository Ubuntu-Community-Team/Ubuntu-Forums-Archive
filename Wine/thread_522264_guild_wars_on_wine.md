---
title: "guild wars on wine"
date: 2007-08-10
forum: Wine
---

### Post by taehC on 2007-08-10
i am trying to get guild wars on my ubuntu system cus my other system doesn't have a new enough video card so i was wondering if there was any way to get guild wars working in wine?  or any way to get it working in ubuntu?  i am going to try a virtual machine but i would rather not if there is an easier alternative such as some type of emulator or ANYTHING!!!
just give me something to make my game work :confused:

---

### Post by cogadh on 2007-08-10
A virtual machine won't work, they don't have hardware acceleration. Guild Wars will work fine in Wine:
[http://appdb.winehq.org/appview.php?iVersionId=8698](http://appdb.winehq.org/appview.php?iVersionId=8698)

---

### Post by taehC on 2007-08-10
i am using wine but is winehq different?

---

### Post by cogadh on 2007-08-10
No, WineHQ is just the name of the website that is the home of Wine (Wine Head Quarters).

---

### Post by taehC on 2007-08-10
the reason i said it wasnt working was because my mouse wasnt showing and it was really hard to click when i didnt know where my mouse was
now my keyboard is working....

i run
```
wine "C:\Program Files\Guild Wars\Gw.exe" -dsound
```
then when i type it types as if i am still on the terminal
it is cus i set the windows wine is using to not interact at all with other windows, this causes it to think i am still in the terminal, but if i try to switch back then it makes the mouse not work again :confused: ...

PLZ HELP ME!!!!!

---

### Post by cogadh on 2007-08-10
That problem is caused by disabled the "Allow window manager to control..." option in winecfg under Graphics. Unfortunately, you usually don't want that enabled because it can screw up full screen games. 

Click on the "Stuff I've learned about Wine" link in my sig and look for the "Advanced Stuff" section. It describes how to create a launcher script that will launch the game in its own X session and eliminate any problems with the window manager.

---

### Post by taehC on 2007-08-10
how do i find where guild wars in located in wine?  

i mean in your thing it says to enter the game location and where it says game i put Guild Wars instead but i dont know what to put at directory

---

### Post by cogadh on 2007-08-10
$HOME/.wine/drive_c/Program Files/Guild Wars/gw.exe

Open your home directory with the file browser and hit CTRL+H to show hidden folders. Look for a ".wine" directory, that is where your fake Windows install is. Inside that directory will be at least two more directories; "dosdevices" which just contains symbolic links to your drives, and "drive_c" which contains a file structure nearly identical to Windows (i.e. "Program Files" and "Windows" directories). Everything that you install through Wine can be found in the "drive_c" directory.

---

### Post by taehC on 2007-08-10
when i type
```
chmod +x ~/launcher.sh
```
the terminal doesnt say anything and when i do the next step it doesnt work or when i try the other way it doesnt work in a different way

---

### Post by cogadh on 2007-08-10
Copy and paste the contents of the script you created into a post here, it sounds like something might be wrong with one of the paths in it.

---

### Post by taehC on 2007-08-10
```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Goto game dir (modify as needed)
cd "$HOME/.wine/drive_c/Program Files/Guild Wars/Gw.exe"

# Forces the system to have a break for 2 seconds, X doesn't launch
instantly
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/Guild Wars/Gw.exe"

```
is that all correct?

---

### Post by cogadh on 2007-08-10
Yup, that's what it was. The "Goto game directory" section shouldn't have the .exe in the path. It should be like this:
```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Goto game dir (modify as needed)
cd "$HOME/.wine/drive_c/Program Files/Guild Wars/"

# Forces the system to have a break for 2 seconds, X doesn't launch
instantly
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/Guild Wars/Gw.exe"
```

---

### Post by taehC on 2007-08-10
it still doesnt say any thing when i type
```
chmod +x ~/launcher.sh
```
and then i use 
```
./ launcher.sh
```
and it says
```
bash: ./: is a directory
```
so then i try to do this
```
sh launcher.sh
```
and it does a lot of things mostly a lot of waiting though...
man i hope i can get this to work!

i have been looking over your wine thing and i think that making the games own x server but will it fix the problem i have now?

---

### Post by cogadh on 2007-08-10
Can't believe I missed this, but you are missing the very first line that creates the new X session for the game to run in. The full script should be like this:
```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac 

# Goto game dir (modify as needed)
cd "$HOME/.wine/drive_c/Program Files/Guild Wars/"

# Forces the system to have a break for 2 seconds, X doesn't launch
instantly
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/Guild Wars/Gw.exe"
```
I'm assuming you don't have an Nvidia card, so I left the Nvidia settings part off.

---

### Post by taehC on 2007-08-10
SO CLOSE

now what happens is when i run it  it has a gray screen and a X for a mouse
but thats it...

---

### Post by cogadh on 2007-08-10
You should get that at first and then the game should launch after a few seconds. If it doesn't, are there any error messages showing up in the terminal?

---

### Post by taehC on 2007-08-10
i waited about a minute and still nothing and after i press ctrl alt backspace it does have anything on the terminal
should i try the alternative way to make it work?

OH AND I FORGOT TO MENTION that i have xgl running  i dont have beryl on at the moment but if xgl is on should that change anything? should i turn it off?

---

### Post by cogadh on 2007-08-10
Are you certain that the Guild Wars executable is actually "Gw.exe" (i.e. could it be all uppercase letters or lowercase letters)?

---

### Post by taehC on 2007-08-10
yes i am sure and 
does me running xgl matter?
i dont have beryl running but i am in a xgl session

---

### Post by cogadh on 2007-08-10
Nope, that shouldn't matter at all. 

Try this script, I know it looks the same, but I removed a line break where it shouldn't have been:
```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac 

# Goto game dir (modify as needed)
cd "$HOME/.wine/drive_c/Program Files/Guild Wars/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/Guild Wars/Gw.exe"
```

---

### Post by taehC on 2007-08-10
i let it sit for a while and now i got some errors

```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux brandon-taehC 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.3.log", Time: Fri Aug 10 10:34:20 2007
(==) Using config file: "/etc/X11/xorg.conf"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```

---

### Post by cogadh on 2007-08-10
Those are all normal errors, unless you actually have a Wacom tablet pointer device attached to your computer. Did you get this result with the slightly modified script I put in my last post?

---

### Post by taehC on 2007-08-10
yes which when i tryed to copy it into the terminal it wasnt changing from what i put in last time but i took out the  "instantly"  that was the only change correct?

---

### Post by cogadh on 2007-08-10
Correct. I think its time to look at something other than the script, it should be working fine at this point. What are your winecfg settings on the Graphics tab?

---

### Post by taehC on 2007-08-10
the only thing i have checked is the allow pixel shader and the vertex shader support is set to hardware
just to say i have the windows version set to windows xp

---

### Post by taehC on 2007-08-10
should i have it emulate a virtual desktop and give the desktop its own x server?

---

### Post by cogadh on 2007-08-10
No, the emulate virtual desktop option just makes it run the game in a window instead of full screen.

Try changing the game launching line of the script to this:
```
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/Guild Wars/Gw.exe" -dsound >/dev/null 2>&1
```

EDIT - I hate to say it, but I won't be able to help any more this afternoon, I have an appointment I need to get to.

---

### Post by taehC on 2007-08-10
nope :(
is there much else to try?

---

