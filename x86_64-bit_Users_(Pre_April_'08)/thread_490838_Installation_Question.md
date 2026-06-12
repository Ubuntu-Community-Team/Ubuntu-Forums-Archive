---
title: "Installation Question"
date: 2007-07-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by theoracle74 on 2007-07-02
Hello All,

     I am a long time windows user who is seriously considering switching over to Ubuntu.  I am currently running an amd athlon 64 x2 5600+, 4 gig ram, 640mb 8800gts, windows xp x64.  I went ahead and downloaded the 7.04 desktop amd64, burned it to a dvd, and edited my bios to boot from a cd first.  I attempted to boot from the Ubuntu disk I just made and i get a message saying "boot disk failed, insert system disk and press enter" or it just boots right into windows.  Any ideas?

Thanks for your time,

     Jon

---

### Post by oldmanstan on 2007-07-02
you check the md5sum (or whatever the heck it's called) on the iso after downloading? could be corrupt, i dunno, maybe

---

### Post by theoracle74 on 2007-07-02
I will take a look.   Thanks very much :)

---

### Post by tgm4883 on 2007-07-03
Also, you burnt it as an image right?

---

### Post by theoracle74 on 2007-07-03
I did burn it as an image :)  I also went out this morning and got a copy of Beginning Ubuntu Linux by Keir Thomas, which comes with a copy of Ubuntu 6.10.  I put that in the drive and rebooted my computer, which brought me to the start screen for Ubuntu.  I clicked on start/install, after which it begins to load.  Then I get the following message:

    "Failed to start the X server (your graphical interface).  It is likely that it is not setup correctly.  Would you like to view the X server output to diagnose the problem?"  

I selected ok, then saw this:

"x windows system version 7.1.1
release date 12 May 2006
X protocol version 11, revision 0, Release 7.1.1
Build operating system: Linux 2.6.15.7  i686
Current operating system Linux Ubuntu 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date 07 July 2006
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from  command line), (!!) notice, (II) informational, (ww) warning, (EE) error, (NI) not implemented, (??) unknown. 
(==) log file: "/var/log/Xorg.0.log", Time: Tue Jul 3 16:52:20 2007 
(==) using config file: "/etc/x11/Xorg.conf"

Not sure if any of that will help, but thanks for your time in advance :) 

Jon

---

### Post by dabl on 2007-07-03
> **theoracle74 said:**
>  went out this morning and got a copy of Beginning Ubuntu Linux by Keir Thomas

Yep, I got that book too -- it's a good one.

OK, I will share the fact that (K)Ubuntu's auto-detector for graphics chips is, uh, not exactly bulletproof.  Probably getting your video display working to your complete satisfaction is the hardest thing to do, and of course it's also the FIRST thing you want to do. Makes it tough!

Here's my advice, having started 8 months ago with Dapper.  Download the 7.04 (Feisty Fawn) Alternate Install ISO and burn that one.  The installer is text mode, more flexible, and gives you more control.  Feisty is somewhat better, in my experience, with the newer hardware.

Upon getting the basic system installed, you're probably going to need to configure your X server first as a VESA display, and then find and install the open source or proprietary driver for your graphics chip.

:)

---

### Post by theoracle74 on 2007-07-03
thanks a TON :)  Gotta love this community.  I will give it a try.

Jon

---

### Post by dabl on 2007-07-03
Sure.

By the way, since you're only in the preliminary stages, if it's not too, late, a separate disk partition for /home is highly recommended.  More reading here:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If you're little queasy about the partitioning thing, I advise downloading the GParted Live CD ISO from here:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

and use that to partition your disk FIRST, then boot your Ubuntu Alternate Install CD, and simply follow the installation process (while skipping partitioning), and choosing the appropriate partitions for mounting /, /home, and /{swap}.

:)

---

### Post by theoracle74 on 2007-07-03
I burned an image of the alternate version, got it to install :)  I booted up for the first time and got a black screen....so I booted into recovery mode and used the command dpkg-reconfigure xserver-xorg to get into the configuration program.  I used the reccomended settings from the Keir Thomas book, rebooted and still black screen.  I could see a quick flash on the screen during bootup, but it would flash then black screen again.  I tried quite a few different permutations with respect to the graphics configuration, but nothing worked...I was at it for about 2 hours.  I am still not discouraged though :)   Anything I am missing?  

Thanks,

Jon

---

