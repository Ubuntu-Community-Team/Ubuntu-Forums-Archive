---
title: "Wine for 64 bit?"
date: 2006-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by crazy_fox on 2006-02-12
I search the repository for wine server. Nowhere to be found..

And when i try to install a library for wine, i get the error that wine is not installable.. Any ideas?

---

### Post by handy on 2006-02-12
Wine is not easily installed on 64bit.  It is possible, if you search the forums, there is a how-to, or two.

There is more than one way to do it, you can **force** it, or you can set up a 32bit environment to run it in!

I had a melt down on my OS, due to something else entirely, & chose to install 32bit Breezy 5.10, out of curiosity, & never looked back!

Life at the moment is a lot less complicated on 32bit.

My attitude is that we are in transition, & when 64bit's time has come I will embrace it joyfuly. :KS

---

### Post by RAOF on 2006-02-12
[QUOTE=crazy_fox]I search the repository for wine server. Nowhere to be found..

And when i try to install a library for wine, i get the error that wine is not installable.. Any ideas?[/QUOTE]
And the short guide to installing wine (without setting up a 32bit chroot) is:
1) Manually download the i386 .deb from [wine.sourceforge.net/apt/breezy](wine.sourceforge.net/apt/breezy)

2) Install it with "sudo dpkg --install --force-architecture whatever_the_name_is.deb"

3) Install some 32bit compatibility libraries: Search for ia32-libs in synaptic.  Install all but the -kde ones.

4) Try running winecfg.  It won't work - it'll say (among other things) something like "could not load xf86ddm.so.1" or something.  Search for the deb corresponding to this library on [packages.ubuntu.com](packages.ubuntu.com) & download the 32bit version.  Open it with file-roller (you should be able to just double-click on the .deb) and copy out the library file you want (it will be in /usr/lib).  Move the library you've extracted to /lib32 "sudo mv libwhatever.so.1 /lib32".  Run ldconfig "sudo ldconfig"

5) Repeat 4 until winecfg runs.

---

### Post by crazy_fox on 2006-02-15
Thanks for the replies.

So there is no 64 bit right now.. Damn.. and i am so proud that linux excists in 64 bit..

---

### Post by Jave27 on 2006-02-15
See [this thread](http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit) on how to set up a 32-bit chroot inside of your 64-bit system (replace all instances of 'hoary' with 'breezy' from the instructions).  It seems like a cleaner solution in some aspects, but a tougher one in other.  I'm using it now, and it does get confusing sometimes when you have a bunch of terminal windows open as to which one is inside the chroot and which isn't, but it works.

---

### Post by RAOF on 2006-02-16
[QUOTE=crazy_fox]Thanks for the replies.

So there is no 64 bit right now.. Damn.. and i am so proud that linux excists in 64 bit..[/QUOTE]
You wouldn't want a 64bit wine, anyway.  How many Win64 binaries do you have to run? :)

---

### Post by Jave27 on 2006-02-16
> You wouldn't want a 64bit wine, anyway. How many Win64 binaries do you have to run? 

