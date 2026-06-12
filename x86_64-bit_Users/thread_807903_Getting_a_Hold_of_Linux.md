---
title: "Getting a Hold of Linux"
date: 2008-05-26
forum: x86 64-bit Users
---

### Post by FirstTimeMan on 2008-05-26
Hi

I'm new to Linux, I'm running Ubuntu 8.0.4.
I am mainly a windows user and decided to try linux cuz I've been hearing a lot of talks about it. So I downloaded Ubuntu and installed it.
The problem is, my video drivers don't work well.
I have an integrated 256mb nvidia card, which I downloaded the drivers for. When I installed the drivers, I was limited to 640x480 screem resolution.
After much fussing I managed to deactivate the drivers and max screen res went up to 800x600,.

Still though, when I try to browse and tweak the system to my liking, I can't do that, I can open programs, but when I make changes and would like to clcik 'ok' at the bottom of the windows, I can't because the screen is stuffed, the resolution is too low.

Another major problem I face, is my mouse, which often freaks out big time, flailing across the screen and clicking things, closing and open programs. I would like to spend more time on linux, but I can't do anything much because the mouse really annoys me.

My system is dual-booted with XP pro and Linux Ubuntu.
Its a custom built pc.


ps,
I've been doing a lot of reading before I post, but I see everyone talking about 'sudo' and run different drivers with it.

Is this a command line interface like in windows? because I cannot find a 'run' option anywhere.

I would really like to give linux a try and have it work for me.
Any help will be greatly accepted.

-FTM

---

### Post by philinux on 2008-05-26
2 things.

Goto system>admin>hardware drivers and make sure you're driver is active.

Second if that makes no difference. Then system>preferences>Main Menu.

Navigate to Others and tick Screens and Graphics.

Now use this menu item to change your res.

