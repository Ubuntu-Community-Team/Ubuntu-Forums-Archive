---
title: "Pimping StarCraft on a Widescreen Display"
date: 2008-06-08
forum: Wine
---

### Post by calcfreak83 on 2008-06-08
if any of you have ever tried running StarCraft on a widescreen display, you'll know what I'm talking about. Either you can run Starcraft in windowed mode, and be forced to squint at the 640x480 display, or you can try and play in fullscreen mode, without the bottom third of your screen. 
Here I show the ordinary user how to play StarCraft the way it was meant to be played. 

The secret to having StarCraft play in fullscreen mode, is X. If you start StarCraft in a custom XServer with its own resolution, you can get it to display the full screen. 

Open /etc/X11/xorg.conf in your favorite editor, and add the follow lines:
```

Section "ServerLayout"
    Identifier     "SCLayout"
    Screen      0  "StarCraft Screen"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Screen"
	Identifier     "StarCraft Screen"
	Device         "Device0"
    Monitor        "StarCraft Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     640 480
        Depth       24
        Modes      "640x480@60" "1280x800@50"
    EndSubSection
EndSection

Section "Monitor"
    Identifier     "StarCraft Monitor"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525  -hsync -vsync
EndSection
```

KeyBoard0 is your keyboard, Device0 is your graphics card, and Mouse0 is your mouse. You should replace these values with the actual values from your xorg.conf

Next, we must change a line of /etc/X11/Xwrapper.config:
change the line
```
allowed_users=console
```
to:
```
allowed_users=anybody
```
this allows anybody to start a new Xserver, even from within an xserver. This shouldn't be a security flaw, unless your running a mainframe with thinside clients, but then you probably wouldn't be try to play StarCraft, would you? :)
Next, create a text file called scstart. Paste the following in:
```
#!/bin/sh
X :1 -layout SCLayout -ac &
XPID=$!
sleep 2
DISPLAY=:1 wine $HOME/.wine/drive_c/\
Program/Files/Starcraft/StarCraft.exe -- /usr/bin/X :1 -layout SCLayout 
sleep 1
kill $XPID
```
This is the basic launcher for StarCraft. Later on, I'll show you how to pimp it for extra features, but this is the basic launcher. 
If you want to switch back to your desktop in the midst of a zerg rush, you can press Ctrl + Alt + F7. To switch back, press Ctrl + Alt + F8.


This is a pretty basic launcher. You'll notice on glaring problem when using this, though. You can't change the volume. The program that handles you pushing the volume buttons is a part of Gnome, and we didn't launch that. Fortunately there is a way around the problem. 
install the xbindkeys package:
```
sudo apt-get install xbindkeys
```
xbindkeys is a nifty little program. It binds specific keys or key codes to commands. I'll show you how to set it up.
Start by creating a default config file.
```
xbindkeys --defaults > .scbind
```
We are going to tell xbindkeys to use a custom config file, so if you ever decide to use xbindkeys for some other purpose, you can keep your StarCraft commands separate. 
Now we have to determine what the key codes for the volume keys are. Gnome sometimes messes with the keycodes, especially for volume control, so to be extra safe, we are going to find our keycodes from a recovery console. Logout, change the session type to recovery console, and log back in. You will be presented with a console in the lower righthand corner. To type in it, your mouse must be over the terminal. Type in:
```
xbindkeys -f $HOME/.scbind -mk
```
Now press the key combos for volume up, volume down, and mute/unmute. xbindkeys should reply saying something like:
```
Press combination of keys or/and click under the window.
You can use one of the two lines after "NoCommand"
in $HOME/.xbindkeysrc to bind a key.

--- Press "q" to stop. ---
"(Scheme function)"
    m:0x0 + c:160
```
the last line is the important one. It is the keycode for whatever key you just pressed (In my case, mute/unmute). Open up .scbind, and add following lines:
```
"amixer set Master toggle"
(mute/unmute keycode)
"amixer set Master 6+"
(volume up keycode)
"amixer set Master 6-"
(volume down keycode)
```
where the stuff in the parentheses are the keycodes xbindkeys returned.
Now add the following line to scstart under "sleep 2":
```
xbindkeys --display :1 -f $HOME/.scbind
```