### Post by dabl on 2007-07-03
> **theoracle74 said:**
>  I am still not discouraged though :)

Good!

Think of your experience so far as "practice" ....  I probably installed my system 8 times before I felt like I kinda knew what I was doing.

You're on the right track, actually -- you're doing the right things.  When you say "black screen", is there actually a little blinking white cursor "_" up in the upper left corner of the screen?  If so, the next time you get to that point, do Alt-F1 and you'll see a text login prompt. Login there, then, if you will start the ```
sudo dpkg-reconfigure xserver-xorg
``` script, and on the first screen choose "NO" to autodetect, and on the second screen choose "VESA" as the display type, you'll probably end up with a functional GUI, although it won't exploit your Nvidia card's capabilities at all.

Your 8800 card is too new for all but the latest (100.14.11) Nvidia driver, so the driver package that Ubuntu is trying to install won't work.  But, I think the Envy installer will work -- it has for others.  You download it from here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You want the file envy_0.9.5-0ubuntu5_all.deb which is downloadable from a link halfway down the page.

---

### Post by theoracle74 on 2007-07-03
ok, when I try to install in regular (not in recovery mode) I see the first few lines of text, then the screen goes black, and the monitor goes into sleep mode.  I went into recovery mode, got to the prompt, logged in, and went throught the reconfiguration again, selecting vesa this time.  When I tried to start up in normal mode, I got the same result, black screen then the monitor went into rest (hybernation) mode.  I am not giving up until I get this installed and working :)   Any ideas?

Thanks,

Jon

---

### Post by dabl on 2007-07-03
Yes.  The problem has to do with the Advanced Configuration and Power Interface (ACPI);  I think you need to tell it to boot with "no acpi" - this is a switch that you set in the boot routine at /boot/menu.lst.  If you search this forum, I think you'll find information about it -- it is not a problem that I have dealt with on my system.

---

### Post by theoracle74 on 2007-07-03
I finally got my system partitioned so I can dual boot :)  However, I am still having problems getting ubuntu to boot up.  It is installed, but when I attempt to boot, I get a quick flash on the screen, then a black screen, then my monitor still hibernates.  I am still unsure how to access the boot routine to turn acpi off.  Thanks for all your patience.

Jon

---

### Post by theoracle74 on 2007-07-04
Just a thought....but would installing the nvidia-glx package from recovery mode fix my problem?  If so, how do I go about doing that?  

Thanks,

Jon

---

### Post by theoracle74 on 2007-07-04
I started up recovery mode, logged in and used the sudo aptitude install nvidia-glx  then sudo nvidia-glx-config enable commands.  The install seemed to work without any errors.  I logged back out and rebooted into normal mode.  I got the screen flash again, but it stayed a black screen after that.  At least my monitor didn't go into hybernation mode this time :)  

I am trying to get this working :)   Thanks for everyones help thus far:)

Jon

---

### Post by dabl on 2007-07-04
You'll need to edit the file /boot/grub/menu.lst, and add "acpi=off" at the end of the line that specifies the kernel to be booted.  You can do that using gedit in Super User mode by entering in the console ```
gksu gedit /boot/grub/menu.lst
``` and then editing the file.

Check this out:

[http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems)

:)

---

### Post by theoracle74 on 2007-07-04
I logged back in via recovery mode and typed in the following:

gksu gedit /boot/grub/menu.lst   and got the following message

(gksu:4715): Gtk-WARNING **: cannot open display


Sorry for being a total noob here and having trouble getting this running. 

I really appreciate all the help thus far :)


Thanks,

Jon

---

### Post by dabl on 2007-07-04
Hmmmmm!

OK, I'm Kubuntu at the moment and can't test it, but maybe "sudo" will work -- try ```
sudo gedit /boot/grub/menu.lst

```

If gedit opens, then you will be able to edit and save the change.  If that doesn't do the trick, I'm afraid you're going to be in for a vi editor lesson, or maybe we'll give nano a try.

---

### Post by oldmanstan on 2007-07-04
wait, if he has no display then how is gedit supposed to work?

try this:

```
sudo nano /boot/grub/menu.lst
```

then when you've made the changes (use the arrow keys) do ctrl-o to save and ctrl-x to quit

---

### Post by dabl on 2007-07-04
Ahhhhhhh -- thank you Stan.  I forgot gedit is a GUI editor!  ](*,)

Yes, nano is a good way to do the editing.  Sorry for being senile ...

---

