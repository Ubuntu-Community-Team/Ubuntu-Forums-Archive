---
title: "Breezy freezes wired mouse &amp; keyboard at first boot on new iMac G5"
date: 2005-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by jack&amp;mary on 2005-11-29
Hi Everyone,

                  We really are not "new" to this forum we have been visiting for several months, first when Ubuntu Breezy Preview came out and when Breezy Final was on the mirrors. After an easy but very successful full install of Breezy Preview on our (at the time) aproximately 4 (four) week old Apple iMac LCD 17" Flat Screen PC froze both wired keyboard and wired mouse at the first GUI Login. There didn't seem to be any answers or workarounds on the Forum at the time.

So we tried different wired keyboards and wired mice all brought the same results a frozen keyboard and mous at the GUI Login.

We then redownloaded Ubuntu Breezy  Preview from a different mirror and had the exact same results .... frozen keyboard and mouse. We again tried several different wired keyboards and wired mice all to no avail !
Nothing seemed to point to a solution anywhere.

BREEZY  5.10 FINAL

By this time Ubuntu Breezy Final was on the mirrors so we downloaded the iso, successfuly burn the image onto a cd and again had a trouble free install. 

At first boot up (post the install) to GUI Login and Desktop ... you guessed it !

The wired mouse and keyboard froze up at the GUI Login.

More wired keyboard and wired mice change overs .... still breezy froze the keyboard and mouse.

Redownloading Breezy Final from a different mirror resulted in exactly the same fault post a successful instal at the first GUI Login brownish screen !

Through the ime frames of Breezy Final problems we didn't see any solutions appear on the Forums, unfortunately.

We are open to suggestions, please post a reply if you have one of the new iMac G5 17"/20" LCD Flat Screen model G5's and have successfuly installed Breezy Preview or Breezy Final.

Thanks for any advice, workarounds and or solutions to the above.

KUBUNTU BREEZY FINAL HAS THE SAME PROBLEMS ON iMac G5's.

Kubuntu Breezy 5.10 Final freezes the mouse and keyboard as the KDE Desktop Components are loading two of our other family member under our roof have the same iMac as us.

We suggest and suspect a driver problem and or a wrong options in the kernel config(s) of both Ubuntu and Kubuntu.

                                                        regards,
                                                        jack&mary :p 

Merry Christmas and Happy New Year to all.

---

### Post by ssam on 2005-11-29
i have not seen this problem before, but it may be that your hardware is not support in the breezy kernel. breezy has a 2.6.12 kernel that was released in june 2005. you may find that a newer kernel would sort out your problems but this not very easy to do, especially if can't log in to the computer.

you could wait until the testing branch (dapper) gets a new kernel (2.6.15 is being pretested before it becomes the default dapper kernel). they will release "flight" cds every few weeks and you could try these, but remember the are beta versions so stuff will be broken.

maybe someone know a better way to fix your problem now.

---

### Post by jack&amp;mary on 2005-11-29
Hi ssam,
            Thanks a lot for yor speedy reply, looking at "anything" about mouse and keyboard freeze's with our forum search function it looks like a Video Driver problem. 

Our Video Graphics Chipset is the ATI 9600. Unfortunately we can't update anything because we don't have a working Ubuntu. We have everything crossed and will download the dapper drake dev iso now and try it.

Such a shame so many newer iMac G5 owners/users are left high and dry. Once again many thanks, you and your family have a really great festive season.

                                                    cheers,
                                                    jack, mary and family.:)

---