There you have it! Volume control for StarCraft. The xbindkeys program is extremely powerful. With a little extra effort, you could have media player controls in StarCraft, this is left as an excercise to the reader (Always wanted to say that! :)), while the idea of launching a program in a separate X Server could be applied to any troublesome game.


So long and thanks for all the fish!

---

### Post by phr0ze on 2008-06-13
Thanks for the post. This can be very useful for many other things as well.

How bad does this mess with Hardy's minimal xorg.conf files?

---

### Post by NelsAV on 2008-07-12
Hey Calfreak,

I like your writeup and I think i can do it, except for the fact that I can't find the first part.

Open /etc/X11/xorg.conf in your favorite editor, and add the follow lines

I am using a Toshiba Laptop, and it runs in that tiny window surrounded by black, and I can't get it to work either, can you explain it more in depth for us slowbies?

PM, or email is fine, [email]NelsAV@gmail.com[/email]

Thanks bud

---

### Post by Crinos512 on 2008-07-26
I know it's possible to force widescreen in Warcraft III by hacking the registry settings, maybe Starcraft has similar settings.

Here's a link:
[Linkity-Link]("http://warcraft.freakygaming.com/tutorials/running_warcraft_3_in_widescreen.html")

Best of luck! :D

---

### Post by pkl266 on 2008-07-28
Nope, unfortunately SC has no such registry hacks, 640x480 or nothing. Thank you very much for this write up though, you have made a SC fan very happy :)

---

### Post by Cyclothymia on 2008-12-19
I tried the solution and it worked, except for the fact that the top and bottom of the screen was still off by a total of a inch. The width is full screen; if I move my mouse near the top or bottom it scrolls, so the problem is getting the window to resize to 640x480.

I'm thinking that it may have to do with my Nvidia video driver having resolution auto-detect capabilities, and my T61 laptop monitor being a widescreen with a 1440x900  native resolution.

I'm pasting the terminal output XRandR errors I got when running the script below:
```
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux JM-laptop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Dec 18 21:22:14 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ramdac" already built-in
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
fixme:advapi:SetSecurityInfo stub
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32f410,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
```

---

### Post by havok1977 on 2009-02-20
Hello, your solution seems very interesting; I tried to implement it but ran into this problem:

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-xen i686 Ubuntu
Current Operating System: Linux raziel 2.6.28-8-generic #24-Ubuntu SMP Wed Feb 18 18:48:55 UTC 2009 i686                                                            
Build Date: 29 January 2009  07:43:28PM                                           
xorg-server 2:1.5.2-2ubuntu3.00~ppa1 (buildd@rothera.buildd)                      
        Before reporting problems, check http://wiki.x.org                        
        to make sure that you have the latest version.                            
Module Loader present                                                             
Markers: (--) probed, (**) from config file, (==) default setting,                
        (++) from command line, (!!) notice, (II) informational,                  
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.             
(==) Log file: "/var/log/Xorg.1.log", Time: Sat Feb 21 15:41:38 2009              
(==) Using config file: "/etc/X11/xorg.conf"                                      
  XRANDR name: VGA-0                                                              
  Connector: VGA                                                                  
  CRT1: INTERNAL_DAC1                                                             
  DDC reg: 0x60                                                                   
  XRANDR name: DVI-0                                                              
  Connector: DVI-D                                                                
  DFP1: INTERNAL_TMDS1                                                            
  DDC reg: 0x64                                                                   
  XRANDR name: LVDS                                                               
  Connector: LVDS                                                                 
  LCD1: INTERNAL_LVDS                                                             
  DDC reg: 0x0                                                                    
finished output detect: 0
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(EE) RADEON(0): Output LVDS enabled but has no modes
(EE) RADEON(0): No valid modes.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
system.reg is not a valid registry file
userdef.reg is not a valid registry file
user.reg is not a valid registry file
wine: could not load L"C:\\windows\\system32\\wine.exe": Module not found
kill: 9: No such process

