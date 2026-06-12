---
title: "blank screen after cd boot"
date: 2006-06-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by kk0425 on 2006-06-05
Im new at linux and trying distros. I've been trying to boot from a breezy badger live CD. It looks like everying installs properly but everytime it boots I get a blank screen. Any help would be appreciated since im trying to move away from M$. And I will try the latest distro of ubuntu. Thanx in advance.
My system specs are:

AMD Athlon 64 +3200
512MB DDR SDRAM
128MB ATI Radeon Xpress 200M

---

### Post by Patsoe on 2006-06-06
Although the Breezy LiveCD can be persuaded to work with the Radeon 200M, it is rather tedious, and since the Dapper LiveCD has been released now - which I could get running with much less effort - I would suggest that you get that.

Should you find that that boots very slowly (say, over 5 minutes), then you might add these boot options: "noapic nolapic" (the LiveCD boot screen for Dapper allows you to edit the boot parameters by hitting F6). I'm not sure if this is a problem that all Radeon Xpress chipsets have...

---

### Post by kahsheung on 2006-06-06
Hi, I'm having the same problem but i'm already using Dapper Drake 6.06 LTS.

My spec:
1. AMD64 processor
2. ATI X800 pro
3. Dell 19" ultrasharp connected thru DVI

Tried starting in safe graphic mode. No help there..screen remains blank after hearing the start up sound.

Please help, this is my first foray into the linux world.

---

### Post by firetux on 2006-06-06
The following should work on breezy and dapper.

When the screen is blank do ctrl+alt+f1
then login and type
```
sudo pico /etc/X11/xorg.conf
```
in the file find a part that says
something like
```
Section "Device"
Identifier "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

```
and add one line ( Option "MonitorLayout" "LVDS,Auto" ) in that part:
```
Section "Device"
Identifier "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
Driver "ati"
BusID "PCI:1:0:0"
Option "MonitorLayout" "LVDS,Auto"
EndSection
```


then exit (ctrl+x) and save the file.
restart gnome by doying:
```
sudo /etc/init.d/gdm restart
```

Please report back if it worked for you, other people will be reading this too!

---

### Post by Thomas,Bakker on 2006-06-06
When my dapper live cd booted (64bits) i also got a blank screen.
after a few tries i removed my network cable and booted again....... no more problems. i logged in browsed a bit and plugged in my network cable.
Havent had the problem again.

---

### Post by kahsheung on 2006-06-07
just out of curiousity...what does

**Option "MonitorLayout" "LVDS,Auto"**

do??

Will give it a go later...thanks..

---

### Post by firetux on 2006-06-07
[QUOTE=kahsheung]just out of curiousity...what does

**Option "MonitorLayout" "LVDS,Auto"**

do??

Will give it a go later...thanks..[/QUOTE]

What it does? It works!

serious: I don't know it either, you might try to find some documentation about xorg.conf.
Lvds is some interface to get a signal to the monitor. see [here]("http://www.okidensen.co.jp/english/catalog/lvdsmi.htm")

---

### Post by Patsoe on 2006-06-07
[QUOTE=firetux]What it does? It works!

serious: I don't know it either, you might try to find some documentation about xorg.conf.
Lvds is some interface to get a signal to the monitor. see [here]("http://www.okidensen.co.jp/english/catalog/lvdsmi.htm")[/QUOTE]

It tells the X server that the first display is a laptop panel, and that it has to try and look for a second (external) display on the second connection.

---

