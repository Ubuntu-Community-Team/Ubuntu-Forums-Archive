---
title: "Duh! Forgot password-how to reset?"
date: 2006-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by threephase on 2006-02-13
this is a bit stupid...:( 

im aware of the following:

sudo passwd root

but how can i get a console/shell up so i can enter the command during the boot process?

hope someone can help.

thanks

---

### Post by Gandalf on 2006-02-13
Boot in recovery mode and change your password..

---

### Post by threephase on 2006-02-13
right-ok, how do i do that...?

---

### Post by BenTyreman on 2006-02-13
Reboot the PC. Hammer the ESC key until the GRUB menu appears. Select the recovery console. Type in
```
passwd <your user name>
```
Then type in your new password (it will ask to confirm). Reboot.

---

### Post by threephase on 2006-02-13
that all sounds good, except keeping ESC pressed throughout the boot process does nothing...i dont get the GRUB menu...

i just end up at the login screen...!

drat.

---

### Post by BenTyreman on 2006-02-13
You need to repeatedly press the key, like you would to get into the BIOS.

---

### Post by threephase on 2006-02-13
i know nothing of PC's/BIOS type stuff-i come from a mac background!

tried what you suggested-no joy just knackered arms and fingers...

it can't be this difficult...can it?

---

### Post by Gandalf on 2006-02-13
No it cant, You will see something normally like "Grub is loading" you begin hitting escape at this moment...

If that didn't work You can boot with Ubuntu liveCD, open a terminal, mount your partition somewhere,
lets say your root partition is at hda3, then do
```

sudo mkdir /main
sudo mount /dev/hda3 /main
sudo chroot /main /bin/bash
passwd <username>
exit

```
and now reboot into your main distro..

hope that helps

---

### Post by threephase on 2006-02-13
hmm...

not getting any GRUB

and i now cant boot from my installer CD (downloaded-not LiveCD)

double drat.

---

### Post by Gandalf on 2006-02-13
Download Live cd then ... or use another livecd i would suggest 
[http://www.archlinux.org/download.php](http://www.archlinux.org/download.php) Arch 0.7.1 base ( 152 Mb ) just boot with it and do what i have wrote without sudo :D

---

### Post by threephase on 2006-02-13
whats annoying is this:  i used the same installer cd to install ubuntu-and it booted up from the disk everytime (i failed to install correctly!)

anyway-im going to do what you suggest Gandalf-thanks for the help.

back later...

---

### Post by threephase on 2006-02-13
grrr-this is getting to be a pain in the neck

i can't boot from the arch base iso either...

maybe i should mention im using a G3 266 MT...old world mac

had a flat battery so i was getting the date bug/brown screen after login last week

then came back today (monday) and have completely forgotten my password

i just cannot figure out what it was-i've tried heaps of combinations

i managed to get to the ash shell when trying to boot the arch cd but im lost here-is there anyway at this stage i can get to where i need to go?

---

### Post by Gandalf on 2006-02-13
arch will boot as shell that's all, though am not sure if it boots or not, i completely forgot that you are a mac user :oops:

can you paste me the result of
```

fdisk -l /dev/hd*

```
in that bash ?

---

### Post by jdp on 2006-02-13
How is he able to boot the Arch Linux Cd when Arch only runs on 686-baed PCs?  I'm missing something here. ;)

Because it's a Beige, it won't boot a Linux CD directly and you'll have to change the settings in BootX to get it to boot.

---

### Post by threephase on 2006-02-14
i see...hmmm. ok, so then, how do you change the settings in BootX?

as i see it there isn't much to change.

everything was as it was pre-ubuntu installation (or so it seems)

kernel arguements is however now:

root=/dev/hdd7
(which makes sense as this is where ubuntu is installed with 6 (9.1) and 8 (swap))

i can delete the above but it makes no difference-each time it reboots. it returns.

do i need to change the above so that it 'points' to the CD-rom?

would i be right in assuming i can find out where it mounts by going through the bootup?

then entering the information in the kernel arg...???

---

### Post by Tiede on 2006-02-14
instead of all this, if you know the root password, you can hit Ctrl+Alt+Del on the login screen and at the shell enter it then su to your nickname and change the password. I think...

---

### Post by oswaldkelso on 2006-02-14
Does Arch have a ppc disto?

---

### Post by oswaldkelso on 2006-02-14
Next time I'll read to the end of the thread :)

---

### Post by slux on 2006-02-14
Actually there is at least a prerelease version of Arch available for PPC. Haven't gotten around installing it yet myself though.

---

### Post by threephase on 2006-02-14
ok well im giving up on this and im going to re-install, as its going nowhere fast.

my own stupid fault for forgetting.

but i am a little surprised no one could really figure this out.

thanks for everyones input though.

drat.

---

### Post by threephase on 2006-02-14
re-install succesful!

im so glad i had to install ubuntu about 1000 times

because it made installing it today really easy

first impressions compared to mac OS 7/8/9/10:

weird pc type windows
horrible fonts
pac man screensaver is good (lol)

aqua on ubuntu?

screen redraw is a bit slow. menu's/cursor can at times appear sluggish then suddenly accelerate!

otherwise so far-it all seems to work ok, it will take me a while to get used to it -and i already want to customise it...

so another succesful oldworldmac installation (albeit with a fair few hiccups).

---