```

Any ideas why?

---

### Post by Sugi on 2009-02-21
Awesome. I have to give this a tried.  Could you upload a screen shot or upload a video of it in action?  Thanks

Sugi

PS: I'll get back to you on the results of this HOWTO runing on my computer.

---

### Post by VeeDubb on 2009-03-06
This definitely does NOT work on 8.10

The principle is sound, but the in 8.10 the xorg.conf file is mostly empty because the latest version of the xorg server auto-detects almost everything on the fly.

When I try this in 8.10, the new x server launches just long enough for me to see the plain gray background and the x cursor in the center of the screen, then crashes out.

restarting x after attempting to apply the settings above, causes my regular desktop to load up at 640x480.  No good.

I 'think' that you would need to explicitly list all of the settings for your default x server AND the settings for your custom server, and then make sure that the right one is launched on boot-up.

Unfortunately, I have no idea how to do that.

Any suggestions?

My particular monitor is a 1440x900 50hz LCD.

---

### Post by gotsanity on 2009-04-22
This however DOES work on 9.04. I have the video working without an issue but im running into the issue of no sound. Im gonna try the sound keybinds mentioned and see if that helps the sound issue.

update: this doesnt seem to help the sound issue. Im betting it has something to do with pulseaudio... perhaps pulse isnt operating in the new environment?

---

### Post by gotsanity on 2009-04-23
> **gotsanity said:**
> This however DOES work on 9.04. I have the video working without an issue but im running into the issue of no sound. Im gonna try the sound keybinds mentioned and see if that helps the sound issue.

update: this doesnt seem to help the sound issue. Im betting it has something to do with pulseaudio... perhaps pulse isnt operating in the new environment?

Sound is fixed now. It had to do with my pulseaudio being broken by an update. I reverted back to the stock jaunty release and fixed it fully.

However, Another issue I have noted is that when swapping back to the desktop and then back the the game it runs as a blank screen. Any ideas?

---

### Post by R2-N on 2009-05-10
I have a question, the basic launcher has to be    scstart.txt? and where should I save it?

Thanks

---

### Post by stradric on 2009-05-15
> **R2-N said:**
> I have a question, the basic launcher has to be    scstart.txt? and where should I save it?

Thanks


Put it in your home folder.  It doesn't need the .txt extension.  Give it executable permissions (chmod +x scstart).  Run it like ./scstart

---

### Post by stradric on 2009-05-15
> **gotsanity said:**
> Sound is fixed now. It had to do with my pulseaudio being broken by an update. I reverted back to the stock jaunty release and fixed it fully.

However, Another issue I have noted is that when swapping back to the desktop and then back the the game it runs as a blank screen. Any ideas?


I am also having the audio issue.  But was your audio completely broken or was it just not working in starcraft?  Because my audio works otherwise.  Just not in starcraft.

---

### Post by Apv507 on 2009-05-17
"KeyBoard0 is your keyboard, Device0 is your graphics card, and Mouse0 is your mouse. You should replace these values with the actual values from your xorg.conf"

Where exactly do I find these values? 

Also, is the scstart thing a must, I'm not sure I understand the role it plays in all of this.

---

### Post by stradric on 2009-05-19
> **Apv507 said:**
> 
Where exactly do I find these values? 

Also, is the scstart thing a must, I'm not sure I understand the role it plays in all of this.

Those values are defined in xorg.conf above where you should insert the config code snippet.  Chances are that keyboard0, mouse0 and display0 will suffice if you haven't messed with your xorg.conf file at all.

scstart is a shell script to launch starcraft for you so that it launches within another x server.  Otherwise you'll have to type out the call to wine yourself every time you want to play.

You'll need to give scstart executable permissions (chmod +x scstart).  Then, you can run scstart by typing ./scstart from the directory where scstart is located.

---

### Post by maudin88 on 2009-07-08
:lolflag: [calcfreak83]("http://ubuntuforums.org/member.php?u=597556") you are the MAN!! THANK YOU !!!!!!  Here is his link  [http://ubuntuforums.org/showthread.php?p=5144003](http://ubuntuforums.org/showthread.php?p=5144003)

---

### Post by OdinHammer on 2009-07-09
[calcfreak83]("http://ubuntuforums.org/member.php?u=597556"), i cant wait to go home and try this out, i've been playing in windowed mode just to play.  :KS

---

### Post by kevmaster on 2009-08-11
Congratulations on a great idea, and a great tutorial altogether, calcfreak83!

For Running Starcraft on Ubunty Jaunty, 

I had to change your /etc/X11/xorg.conf modifications like so:

```
Section "ServerLayout"
	Identifier     "SCLayout"
	Screen      0  "StarCraft Screen" 0 0
