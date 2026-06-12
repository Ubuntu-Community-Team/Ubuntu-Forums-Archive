---
title: "Complete Linux novice - help with display &amp; file editing"
date: 2005-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by audscott on 2005-02-27
System:  DFI NF3 UT3 boad (nforce 3 chipset soc 754), A 64 3200, 1 Gig RAM, Gigabyte 6800 GT (nvidia) 7200 WD IDE 1, CD ROM, floppy IDE 2, onboard sound & LAN, 500 watt PSU well ventilated case.

I loaded the 64 bit version from a pressed CD - could not load the GUI.  I get a message instructing me to edit the necessary files.   

I don't know how....I've spent hours on the net, in the help files and I just can't figure it out.

I would like to see the tutoral that's displayed in the VIM help, but I can't get that to run either.  

I've checked every site I oculd find googling "linux newby, Linux for morons, ect."

Any help or direction will be much appreiated, 'cause I want to get the XP monkey off my back.  :D

---

### Post by FluffyElmo on 2005-02-27
I'm a newbie myself, but I'll try to help. Exactly what files is it telling you to edit?

Instead of VI try nano, it's much easier to use IMO. Also to save most system files you have to open them as root, so if you aren't at a root prompt use sudo. ```
sudo nano *filename*
```

---

### Post by audscott on 2005-02-27
Thanks for the reply:

I've done some more exporation, of course understanding such a venture takes time and effort. 

The start message: "I cannot start the Xserver (your GUI). It is likely that it is not setup correctly."

I then look at the output/diagnosis which tel;ls me the version and legal stuff, but I don't see a specific solution....but I probably wouldn't recognize it yet, anyway.

I tried an environment command:  

$ sudo apt-get install nvidia-glx
$ sudo nvidia-glx-config enable
then restart X using Ctrl+Alt+Bkspc

The install command invoked a file and nvndia-glx was enabled. The Ctrl+Alt+Bkspc didn't do anything, so I tried loading with the "gimp" command.

Once again, I'm having some fun, but would appreciate any ideas so I could see the desktop.   :roll:

---

### Post by FluffyElmo on 2005-02-27
You should be able to get the GUI running without installing the Nvidia stuff, you can add that later for performance. 

You may have Googled most of this already but when my X wouldn't run here are a few things I remember finding useful...

To start the gui from a command prompt, type *sudo gdm*, the Gnome Display Manager will start X.

The X config files are at: */etc/X11/XF86Config-4* for warty, or */etc/X11/xorg.conf* for Hoary. The GDM config file is at */etc/gdm/gdm.conf*.

You could try reinstalling the X server, try something like *sudo apt-get update*, then *sudo apt-cache search XF86*, then apt-get install the X server package. Sorry I can't confirm the exact package...I'm running Hoary and XF86 doesn't seem to be in the Hoary repositories. (Hoary uses xorg X server, Warty uses XF86).

Come to think of it, given your current situation an upgrade to Hoary couldn't hurt, and may even help :)  There are many how-to's in the forum, but briefly: *sudo nano /etc/apt/sources.list*, anywhere you see *warty* replace it with *hoary*, then run *sudo apt-get update*, and finally *sudo apt-get dist-upgrade*. 

Last time I did it, I had to use *sudo apt-get -f dist-upgrade*, and run it twice..but it may have been dependency issues with other software I'd installed.

Good Luck!

---

### Post by audscott on 2005-02-27
Thanks for all the pointers:  I found this page: [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto) - which walked me through the driver configuration, getting me into the GUI.

Now that I'm in the GUI, any suggestions on suggestions on a tutorial? 

Oh, us donegone newby's!  :D

Thanks for the input thus far, pleae keep humoring me....I think this could be my first and (for a while) OS of choise.

---

### Post by FluffyElmo on 2005-02-27
Glad you're up and running, now you can really start to have some fun. This forum is probably your best guide for most 64bit related issues. And the other Ubuntu forms have useful info.

As far as guides go, I found this one to be the most useful starting out. It'll get you playing DVDs and MP3s at the least...
[http://ubuntuguide.org/index.html](http://ubuntuguide.org/index.html)  

On a 64bit install some apps, (ie. W32Codecs, Flash and WINE) won't work. Getting them to work is a bit involved. You have to install a 32 bit chroot, or some will run by installing the relevant dependecies to lib32 and pointing the app to them. 

Myself, I've been living without them for now...just starting to look into running 32bit apps without a chroot now.  

And this page has useful info on tuning your install and getting 32bit apps to work...
[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#UPDATED_AMD64_pure64_w.2F32bit_libs_and_NO_32bit_chroot](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#UPDATED_AMD64_pure64_w.2F32bit_libs_and_NO_32bit_chroot)

Mostly though, I've learned by breaking things and figuring out how to fix them :)

---

### Post by audscott on 2005-02-27
[QUOTE=audscott]Thanks for the reply:

I've done some more exporation, of course understanding such a venture takes time and effort. 

The start message: "I cannot start the Xserver (your GUI). It is likely that it is not setup correctly."

I then look at the output/diagnosis which tel;ls me the version and legal stuff, but I don't see a specific solution....but I probably wouldn't recognize it yet, anyway.

I tried an environment command:  

$ sudo apt-get install nvidia-glx
$ sudo nvidia-glx-config enable
then restart X using Ctrl+Alt+Bkspc

The install command invoked a file and nvndia-glx was enabled. The Ctrl+Alt+Bkspc didn't do anything, so I tried loading with the "gimp" command.

Once again, I'm having some fun, but would appreciate any ideas so I could see the desktop.   :roll:[/QUOTE]
 Thanks a bunch ***FluffyElmo***, I certainly appreciate the support.

Had to switch back to windows for a few hours to finish my Algebra final (I'm an old man whose a Junior in College...hehehehe)

I'll post how my fixing is going and how the breaking went.  :D

---