You can laugh now, but not in a year or two.  There are already Win64 binaries floating around the web (I know, I've created a few), and it will become the defacto standard at some point in the not-so-distant future.  There are still a lot of bugs to work out (mostly driver issues), but Win64 is not Vaporware(TM), and someone soon will want to run native Win64 apps on Linux.  At which point, someone will have to come up with WINE64 or modify WINE to handle them (which will be a HUGE undertaking).

---

### Post by RAOF on 2006-02-16
[QUOTE=Jave27]You can laugh now, but not in a year or two.  There are already Win64 binaries floating around the web (I know, I've created a few), and it will become the defacto standard at some point in the not-so-distant future.  There are still a lot of bugs to work out (mostly driver issues), but Win64 is not Vaporware(TM), and someone soon will want to run native Win64 apps on Linux.  At which point, someone will have to come up with WINE64 or modify WINE to handle them (which will be a HUGE undertaking).[/QUOTE]
...Which has already started (there's a bunch of #ifdef'd WIN64 stuff in the code).  It will be at least a couple of years before Win64 binaries become really commonplace, and a long time before you won't be able to get Win32 binaries.

---

### Post by John Jason Jordan on 2006-02-16
[QUOTE=RAOF]...Which has already started (there's a bunch of #ifdef'd WIN64 stuff in the code).  It will be at least a couple of years before Win64 binaries become really commonplace, and a long time before you won't be able to get Win32 binaries.[/QUOTE]
I tried Wine in my chroot environment. Never could figure it out. After fumbling around with commands for several days I decided I didn't want it running in chroot anyway. It's a big enough PITA to have Firefox, RealPlayer and Adobe Reader running in there. I just uninstalled it and forgot about it. 

But I do have one Windows 2000 app I need to run and there is no replacement in Linux. And it won't run under Wine anyway, or even Crossover Office. As it turns out I have a spare Windows 2000 license, so I've been looking at Qemu. Anyone know anything about it?

---

### Post by thomasleveil on 2006-02-23
You could try vmware, which is now free. I run winXP pro as a guest in my Breezy, works great.

---

### Post by MighMoS on 2006-02-23
[QUOTE=thomasleveil]You could try vmware, which is now free. I run winXP pro as a guest in my Breezy, works great.[/QUOTE]
VMWare is a great solution, if its what you want.  Which sounds retarded, but some people don't have a Windows licence, and some don't want to / can't run another operating system at the same time.

Also, Because of Linux's coolness factor (and also in part to the developers working on it), some programs (Office, and other non-3d) actually run *faster* on WINE than on Windows.

Somewhat unrelated, but the only times I've had Linux crash on me that weren't hardware issues were when I was running VMware to emulate Windows.

---

### Post by diablozx9 on 2006-03-08
how do I put VMWARE on my 64 bit ubuntu Breezy?

My wife gives me a hard time because some of her windoz apps won't work.

---

### Post by hollywoodb on 2006-03-09
[QUOTE=Jave27]See [this thread](http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit) on how to set up a 32-bit chroot inside of your 64-bit system (replace all instances of 'hoary' with 'breezy' from the instructions).  It seems like a cleaner solution in some aspects, but a tougher one in other.  I'm using it now, and it does get confusing sometimes when you have a bunch of terminal windows open as to which one is inside the chroot and which isn't, but it works.[/QUOTE]

put:```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
``` into ~/.bashrc

The **${debian_chroot:+($debian_chroot)** is the important part.

If your home directory is not shared with the chroot environment put it in both ~/.bashrc

Then create and edit the file <chroot>/etc/debian_chroot, in it just put what you want the displayed name of your chroot to be on your bash prompt. Mine looks like this:
```
hollywoodb@hollywoodb:~$ cat /home/chroot32/etc/debian_chroot
breezy32
hollywoodb@hollywoodb:~$
```

Then try entering & exiting your chroot on the command line.  If it doesn't work try:

```
source ~/.bashrc
```

---

### Post by diablozx9 on 2006-03-09
no really,,, how do i get and load VMWARE on my 64 bit breezy???

---

### Post by Jave27 on 2006-03-10
> **hollywoodb]put:```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01 said:**
> \u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
``` into ~/.bashrc

The **${debian_chroot:+($debian_chroot)** is the important part.

If your home directory is not shared with the chroot environment put it in both ~/.bashrc

Then create and edit the file <chroot>/etc/debian_chroot, in it just put what you want the displayed name of your chroot to be on your bash prompt. Mine looks like this:
```
hollywoodb@hollywoodb:~$ cat /home/chroot32/etc/debian_chroot
breezy32
hollywoodb@hollywoodb:~$
```

Then try entering & exiting your chroot on the command line.  If it doesn't work try:

```
source ~/.bashrc
```

hollywoodb, thanks, I actually just managed to figure that out a few days ago.  However, I have a different problem now involving locales - I've tried a bunch of different programs and settings, but some libs are still having trouble recognizing my locale as en_US (tried both UTF-8 and ISO-8859-1).  Is there a simple script that will clean that stuff up?  Here's my export list while inside the chroot:

```

declare -x COLORTERM="gnome-terminal"
declare -x DBUS_SESSION_BUS_ADDRESS="unix:abstract=/tmp/dbus-7iyHzCr68x,guid=92c510445cdf1d319a855b6a76e97d00"
declare -x DESKTOP_SESSION="default"
declare -x DESKTOP_STARTUP_ID=""
declare -x DISPLAY=":0.1"
declare -x GDMSESSION="default"
declare -x GDM_LANG="en_US.UTF-8"
declare -x GDM_XSERVER_LOCATION="local"
declare -x GNOME_DESKTOP_SESSION_ID="Default"
declare -x GNOME_KEYRING_SOCKET="/tmp/keyring-JhOQY9/socket"
declare -x GTK_RC_FILES="/etc/gtk/gtkrc:/home/jason/.gtkrc-1.2-gnome2"
declare -x HOME="/home/jason"
declare -x LANG="en_US.ISO-8859-1"
declare -x LANGUAGE="en_US.ISO-8859-1"
declare -x LC_ALL="C"
declare -x LESSCLOSE="/usr/bin/lesspipe %s %s"
declare -x LESSOPEN="| /usr/bin/lesspipe %s"
declare -x LOGNAME="jason"
declare -x LS_COLORS="no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:"
declare -x OLDPWD="/home/jason/civ4/DirectX9"
declare -x PATH="/usr/local/jdk1.5.0_06/bin:/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games"
declare -x PWD="/usr/src/wine/wine-git"
declare -x SESSION_MANAGER="unix/jave02:/tmp/.ICE-unix/8281"
declare -x SHELL="/bin/bash"
declare -x SHLVL="2"
declare -x SSH_AGENT_PID="8320"
declare -x SSH_AUTH_SOCK="/tmp/ssh-WSnOze8281/agent.8281"
declare -x TERM="xterm"
declare -x USER="jason"
declare -x USERNAME="jason"
declare -x WINDOWID="16972534"
declare -x XAUTHORITY="/tmp/.gdm1Y0hJV"

```

I've been changing the LC_ALL, LANG, and LANGUAGE options all around, and none of them seem to matter to certain apps (wine in particular). How is this supposed to be configured?

---

### Post by Jave27 on 2006-03-10
I may have fixed my issue by installing language-pack-en-base...  if not, i'll post back.

---

### Post by zonerr on 2006-03-10
Vmware has recently released player as semifree ware. Go to the VMware sight and look through their offerings. You can also download a version of the actual server on a trial basis. Wine has stated they were going to start working on a 64 bit version but it will constitute a complete rewrite. I agree with some of the previous posts 64 but will be the future but we probably have to wait for MS to get behind it in the long run.

---

### Post by hopper on 2006-03-30
[QUOTE=RAOF]And the short guide to installing wine (without setting up a 32bit chroot) is:
1) Manually download the i386 .deb from [wine.sourceforge.net/apt/breezy](wine.sourceforge.net/apt/breezy)

2) Install it with "sudo dpkg --install --force-architecture whatever_the_name_is.deb"

3) Install some 32bit compatibility libraries: Search for ia32-libs in synaptic.  Install all but the -kde ones.

