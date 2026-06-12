---
title: "New ATI drivers, Hangs on shutdown/reboot"
date: 2006-09-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by togume on 2006-09-30
Hello all, 

So, I finally got my dual monitor setup working well by installing the ATI drivers and performing an aticonfig command. The problem is that now it hangs whenever it exits X, wither shutting down, rebooting, or logging off.

If anyone has any ideas as to why this is happening please let me know. 

Also, if you know of any fancy tricks to get the error message (if any) when the screens go blanc (as in not recognized), I would love to hear it.

Thank you, 

Tomás

---

### Post by Kilz on 2006-09-30
> **togume said:**
> Hello all, 

So, I finally got my dual monitor setup working well by installing the ATI drivers and performing an aticonfig command. The problem is that now it hangs whenever it exits X, wither shutting down, rebooting, or logging off.

If anyone has any ideas as to why this is happening please let me know. 

Also, if you know of any fancy tricks to get the error message (if any) when the screens go blanc (as in not recognized), I would love to hear it.

Thank you, 

Tomás

That used to happen with the 8.25.18 drivers currently in the repositories. But changing to the 8.26.18 or up from ATI usualy solved it.

---

### Post by togume on 2006-10-01
I figured it would more than likely be a bug with the current drivers... I am using their current version 8.29.6 (hot off their website). I guess it's for a reason that they state not to install the drivers unless something is not working right...

---

### Post by 25an on 2006-10-15
Hi i had the same problem on Dapper i updated to the most resone version of fglrx but it did't help but i found a solution to it when searching for fglrx problems.
What i did was to edit in /etc/X11/xorg.conf file.
Comment the Load "extmod" and see if it helps.

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
#       Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

---

### Post by jkwarras on 2006-10-16
> **25an said:**
> 
Comment the Load "extmod" and see if it helps.

I'll give it a try. I hope it works. I'm having the same problem, even with newer versions of the drive that is supposed to fix this problem. Thanks for the tip.

---

### Post by jkwarras on 2006-10-16
> **jkwarras said:**
> I'll give it a try. I hope it works. I'm having the same problem, even with newer versions of the drive that is supposed to fix this problem. Thanks for the tip.
Damn, it doesn't work.

---

### Post by togume on 2006-10-30
I upgraded to Edgy... and I am still running into the same issue. I also submitted a bug report to ATI's developers (anyone want to make bets on whether they look at them?). 

Any more comments would be welcome.

---

### Post by hardyn on 2006-10-30
Ditto, 

Actually pretty disappointed with ubuntu this time round; and i was really excited about this release.

on shutdown i get amazing screen corruption and it loops in one tone of the shutdown music.  I get the same amazing display of color when the system attempts to suspend (the video corruption made me think it might be video related) both cases result in total lock up and the system must be powered down (which cant be good for the file system)

has anybody had any luck with the new drivers?  I would like to stop using my M$ partition and get back on the linux drive but i really need a fuctioning machine at this point too.

---

### Post by bioalchemist on 2006-10-30
I currently have Kubuntu 6.10 installed and it experiences this problem.  I have not installed ATI's drivers - it's a fresh install.  I also installed Ubuntu 6.10 and it does not hang on reboots at all.  Any ideas why?

---

### Post by hardyn on 2006-10-30
Still sucks with new driver :(

did you install the fglrx driver in both cases? luck?

is anybody else finding that edgy appears to be amazingly broken? more so than other releases?

thanks.

---

### Post by bioalchemist on 2006-10-30
@ hardyn:

I didn't install any drivers - it's using whatever it installed by default.  I'll check and see which one they're using.  Other than this issue, which only seems to effect Kubuntu, Ubuntu Edgy seems fine to me.

---

### Post by hardyn on 2006-10-31
i guess that really means that there is a problem with ATI and linux using the proprietary drivers... there has been much mention about it...  with the ATI and pentium M on my notebook Ubuntu is REALLY broken for me.

---

### Post by kuja on 2006-10-31
> **bioalchemist said:**
> @ hardyn:

I didn't install any drivers - it's using whatever it installed by default.  I'll check and see which one they're using.  Other than this issue, which only seems to effect Kubuntu, Ubuntu Edgy seems fine to me.
Which driver are you using? ati? radeon? vesa? Try switching amongst those and see if it yields any results to you.

---

### Post by markkun on 2006-11-01
I've had the same annoying problem. I usually do fresh install when ever new (k)ubuntu version comes, and every time it's the same problem.

Ati really should try to make a decent driver for Linux. Shutting down isn't the only problem Ati has in it's current drivers.

There has been quite a many config tweaks that have said to work, but none of them has..

Very Annoying! ](*,) 

I'll never recommend Ati to anyone anymore. I thought once it was good, but no more. If they can't make a decent driver for such a popular operating system, they are not worth the support.

---

### Post by togume on 2006-11-02
Good point. Let's just hope that they improve greatly now that AMD owns them. I've had great experiences with both cards; it just so happened that at the time I made my latest box I put an X800 into it... now I am paying for it. "Ok, let's use linux for a while... ok... time for windows... HARD RESET..."

Needless to say, my raptors are pretty angry at me. 

I will submit more bug reports shortly. As should we all.

---

### Post by togume on 2006-11-02
UuUuuUuu... New ati driver out as of 10/31/06... Hopefully that will be better?

---

### Post by jkwarras on 2006-11-04
For those hqving problems when shutting down, logging out, switching users, etc... with fglrx, yesterday I found a solution after heavy googling. It seems that the drivers have two problems:

- DVI plug (it doesn't work correctly)
Solution; plug the monitor via VGA.
- X hangs when shutting down, switching console, switching users, etc...
Solution: edit /boot/grub/menu.lst and remove splash from boot options and add vga=788.

Everything works fine after adding the vga boot parameters :)

