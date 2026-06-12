---
title: "Monitor goes into sleep mode when installing 64bit 7.10."
date: 2007-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by can8dnSix on 2007-12-04
I have been running Ubuntu (32bit flavor) on various machines since release 4.x, I have installed the 64bit flavor on several occasions on different machines. When installing on this machine, an HP m8000n, Intel Q6600, nVidia 8600GTS OC, I run into an issue. No matter what i have chosen thus far, from "command line install," to "safe mode install," my monitor goes to sleep and the system ceases to do anything (as far as i can see.. as i have no monitor). :confused:

BUT,:confused: when I install the 32bit version (Gutsy 7.10 -32bit), the LiveCD takes me all the way into the GUI and lets me install the system like I have so many times before. My question is the why behind this? I also tried to alternative install CD-ROM. 

Lastly, can I install 32bit 7.10, change the repositories to 64bit and upgrade the install? AND if that is possible can I have both a 32bit kernel and a 64bit kernel to choose from in the GRUB menu? Would that require to different filesystems or can I try to run them at the same time. Sorry for the long, long, post. 

Thanks,

Lindis.:popcorn:):P

---

### Post by can8dnSix on 2007-12-04
I went ahead and installed 7.10 32-bit version, for reason of making sure all my little devices and things get connected and to check the wireless. Anyway, it all seems to work. Now back to the chore of figuring this little setback out. Anyway, thanks,

Lindis.

---

### Post by th1rst on 2007-12-04
I have the exact same problem as you

It happens when I try to run it live from the cd

both my monitors go into sleep mode
and nothing happens


what sucks is I have no choice to go with 64bit cause I have an X-FI :-(
and I can't even install it

---

### Post by can8dnSix on 2007-12-04
did you try the alternative install CD-ROM? If not, I certainly would recommend trying that out. Right now Im on my notebook, I've had this on here for a week or so and I love it. Anyway, try that, use the command line install option, if you haven't tried it of course. 

Lindis.

---

### Post by Kilz on 2007-12-04
> **can8dnSix said:**
> 

Lastly, can I install 32bit 7.10, change the repositories to 64bit and upgrade the install? AND if that is possible can I have both a 32bit kernel and a 64bit kernel to choose from in the GRUB menu? Would that require to different filesystems or can I try to run them at the same time. Sorry for the long, long, post. 

Thanks,

Lindis.:popcorn:):P

You cant install both kernels in one install. If you have room on your hard drive you can install complete versions to separate partitions. Then use grub to boot into the one you want. 
But now that you have a 32bit install all it will ever be is 32bit and you are loosing out on the performance you paid for with buying 64bit hardware.

---

### Post by picopir8 on 2007-12-04
First, try installing with the safe graphics option.  If that does not work then do the custom boot option (I think it is F9 or one of the items listed at the bottom of the first screen you get at boot) and edit the boot command to remove the word "splash".  If that still does not work, then download the alternate install CD and boot up with that.

---

### Post by th1rst on 2007-12-04
Unfortunately I'm just starting out with linux and don't know a whole lot about it
I just might go out and buy a 20 dollar sound card for now, until I get a feel for it, and how things work.

**EDIT**

whoa, there were two posts made by the time I posted this, I'm gonna try out what you guys suggested, thanks

---

### Post by can8dnSix on 2007-12-04
did all the above to no avail, I've got a super linux guru coming over in a bit to "fix' this issue. As far as the "all it will ever be... 32 bit," it will pretty much be whatever I want it to be. Where there is a will there is a way... :) Oh, I will try removing the "splash" screen though, we'll see how that goes. Anyway, thanks for the comments... seems like the morning shift is coming onto the forums... cool cool. :lolflag:

---

### Post by Kilz on 2007-12-04
> **th1rst said:**
> Unfortunately I'm just starting out with linux and don't know a whole lot about it
I just might go out and buy a 20 dollar sound card for now, until I get a feel for it, and how things work.