4) Try running winecfg.  It won't work - it'll say (among other things) something like "could not load xf86ddm.so.1" or something.  Search for the deb corresponding to this library on [packages.ubuntu.com](packages.ubuntu.com) & download the 32bit version.  Open it with file-roller (you should be able to just double-click on the .deb) and copy out the library file you want (it will be in /usr/lib).  Move the library you've extracted to /lib32 "sudo mv libwhatever.so.1 /lib32".  Run ldconfig "sudo ldconfig"

5) Repeat 4 until winecfg runs.[/QUOTE]

This sounds like a nice, simple & relatively painless way of getting a 32-bit Wine environment on amd64 - perfect for what I need (running Win32 command line apps).  

I have one question, is it guaranteed not to overwrite or otherwise mess up my currently happy & stable system?

M

---

### Post by Yagisan on 2006-03-30
[QUOTE=hopper]I have one question, is it guaranteed not to overwrite or otherwise mess up my currently happy & stable system?[/QUOTE]Nope. The happy and stable way is to use a chroot.

---

### Post by johnnymac on 2006-03-30
The only ways are...

1.  Set up a chroot environment - search around the forums there's about 50-billion posts on it.

2.  Xen a 32-bit Linux OS - but Xen is a pain in the butt to get running

3.  Vmware really won't do it for you but you can install it...the colorful way :D 
a.  Download the demo versio of vmware and install it
b.  Use vmware to install you flavorite Winblows OS.  This will create a vmx image for you.
c.  Download and install vmware-player (you can remove vmware if you like) 'cause it's a free vmx player by VMWare.

Good luck.....I myself use #3 :cool:

---

### Post by crazy_fox on 2006-04-04
how do u mount windows on vmware? I mean u have to download a file for it? Dont you?

---