### Post by bwog on 2005-11-29
[http://ubuntuforums.org/showthread.php?t=76187](http://ubuntuforums.org/showthread.php?t=76187) seems to have a working imac g5

---

### Post by ssam on 2005-11-29
does crtl+alt+f1 do anything when it freezes up?

---

### Post by jack&amp;mary on 2005-11-29
[QUOTE=ssam]does crtl+alt+f1 do anything when it freezes up?[/QUOTE]
Reply to ssam, 
        No, it's a total "lockup"
We are currently half way through a dapper download we'll see how it goes.

                                           jack, mary and family.

---

### Post by jack&amp;mary on 2005-11-29
[QUOTE=bwog][http://ubuntuforums.org/showthread.php?t=76187](http://ubuntuforums.org/showthread.php?t=76187) seems to have a working imac g5[/QUOTE]
Hi,
    Thanks for the reply, yep we spotted that post some time back thats an earlier (older) iMac than ours. I think that model my have the nVida Graphics Chipset, ours has the new ATI 9600 Chipset, (Revision 2) not sure if it has the older PMU Chip or the newer SMU chip on board, we have and it may not have the newer SATA hdd controller. the SMU Chip involves firewire and or usb and or timings and or thermo fan control, many are still reverse engineering the chip as apple aren't that forthcomeing about their board and chip revisions and how to access them. But that always been Apples stance. As they are a monolopy it probably will never change as far as tech stuff to open source is concerned re their on board chipsets.

                                                     regards and thanks

                                                     jack, mary and family.

---

### Post by pechang on 2005-12-13
Hi Just got a iMac G5 2.0G and went to install ubunto on in. I am a Debain user
and this seemed the logical best fit. But. I am getting the same error.
i.e. When I boot up it gets to the login screen then freezed. ctlAltF1 doesn't help.

I booted the maching in Single this sort of worked but I have a second problem when I press the tab key the machine freezed also.

Any solution would be nice

---

### Post by Achille on 2006-01-08
I don't have a iMac G5 myself. But I found this hint:

[http://www.suseforums.net/index.php?showtopic=19034](http://www.suseforums.net/index.php?showtopic=19034)

---

### Post by ctt1wbw on 2006-01-08
I have a G5 iMac as well, 17" rev b model.  I tried the live cd of Ubuntu Breezy and Dapper, and the live cd of Kubuntu.  None worked, same problem.  Now I'm scared to try to install anything on this computer.  I am thinking of putting it up for sale!  :smile:

---

### Post by ctt1wbw on 2006-01-09
Has anyone tried Yellow Dog on this G5 iMac?  They tout their distro as the one best suited for a G5, so I was wondering if anyone had any success here.

---

### Post by Achille on 2006-01-09
Did you try this solution?

[http://ubuntuforums.org/showthread.php?t=108600](http://ubuntuforums.org/showthread.php?t=108600)

It should work!

---

### Post by ctt1wbw on 2006-01-09
Well, I read that several times in the past, and I can't get to a console to rename the artsd sound daemon.  My system freezes at the brown screen and no key combo works to get there.  I'm confuzzled as heck here.

---

### Post by Achille on 2006-01-09
This solution works for Kubuntu (and not Ubuntu).

I customized a Breezy Kubuntu liveCD (moving /usr/bin/artsd to /usr/bin/bakartsd) and tried it this morning. And it worked!

Try to install Kubuntu Dapper flight2.

I suppose that for Ubuntu you have to do a similar operation (perhaps with esd, I don't know).

---

### Post by ctt1wbw on 2006-01-09
I already tried the Kubuntu Live cd and Dapper cd as well.  Both times I got to the brown screen, or blue screen as it were, and the keyboard and mouse froze up.

What do I do to get to a terminal window and when do I do it?

---

### Post by Achille on 2006-01-09
I suppose that you can get the login screen like this:

[http://www.kubuntu.org/docs/kquickguide/C/ch02.html#sect-login](http://www.kubuntu.org/docs/kquickguide/C/ch02.html#sect-login)

Then, according to Jack, you have to click on Session Type and select failsafe for getting a terminal.

Otherwise, hit simultaneousy Ctrl+Alt+F2 (or Ctrl+Alt+Apple+F2 or something like that). You should get a black screen with
login:
Enter your login and your password.

Then type:
sudo mv /usr/bin/artsd /usr/bin/bakartsd
(followed by your password) and
sudo shutdown -r now

and all should work!

---

### Post by ctt1wbw on 2006-01-09
Thanks, I tried that and still can't get past a brown screen in Ubuntu or the blue screen in Kubuntu before my keyboard and mouse freeze up.  So I am not able to hit any keys at all, no key combos to get to a terminal window...  I just don't know what to do here.  :confused:

---

### Post by Achille on 2006-01-09
If you try with a LiveCD, it is very difficult, because you don't get the login screen and have just one second (or less) for hitting the right keys and typing the commands: impossible mission. I did success with a LiveCD that I customized first, before using it.

Download the install CD (Dapper flight2 of Kubuntu) and install it. In the second stage, you have a lot of time for hitting Ctrl+Alt+F2 and getting a console. Type first ls -l /usr/bin/artsd to be sure that arts has been installed.

---

### Post by ctt1wbw on 2006-01-09
Okey dokey.  I didn't realize that live cd's were so different.  I'll try soon with an install disk and see how it goes.  Since I have an iMac with Airport Extreme, I have to wait to get an ethernet cable strung somewhere so I can have a direct connection to the internet, otherwise I'm up sh!t creek without the proverbial paddle.  :razz:

---

### Post by Achille on 2006-01-10
I can confirm you what I supposed: the liveCD Breezy 5.10 works with iMac G5 if you move /usr/bin/esd to /usr/bin/bakesd.

---

### Post by ctt1wbw on 2006-01-10
Okay cool!  I'm getting my house wired with CAT5 cable all over today, so sometime today or tomorrow I'm going to attempt an Ubuntu load on my iMac.  So when, if all goes well, I get to a login window, I can go to a console window and rename esd to bakesd and then reboot, everything should work?  I don't need to rename artsd or anything, just esd?

Dude, I'm getting stoked!

---

### Post by Achille on 2006-01-10
In a console type:

ls -l /usr/bin/esd
ls -l /usr/bin/artsd

and you will see what is installed (esd with Ubuntu and artsd with Kubuntu)

Then type

sudo mv /usr/bin/esd /usr/bin/bakesd
or
sudo mv /usr/bin/artsd /usr/bin/bakartsd

And reboot. It worked fine with a liveCD customized in such a way.

---

### Post by ctt1wbw on 2006-01-10
Okay, but one question though.  This won't disable sound, will it?  I thought esd was related to sound?  And if so, I can still use alsa, right?

---

### Post by Achille on 2006-01-10
I suppose. You have to try. I don't own a iMac G5. I can just test liveCD at work, but I can't install Ubuntu on a iMac G5. So try it yourself and tell us what happens.

---

### Post by ctt1wbw on 2006-01-11
Okay, I got Ubuntu on my G5 iMac.  It boots up to the login screen, and then the keyboard and mouse freeze up.  How and where in the boot process do you hit control-apple-f1 to get to a console?  I tried that and now my iMac is sitting at :boot prompt in the Yaboot section.

What do I do now?

---

### Post by ctt1wbw on 2006-01-11
I've tried and tried and tried and tried...  I'm just going to put os x back on there for now.

---

### Post by Achille on 2006-01-11
There is another possibility: download and burn a CD installation of Gentoo. For example here: (minimal should suffice)

[ftp://mirror.switch.ch/mirror/gentoo/releases/ppc64/current/installcd/](ftp://mirror.switch.ch/mirror/gentoo/releases/ppc64/current/installcd/)

Boot from the CD and you will arrive to a terminal console as root. Then type:

mkdir -p /mnt/ubuntu
mount /dev/hdaX /mnt/ubuntu
(where X is the number of the partition where you installed ubuntu)
mv /mnt/ubuntu/usr/bin/esd /mnt/ubuntu/usr/bin/bakesd
umount /mnt/ubuntu

reboot

And the modification will be effective.

---

### Post by ctt1wbw on 2006-01-11
Thanks man.  And I just got OS X back up.

I'll give it another go soon.

---

### Post by cvmostert on 2006-01-12
[QUOTE=Achille]In a console type:

ls -l /usr/bin/esd
ls -l /usr/bin/artsd

and you will see what is installed (esd with Ubuntu and artsd with Kubuntu)

Then type

sudo mv /usr/bin/esd /usr/bin/bakesd
or
sudo mv /usr/bin/artsd /usr/bin/bakartsd

And reboot. It worked fine with a liveCD customized in such a way.[/QUOTE]

I do not have a Mac, but my pc also hangs when i put in my soundcard... a crystal CS4614A-CM

changing /usr/bin/esd to /usr/bin/bakesd did not work... how do i boot without loading the sound modules?:(

---

### Post by limey on 2006-01-12
:-) Sorry wanted to add redundant information!

---