# commented out by update-manager, HAL is now used
#	InputDevice    "Keyboard0" "CoreKeyboard"
# commented out by update-manager, HAL is now used
#	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Screen"
	Identifier     "StarCraft Screen"
	Device         "Device0"
    Monitor        "StarCraft Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     640 480
        Depth       24
        Modes      "640x480@60" "1280x800@50"
    EndSubSection
EndSection

Section "Monitor"
    Identifier     "StarCraft Monitor"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525  -hsync -vsync
EndSection

```
(cause things like keyboard are set up automatically and had to be commented out)

And change my ~/bin/scstart.sh to:
```

#!/bin/sh

# If found isn't working, try uncommenting these two lines
#sudo adduser $USER pulse-rt # logout after this
#sudo chmod 777 /dev/snd/seq

# Kill previous instances
ps auxf |grep SCLayout | grep -v grep | awk '{print "kill -9 "$2}' |bash

# Start new X
X :1 -layout SCLayout -ac &
XPID=$!
sleep 2

# Do Volume Key Control mapping if set up 
if [ -f $HOME/.scbind ]; then
    xbindkeys --display :1 -f $HOME/.scbind
fi

# Start Pulse Audio & Starcraft in new X
DISPLAY=:1 ck-launch-session wine $HOME/.wine/drive_c/Starcraft/StarCraft.exe -- /usr/bin/X :1 -layout SCLayout

# Cleanup
sleep 1
kill $XPID

```
(adds some checks but most importantly the ck-launch-session to enable sound)

And the hotkeys for switching to my Starcraft X session were: CTRL + ALT + F9

And I was golden. This is a great setup and like you said: Could be used for every troublesome game.
The fact that you can switch easily to your normal X config is really nice.

Thanks. :)

---

### Post by foogs on 2009-08-11
Thank you kevmaster. I had to edit the path in scstart.sh to $HOME/.wine/drive_c/Program\ \Files/Starcraft/StarCraft.exe because mine was installed to Program Files and not just Starcraft.

Alt tabbing works now for me, but there is a big black X cursor in the middle of my starcraft screen that just stays there which i believe is the default cursor for a normal X session. This only happens after alt tabbing (ctrl+alt+f9) back into starcraft. How did you get rid of that?

Edit: I got rid of the X cursor by installing a package named unclutter. Then I opened starcraft, alt tabbed back to gnome and ran this from the terminal: unclutter -display :1 -root. I have no idea how to add it to the script so I dont have to open up the terminal and manually type that though. I'll post back here if I figure it out.

Figured it out. Here's what I added to my scstart.sh:
```
#!/bin/sh

# If found isn't working, try uncommenting these two lines
#sudo adduser $USER pulse-rt # logout after this
#sudo chmod 777 /dev/snd/seq

# Kill previous instances
ps auxf |grep SCLayout | grep -v grep | awk '{print "kill -9 "$2}' |bash

# Start new X
X :1 -layout SCLayout -ac &
XPID=$!
sleep 2

#start unclutter to hide the X cursor when alt tabbing
unclutter -root &
UNCLUTPID=$!
sleep 2

# Start Pulse Audio & Starcraft in new X
DISPLAY=:1 ck-launch-session wine $HOME/.wine/drive_c/Program\ \Files/ICCup/Launcher/Launcher.exe -- /usr/bin/X :1 -layout SCLayout -display :1

