---
title: "Ubuntu Boot Problems"
date: 2009-05-11
forum: x86 64-bit Users
---

### Post by tom.swartz07 on 2009-05-11
Hi All, 

Im still rather new to Ubuntu, but Ive managed (with a little help so far here) to get Ubuntu 9.04 64 bit running on my Dell Inspiron 1521. I had some problems with the drive partitions, but everything was fine and running excellently- until..

I was adding some new applications, and I came across one in the 'add/remove programs' list called desktop effects, or something similar. I wasnt sure exactly what it did, but I remember seeing the phrase 'edits compiz' or something to that effect. I had noticed on some of the online articles that compiz was a pretty cool application/tool for desktop effects, but I had no idea that it was difficult to manage. 

Anyway, I installed it, but couldnt find where the menu/program installed (applications, video, system settings, personal settings, etc). At this point, my laptop battery was going dead, so I shut the system down and decided to look more later on. 

Upon returning, and charging my battery, I discovered that Ubuntu will no longer boot to the workspace area. When I hit the power button, I see the Dell BIOS, then I could select what OS to use (Vista or Ubuntu). Grub shows the usual loading messages across the screen as the OS loads, but just as the computer would normally show the desktop, the screen goes black, then flashes lines of green, red, and what appears to be broken letters all across the top of the screen, upon which the system freezes, and I am forced to do a hard reset.

I was wondering if anyone knows how to fix this problem, as much of my upcoming work depends on fixing this problem ASAP

Thanks to anyone who could help me solve this problem!

---

### Post by tom.swartz07 on 2009-05-11
Here are a few pictures of what the screen looks like.
It happens right after Ubuntu loads, and the progress bar completes. When it reaches this point, the screen may flicker once or twice, showing different patterns, but usually after 1-2 flickers, it sticks to a messed up screen like this..

[IMG]http://lh3.ggpht.com/_tORug_uHNu4/SgjsuaRFqyI/AAAAAAAAAEc/bkIoCoohEEY/s800/IMG_0128.JPG[/IMG]




and another...
[IMG]http://lh3.ggpht.com/_tORug_uHNu4/SgjsukdwIlI/AAAAAAAAAEg/3hdV_tJDKco/s800/IMG_0129.JPG[/IMG]

---

### Post by bashphoenux on 2009-05-12
probably it couldnt detect the video drivers ! press ctrl f8 and check for the error message you get !

---

### Post by zeex on 2009-05-12
> **tom.swartz07 said:**
> Hi All, 

Im still rather new to Ubuntu, but Ive managed (with a little help so far here) to get Ubuntu 9.04 64 bit running on my Dell Inspiron 1521. I had some problems with the drive partitions, but everything was fine and running excellently- until..

I was adding some new applications, and I came across one in the 'add/remove programs' list called desktop effects, or something similar. I wasnt sure exactly what it did, but I remember seeing the phrase 'edits compiz' or something to that effect. I had noticed on some of the online articles that compiz was a pretty cool application/tool for desktop effects, but I had no idea that it was difficult to manage. 

Anyway, I installed it, but couldnt find where the menu/program installed (applications, video, system settings, personal settings, etc). At this point, my laptop battery was going dead, so I shut the system down and decided to look more later on. 

Upon returning, and charging my battery, I discovered that Ubuntu will no longer boot to the workspace area. When I hit the power button, I see the Dell BIOS, then I could select what OS to use (Vista or Ubuntu). Grub shows the usual loading messages across the screen as the OS loads, but just as the computer would normally show the desktop, the screen goes black, then flashes lines of green, red, and what appears to be broken letters all across the top of the screen, upon which the system freezes, and I am forced to do a hard reset.

I was wondering if anyone knows how to fix this problem, as much of my upcoming work depends on fixing this problem ASAP

Thanks to anyone who could help me solve this problem!

Hi, 

Seems like problem with video driver. Reboot and when you see grub boot inti Single user mode. After boot it'll open up a screen with option XFIX. Try that. but later you'll 've to install Graphics card drivers, again.

For easy Compiz config access, Install *compizconfig-settings-manager* and you can access it from System -> Preferences -> compizconfig-settings-manager

---

### Post by tom.swartz07 on 2009-05-12
Thanks for the help zeex and bash, but unfortunately neither of those solutions worked. It does appear to be a video card driver error, but I can't figure out how to get into Ubuntu to fix it. Like I mentioned before, when those colors and patterns appear, the whole system locks up, or at least the keyboard becomes unresponsive. (caps lock light, etc won't toggle)

Is there an way to disable the previous packages that were installed, or start in a windows-esque safe mode?
If not, what are my other options other than a format and reinstall?

---

### Post by tom.swartz07 on 2009-05-12
Im going to copy this thread to the dell section of the forum to see if anyone there knows what to do... they might be intimidated by the 64 bit heading... I feel that this problem is more in tune with a software/driver problem rather than Ubuntu itself.

Still feel free to post here too!

---

### Post by zeex on 2009-05-12
> **tom.swartz07 said:**
> 
Is there an way to disable the previous packages that were installed, or start in a windows-esque safe mode?
If not, what are my other options other than a format and reinstall?

Hi, 

You can boot into single user mode it's like the recovery console of windows. There you can remove the installed drivers. Since it's a totally CLI interface you might face problem what packages you 've installed so use this 