---

### Post by jkwarras on 2006-11-05
Just FYI you don't have to remove the splash parameters from the boot options, just specify vga=788 (800x600 resolution).

---

### Post by hardyn on 2006-11-06
VGA=791 works too, and centres the screen.

THANKYOU THANKYOU THANKYOU jkwarras!!!

(moderator... maybe stickey this vga=XXX thing)

---

### Post by togume on 2006-11-06
... Did not work.
Can either of you please post your menu.lst?

Mine is as follows:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=7910895e-667e-4a43-ac63-e5aedc3254a7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

defoptions=vga=791

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=7910895e-667e-4a43-ac63-e5aedc3254a7 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=7910895e-667e-4a43-ac63-e5aedc3254a7 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Windows XP x64 Pro
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

```

Any bashing, comments, or suggestions are more than welcome!

---

### Post by ravenon on 2006-11-07
I had this problem running 32 bit Edgy on a 64 bit Turion, fglrx driver for X700 graphics. I edited /etc/gdm/gdm.conf-custom and added

[daemon]
AlwaysRestartServer=true

Now I have no problems on shutting down, logging out. In my case before this change, my screen would just go white and only the power button could save the day.
Curious point: this machine dual boots 64 bit Edgy and I have not had this problem there.

Addition: Fix one thing, break another. The laptop will now not suspend.

---

### Post by hardyn on 2006-11-07
kernel             /boot/vmlinuz-2.6.17-10-generic root=UUID=7910895e-667e-4a43-ac63-e5aedc3254a7 ro quiet splash [COLOR="Red"]vga=791[/COLOR]

---

### Post by jkwarras on 2006-11-07
> **hardyn said:**
> VGA=791 works too, and centres the screen.

THANKYOU THANKYOU THANKYOU jkwarras!!!

(moderator... maybe stickey this vga=XXX thing)
Nice to know it helped someone :) 

vga=791 doesn't work here, I can't go higher than 800x600.

Anyway, if someone knows how to make fglrx work with DVI it'll be nice.

---

### Post by hardyn on 2006-11-07
I don't have a DVI out or DVI device, so i wont be much help... But...

I think us ATI guys/gals basically have to hammer the ATI/AMD linux driver suggestion area with requests for some more features.  I would like to see a linux driver written with the same effort that they put in to the windows drivers. aiglx support, DVI support, TV in/out support, all the notebook power management stuff and a reasonable front end for the driver; fireglcontrol is a little sparse in features.

I really dont care that is stays closed source, but we really need something that works. There have got to be thousands of ATI/linux users out there, we might just have to raise our voices a little to get something rolling.  I respect that linux is only 5% of the computing community, so ATI is not going to spend money where they dont need to... lets give them a reason to spend money. (that or we all buy our next machines with nvidia graphics)

Arlen.

---

### Post by deviant on 2006-11-07
I`m having the same problem with my Kubntu machine. Seems like Ati has troubles providing good drivers for Linux.
Anyway, I`v try the vga=791 trick, but with no success.
My machine freezes right after de Kunbuntu splash screens appears when I try to shut it down or reboot it, and the only solution is to hit the power button.

---

### Post by hardyn on 2006-11-07
I had no trouble booting in... only with suspend and shutting down... it sounds like your problem is somewhat more serious and not all that similar to the above problems.

What board are you using?
does it work with "ati" or "radeon" drivers?
notebook or desktop?  if notebook, about how old?

arlen.

---

### Post by daradib on 2006-11-10
I think we should send messages to ATI requesting better support for the ATI Radeon. We should tell them to fix the problems with composite extensions (which I must disable for 3D support) and shutdown. They really should make better drivers. If not, they should make their drivers open source.
Link to contact ATI regarding Linux driver:
[http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web](http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web)

---

### Post by iLoVe.cF- on 2006-11-11
uhm.. i had no problems at with the new ati drivers.. 8.30.3 with my ati x800XL.. :p

But.. i got a damn ugly startup loading screen.. Grey and stuff.. is it supposed to be like it ? :S

---

### Post by carlgm on 2006-11-11
> 
They really should make better drivers. If not, **they should make their drivers open source.**


Sigh, not going to happen and to be honest I wouldn't want it happening either. ](*,)

---

### Post by daradib on 2006-11-12
> **iLoVe.cF- said:**
> uhm.. i had no problems at with the new ati drivers.. 8.30.3 with my ati x800XL.. :p

But.. i got a damn ugly startup loading screen.. Grey and stuff.. is it supposed to be like it ? :S

I also get an ugly startup screen. My boot up screen looks pretty bad. It's black and says Ubuntu (like normal boot up screen), but where it shows the status of booting there are several small lines and the status bar going to the right. It looks pretty ugly since the lines make black marks when the status bar passes through them. I don't know why I have this problem, but I didn't have it before I had Edgy.

---

### Post by jkwarras on 2006-11-12
The grey startup problem is specific Edgy 64 bits version. AFAIK it has nothing to do with the display driver you're using.

---

### Post by twstokes on 2006-11-17
My laptop (Inspiron 6000) has an ATI X300 and I've had this infamous problem too. What solved it for me was using the 8.26.18 drivers and uncommenting TerminateServer=true in /etc/kde3/kdm/kdmrc.

I even tried the latest drivers just to see if they have fixed the bug, but I still had problems. Rolling back to the 8.26.18 version works every single time for me. They are really stable too and I've never had a problem.

I just wanted to chime in for anyone that might want to try another combination to get theirs working.

---

### Post by pay on 2006-11-17
Ati really should get there Linux drivers up to scratch or make them opensource so then others can make them  up to scratch because they are quite pathetic right now.

---