# Cleanup
sleep 1
kill $XPID
kill $UNCLUTPID
```Thanks calcfreak83 and kevmaster. I can now play starcraft on Linux the way it was meant to be played and then some! I can now turn on my music or go back to pidgin and chat. This was the only thing holding me back from using Ubuntu (I kept going back to Windows just because it made playing my favorite game easier) and I've been trying to get all this to work off and on for a couple of years now.

I found one more problem that I'm trying to fix now. In my normal setup (without using scstart.sh to start starcraft) I have my mouse acceleration turned off, but when I use scstart.sh to start starcraft the mouse acceleration comes back. I've looked everywhere and I'm unable to find an answer for that. My question to help me answer would be: how do I take my main mouse settings (the mouse settings im using in gnome) and transfer them over to a new X session?

Fixed the mouse acceleration / sensitivity problem. Thread here: [http://ubuntuforums.org/showthread.php?t=1237755](http://ubuntuforums.org/showthread.php?t=1237755).

Now Starcraft works, doesn't have an X cursor when alt tabbing back in (this is a good thing), and the mouse sensitivity stays the same when its started in a new X window. ICCUP even works for me with the latest wine version. This is golden!

---

### Post by melkor2.0 on 2009-08-30
Gratz for the tuturial, For me I just had to change the path in the scstart script, so now it looks like 

env WINEPREFIX="/home/*USERNAME*/.wine" wine "C:\Program Files\StarCraft\Starcraft.exe" 

however I have also the sound problem, and I don't know how to solve it, I have last version of pulseaudio, do I have to search for an old one? 

Anybody did fix this?

Thanks a lot!

---

### Post by RizzLinux1388 on 2009-10-12
WOW Thank you so much this worked!

---

### Post by Adict on 2009-10-19
Unfortunatelly this doesnt work for me.
I have 9.04 and really dont know where is the problem. 
I have added the lines to the xorg.conf
Then I created the launcher. Hopefully succesful.
But pictures are more then words.

[IMG]http://img237.imageshack.us/img237/64/launchery.png[/IMG]

and

[IMG]http://img193.imageshack.us/img193/8415/directory.png[/IMG]

When trying to open the launcher through console, the screen gets black for about 2seconds and then this is what I get:

```
gitas@gitas:~$ '/home/gitas/Pracovná plocha/scstart.sh' 
bash: /home/gitas/Pracovná plocha/scstart.sh: /bin/sh^M: chybný interpreter: No such file or directory
gitas@gitas:~$
```

So..what am I doing wrong? :confused:

---

### Post by RizzLinux1388 on 2009-10-19
I've got it to work thanks to all of you but the sound cuts out after awhile, what do you guys think is the reasoning for that? 

Adict, this is how I have my scstart.sh file setup under Ubuntu 9.04, make sure you have the ck-launch-session wine in that line. Good luck.
```
#!/bin/sh
X :1 -layout SCLayout -ac &
XPID=$!
sleep 2

# Do volume key control mapping if set up
if [ -f $HOME/.scbind ]; then
    xbindkeys --display :1 -f $HOME/.scbind
fi
DISPLAY=:1 wine $HOME/.wine/drive_c/Program\ Files/Starcraft/StarCraft.exe  -- /usr/bin/X :1 -layout SCLayout
# Start Pulse Audio & Starcraft in new X
DISPLAY=:1 ck-launch-session wine $HOME/.wine/drive_c/Program\ Files/Starcraft/StarCraft.exe  -- /usr/bin/X :1 -layout SCLayout -display :1
sleep 1
kill $XPID

#!/bin/sh