```
$ dpkg --get-selections | grep -i <package name>
```

for example listing all nvidia packages 

```
$ dpkg --get-selections | grep -i nvidia
```

Now you can remove the packages using apt

```
$ sudo apt-get remove <package name>
```

After removing the drivers you 'd installed try this

```
$ sudo dpkg-reconfigure -phigh xserver-xorg
```

try this and let us know what happens :)

---

### Post by tom.swartz07 on 2009-05-12
Hi again, Thanks for the speedy reply. I did as you said, and was able to locate and remove both the nvidia packages and the desktop effects package. I used autoremove for desktop effects as there were many dependent packages installed also. Just for reference, the program in question is 'desktop effects kde' from the add/remove panel. Unfortunately, I still get the messed up screen, but at this point now I could at least push the power button and a garbled ubuntu shutdown loader is displayed and the comiter powers off. How would I go about installing the right drivers? Like I mentioned before, I have an ati radeon x1270 card. 

Thanks!

---

### Post by pixel :-) on 2009-05-12
Revert to default X configuration, from the recovery menu doesn't work?

---

### Post by tom.swartz07 on 2009-05-12
Ive managed to figure it out with a little help of our university's resident linux guru. Apparently, it wasn't the desktop effects, but Catalyst Control Center. When the package installed, there was an error in the file, and it overwrote the default value for the display driver. 

I was able to do just what you had suggested, pixel, and re-installed xorg completely, after removing CCC, and it cleared the problem right up!

Thanks to everyone for the help!

---

### Post by Stevie78 on 2009-08-24
> **zeex said:**
> Hi, 

You can boot into single user mode it's like the recovery console of windows. There you can remove the installed drivers. Since it's a totally CLI interface you might face problem what packages you 've installed so use this 

```
$ dpkg --get-selections | grep -i <package name>
```for example listing all nvidia packages 

```
$ dpkg --get-selections | grep -i nvidia
```Now you can remove the packages using apt

```
$ sudo apt-get remove <package name>
```After removing the drivers you 'd installed try this

```
$ sudo dpkg-reconfigure -phigh xserver-xorg
```try this and let us know what happens :)


Ive got exactly the same problem with my desktop, and an ATI 2100. I had this problem in the past and wiped the HDD as nobody could help. [http://ubuntuforums.org/showthread.php?t=1176226](http://ubuntuforums.org/showthread.php?t=1176226)

Not that bad as I havent had the computer for long then. 

But now I tried to update my drivers again and knowing what happened I did a backup of (almost) everything.  A wise choice as it turns out now.

This time however Im determined to fix the problem. Though when I try your solution and type 

```
$ dpkg --get-selections | grep -i fglrx
```in grub> I get:

Error 27: Unrecognized command

Please tell me where and how exactly I can locate and delete the two fglrx packages installed yesterday that messed everything up.

---

### Post by Stunts on 2009-08-24
That command is not to be run from grub.
When you get the choice over which OS you choose, pick ubuntu recovery option. Just like that.
After a while you will get a menu to choose some options from. Pick "Root terminal" (or "Root terminal with internet access", if you are connected to an ethernet network).
After getting the CLI prompt - a a blinking cursor - you can try and run the mentioned commands, such as the one you posted.

Good luck!

---

### Post by Stevie78 on 2009-08-24
> **Stunts said:**
> That command is not to be run from grub.
When you get the choice over which OS you choose, pick ubuntu recovery option. Just like that.
After a while you will get a menu to choose some options from. Pick "Root terminal" (or "Root terminal with internet access", if you are connected to an ethernet network).
After getting the CLI prompt - a a blinking cursor - you can try and run the mentioned commands, such as the one you posted.

Good luck!


It worked! :)

I went to root with networking and entered the command (though without the dollar sign at the beginning or it wouldnt work)

Then it located four files:

fglrx-amdcccle                   install
fglrx-kernel-source             install
fglrx-modaliases                install
xorg-driver-fglrx                install

Im almost certain that 'fglrx-amdcccle' was one of the two that I installed yesterday and which messed everything up. As far as I remember Synaptic suggested it as a dependent file. Which was the file it depends on - I need to get rid of them both I guess?

1) Can anyone check this in Synaptic - or even knows this offhand? 

2) How do I delete/uninstall them? Whats the command?

---

### Post by Stunts on 2009-08-25
The $ is just there to represent the prompt, not to be typed. Sorry, I should have mentioned this.
since you've found the "offending" packages, all you have to do now is remove them. Just type:
```
 apt-get purge fglrx-amdcccle fglrx-kernel-source fglrx-modaliases xorg-driver-fglrx
```
Since you are already in a root prompt, you don't need to issue "sudo" at the beginning of the command.

I hope this works out for you.

---

### Post by Stevie78 on 2009-08-25
PROBLEM SOLVED :)


I purged the following two files in root:
[B]
fglrx-amdcccle
xorg-driver-fglrx[/B]

And the problem (see Tom's photos on page one) is gone. All is back to normal. Thanks a lot everyone!! :)


PS: Word of warning to everyone with an ATI 2100 graphics card - best do not install those two packages above...

---

### Post by Stunts on 2009-08-25
I'm glad you got it sorted out!
Enjoy Ubuntu!

---

