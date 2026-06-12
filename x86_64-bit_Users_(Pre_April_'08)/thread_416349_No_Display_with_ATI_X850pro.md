---
title: "No Display with ATI X850pro"
date: 2007-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by kapellen421 on 2007-04-21
I have an ATIx850 pro. I installed the Ubuntu 7.04 64bit edition on my PC:cry: :cry: :cry: . When I go into grub and select Ubuntu. It puts out some stuff on bottom of the screen and then goes into sleep mode because it can't detect a signal. I don't know what to do. please Help.
	:cry:
	:cry:

---

### Post by HKiCore on 2007-04-21
I have the same problem with ATI X800 XL, though I  can get to the desktop by selecting the recovery mode when I get to the GRUB. Then I jus run the command startx. But that's not really a solution. 

So...Help...someone...pleace

---

### Post by jaimz on 2007-04-21
press e to edit and edit it out the "ro  quiet splash" and boot it

that's how I do it
I'm sure it's the same problem I have with the x800 lol

---

### Post by TheMafioso on 2007-04-21
> **jaimz said:**
> press e to edit and edit it out the "ro  quiet splash" and boot it

that's how I do it
I'm sure it's the same problem I have with the x800 lol

Yes, this solution  works perfectly... I was also gettin the same problem with my x850xt, but now its fixed.....Thanx Man :guitar:

---

### Post by kapellen421 on 2007-04-21
OK that allows me to get to the login screen for Ubuntu. But I can't login. I know I type by username and password in correctly. I don't get it. Does it some how magically forget my username and or password?

---

### Post by HKiCore on 2007-04-21
Yup, that gets me to the login. When I login I get an error message that says that the session lasted only 10 seconds that it could be a sign of installation failure/error or lack of space in hd. If I view the details from that error it gives me this:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: runnig: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "hki"
/etc/gdm/Xsession: Beginning session setup...
Gnomen pikanäppäinkansion "/home/hki/.gnome2/accels" luonti epäonnistui: Permission denied


The strage language from outer space that you see is Finnish and basically it says that:
Gnomes shortcut directory "/home/hki/.gnome2/accels" creation failed: Permission denied

---

### Post by TheMafioso on 2007-04-21
> **TheMafioso said:**
> Yes, this solution  works perfectly... I was also gettin the same problem with my x850xt, but now its fixed.....Thanx Man :guitar:

One noob problem though, how do I make these changes permanent, I have to edit these option every I boot :(

---

### Post by Sageinarage on 2007-04-21
Hey, awesome, I was having this same problem with my x700.  Editing out that stuff in grub did the trick, seems to be running fine for me now, thanks!

---

### Post by cham64 on 2007-04-22
i have this exact problem but unfortunately this solution didn't help.
when i pressed e to edit i only had 'quiet' not "ro quiet splash". When i deleted the line "quiet" and pressed b to boot i get the same problem, my screen starts searching for an input then turns off.
Is there another way to do this? im not sure that its saving anything because when i press escape and go back in quiet is still there.
*edit* i was a noob, found the line to edit (had to go across) - when i do this it now boots up ok.

this is the first time ive installed ubuntu and really want to give it a good shot but at the moment i cant even boot without going into the system recovery mode.

interestingly, the live cd boots ONLY when i change the resolution on the splash screen from VGA to another res (1280x1024x32). If i try to boot the live cd in the default VGA it does the same thing (screen turns off). Once the live cd has booted it works perfectly. After installing i reboot and it turns off when starting)

please help!! :confused:

---

### Post by FiggyG on 2007-04-22
Cham, when booting the Live CD, you have to change it to 1280x1024 eh? The default xorg.conf params are probably trying to use a display mode outside of your monitor's range. This can be fixed though!

Boot up to the blank screen. What we need to do is backup and edit the xorg.conf file.

Press Ctrl+Alt+F1, it should ask for logins to your machine, use your name & pass.
Next, backup your xorg configuration file.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Now to edit it...
```
sudo nano -w /etc/X11/xorg.conf
```
Go to the bottom of the file where it has stuff like
"Modes           "1440x900" "1280x1024" "1280x960" "1280x768""
Under "Depth", it should say "24", the line under it is what we want to change. Delete out any resolutions higher than 1280x1024 or which ever you know works.
Press Ctrl+O to write thew new conifg (the letter "O", not number "0")
Press Ctrl+X to exit nano back to the console.
Press Ctrl+Alt+F8 should take you to your blank screen, once there, Ctrl+Alt+Backspace to restart X.

If that doesn't work, use the Ctrl+Alt+F1 to go back to the console, open up the log file for Xorg
```
nano /var/log/Xorg.0.log
```
Where it says (EE) let me know what it says.

This should work for anyone that's having problems with coming up with a blank screen. However there are still a few things to do after getting display, like installing proper drivers. [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu) is an excellent guide that I use, however with the x64 Feisty, the aitconfig failed to work, so I wrote my xorg file manually. If anyone needs help with that, PM me or reply to this thread.

Hope this was helpful for everyone. I had the issue on my X1600XT 256 booting to blank screen, it was trying to use the vesa driver to load 1440x900, so I dropped it to 1024x768 for installation. I Installed the latest AMD fglrx drivers and then wrote up an xorg.conf file, rebooted into 1440x900 hotness with 3d accel working.

---