```

---

### Post by munchi3s on 2009-11-25
It works for me sorta. I have a Dell XPS M1210 laptop. It starts up and everything works for about 5 minutes and then it crashes. I don't know what is wrong. I created everything from the first post and the long post on page two, but StarCraft will not stay up for more then 5 minutes. Anyone have a solution to this problem? So I fixed the first problem. 

>>I really don't know how. I just think it needed a restart. 
But not I have a new problem. I need to restart again to make sure but I had a problem with loading into ubuntu and having a 640x480 resolution that I could not change, so I just reloaded my xorg.conf file using #sudo nvidia-xconfig and that rewrote my config file and I added the starcraft screen back on and it works fine for right now. I need to restart again to see if it will still give me a 640x480 screen. I sure hope not. Will update soon.

>>>Well everything works fine now. Game stays up and my regular X server doesn't take the starcraft screen resolution. Thanks for the great tutorial.

---

### Post by vjcamarena on 2009-12-21
Wow, nice!
I'm a huge newb, and I'm so grateful someone took the time to do this!
It was kevmaster's version which did the trick for me (Ubuntu 9,10). Thanks, all!

---

### Post by nominal on 2009-12-22
Wow. thanks OP.

i'll have to check this out, i recently got starcraft to work properly when you get to the bnet screen...in case anyone was wondering:

configure wine to run starcraft.exe as **windows nt 4.0**

the guide for dvdecrypter suggested that fix, so i applied it to SC and bam! it worked. now i can show up my windows friends on [COLOR="Red"]**TWO**[/COLOR] operating systems windows and ubuntu!!.

**[COLOR="Red"][SIZE="5"]Actually, I MEAN 3!!! STARCRAFT 64!!!!!!!!!![/SIZE][/COLOR]**

---

### Post by ajayrockrock on 2010-01-04
The sound issue has been mentioned a few times in this thread.  The one where sound would come in for the first few minutes and then cut out.  Has anyone figured out why this happens or any resolution?

---

### Post by ghostpaladin on 2010-01-06
> **Apv507 said:**
> "KeyBoard0 is your keyboard, Device0 is your graphics card, and Mouse0 is your mouse. You should replace these values with the actual values from your xorg.conf"


I use ubuntu 9.10 and when I open the file /etc/X11/xorg.conf the only information inside is:

```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```

Can anybody tell me which one belongs to device0, keyboard0 and mouse0?

---

### Post by Soulcage on 2010-01-06
Ghost you may want to run sudo nvidia-settings in a terminal. Then click: X server display configuration then click save to x configuration file then unclick the checkbox and click save.
If that gives you an error you can type sudo rm /etc/X11/xorg.conf then try it again. I had to on my comp.
Doing this will add alot more settings to change around.

---

### Post by ghostpaladin on 2010-01-06
> **Soulcage said:**
> Ghost you may want to run sudo nvidia-settings in a terminal. Then click: X server display configuration then click save to x configuration file then unclick the checkbox and click save.
If that gives you an error you can type sudo rm /etc/X11/xorg.conf then try it again. I had to on my comp.
Doing this will add alot more settings to change around.

Thank for the tip, actually it did work fine :). This is my new xorg.conf:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    Option         "NoLogo"    "True"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6150"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "SCLayout"
    Screen      0  "StarCraft Screen"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Screen"
    Identifier     "StarCraft Screen"
    Device         "Device0"
    Monitor        "StarCraft Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     640 480
        Depth       24
        Modes      "640x480@60" "1280x800@50"
    EndSubSection
EndSection

Section "Monitor"
    Identifier     "StarCraft Monitor"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525  -hsync -vsync
EndSection

```but when I try to run the scstart script the console returns me this:

```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux GHOST-PC 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=3e663406-e6b4-44f0-a0c6-3d0bfe89482c ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Wed Jan  6 19:29:18 2010
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) Failed to load module "freetype" (module does not exist, 0)
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't register object path
ghostpaladin@GHOST-PC:~/Downloads$ fixme:advapi:SetSecurityInfo stub
 ddxSigGiveUp: Closing log
XIO:  fatal IO error 25 (Inappropriate ioctl for device) on X server ":1.0"
      after 431 requests (383 known processed) with 0 events remaining.
ddxSigGiveUp: Closing log

```did I do something wrong?

---

### Post by biodiesel-bri on 2010-01-08
I solved the sound cutting out issue by running
```
winecfg
``` from terminal in the Audio tab unchecking "ALSA" and checking "OSS Driver"

---