You might also try this forum as it's more active.
[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

---

### Post by FirstTimeMan on 2008-05-26
> **philinux said:**
> 2 things.

Goto system>admin>hardware drivers and make sure you're driver is active.
I had to de activate the drivers so I could get a better resolution.



> **philinux said:**
> Second if that makes no difference. Then system>preferences>Main Menu.

Navigate to Others and tick Screens and Graphics.

Now use this menu item to change your res.

I've selected Screens and Graphics but the options do not appear in the menu after wards.

---

### Post by Sef on 2008-05-26
> I've been doing a lot of reading before I post, but I see everyone talking about 'sudo' and run different drivers with it.

Is this a command line interface like in windows? because I cannot find a 'run' option anywhere.

[Sudo]("https://help.ubuntu.com/community/RootSudo") allows for temporary root access.

Could you be more specific about your graphics card?  That would help us fix your problem.

---

### Post by aaron.d on 2008-05-26
> **FirstTimeMan said:**
> Hi

I'm new to Linux, I'm running Ubuntu 8.0.4.
I am mainly a windows user and decided to try linux cuz I've been hearing a lot of talks about it. So I downloaded Ubuntu and installed it.
The problem is, my video drivers don't work well.
I have an integrated 256mb nvidia card, which I downloaded the drivers for. When I installed the drivers, I was limited to 640x480 screem resolution.
After much fussing I managed to deactivate the drivers and max screen res went up to 800x600,.

Still though, when I try to browse and tweak the system to my liking, I can't do that, I can open programs, but when I make changes and would like to clcik 'ok' at the bottom of the windows, I can't because the screen is stuffed, the resolution is too low.

Another major problem I face, is my mouse, which often freaks out big time, flailing across the screen and clicking things, closing and open programs. I would like to spend more time on linux, but I can't do anything much because the mouse really annoys me.

My system is dual-booted with XP pro and Linux Ubuntu.
Its a custom built pc.


ps,
I've been doing a lot of reading before I post, but I see everyone talking about 'sudo' and run different drivers with it.

Is this a command line interface like in windows? because I cannot find a 'run' option anywhere.

I would really like to give linux a try and have it work for me.
Any help will be greatly accepted.

-FTM

Welcome, glad you are trying Linux out. For a windows user, I believe you have made a good choice, as integration is a key feature of Ubuntu vs. other os'. Comming from years of slackware/SuSE/debian use, this is a great distro to use if you want a modern OS that lets you concentrate more on working and (a little) less on tweaking.

Let me say first though, you may want to try a 32bit version of any distro first, as the few caveats that apply to 64bit distros may turn you of Ubuntu or Linux in general.

That said, since you have it installed, lets give it a shot.

For your video/res issue, you may want to check this very thread out, as it seems to be nearly the same issue you are suffering:

[http://ubuntuforums.org/showthread.php?t=793769](http://ubuntuforums.org/showthread.php?t=793769)

A lot of the time here you will see actual commands, where are to be run straight from the command line interface (aka SHELL). To get a shell open, usually you want to find the "terminal" application. It might be also "console", "shell" or "term".

'sudo' itself, is a command that is used in conjunction with other commands run in a shell, and basically it tells the system to " run the following command(s) with root privileges". This gets rid of the need to "login" directly as root frequently, which can be a security concern.

---

### Post by aaron.d on 2008-05-26
I was just perusing one of me fave sites and remembered this old gem, which sums sudo up quite nicely:

[http://xkcd.com/149/](http://xkcd.com/149/)


:) enjoy

---

### Post by FirstTimeMan on 2008-05-26
> **aaron.d said:**
> I was just perusing one of me fave sites and remembered this old gem, which sums sudo up quite nicely:

[http://xkcd.com/149/](http://xkcd.com/149/)


:) enjoy




LOL that was funny.

---

### Post by FirstTimeMan on 2008-05-26
> **aaron.d said:**
> Welcome, glad you are trying Linux out. For a windows user, I believe you have made a good choice, as integration is a key feature of Ubuntu vs. other os'. Comming from years of slackware/SuSE/debian use, this is a great distro to use if you want a modern OS that lets you concentrate more on working and (a little) less on tweaking.

Let me say first though, you may want to try a 32bit version of any distro first, as the few caveats that apply to 64bit distros may turn you of Ubuntu or Linux in general.

That said, since you have it installed, lets give it a shot.

For your video/res issue, you may want to check this very thread out, as it seems to be nearly the same issue you are suffering:

[http://ubuntuforums.org/showthread.php?t=793769](http://ubuntuforums.org/showthread.php?t=793769)

A lot of the time here you will see actual commands, where are to be run straight from the command line interface (aka SHELL). To get a shell open, usually you want to find the "terminal" application. It might be also "console", "shell" or "term".

'sudo' itself, is a command that is used in conjunction with other commands run in a shell, and basically it tells the system to " run the following command(s) with root privileges". This gets rid of the need to "login" directly as root frequently, which can be a security concern.



Well I don't know exactly what version of Ubuntu i have (32 or 64bit).
All I know is that I have a 64bit processor (AMD Dual Core) hence the reason why I posted in 64bit forums, I thought that that might've helped.

I did the reading from rootsudo documentation you gave me, I'll say for the most part I understand what sudo is, but I still don't know how to access a terminal window where I can actually type in the command.

There are lots of places where it says just type this and type that and you'll get this or could do that.
But WHERE do I type?

ps,
My resolution problem is solved, I followed philinux's instructions again and I found out how to get my res up. thanks. Now am just interested in getting the window to type in commands.

---

### Post by pixel :-) on 2008-05-26
you whant gnome terminal[http://en.wikipedia.org/wiki/GNOME_Terminal]("http://en.wikipedia.org/wiki/GNOME_Terminal")

I'm in kde,in gnome i think you should find it somewhere in system,in the menu

when you opened your terminal copy paste 
uname -m

it will tell you what system you are on,"x86_64" you are in 64bit, "x86" you are in 32bit.

---

### Post by aaron.d on 2008-05-26
I think by default, in 8.04 Gnome terminal is located in Applications > accessories> terminal

---

### Post by soxs on 2008-05-26
for resolution and other advanced stuff, you have to edit ```
/etc/X11/xorg.conf
``` via ```
sudo gedit /etc/X11/xorg.conf
``` or ```
sudo nano /etc/X11/xorg.conf
``` by hand or with scripts/programs. But there is A LOT to think of when editing that .conf file
```
... blah
Section "Screen"
        Identifier      "Screen0"
        Monitor         "AL1711"
        Device          "RadeonHD3870"
## go and search in your xorg.conf for the "Screen" Section and look what resolutions there are listed, they will later appear in your menu
## adjust them to your needs and save the file via <STRG><O> (nano) or <STRG><S> (gedit)
        SubSection "Display"
                Modes           "1280x1024"     "1024x768"      "800x600"       "640x480"
        EndSubSection
## end
        Defaultdepth    24
EndSection
...blah
```

Note: Plx post your onboard video chip, this is VERY important in order to get the correct driver working.
Note: This might all sound very nasty, but once done, you got the biggest stair to linux eternity :-P

---

### Post by FirstTimeMan on 2008-05-26
> **aaron.d said:**
> I think by default, in 8.04 Gnome terminal is located in Applications > accessories> terminal


Thanks, that was very helpful.
:)


> **pixel :-) said:**
> 

when you opened your terminal copy paste 
uname -m

it will tell you what system you are on,"x86_64" you are in 64bit, "x86" you are in 32bit.


I get "x86_64"

So I am 64bit then.


Thanks alot for your help guys.

Now I need to work on my sound.

---

### Post by soxs on 2008-05-26
What works does work so far with your soundcard?
You may use the search funtion: There are plenty tutrials gettinge pulseaudio to work.

---

