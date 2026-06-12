---
title: "Install/startup help"
date: 2008-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by CarollaTony on 2008-04-07
Long time user and programmer of MS/IBM/Commodore systems, but brand spankin' new Linux user here.  I have heard so much about Ubuntu on all the blogs, I thought I would see what all the hype is about!  :KS

So I burned the iso for 7.10, and here's what is happening.  When I boot from the CD, I get a menu screen that has several choices.  I have tried the first two, "Start or Install" and "Start in graphics safe mode".  What happens is my screen says something at the bottom like "kernel is alive", and another line that is gone before I can read it (I am almost 40).  Then my screen goes blank, the CD and hard drive tick away for awhile, then nothing.  Nothing on the screen, hitting keys does nothing, pressing Ctrl-Alt-Delete gives me a beep repeatedly, then ejects the CD, and reboots.  The Safe Mode option does the same thing, but starts beeping constantly.  

I tried the menu option to "Check CD for Defects", and it does the same thing but turns the CD light on for a lot longer.  I presume it is checking the CD for defects, but with no display or prompt, I don't know if it works.  

So I could use some help--just a hand up to get this bad boy installed.  TIA!

---

### Post by Belak on 2008-04-07
Are you using the Alternate Install CD, or the Desktop Install CD?

---

### Post by CarollaTony on 2008-04-07
I am using the desktop install.  I will try the text-based alternate one.  Thanks!

---

### Post by Belak on 2008-04-07
Yep.
No problem.
I usually use the text based alternate cd because it gives you more control.
I also usually make a separate home partition so it's easier to upgrade (You can keep all or your personal data between installs - if you have to upgrade or do a clean install)

---

### Post by CarollaTony on 2008-04-07
The install went great.  I was able to install on an empty partition, chose three supported screen resolutions, chose my language, my time zone, everything!  Now, when I boot... same thing.  
Grub--> select Ubuntu
Kernel alive... Kernel sumpm sumpm mapping 100000000... 
Blank screen.  10 minutes later...  Blank screen.  

I have tweaked and hacked at OS's for awhile now, but I have no options.  If the screen is blank, things kinda stop right there.  Are there any "magic" keystrokes that re-init the disp?  or can I start in command line mode (which I know nothing about linux commands, but at least I can see something on the screen!)

TIA

---

### Post by CarollaTony on 2008-04-07
Okay, I have scrounged around the internet, and actually seen the desktop.  It looks pretty sweet.  

Here is what I _can_ do.  I choose 'recovery mode' from Grub, and at the prompt, type 'startx'.  Poof, up comes a moire patterned desktop, telling me that I am started as a priveliged user (my wife does have royal blood), I choose continue, and voila!  I am at the desktop.  It feels like windows safe mode though, because the network doesn't work (which was set up during installation).  Also, I chose which model of monitor I had, but when I went into 'Screen Resolutions' afterward, there were no resolutions listed.  

Oh and the biggie:  I can't seem to shut down/restart normally.  I click the power button, and all buttons on the desktop become unresponsive.  I can move the mouse, but nothing is clickable.  But it never shuts down.  

Oh I also found an article that said to type in 'sudo apt-get install ubuntu-desktop', so I tried that, but it said that basically, there was no upgrade done.  

I will keep tweaking this sucker until I get it, but any help would be greatly appreciated.

---

### Post by ahickey on 2008-04-08
I had something similar and it was my graphics card was driving the display at a refresh rate that it could not support.  

Try [ctrl]-[alt]-[+] on the numeric key pad.
This will change the resolution of the screen.

I changed to 1024x768 from a native of 1280x1024.
The installed the restricted drivers for my Nvidia card. 
This sorted it out.

If after doing the restricted drivers it is still not owrking then a minor edit to the xorg.conf should fix it.

Open Terminal
cd /etc/X11
sudo cp xorg.conf xorg.conf.backup
vi xorg.conf

Find the display section and the horizontal and vertical refresh rates.
I (becuase I didn't know any better) dropped the max vertical refresh rate by 10 and dropped the max horizontal refresh rate by 20.

Then went back and changed the screen resolution to 1280x1024, tested and kept the new settings.

I hope this helps.



This sorted it for me.

---

### Post by CarollaTony on 2008-04-08
Thanks.  

I think I have something else wrong though.  When I start up, and I get to the blank screen, ctrl alt + doesn't do anything visible.  I have also tried ctrl-alt-f1 and alt-f1.  

When I boot into recovery mode, I can't seem to CD to the \etc\X11 folder.  It says that folder doesn't exist.  When I type 'dir', I have a short list of folders, like:

Documents
Desktop
others...

Is there a way I can edit the boot entry in grub to just boot to a command line?

---

### Post by CarollaTony on 2008-04-08
I'M IN!!!  Posting this from UBUNTU 7.10!!!  Thanks to all for the advice.  

I had to mish-mosh a few posts around the 'net to find the following solution:

1)  at the GRUB screen, type an [e] to edit the boot commands
2)  arrow down to the kernel line, and press [e] to edit it
3)  change the word splash to nosplash and press [enter]
4) press [b] to boot

VOILA!  Now, I am not sure the change was perm, and this would be a pain to have to do at every boot, so my question now is, how do I make this option permanent?

---

### Post by gonesolo on 2008-04-08
to make the change permanent do the following.

open a console and

> su nano /boot/grub/menu.lst

now scroll down till you find the line that loads your os (it'll be one of the lines without the #)

delete the word SPLASH off the end of the line.

press CTRL+X

Press Y to save and save as menu.lst.

reboot and you should be sorted.

Sorry I can't be too descriptive i'm in work and my Ubuntu machine is at home.

---

### Post by CarollaTony on 2008-04-08
Okay.  Next question.  I enabled the 'restricted driver' for my NVidia graphics card (8800), and was able to get full res only Samsung 226bw.  Sweet.  

Then I read a post on how to use both of my monitors (both hooked up to my 8800).  It said to type in 'sudo apt-get install nvidia-glx'.  A package was installed, and now when I boot into X, I get a low-res warning saying that drivers couldn't be found, and that I was in safe graphics mode.  No matter what I do from there, whether I config a supported res, or click shut down, I get a blank screen.  

I am just about to reload, but I was hoping somebody knows a way to easily undo what 'sudo apt-get install nvidia-glx' did.

---

