---
title: "Power Book 15&quot; G4 667"
date: 2006-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by tymiles on 2006-01-27
When I install or even run the live CD of 5.10 or the new Dapper RC3 I just get a white screen that looks like burn in. 

Anyone seen this problem, anyone have an idea how I might get Ubuntu to work on this powerbook!

Thanks everyone for your help!

---

### Post by tymiles on 2006-01-29
Not even a shot in the dark on this one? I guess its back to the Mac OS for me? :( 

Ouch..

---

### Post by linear on 2006-01-29
A shot in the dark? Sure. Possible problem in /etc/X11/xorg.conf.

Can you get to a shell by typing ctrl-opt-F1? Try to reconfigure with:

**sudo dpkg-reconfigure xserver-xorg**

---

### Post by tymiles on 2006-01-29
Thanks for your shot. But can't get to command prompt, all I get is a flicker on the screen using Ctrl opt f1. 

Oh well. I tried. LOL! 

Thanks for the help. :-)

---

### Post by koni2005 on 2006-02-04
Same Problem here - TiBook 1Ghz etc.

Check other posts....

At least it sounds like my problem:

shortly after yaboot, the screen turns black - with two lines of weird graphics - middle and lower part of the screen. One can still read the ascii letters on the left side, but the longer the appearent boot process takes, the weirder the color in the two lines gets. I can even make out the blue color of the installer text window asking wich language I want (k)ununtu to be installed in...

Please help me - until a few days ago I ubuntu was working fine - now I can't even reinstall it - because I get that weird screen.

P.S.

install video=ofonly works for a reeinstall, but I only get a black screen instead of the login window. Any suggestions here????

Thanks again...

---

### Post by N8K99 on 2006-02-04
I believe using Command-Option-F-O gives you a 'Bios' environment when you turn on the computer. I did this a couple of times just to get the CD to be recognized, no adjustments, just exercised the option then allowed the computer to boot from the cd by press C after selecting 'Restart' from the OS X login splash screen. Now, I am running only Breezy Badger - yup I wiped OS X off my computer (TiBook G4.) I have both KDE and GNOME environments installed, and am really enjoying the process of working with Linux on PPC.

---

### Post by koni2005 on 2006-02-05
Thanks for the tip - although the problem seems to be somewhere else.

I tried installing Ubuntu 5.10 again from the DVD and in expert mode it workes fine everytime - but after the first part of the installation - when the DVD is extracted and the system reboots to finish the installation, the display weirdnes starts again.

After reboot, yaboot starts with no problems, so I hit l for linux boot.
then I am prompted again to select a device - as I want to boot from the standard device, I just hit return and the boot process starts.

There are some ascii outputs - whatever they mean - and after that, the display crashes and I only get those two weird lines that look kind of like a screen burn with some parts of the ascii letters still eligible.

The boot process itself seems to work fine - again I can blindly log in and hear the ubuntu sound.

CTRL-OPTION-F1 does not help, as I probably get into an open shell, but I can't make anything out as the display is still fucked up - so I can't reconfigure the xserver as mentioned above.

Is there any way I can - in yaboot - make ubuntu boot up with the most basic graphic's driver - and not the one "it" thinks is right for my card?

Thanks...

---

### Post by koni2005 on 2006-02-08
Well, I tried rebooting again - and at the second try it worked!
Of course the next try wasn't succesfull anymore - and I ended up with those weird artifacts again.

But now I know exactly were the display crashes: If it does not crash, there is a message saying something like:

radeonfb: Invalid ROM signature 0 should be 0xaa55

although the numbers are different, I guess...

Does this ring a bell with Anybody?

---

### Post by Lanrond on 2006-02-08
[QUOTE=koni2005]But now I know exactly were the display crashes: If it does not crash, there is a message saying something like:

radeonfb: Invalid ROM signature 0 should be 0xaa55

although the numbers are different, I guess...

Does this ring a bell with Anybody?[/QUOTE]

ding ding ding. ;) 

I get a very similar message when I boot Ubuntu on my iMac.
Damn those ATI video card! 
Fortunately the only set back I have is that (despite all the hints I found on this forum and tried) I can only work with the 1024x768 75Hz resolution.
Have you tried the *famous* xorg.conf edinting?

---

### Post by koni2005 on 2006-02-08
Well, the infamous xorg.conig does not help at all - as I am stuck with a malfunctioning video-card and thus no usable display at all - not even ascii mode - i.e. I can´t make out a thing I would type even if I could try to reconfigure xorg.

Well, as for the damn ATI video cards in the PPC (K)Ubuntu distribs: the xorg drivers used to work fine for me on my TiBook with ATI Readeon 9000 Mobility. I even had support for a resolution of 1280x856 until this weird problem occured out of nowhere. Then sometimes I only got a resolution of 800x600 - again out of nowhere.

Is there any chance that the problem could have to do with any Mac OS X update? Maybe the update from 10.4.3 to 10.4.4 made somekind of change somewhere in the inner workings of my laptop. Under 10.4.3 kubuntu worked perfectly, and even under 10.4.4 it worked for a while until above mentioned problems occured.

I´d really like to go back to kubuntu, but have no idea what to do anymore.

As said above: a fresh install does not solve the problem...

---

### Post by tymiles on 2006-04-21
This machine has ATY,RageM6 card. (I know Aty looks like ATI but I copied how it was written in the system profiler in Mac OS) 

I would love to get daper working on this machine but no dice. 

Maybe someone knows something I don't! 

Help! :-)

---

### Post by RichardHaads on 2006-12-31
You know it is not often I find usefull stuff...  I have been researching this for a while, your site raises some valid points I added your page to my bookmarks and hope to see more interesting comments in the future.Anyone got their hands on a [ Zune MP3 Player](http://whatisazune.confusionreigns.com/index.pl) yet? 
How do they compare to a Nano?

---

