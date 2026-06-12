---
title: "Need hlp to get Mx Revo mouse to work properly"
date: 2008-06-21
forum: x86 64-bit Users
---

### Post by slope on 2008-06-21
I just innstalled Xubuntu 64 bit the latest version 8.04 hardy.
It all seems good except I can not use my logitech Mx Revolution properly. The "thumbs" buttons on the left side does ot work, neither does the left side scroll wheel and finally the now long trusted tilt function in the regular scrollwheel does not work either work.

I have tried a few good solutions, none that worked for med however:

[http://ubuntuforums.org/showthread.php?t=485175&highlight=logitech+mice]("http://ubuntuforums.org/showthread.php?t=485175&highlight=logitech+mice") as I read that this with also work under xubuntu and with mx revo. I did not work for me, and I check the xorg.conf manually I can see the changes was made and I even followed the guide top-bottom-

then I changed xorg.conf to this:
```
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 6 7"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "false"
```

Guess what still not working. Ok I read all posts I could find on Logitech and Mx Revolution and got my hands dirty. After a lot of digging I found this one and that might just work had I only fully understood it. See btnx: [http://ubuntuforums.org/showthread.php?p=2727025]("http://ubuntuforums.org/showthread.php?p=2727025")

Now my first problem is that I do not understand the part 1:
```
deb http://ppa.launchpad.net/daou/ubuntu DISTRO main
deb-src http://ppa.launchpad.net/daou/ubuntu DISTRO main
```

The btnx is actually for kubuntu rather then xubuntu and I do not know what code to put there to make it correct.

I have seen that flash does not install well with xubuntu 64 bit, could that be the case with the mx revo mouse as well or is it really about getting the button settings correct?

Will the btnx work for me in xubuntu?

At least I am learning better english while roaming the forums :)

---

### Post by Nepherte on 2008-06-21
This worked for someone. I suggest you BACKUP your xorg file first though!
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Open up your xorg file:
```
gksudo /etc/X11/xorg.conf
```
Change *a part* of your xorg file to look like this:
```
Section "ServerLayout"
        # ...
        InputDevice     "Logitech Revolution"
EndSection

Section "InputDevice"
        Identifier      "Logitech Revolution"
        Driver          "evdev"
        Option          "Name" "Logitech USB Receiver"
        Option          "Device" "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"
        Option          "CorePointer"
EndSection
```

Btnx should work for xubuntu as well (I use it on Ubuntu). With DISTRO they rather mean hardy, gutsy, feisty or something else. The lines should go into /etc/apt/sources.list:
```
gksudo /etc/apt/sources.list
```
Add them at the end of the file. Continue with the rest of the btnx tutorial.

---

### Post by slope on 2008-06-21
I have a backup from a working stage but now my mouse is totally dead so I can not even start a terminal window. Any chance I can start terminalwindow from keyboard in xubuntu 64 bit? Btw I have not assigned any special keys after installation yesterday, so except from struggling with the mouse it is a standard install.

Pls tell me there is a way to start a terminal without using the mouse.......

I was still strugglig with the Revo mouse and I found a step by step guide that I followed. I made changes to xorg.conf as well as d.19 or something. When done I pressed Ctrl+Alt+Backspace and loggen in. 

I do not find back to the tutorial I used, and I do not know how to open Firefox without a mouse so sry I can not provide a link for the step by step guide.

---

### Post by Nepherte on 2008-06-21
Praise yourself lucky you don't need a mouse for it :)
Press alt+F2 and type gnome-terminal in the box that just appeared. That will give you a terminal. If you have a backup already you might get your mouse to get the basic functionalities again with restoring your xorg file:
```
sudo cp /location/of/your/backup/file /etc/X11/xorg.conf
```

---

### Post by slope on 2008-06-21
Hmm. Ok so typing gnome-terminal does not work in xubuntu.
Sure there is another command that will work, cause here is the error I get:

Failed to execute child process "gnome-terminal"(Nos such file or directory)

SO if I can figure out what command to use maybe I do not need to format disk.

---

### Post by Nepherte on 2008-06-21
I'm sorry, I forgot you used xubuntu. You should type xfce4-terminal I think.

---

### Post by slope on 2008-06-21
Xubuntu ;-)
So typing xfce4-terminal saved me.

---

### Post by slope on 2008-06-21
hmm cant remember correct file name of the backup. I'll just put it in the same folder as the xorg.conf, so how do I change directory to that folder and also list all files?

---

### Post by Nepherte on 2008-06-21
Some brief command explanation then. To **c**hange **d**irectory, you use the cd command. You specify the path to which you want to navigate as argument of the **cd** command. That would be:
```
cd /etc/X11
```

This is the full path to that directory. You can also use relative paths. Say you are in /usr directory and you want to go to /usr/share. You don't have to specify the full path, you can just give share as argument:
```
cd share
```

There are also some special characters you can use. A tilde ~ is actually a shortcut to your /home/username directory. So this command will get you to the Music map (if you have any) in your home directory:
```
cd ~/Music
```

One dot . means the current directory you are working in. Two dots means to navigate the directory right above the current one, also called the parent directory:
```
cd ..
```

If you just use cd, you'll get to your home directory /home/usrname:
```
cd
```


To list file a directory, you use the **ls** command:
```
ls
```

If you'd like the see more details of each file, use:
```
ls -l
```


A detailed information on a command can be found by typing:
```
man commandname
```

---

### Post by slope on 2008-06-21
Thx 4 all the help. I am now back on the linux machine and will continue to see of there actually is a way to make all buttons work. do not really now what happend after I restored the orginal xorg.conf and rebooted but now the left side thums buttons works and they did not before. Maybe I have forgotten to do a reboot after one of the steps I have tried so I guess it is just to start all over again from step one.

My goal for the day:
Make top scroll wheels tilt function will in Firefox and preferable all other app give me PageUp and PageDown function as I have grown addicted to that.

As the Mx Revolution works partially now I will be sure to back up files before editing and also to make a reboot after changes are made just to be sure the changes are put to work.

---

### Post by pixel :-) on 2008-06-21
Re-ask here [http://ubuntuforums.org/forumdisplay.php?f=332]("http://ubuntuforums.org/forumdisplay.php?f=332")

Also,at boot up, you can chose, recovery mode,for problems like these.

---

