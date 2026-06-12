---
title: "G3 iMac DV blank screen with live-CD"
date: 2005-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by twongkee on 2005-10-13
initially X does not start....
:???: 

Got it working with a quick text edit:

drop to console (ctrl - option  F1)

and edit the X config file as follows:

[FONT="Fixedsys"]sudo pico /etc/X11/xorg.conf[/FONT]
or if you prefer:
[FONT="Fixedsys"]sudo vi /etc/X11/xorg.conf[/FONT]
(or your favorite editor)

change the frequencies in monitor section as follows:

[FONT="Fixedsys"]Section "Monitor"
[INDENT]        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       60-60
        VertRefresh     43-117
[/INDENT]EndSection[/FONT]

restart X

---

### Post by stepore on 2005-10-14
[QUOTE=twongkee]
[FONT="Fixedsys"]Section "Monitor"
[INDENT]        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       60-60
        VertRefresh     43-117
[/INDENT]EndSection[/FONT]

restart X[/QUOTE]

Firstly -- cheers! Thanks so much for this, i thought Breezy went a step backwards when i booted the live PPC cd and got no display. My little iMac display worked fine with Hoary. Didn't need to modify xorg.conf at all. What changed in Breezy?

Secondly, how did you know what to put in the Hor. and Vert. refresh rates? Truth be told, i've never known where to get this information. Even for a PC monitor.

cheers,
jb

---

### Post by neatokino on 2005-10-19
Hi--

I'm very much a newbie to Linux, and I'm having the same problem trying to run Breezy 5.10 live CD on a G3 iMac DV (I get that black screen).    I want to try running  with the live CD before attempting to do a complete install on the iMac.

I don't understand exactly how to edit the X config file or to restart X while booting with the live CD.  Can anyone give me exact, idiot-proof step-by-step instructions?

TIA
Michael

---

### Post by stepore on 2005-10-20
[QUOTE=neatokino]
I don't understand exactly how to edit the X config file or to restart X while booting with the live CD.  Can anyone give me exact, idiot-proof step-by-step instructions?[/QUOTE]

didn't you read the Original Poster's message. he told you how to do it. we'll try it again, with a bit more added.

[QUOTE=twongkee]
drop to console (ctrl - option F1)
** this means once you boot up to a blank screen hit the 'ctrl' key, the 'option' key and the F1 key all at the same time. you'll be in a terminal window. **

** if you need to log in use the name ubuntu to log in. **

and edit the X config file as follows:

** type this in exactly as you see it (vi is a terminal editor)**
sudo vi /etc/X11/xorg.conf

change the frequencies in monitor section as follows:
** find this part in the file you are now in (xorg.conf) and make these changes **

Section "Monitor"
    Identifier "Generic Monitor"
    Option "DPMS"
    HorizSync 60-60
    VertRefresh 43-117
EndSection

** after the changes then hit the 'esc' or 'escape' key, then type ':wq'
** no 'quotes' -- but yes the ':' is part of the command
** that will write the changes to the file and quit from vi **

** restart X by typing: sudo /etc/init.d/gdm restart 
** or maybe just hit 'ctrl' 'alt' 'delete'
that should be it. now ubuntu should start right up.
[/QUOTE]

---

### Post by neatokino on 2005-10-20
Thank you thank you thank you!  I had read the first post but really did need all your very specific instructions.  It's all set up and working now.  Your help is much appreciated.

---

### Post by stepore on 2005-10-20
[QUOTE=neatokino]Your help is much appreciated.[/QUOTE]
glad to have helped.

---

### Post by Avicus on 2005-10-21
Are you guys running the color mode at 15 bit? I can't get 24 bit to work properly... and 15 bit is the only mode that gives me decent performance....

Yet 24 bit worked fine in Hoary....

---

### Post by RHTopics on 2005-12-06
To save keystrokes and eliminate typing errors, I created a script to copy a xorg.conf file from a Hoary installation to the Live CD's /etc/X11/xorg.conf.  The script also executes the command "/etc/init.d/gdg restart" to restart X.