Download and install with the Alternate install cd rather than buy useless hardware and loose performance. imho you are rationalizing an excuse to do what you know is a bad idea.

---

### Post by Kilz on 2007-12-04
> **can8dnSix said:**
> did all the above to no avail, I've got a super linux guru coming over in a bit to "fix' this issue.** As far as the "all it will ever be... 32 bit," it will pretty much be whatever I want it to be**. Where there is a will there is a way... :) Oh, I will try removing the "splash" screen though, we'll see how that goes. Anyway, thanks for the comments... seems like the morning shift is coming onto the forums... cool cool. :lolflag:

Once a 32bit install is installed it cant have parts of a 64bvit system. It will remain a 32bit system. Not even a guru will bbe able to make a 64bit kernel work at 64bit on a 32bit install.

---

### Post by can8dnSix on 2007-12-04
If you read the post previous, I specifically stated that i installed the 32 bit to check if everything was detected, thus, in my humble opinion, maybe you should have throughly read the original post which stated my intentions. Further, I don't post here so someone can try to build up their own self-esteem by trying to belittle other people who are asking questions... again, in my humble opinion. 

Lindis.

p.s. it was not a rationalization, it seems logical to see if this distro will work with my hardware.. does it not? If the 64bit version would not go, why not then test the 32bit version... it's not all too much time consuming to reinstall a 64bit version,... is it? Thus, IMHO... have a nice morning.

---

### Post by th1rst on 2007-12-04
ok, I pressed escape at the menu and it brought me to a screen with only

boot: 



so how do I edit the boot command to remove the word splash?




and for kilz



I know I'd lose some performance, but almost no software runs at 64bit anyway,  I just don't have much of a use for it right now... and I didn't say I would go out and buy a sound card, I said I may, if I wind up spending to much time on this only to realize that I can't fix it because I'm not knowledgeable enough on the subject
  you may say something like "if I don't want to learn I shouldn't use linux."  Well I do want to learn, but I also want to use my pc for day to day activities that I usually use it for, and not be stuck with some machine that won't even boot into the os while I try to fix it for weeks.  If I do buy a sound card, I will come back on this and try to fix it, when I feel like it and when I have time

---

### Post by can8dnSix on 2007-12-04
Iif I recall, once you get the little boot option at the bottom of the screen, you can select the one you want to choose from the menu above and remove or add whatever option you want. Secondly, I think Kilz is referring to me about wasting money and funds.. as if how I spend any of my money is any of his/her concern; if I want financial advise I'll talk to my accountant... thus the original post was clear in what its context was... Ubuntu install. 

Lindis.

---

### Post by can8dnSix on 2007-12-04
The First;

Hey do this, when you get to the boot option screen, press F-6 or whatever key in the selection menu. You will see "boot" with a bunch of options come up. Select either "safe mode" or the first one, delete the word 'splash' and press enter. It's got me into the GUI for the install, cool cool.
[B][SIZE="4"]
picopir8[/SIZE][/B], you get points and thanks for your input. Certainly worked... and you gave advice in a way that can both be considered 'professional' and 'courteous,' so thanks a lot. 

Lindis.:guitar:

---

### Post by th1rst on 2007-12-04
well, I've made some progress on the subject I think


I took of the splash like one of you suggested

this is the result
my monitors don't go on sleep mode anymore but I get errors


[    89.346692]  Buffer I/O error on device fd0, logical block 0
[    98.539823] Buffer I/O error on device fd0, logical block 0
[   123.920049]Buffer I/O error on device fd0, logical block 0
[   164.341850] Buffer I/O error on device fd0, logical block 0



basically it just come coming every few second a new entry is added and those numbers on the left increase

---

### Post by can8dnSix on 2007-12-04
Odd question, do you have a floppy diskette in the computer? My install is rolling forward... formatting the two drives now. Anyway, cool cool. If you want, hit me up on AIM.

Lindis.

---

### Post by th1rst on 2007-12-04
I don't have a floppy drive