### Post by WidowMkr on 2006-06-07
Same problem with A64 3200+ with nvidia 6600gt  and LG 1710s (LCD). Try the options in xorg.conf and when I try to restart gnome give me Stopping Gnome Ok, restarting Gnome Fail... :(

I try with the VGA standard out and DVI of my VGA card.

I´m looking for a solution in the forum and read too much people with different hardware configurations with the same problem... That´s not happend in betas?!?!?!?!?. I don´t understand how can ubuntu people can´t see the problem before the final release.

---

### Post by Stoffel on 2006-06-08
I'm having a similar problem on both the x64 and the i368 distro's.

When I try to install Ubuntu 6.06 I get the welcome screen (messed up, I don't see the keys on the bottom ( F1, F2, ...)). When I click on a link (start or install ubuntu, start in safe graphics mode, ...) I see one more message (something with compiling kernel I think) and then my screen goes blank.

My Specs:
AMD Athlon 64 +3200
1512MB DDR SDRAM
ATI Radeon X800XT ViVo

Any help would be appreciated

---

### Post by firetux on 2006-06-08
The only thing you can try is to use the alternate cd and install from that.
Unless someone else has an idea how to fix this?

---

### Post by Gelupah on 2006-06-08
I have the same (or a very similar problem):

Breezy used to run fine, I had it installed. Since I updated to dapper, it wouldn't boot properly. Ubuntu would load up most things, and then the screen would go blank. The screen stays on, so it's receiving some kind of signal. 

I tried formatting, tried the live CD, and I get the same problem. I have also tried the graphical safe mode - which also loads up blank.

I have the following specs:

A64, asus K8V SE
Radeon 9800 pro
SATA HDs, 1Gb ram...

Any ideas would be much appreciated!

Cheers

---

### Post by firetux on 2006-06-08
Use the alternate cd to install, that should go fine. Then, when you get the blank screen again on login, you do what's described in the #4 post on this thread. Or you install the using the alternate cd but you just install the ati propietary drivers(sudo apt-get install xorg-driver-fglrx).

---

### Post by Gelupah on 2006-06-08
I assume the "ctrl+alt+f1" will get the login screen to show up then?! Does it reset graphical settings?

---

### Post by firetux on 2006-06-08
Ctrl-alt-F1 puts you in text mode, there your screen does display something, then you can login and make the neccesary changes.

Then (at the end) you restart gnome and you should get to see the (graphical) login.

---

### Post by psykotron on 2006-06-08
[QUOTE=WidowMkr]Same problem with A64 3200+ with nvidia 6600gt  and LG 1710s (LCD). Try the options in xorg.conf and when I try to restart gnome give me Stopping Gnome Ok, restarting Gnome Fail... :(

I try with the VGA standard out and DVI of my VGA card.

I´m looking for a solution in the forum and read too much people with different hardware configurations with the same problem... That´s not happend in betas?!?!?!?!?. I don´t understand how can ubuntu people can´t see the problem before the final release.[/QUOTE]


Well I'm having the same problem and I got the "Stopping GDM Ok, Restarting GDM Fail"
something is wrong with being able to restart gdm, so try:
sudo /etc/init.d/gdm stop
sudo killall gdm
sudo /etc/init.d/gdm start

It didn't fix it for my system, maybe it will help you.
Good luck

---

### Post by tibro on 2006-06-08
hi!
i have exactly the same problem here!
i have amd64 3200+ with nforce 4 chipset, x800xt (pci-e) vga.

downloaded 6.06 AMD64 desktop install CD
ran the 'check disk' option after CD boot - ok

start normal boot...
loading fine, up to a point loading 'X Server' when booting breaks with an error console screen - but no information about the nature of the encountered problem is displayed

tried boot "display safe mode"....
I observe that at about a very similar point of time, the display switches from the boot screen to application mode, where it stays black
Please help me, i'd like to use the new ubuntu!

---

### Post by Stoffel on 2006-06-08
[QUOTE=firetux]The only thing you can try is to use the alternate cd and install from that.
Unless someone else has an idea how to fix this?[/QUOTE]

I tried it, didn't work :(
Even text mode didn't work.


Isn't anyone else having the same problems?

---

### Post by firetux on 2006-06-08
If the desktop-cd doesn't work, use the alternate cd and install using that.

---

### Post by firetux on 2006-06-08
[QUOTE=Stoffel]I tried it, didn't work :(
Even text mode didn't work.[/QUOTE]

Define "didn't work", I cant help you if I don't get any error messages or a description of what went wrong.

---

### Post by Stoffel on 2006-06-09
Same thing as the first time.

I start with the cd.  I get the menu (messed up, can't see the keys on the bottom (F1, F2, ...).
When I start text-mode or the normal mode this is what happens:
First I see a progressbar filling.
Then I get the following message:
[i]Uncompressing Linux ... done
Booting Kernel[/i]

And then my screen goes black and I get the message "No Support" from my screen.

---

### Post by Patsoe on 2006-06-09
[QUOTE=Stoffel]
I start with the cd.  I get the menu (messed up, can't see the keys on the bottom (F1, F2, ...).
When I start text-mode or the normal mode this is what happens:
First I see a progressbar filling.
Then I get the following message:
[i]Uncompressing Linux ... done
Booting Kernel[/i]

And then my screen goes black and I get the message "No Support" from my screen.[/QUOTE]

I used to have similar behaviour when installing Breezy. It had to do with the fancy text-mode that is used by default to display the boot messages with an ubuntu logo. (Not relevant to you: for some reason it does work for me in Dapper)

On the alternate install CD, you can edit the boot options and put in this option at the end of the line: ```
debian-installer/framebuffer=false
```

This removes all the cool splash screens at boot, but at least you get to see some boot messages :)
You don't have to memorize that line by the way (unless they changed the help menu's - I don't have the Dapper alternate disc); you can hit several F-buttons to see some help, and this particular option is mentioned somewhere under F4 or F5 I think. So you can copy it from there :)

---

### Post by Stoffel on 2006-06-09
Thank you very much
That did the trick!!

---

### Post by shanepardue on 2006-06-09
this is the same problem i've had. is it just a coincidence that they are all 64-bit processors?

i'll have to check out that code when i get a chance. hopefully that will fix my problem.

---

### Post by Gelupah on 2006-06-10
> On the alternate install CD, you can edit the boot options and put in this option at the end of the line:
Code:

debian-installer/framebuffer=false

I am sorry but I am lost here. I tried Ctrl Alt F1 and nothing happens. I tried it during booting, and after (when the screen is left blank).

I downloaded the alternate CD but the installer keeps crashing. How do I add the command? I tried exiting the GUI (Esc), and in text mode type "install /framebuffer=false" - But this is probably what gets it to crash. How do I edit boot options?

This is strange as breezy runs fine, but when I update it to dapper, i can't use it! :(

I'm still learning a lot about all of this, so I appreciate your time and comments!

Cheers

---

### Post by shanepardue on 2006-06-10
yeah, that didn't help me either.

---

### Post by Patsoe on 2006-06-10
[QUOTE=Gelupah]I am sorry but I am lost here. I tried Ctrl Alt F1 and nothing happens. I tried it during booting, and after (when the screen is left blank).

I downloaded the alternate CD but the installer keeps crashing. How do I add the command? I tried exiting the GUI (Esc), and in text mode type "install /framebuffer=false" - But this is probably what gets it to crash. How do I edit boot options?

This is strange as breezy runs fine, but when I update it to dapper, i can't use it! :(

I'm still learning a lot about all of this, so I appreciate your time and comments!

Cheers[/QUOTE]

It is a boot option only - you can't pass it to a running system. Also, it applies only to the alternate CD - the LiveCD doesn't use the debian-installer anymore.

You have to specify these flags in the very first screen that appears when booting from the CD - that is, before the installer loads its kernel.

I hope Stoffel can give you a more specific walkthrough, I did this half a year ago, and don't really remember what the boot screens looked like :)

---

### Post by Stoffel on 2006-06-11
[QUOTE=Gelupah]I am sorry but I am lost here. I tried Ctrl Alt F1 and nothing happens. I tried it during booting, and after (when the screen is left blank).

I downloaded the alternate CD but the installer keeps crashing. How do I add the command? I tried exiting the GUI (Esc), and in text mode type "install /framebuffer=false" - But this is probably what gets it to crash. How do I edit boot options?

This is strange as breezy runs fine, but when I update it to dapper, i can't use it! :(

I'm still learning a lot about all of this, so I appreciate your time and comments!

Cheers[/QUOTE]
I am not sure if you see the whole screen, or like me only a part of it.  On the bottom there are some key's you can press. 

I see you're french so you probably would prefer azerty. Press **F3** and select your nationality. 

Then press **F6**.  If you see nothing appearing, adjust your screen (move your view to the bottom) so you can see what you type. Then just add this **debian-installer/framebuffer=false** and press enter

I hope this helps

---

### Post by Gelupah on 2006-06-11
> Then press F6. If you see nothing appearing, adjust your screen (move your view to the bottom) so you can see what you type. Then just add this debian-installer/framebuffer=false and press enter

Thanks! I have finally installed it with the framebuffer, but sadly my ubuntu still won't load up! Same problem: all the things load up (without graphics now), but then the whole thing locks up with a blank screen. I tried the safe mode, which eventually comes up with "root@gelupah:~# ". However the following message shows up during the loading:

"There are differences between boot-sector & its backup. Differences: (offset: original/backup)
71:46/00, [etc...]
Not automatically fixing this."

Could this be related? I even tried deleting all my partitions, re-creating some, re-installing, etc... I have WinXP also installed . Once again - Breezy installs and runs fine :(

Thanks for your help!

---

### Post by Stoffel on 2006-06-11
After installing Ubuntu, the graphical interface wouldn't work so I had to the ati drivers manually.

I got my info from here: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
If this is related to your problem, maybe, don't know.

---

### Post by Gelupah on 2006-06-11
I edited the file  /etc/X11/xorg.conf and replaced  "ATI" by "vesa" - this finally allowed me to boot up! Will have to work on ATI drivers from the link you pointed out.

Thanks very much!

---

### Post by kk0425 on 2006-06-12
thanx for all the help. I didnt think i would get so many replies. I still need to try the new dapper drake boot disk but im glad to see that im not the only one with this problem.

And here is more information about the problem:
I dont get any sound from the boot,
the only way to turn off my labtop it to hold the pwr button for 5 seconds,
I cant eject the cd,
like i said in my first post i see the list of stuff saying that it passed or failed (the only thing i see failing is the test to the ubuntu server)

I apoligize if that lack of info caused any confusion but it sounds like your answers might help.

---

### Post by togume on 2006-06-16
you should also try changing the "ati" driver for the "radeon" driver in the xorg.conf, this kinda worked for me...

---

### Post by Ocaña on 2006-06-22
In a hurry right now - but I feel the urge to post

Hi Ubuntu community. My name is Leonardo Ocaña, I'm Brazillian, and this is my first post. I'm also completely new to Linux, but I'm getting help from this forum and a bunch of friends.

I could not install Ubuntu on my machine, at first.
It's an amd64 system, on a VIA chipset mobo, with an ATI radeon X800PRO.

The amd64 desktop CD would always give me a blank screen. I could manage through that in many ways, not going much further though.

To shorten a long long story, I could manage to install Ubuntu Dapper 6.06 LTS in my system by *downloading the alternate CD*, and what *really* did the trick for me was **commenting the glx line** of /etc/X11/xorg.conf. Without doing that, I would not get to the login screen by any means (not even by switching ati to vesa - that did not work at all, here).

Also, I might mention I'm now with both amd64 and i386 versions installed (not to mention my WinXP), because I won't find 64 drivers for my Agere Lucent Windmodem that soon (besides not being able to install it to my 32bit Ubuntu yet - *that's* another *long long story*, with no happy ending up to date)

-- When not in such a hurry, I might post properly.

I hope this might help someone.
Thanks for all the help!

***Leonardo Ocaña***

---

### Post by willd on 2006-08-12
Option "MonitorLayout" "LVDS,Auto"

This worked for me thanks!

---

### Post by dbw on 2006-08-21
I had a similar problem (also using x64 distro). The GUI live cd crashes at boot, and even if I install using the no-GUI alternative CD (text only), X initially would not start.  I noticed that everything worked fine when I used a CRT instead of my 20" widescreen LCD.

notes: I am using an nvidia 6600 GPU, and 4600 amd x2
       I tried both dvi and vga heads of the graphics card, same results
       I have tried open and closed source nvidia drivers as well as the vesa driver.

**SOLUTION:**
 Install from the alternate text-cd, or using a CRT
 be sure to back up your xorg.conf!
 

**Booting to GUI:**
  noticed that autodetect of hardware leads to adding Wacom tablet to my xorg.  I do not have a Tablet - when I removed these sections from my xorg, I was able to boot to the gdm.  Note that most solutions posted on the forums will suggest that you do x-reconfigure.  This did NOT work for me, as it adds the frelling Wacom sections to my xorg again.

**Decent Resolution:**
  ```
gtf 1680 1050 60
```
    this will produce xorg mode information for a 1680x1050 resolution screen at 60hz.  Put the output in the "Monitor" section of your xorg, and be sure to put a matching entry in the "Screen" section.  This is documented more fully [here]("https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration").
  In my case, this gave me a beautiful gdm.  However, when I entered xfce, the resolution changed dramatically, and everything got all staticy.  Fluxbox does not create this problem, and I prefer it anyway.  However, I cannot use any xfce gui tools, or else my screen goes to hell again.  If y'all have any ideas about this, that would be lovely.


anyhow, there's my 4 cents, hope it's useful for someone.

---