### Post by ajayrockrock on 2010-01-11
> **biodiesel-bri said:**
> I solved the sound cutting out issue by running
```
winecfg
``` from terminal in the Audio tab unchecking "ALSA" and checking "OSS Driver"

Excellent.  Thanks for the tip, I now have a perfect running starcraft!

---

### Post by Mike404 on 2010-01-17
Hi,  I've successfully have starcraft working under Ubuntu 9.10 following the directions here however I'd rather have a fixed aspect ratio on my wide screen (ie black bars on the right and left) instead of stretching it.  Can this be done?  Thanks,  Mike

---

### Post by sungohan on 2010-01-21
The file xorg.conf does not exist in my folder /etc/X11/
I'm using kubuntu 9.10
How can I check mouse keyboard values?

What should I do?

---

### Post by StonedOne on 2010-01-22
@sungohan
Look at the post of "Soulcage" that is the solution for nvidia cards and use ati-control-center for ati cards.

@Mike404
Did you find a solution for the problem? I also have a 4:3 screen image, stretching would be nice ;)

I want to give my regards to the thread creator. My starcraft installation works very well, i even created a ".deb"-package for automated installation of starcraft with the extra screen.

Too bad it is still under license so i cant publish it :(

---

### Post by sungohan on 2010-01-23
> **StonedOne said:**
> @sungohan
Look at the post of "Soulcage" that is the solution for nvidia cards and use ati-control-center for ati cards.

@Mike404
Did you find a solution for the problem? I also have a 4:3 screen image, stretching would be nice ;)

I want to give my regards to the thread creator. My starcraft installation works very well, i even created a ".deb"-package for automated installation of starcraft with the extra screen.