The script file and the xorg.conf file are stored on a USB pen drive.  The steps for initiating the script are:

[LIST=1]
[*]After coming to the point where the screen is blank, insert the the USB pen drive containing the script file and xorg.conf file into an available USB port.
[*]Press the 'control' key, the 'alt/option' key and the F1 key all at the same time to go to a terminal window.
[*]My USB pen drive is a Lexar Jump Drive which causes Ubuntu to create the mount point /media/LEXAR.  The name of my script file is fix_xorg.sh, so I enter "cp media/LEXAR/fix_xorg.sh ." to copy the script to the home directory for ubuntu.
[*]enter "./fix_xorg.sh" to execute the script
[/LIST]

Below are the file listings for the fix_xorg.sh script file and the xorg.conf file.  I hope this is helpful to someone.


[B]Listing of the fix_xorg.sh script file:
[/B]
#!/bin/bash
# Name: fix_xorg.sh
# 
# Copy this script from a portable storage device (ie USB pen drive) connected
# to an iMac running Live CD version Ubuntu Breezy Badger (aka version 5.10) to
# the home directory of the default user, ubuntu.  Then execute script by entering
# ./fix_xorg.sh 

# This script replaces the disfunctional xorg.conf created by the Live CD
# boot process with a functional one located on the portable storage device.
# The X server is then restarted inorder to use the new xorg.conf file.
# note: the subdirectory under media will need to be changed to match the name
#       of the device you are using

sudo cp /media/LEXAR/xorg.conf /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart

exit 0

**The following xorg.conf file listing works for a slot loading G3 iMac 350 mhz.  It puts the the X display in 24 bit mode.**

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 (RL/VR AGP)"
	Driver		"ati"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"iMac"
	Option		"DPMS"
	HorizSync	58-62
	VertRefresh	75-117
        ModeLine        "1024x768" 78.5 1024 1045 1141 1312 768 769 772 796 +hsync +vsync
        ModeLine        "800x600" 62.4 800 813 893 1040 600 601 604 632 +hsync +vsync
        ModeLine        "640x480" 49.9 640 653 717 832 480 481 484 514 +hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 (RL/VR AGP)"
	Monitor		"iMac"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by JonGrubbs on 2005-12-07
I am also having problems with booting the Live CD on my iMac G3 400; am also a Linux newbie.  It boots until I hear the Ubuntu logon chimes sound effect, but screen is blank.  I've CTRL-OPT-f1 'ed into the terminal and typed the edit xorg.conf command as twongkee suggested, but after entering pico or vi the editor is devoid of any text or editable content that is supposed to pop up.  Any suggestions?  I can exit the editor, etc., but there's no options to change like you guys have been talking about.  Confused, but want to enter the Linux universe....   :confused:

---

### Post by RHTopics on 2005-12-07
JonGrubbs

It may be that you are not entering the exact path to the xorg.conf file.

** type this in exactly as you see it **

sudo vi /etc/X11/xorg.conf

If you entered just "sudo vi xorg.conf", it would come back with a blank "xorg.conf" file that if saved would be stored in the home directory of user ubuntu.

Another way to make sure you are editing the correct file is to do the following:

```
Command:              Comments do not enter:

cd /etc/X11/          # change to the directory that contains xorg.conf
ls xorg.conf          # list command to ensure the file is there
sudo vi xorg.conf     # load the xorg.conf into vi for editing
```

---

### Post by linear on 2005-12-07
It's worth mentioning, in case you missed it, that for some iMac models you'll need to comment out or delete the  **Load "dri"** line in xorg.conf.

---

### Post by ULffuntu on 2005-12-14
Hi All,

Hope everyone is doing well. So how do you fix the Breezy LiveCD iso and then reburn it correctly for Imac?... would you need a new isolinux script or something? I think that's what we're all after, a fixed Breezy Imac cd.

thx in advance

---