anyway, I just let it run for a while, and I got impatient then typed boot and hit enter
I dont' know if it's because I typed boot and hit enter or it wass just done reporting those errors, but the GUI loaded
should I still go about installing it now that I'm in the GUI?
or would that error cause problems?

---

### Post by can8dnSix on 2007-12-04
Hell, I'd just go and let it update itself when it gets installed. I mean we could troubleshoot it, but they might be typical of this install? We did cut out the SPLASH screen, thus, we'd see what we would normally not see. So those messages might be normal for this install. It installing the files now, so yay. Internet worked right out of the box; cool.

Lindis.

---

### Post by th1rst on 2007-12-04
mine is currently installing right now too XD.... and the internet worked for me as well :-)


I only hope I can install my sound drivers for the X-FI

if that works, I'll be happy XD

---

### Post by can8dnSix on 2007-12-04
Rebooting now, so here goes. I hope your X-Fi works too. Everything installed and updated, cool cool. You get so much more done in such a short period of time when you can download at 8,250Mbits/sec... ha cool.

Lindis

---

### Post by th1rst on 2007-12-04
the monitors still go on sleep mode when it's time for the splash screen to come up, guess I'll have to delete that line again... wait, I don't even have the option to do that.. as far as I can tell

---

### Post by can8dnSix on 2007-12-04
Give it some time, I had to give it about a minute or so; then it loaded the logon screen. If that doesn't work, when GRUB is loading, hit escape, go into safe-mode and try updating your system. 

Lindi

---

### Post by th1rst on 2007-12-04
cool I'll try that right now, thanks

---

### Post by can8dnSix on 2007-12-04
You can also edit your GRUB config file. Get into a console, use an editor of sorts to edit:

/boot/grub/menu.lst

> title BLAH BLAH
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UU--BLAH BLAH--2203 ro quiet spash

remove splash

> kernel /boot/vmlinuz-2.6.22-14-generic root=UU--BLAH BLAH--2203 ro quiet 

you can try that also. If you get into a GRUB menu, start in safe mode and edit that, it should remove the splash screen.

lindi

---

### Post by th1rst on 2007-12-04
is recovery mode what you meant? If so, it brings me to a command line, it doesn't load the GUI... if it's suposed to be this way I'm not quite sure how to update the system in this fashion

---

### Post by can8dnSix on 2007-12-04
at the prompt, you can
> 
sudo vi /boot/grub/menu.lst

or use "vim" instead of vi.
[B]
or you can update your apt and distro[/B]

> sudo apt-get update
> 
sudo apt-get -u dist-upgrade

You should have Internet so update your system like that.
[B]
OR[/B]

You could try to start the xserver

> 
sudo startx

Lindi

---

### Post by th1rst on 2007-12-04
post deleted

---

### Post by th1rst on 2007-12-04
internet doesn't work, so I accessed menu.lst
I removed the line with splash

how do I save the file now?

I tried hitting ctr-z 
but that undid the changes
and it's the only way I know of getting out

---

### Post by th1rst on 2007-12-04
anyways I figured it out and I made it boot!

thanks for all your help!

---

### Post by mozkill on 2007-12-04
When I boot from the standard install DVD I get the Ubuntu DVD menu and I choose "install new system" and then as soon as the kernel tries to load my monitor is blank for about 3-4 minutes and then X windows comes up and I can proceed with the install.

also, after the system is installed, I still get a blank screen on bootup but it only lasts for 30 seconds in that case.

I dont see any of the "dmesg" output that I normally would see on a 32-bit version of Ubuntu.

---

### Post by can8dnSix on 2007-12-04
Yea, that is the same for me too. Cool, well I am glad you got most of everything working. Sorry for not responding earlier, I was sleeping and running errands. Well thanks,

lindi

---

### Post by Brando569 on 2007-12-10
i have the same type of problem with my 8600GTS OC, it doesnt show the splash screen when i boot up kubuntu (i already have it installed) but after its done booting up i dont have a problem with it. i gotta see if i can see the output if i remove the 'splash' option. glad to see im not the only one with this problem

---