Too bad it is still under license so i cant publish it :(


Thanks, 
but what if mine is just Intel Graphics Media Accelerator 4500MHD.

---

### Post by Evan_G on 2010-02-15
I did everything in the original post, and got StarCraft running properly at fullscreen.  However, now I don't have any sound, and in fact the sound options themselves in the ingame options menu are greyed out.  Sound works fine if I run Starcraft normally without the script.  Here is the output when I run the script (editing out tons of blank lines):

```
snes64@victory64-laptop:~/Starcraft$ sh scstart

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux victory64-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=52a27a84-3cea-4315-baea-6a086c6261c6 ro quiet splash
Build Date: 14 November 2009  05:48:57PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Mon Feb 15 00:04:18 2010
(==) Using config file: "/etc/X11/xorg.conf"

(EE) Failed to load module "type1" (module does not exist, 0)
(EE) Failed to load module "freetype" (module does not exist, 0)

fixme:advapi:SetSecurityInfo stub

fixme:win:EnumDisplayDevicesW ((null),0,0x32f3f4,0x00000000), stub!

fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8


XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1.0"
      after 21 requests (13 known processed) with 0 events remaining.

snes64@victory64-laptop:~/Starcraft$  ddxSigGiveUp: Closing log
^C
```

Also note that the script hangs when the program is closed (resulting in me having to press ctrl-C).

Here is the contents of my xorg.org file:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CMO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7150M / nForce 630M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by bassliu on 2010-02-15
very cool!

---

### Post by Nate53085 on 2010-02-23
After changing the Xwrapper I still have 

X: user not authorized to run the X server, aborting.

Any ideas?

--EDIT--

Nevermind, I was just being dumb

---

### Post by morgue on 2010-03-05
> ext, create a text file called scstart. Paste the following in:

```

#!/bin/sh
X :1 -layout SCLayout -ac &
XPID=$!
sleep 2
DISPLAY=:1 wine $HOME/.wine/drive_c/\
Program/Files/Starcraft/StarCraft.exe -- /usr/bin/X :1 -layout SCLayout 
sleep 1
kill $XPID

```


How exactly do I perform this step? What type of file? How do I create it? How do I execute it?

---

### Post by morgue on 2010-03-05
Ok here are the [steps]("http://www.go2linux.org/starting-with-shell-script"), I got this message though...

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux david-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=3baa2436-d2e4-42ca-a66c-f591552ed5c7 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Fri Mar  5 21:06:03 2010
(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
	Undefined InputDevice "Keyboard0" referenced by ServerLayout "SCLayout".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
kill: 7: No such process

```

---

### Post by morgue on 2010-03-05
OK it worked, I first just commented (#) the keyboard and mouse lines... I polished it using Nvidia X Server Settings and clicked 'Saved to X Configuration File' to create this xorg.conf + the details on this guide

My xorg.conf file now looks like this

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LPL"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7400"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x800 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection










Section "ServerLayout"
    Identifier     "SCLayout"
    Screen      0  "StarCraft Screen"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Screen"
	Identifier     "StarCraft Screen"
	Device         "Device0"
    Monitor        "StarCraft Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     640 480
        Depth       24
        Modes      "640x480@60" "1280x800@50"
    EndSubSection
EndSection

Section "Monitor"
    Identifier     "StarCraft Monitor"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525  -hsync -vsync
EndSection
```

It runs but I get no sound on the game whatsoever when running the launcher... Any suggestions?

---

### Post by zyx1141 on 2010-05-20
Hello,

I've tried to run Starcraft in full screen with the indication on first page but with no luck.
Read entire topic but no solution for my problem.

Here is the error i receive after trying to run scstart.sh

> 
./scstart.sh 

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux  2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686
Kernel command line: root=UUID=5ac98afc-04fb-4fe0-9219-0ca211e5e6e2 ro quiet splash 
Build Date: 04 March 2010  09:56:47AM
xorg-server 2:1.6.4-2ubuntu4.2 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu May 20 20:13:29 2010
(==) Using config file: "/etc/X11/xorg.conf"
:~/FUN/Brood$  ddxSigGiveUp: Closing log
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

Running on Dell E6400 with Nvidia Quadro M160 if helps, Ubuntu 9.10.
Any ideas are welcome, thanks.


LE:

The problem was that on firs display  resolution 640x480 wasn't mentioned, after that works fine, even without the scipt from here.

Cheers!

---

### Post by OlympicSoftworks on 2011-08-02
WOW!  Calcfreak83, that was a fantastic idea!  I got a wild hair to play SC a week ago and found my disks were damaged.  I had logged my code with Battle.net though so I was able to download the client again.  But their client does not pay attention to WINE trying to handle screen sizing.  So no joy.

This is not only superior to a 640x480 window on a 1920x1024 monitor, but it works with the new downloaded client!  Dude, my gratitude to you big time.

You have a typo though in the script you use to execute Starcraft...a backslash out of place.

Replace the line beginning with DISPLAY to this:

DISPLAY=:1 wine $HOME/.wine/drive_c/Program\ Files/Starcraft/StarCraft.exe -- /usr/bin/X :1 -layout SCLayout 

What an excellent way to play SC!

I am going to write this up and put it on my GNU/Linux advocacy website with full credit to you bro.  Very well done.=D>

---

### Post by kaustikos on 2011-12-27
Hello! I used the proposed method, but the result was slightly different of what I expected. The game indeed runs fullscreen, but it fits the screen WIDTH keeping aspect ratio of 4:3. Hence the bottom part of the Starcraft menues is invisible in this mode. I mean it does not stretches in width, It just extands the width keeping aspect ratio and crops the bottom part of screen off. I woul be ok since its possible to use hotkeys and menues are not necessary. But it also prevents in-game scrolling downwards! I believe that the solution for me can still be found usind virtual desktop, but I don't understand it enough. Have anyone dealt with such problem? Please, help me! 

I run SC in wine 1.2.2, Ubuntu 10.04, Lenovo SL500 laptop (integrated intel video)

---

### Post by rafaelhsn on 2013-01-29
Hi,

Very old topic but I'm a fan of startcraft hahah

I followed all steps but I cannot open the game.

It try to open it but give me this error: [http://pastebin.com/GqU8EkCG](http://pastebin.com/GqU8EkCG)

Anyone can help me please? =)

Thanks

---

### Post by howefield on 2013-01-29
Old thread closed.

---