### Post by linear on 2005-12-14
I think there are instructions in the Ubuntu Wiki, but it sounded like a major effort. Also I assume that xorg.conf is getting built at boot, so it's not as simple as popping in the xorg.conf you want.

---

### Post by npeev on 2005-12-16
Hello
I had the same problem with G3 iMac DV, but the reason was different.
iMac DV works with 1280-1024 resolution/60Hz.
Try it this options. During the live setup you have to choose different resolutions. Enable this resolution and will be OK.
In my case ubintu 5.1, kubuntu 5.1 and debian 3.1 works perfect as a live and normal distribution.
Good luck

---

### Post by RHTopics on 2005-12-17
Live CD also worked when selecting 1280 x 1024 from the list of resolutions when booting up a slot loading iMac G3, 350mhz.  Yet, the screen geometry was squeezed.

Looking through my old documentation on the specifications of this computer, the highest stated resolution is 1024 x 768.  Using this higher resolution of 1280 x 1024 could damage or shorten the life of the monitor.

---

### Post by Skitzer on 2005-12-27
[QUOTE=JonGrubbs]I am also having problems with booting the Live CD on my iMac G3 400; am also a Linux newbie.  It boots until I hear the Ubuntu logon chimes sound effect, but screen is blank.  I've CTRL-OPT-f1 'ed into the terminal and typed the edit xorg.conf command as twongkee suggested, but after entering pico or vi the editor is devoid of any text or editable content that is supposed to pop up.  Any suggestions?  I can exit the editor, etc., but there's no options to change like you guys have been talking about.  Confused, but want to enter the Linux universe....   :confused:[/QUOTE]

I'm in the same boat as you, kind of. I am dual booting OS X Panther and Ubuntu. Everything went perfect and the boot loader works great. I can get into OS X no problem but when I try to get into Ubuntu it goes into Black screen mode just after the splash screen. I can get into the terminal with the above commands but once there I can see nothing to edit. I wonder if there is an alternate method to edit the xorg.conf.
Anyone have any suggestions? 
Oh, I'm using an imac g3 graphite slot loader, 600 Mhz with 780MB ram and 10 GB partition for Ubuntu.
Thanks in advance.****

---

### Post by linear on 2005-12-27
[QUOTE=Skitzer]but when I try to get into Ubuntu it goes into Black screen mode just after the splash screen. I can get into the terminal with the above commands but once there I can see nothing to edit.[/QUOTE]
When you say "see nothing to edit", what do you mean? If you type "sudo nano /etc/X11/xorg.conf" and a new blank file opens, check spelling of the file path and name. (Remember that case matters in Linux.)

(BTW, I put "nano" in the command instead of "vi" on purpose. Nano is a bit more friendly.)

---

### Post by ctt1wbw on 2005-12-28
I'm trying to get the live cd to work on a G5 iMac, to no avail.  I get the brown screen, the cursor, and that's it.  I can't do any keystroke combo at all on this one.

Any suggestions would be greatly helpful.  I've read the other threads here about getting a G5 iMac to work, and that's not really helpful at all either, since I can not get to a termianl window yet.

---

### Post by ctt1wbw on 2005-12-28
BTW, I have tried to boot using live, live-powerpc and live powerpc64 and none work...

---

### Post by Skitzer on 2005-12-29
[QUOTE=linear]When you say "see nothing to edit", what do you mean? If you type "sudo nano /etc/X11/xorg.conf" and a new blank file opens, check spelling of the file path and name. (Remember that case matters in Linux.)

(BTW, I put "nano" in the command instead of "vi" on purpose. Nano is a bit more friendly.)[/QUOTE]

Well, I finally got the terminal to display thanks to you.
I was using a lower case x when typing X11.
I still can't get the video to come up even after editing the xorg.conf file though. I tried Yellowdog 4.01 also and it installed about halfway through the first disc and then stopped with a fatal error. The error was "Fatal IO error: 104, which is another,(maybe same?), video problem from what I have read. So I give up!
I've decided I've had enough after 3 days of messing with it so I'm going to wipe the drive again and do a fresh install of Panther.
Thanks to all for your help.

---

### Post by Sav on 2006-06-03
[QUOTE=twongkee]initially X does not start....
:???: 

Got it working with a quick text edit:

drop to console (ctrl - option  F1)

and edit the X config file as follows:

[FONT="Fixedsys"]sudo pico /etc/X11/xorg.conf[/FONT]
or if you prefer:
[FONT="Fixedsys"]sudo vi /etc/X11/xorg.conf[/FONT]
(or your favorite editor)

change the frequencies in monitor section as follows:

[FONT="Fixedsys"]Section "Monitor"
[INDENT]        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       60-60
        VertRefresh     43-117
[/INDENT]EndSection[/FONT]

restart X[/QUOTE]

Thanks, you saved my day.
I was wondering how to install the brand new xubuntu dapper on my old iMag g3 dv 500, and after hours I found this post.

---

### Post by Phsyco_kid on 2006-06-04
I changed the xorg.config file, but I can't seem to reboot properly. I typed in "sudo /etc/init.d/gdm restart, and it said
"* Stopping GNOME Display Monitor                              [ ok ]
* Starting GNOME Display Monitor                                [ fail ]"

I tried doing the "control alt delete" combination, and it rebooted the whole system, ejected the disk, and I had to change the file all over again.

Where did I go wrong?

---

### Post by linear on 2006-06-04
You probably didn't do anything wrong.

I've been trying to boot the Ubuntu Dapper Live CD on an iMac G3 with similar results (the previous poster was using Xubuntu, not Ubuntu).

Try this: even if you don't edit xorg.conf - don't change a thing, Gnome fails to start.

Still trying to figure it out...

---

### Post by Phsyco_kid on 2006-06-05
Then how do I install Ubuntu onto my mac? How did everyone else do it?

---

### Post by linear on 2006-06-05
OK, I think I have a solution now - the reason we couldn't restart Gnome is that it never actually stopped. The "* Stopping GNOME Display Monitor                              [ ok ]" message is false, as the gdm process is still running afterwards.

So instead, try this:

To stop the process, use:

**sudo killall gdm**

Then make your edits to xorg.conf. Now start gdm:

**sudo /etc/init.d/gdm start**

It should work. Good luck!

---

### Post by ebeyer on 2006-06-06
[QUOTE=twongkee]initially X does not start....
:???: 

Got it working with a quick text edit:

drop to console (ctrl - option  F1)

and edit the X config file as follows:

[FONT="Fixedsys"]sudo pico /etc/X11/xorg.conf[/FONT]
or if you prefer:
[FONT="Fixedsys"]sudo vi /etc/X11/xorg.conf[/FONT]
(or your favorite editor)

change the frequencies in monitor section as follows:

[FONT="Fixedsys"]Section "Monitor"
[INDENT]        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       60-60
        VertRefresh     43-117
[/INDENT]EndSection[/FONT]

restart X[/QUOTE]

This is my first experience with linux on an iMac, so forgive me for sounding dense.

When the screen goes black I drop to console as you say - CTRL-OPT-F1 and a text prompt will come up?

Thanks.

---

### Post by Phsyco_kid on 2006-06-06
Yup, it worked. Thanks for all the help.

---

### Post by linear on 2006-06-06
[quote=ebeyer]This is my first experience with linux on an iMac, so forgive me for sounding dense.

When the screen goes black I drop to console as you say - CTRL-OPT-F1 and a text prompt will come up?

Thanks.[/quote] Exactly. Sometimes it takes a couple of tries.

---

### Post by everettattebury on 2006-06-16
[QUOTE=Phsyco_kid]Then how do I install Ubuntu onto my mac? How did everyone else do it?[/QUOTE]
I used the alternate install cd, used "expert vga=771" at the boot prompt, then had to edit xorg.conf and comment out the line that says "load DRI" to get it to work.

Kind of a pain to figure it all out, but it finally worked.

---

### Post by zubun on 2006-09-28
hi all, hi linear I tried your method with the dapper live CD (DV400 512MB) but the first time I start gdm I'm taken back to the command line, and the second time I start it everything hangs and I have to power off.

I think I've tried all the edits to xorg.conf that are posted here and elsewhere, including changing to 16bit. Am I missing something? 

There are some OS8.6 disks around, but I don't really want to go down that road!

---

### Post by linear on 2006-09-28
Too many edits, perhaps? It's possible that there's a typo in your xorg.conf.

Make sure you are changing HorizSync and VertRefresh only, and disabling DRI.

---

### Post by zubun on 2006-09-28
Maybe I'm making a mistake in the disabling DRI part, all I do is delete that section - should I be doing something more constructive?

---

### Post by everettattebury on 2006-09-28
> **zubun said:**
> Maybe I'm making a mistake in the disabling DRI part, all I do is delete that section - should I be doing something more constructive?


When you boot the live CD, add vga=771 to the boot options.  After you get a terminal, edit xorg.conf and just put a # in front of the line in the modules section that says "load DRI" and then startx and see what happens.

---

### Post by linear on 2006-09-28
> **zubun said:**
> Maybe I'm making a mistake in the disabling DRI part, all I do is delete that section

Hard to say what else you're deleting when you "delete that section". As everettattebury said, just comment out the line "load dri".

---

### Post by zubun on 2006-09-29
Thanks everyone! It's working, and here's what I did:

>restart holding down **c**, hit **enter** to boot from CD<

**ctrl-option-f1**

**sudo killall gdm**

**sudo pico /etc/X11/xorg.conf**

>made the changes already mentioned here to the sync and refresh, then scrolled down to the end and deleted the whole section relating to DRI including the numbers (**mXXXX**, I can't remember, **0666** maybe?) - this means all the stuff about the monitor resolution is now the last section of the file< 

**ctrl-o**
[B]enter
ctrl-x[/B]

**sudo /etc/init-d/ gdm start**



I didn't see a **load DRI **anywhere to put a **# **in front of, and I'm not sure how to add anything to the boot - the last time I did anything remotely code-like was when I thought 'format' meant 'clean up' and I had to write autoexec and config files for a 4mHz PC that ran WordStar in yellow - but the steps I mentioned here worked for me, hopefully they'll work for someone else too - thanks linear I must've made a typo the first time I tried, and I think the **killall gdm **was the key

---

### Post by Mushed Mango on 2006-10-24
> **zubun said:**
> Thanks everyone! It's working, and here's what I did:

>restart holding down **c**, hit **enter** to boot from CD<

**ctrl-option-f1**

**sudo killall gdm**

**sudo pico /etc/X11/xorg.conf**

>made the changes already mentioned here to the sync and refresh, then scrolled down to the end and deleted the whole section relating to DRI including the numbers (**mXXXX**, I can't remember, **0666** maybe?) - this means all the stuff about the monitor resolution is now the last section of the file< 

**ctrl-o**
[B]enter
ctrl-x[/B]

**sudo /etc/init-d/ gdm start**



I didn't see a **load DRI **anywhere to put a **# **in front of, and I'm not sure how to add anything to the boot - the last time I did anything remotely code-like was when I thought 'format' meant 'clean up' and I had to write autoexec and config files for a 4mHz PC that ran WordStar in yellow - but the steps I mentioned here worked for me, hopefully they'll work for someone else too - thanks linear I must've made a typo the first time I tried, and I think the **killall gdm **was the key

I did this, but I used:

**sudo /etc/init.d/gdm start**

instead of the above:

**sudo /etc/init-d/ gdm start**

It only works like this for me. I got it from one of the other posts. If the above doesn't work, try my suggestion. Quite slow, and freezing for a few seconds every now and then, but there's live for you on a 600mhz G3 iMac Powerpc.

Also, the computer is really slow when I try to open the install part. Any way of optimizing it? Should I use a faster CD drive?

---

### Post by Mushed Mango on 2006-10-27
Will this work *after* I've installed the alternate version? Live is just too slow.

---

