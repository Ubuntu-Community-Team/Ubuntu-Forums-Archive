---
title: "Ubuntu won't boot"
date: 2007-06-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Deathwish238 on 2007-06-11
Ubuntu won't boot...at first it'ld only boot one out of every two or three tries, but now it won't boot at all.  GRUB loads, I select Ubuntu, it seems to be doing a few things but the Ubuntu splash screen never comes up!

What should I do/check?  What do you need to know about my setup?

I'm dual booting with Vista(installed it first a long long time ago) and it worked perfectly in the beginning

---

### Post by darknightuk on 2007-06-11
it's a well known bug loads of posts, it's booting, splash screen just aint there leave it for a bit it will load

---

### Post by crjackson on 2007-06-11
> **darknightuk said:**
> it's a well known bug loads of posts, it's booting, splash screen just aint there leave it for a bit it will load

That doesn't work for me at all.

Here's what I did...

1) Start liveCD
2) Hit F4 and change the screen resolution to 640x480
3) Select LiveCd/Install (option 1 on the 1st menu)
4) After desktop comes up, you can install if you want - I did

After installed - Edit your boot file and change "SPLASH" TO "NOSPLASH" save and you shoud be good.

Now everytime you boot, you will see text scrolling up the screen, but at least it won't hang and it runs perfectly.

Hope this helps...  Keep in mind I'm a Linux newbie too....:D

---

### Post by Cappy on 2007-06-12
Here are some more in-depth instructions if you are able to use (recovery mode) to boot:
[http://ubuntuforums.org/showthread.php?t=464513&page=2](http://ubuntuforums.org/showthread.php?t=464513&page=2)

---

### Post by sataniceaden saklura on 2007-06-12
**edit**please excuse spelling**Help please first of i will say hello  i have been a member for ages but never got around to installing (games needed windows)well finaly i cracked it uninstalled windows and installed Ubuntu 7.04 amd 64bit(fiest fawn)**EDIT**i dont know the exact version of kernal im using as at the moment i have reinstalled xp**

well i got a little issue  i figured here would be a good place to start as im getting similar to this

ok so i install all is ok i do the updates that the system askes and seems to be ok install Nvidia 8600gts drivers wont boot after i get the must reboot popup

but here is the weird thing

mine on install switches the monitor into standby but then boots login screen after like 10 sec
but after update and reboot it just stays in standby

HELP!!!!

so im running an amd64 dual core 4600
Msi Nvidia 8600gts (dual dvi)-Monitor 20 inch flat samsung SyncMaster 203b
1.7terra sata hdd
usb Keyb&mouse


any help would be apreciated i have tried everything that i can think of this includes

**

Sudo dpkg-reconfigure xserver-xorg (ran through fine boot didnt fix same deal)
reinstalled Ubuntu this time did updates with *automatix*

now the program installed Nvidia gfx drivers 
and told me to run 
x server-xorg configuration(command not found)
restart x:automatix-nvidia-restore(command not found)

reinstalled again
installed NVIDIA-Linux-x86_63-100.14.09-pkg2.run drivers reboot worked fine
did update from the buble telling me to reboot (back to monitor in standby)

tried
**
sudo gedit /boot/grub/menu.1st (command not recognised)
nano /boot/grub/menu.1st (worked ok removed all splash(aprat from the very first one in the ##section))
reboot no different 

now i have installed windows again and i dont want it on here please please please help

the oly thing i realy run on windows is my online game (Last Chaos) so i am quite happy to remove it please help me

---

### Post by Cappy on 2007-06-12
When you tried editing your menu.lst (that is menu.LST not 1st) were you in recovery mode (text only)? Have you checked to make sure you actually saved the file?

You are correct, you need those nvidia drivers (from the nvidia site). The ones that can be easily installed with Ubuntu will not work with the 8600 yet.

Before you install the nvidia drivers (from their site) you should remove all ubuntu nvidia drivers:
```

sudo apt-get --purge remove nvidia-glx* nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo sh NVIDIA-Linux-x86_63-100.14.09-pkg2.run

```
If you end up running that in (recovery mode) just take the "sudo" off the front. 
You may need to ```
sudo apt-get install linux-restricted-modules-`uname -r`
``` before you install that NVIDIA-Linux drive, I'm not sure. Notice that that is the tilda key and not a parenthesis. 



If you can get into (recovery mode) and something is still not working you don't need to reinstall. You can run
```

dpkg-reconfigure xserver-xorg
```
The first selection you get is where you have a long list of video drivers and the one selected will probably be "nvidia". You just need to change that to "nv". You can hit "enter" on everything else until it is done. This changes the system from using the nvidia drivers back to the open-source "non-3d" drivers. Edit: You may need to use "vesa" instead of "nv" if that doesn't work.

Finally, know that if you are using a terminal/(recovery mode) you can hit the TAB button and it will autocomplete a file name or command. For instance, if you typed "sh NVIDIA" and hit tab it will autocomplete to the whole file name. I wouldn't normally mention it, but it is kind of hard getting around in a terminal without it.

Oh, and the command "reboot" will reboot if you're in (recovery mode). =P

---

### Post by sataniceaden saklura on 2007-06-12
thank you will try it right now hope it works =^_^=
**edit**thank you i am back in ubuntu ok so the issue with it going to standby is still there but i think that was my stuff up for reading incorectly 
but now i got another problem it cant open the sh NVIDIA-Linux-x86_63-100.14.09-pkg2.run package
> sakura@sakura-desktop:~$ sudo apt-get --purge remove nvidia-glx* nvidia-settingsReading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-glx-dev for regex 'nvidia-glx*'
Note, selecting nvidia-glx-new for regex 'nvidia-glx*'
Note, selecting nvidia-glx-src for regex 'nvidia-glx*'
Note, selecting nvidia-glx-legacy-dev for regex 'nvidia-glx*'
Note, selecting nvidia-glx-legacy for regex 'nvidia-glx*'
Note, selecting nvidia-glx for regex 'nvidia-glx*'
Note, selecting nvidia-glx-new-dev for regex 'nvidia-glx*'
Package nvidia-settings is not installed, so not removed
The following packages will be REMOVED:
  nvidia-glx-new*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 26.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 157133 files and directories currently installed.)
Removing nvidia-glx-new ...
Purging configuration files for nvidia-glx-new ...
sakura@sakura-desktop:~$ sudo rm /ect/inti.d/nvidia-*
rm: cannot remove `/ect/inti.d/nvidia-*': No such file or directory
sakura@sakura-desktop:~$ sudo rm /etc/init.d/nvidia-*
sakura@sakura-desktop:~$ sudo sh NVIDIA-Linux-x86_64-100.14.19-pkg2.run
sh: Can't open NVIDIA-Linux-x86_64-100.14.19-pkg2.run
sakura@sakura-desktop:~$ sudo sh
# cd Desktop
# NVIDIA-Linux-x86_64-100.14.09-pkg2.run
sh: NVIDIA-Linux-x86_64-100.14.09-pkg2.run: not found
# rid
sh: rid: not found
# dir
automatix2_1.1-4.4-7.04feisty_amd64.deb  NVIDIA-Linux-x86_64-100.14.09-pkg2.run
listen.pls
# NVIDIA-Linux-x86_64-100.14.09-pkg2.run
sh: NVIDIA-Linux-x86_64-100.14.09-pkg2.run: not found
# sh NVIDIA-Linux-x86_63-100.14.09-pkg2.run
sh: Can't open NVIDIA-Linux-x86_63-100.14.09-pkg2.run
# sh NVIDIA-Linux-x86_63-100.14.09-pkg2.run
sh: Can't open NVIDIA-Linux-x86_63-100.14.09-pkg2.run
# dir
automatix2_1.1-4.4-7.04feisty_amd64.deb  NVIDIA-Linux-x86_64-100.14.09-pkg2.run
listen.pls
# sh NVIDIA-Linux-x86_63-100.14.09-pkg2.run
sh: Can't open NVIDIA-Linux-x86_63-100.14.09-pkg2.run
# 



sorry i dont know how you do the code thingy

i re downloaded the drivers same issue do i have to do it from ctrl+alt+delete+F1 ??

sorry im asking lots of questions i know thanks again for the help
=^_^=

---

### Post by Cappy on 2007-06-12
I assume the nvidia install is on your Desktop?

Close out that window where you did the "sudo sh". Use a new terminal.

```

cd ~/Desktop
sudo sh NVIDIA-Linux-x86_64-100.14.09-pkg2.run

```

By the way, ```
ls -l
``` lists out the files/folders in a directory. It makes it colorful? =P

It's Control + Alt + F1 (Control + Alt + F7 to get back to Gnome). You can do it in a terminal in Gnome. I wouldn't use a virtual terminal (the Control + Alt + F1 thing) to do this.

---

### Post by sataniceaden saklura on 2007-06-12
i love you thank you soo much i mean love in the friendly term not meh if i offend im sorry
thank you soooooooo much


as for control+alt+F7 it does nothing ????

(i got ctrl+alt+del F1 form "post:Re:Problem with Nvidia beta driver on 8600gts"so i assumed it was correct my appoligies

aldo i deleted the menu files i created but it wont let me edit menu.lst so i still get the monitor turning off:(

thanks again for all the help 

p.s. i was wondering i did your restriced drivers thing and it couldnt find the folder and when i go into restricted drivers under my user account it says there is none???
mabey i should just give up:P **shudders at the thought**

---

### Post by Cappy on 2007-06-12
Maybe it needs:
```

cd ~/Desktop
chmod +x NVIDIA-Linux-x86_64-100.14.09-pkg2.run
sudo sh NVIDIA-Linux-x86_64-100.14.09-pkg2.run

```

If that doesn't work then you either don't have that file on your desktop or the file is named differently. You are copying and pasting the code into the terminal, right? Running "sudo sh" on a line by itself isn't what you want.

"when i go into restricted drivers under my user account it says there is none???" You havn't installed any nvidia drivers, this is what we are doing.

"aldo i deleted the menu files i created but it wont let me edit menu.lst" You aren't doing it properly, now that you are in Gnome you must
```
gksudo gedit /boot/grub/menu.lst &
``` to be able to save. This assumes that you are using Ubuntu and not Kubuntu or Xubuntu.

---

### Post by sataniceaden saklura on 2007-06-12
i lgoin to gnome through the login page and im still restricted *** it says x driver still running if i shut gdm down it goes black***edited**
and it wont boot into ubuntu i installed the driver then installed wine rebooted to make sure all was good back to monitor switching to standby 

yes i am using ubuntu 7.4 amd 64 bit
of swinburn uni (australia)

i dunno what to do ill go back fresh install and try everything yo said i think i stuffed something up majorly \im good at that:P =^_^=

---

### Post by Cappy on 2007-06-12
Well you still have Windows and Linux will at least work without 3D acceleration. If you still can't get it to work, I wouldn't worry about it too much at the moment. You can still run Linux and boot to Windows for games. I ran Ubuntu part-time for about 2 weeks until I got sound and all my applications working well enough for me to switch over. I don't like dual booting much but it really is the best way to get one thing figured out at a time.

---

### Post by sataniceaden saklura on 2007-06-12
yeah this is were the issue comes in the driver for the 8600 works on windows but as its a dual dvi card it crashes with my game as i cant set windows to only register the one port for the game cause its a usless operating sys im going to tryr a different driver version though cause the error i got (i fixed the boot file)was
"Failed to start the x server(your graphical interface). It is likely the it is not setup correctly. Would you like to view the x server output to diagnoce the problem"(hit yes)

main error is =cannot load kernal as driver and kernal do not match driver 100.14.09 installed cannot find kernal



ok this is from the messages log so i dunno how usefull it will be 

un 12 00:07:10 sakura-desktop kernel: [   52.243860] nvidia: module license 'NVIDIA' taints kernel.
Jun 12 00:07:10 sakura-desktop kernel: [   52.499097] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
Jun 12 00:07:10 sakura-desktop kernel: [   52.499101] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 16
Jun 12 00:07:10 sakura-desktop kernel: [   52.499261] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  1.0-9755  Mon Feb 26 23:16:31 PST 2007
Jun 12 00:07:10 sakura-desktop kernel: [   52.687421] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
Jun 12 00:07:10 sakura-desktop kernel: [   52.687425] ACPI: PCI Interrupt 0000:00:0e.1[B] -> Link [AAZA] -> GSI 20 (level, low) -> IRQ 20
Jun 12 00:07:10 sakura-desktop kernel: [   52.863989] wiphy0: hwaddr 00:15:af:0f:53:43, rtl8187 V1 + rtl8225z2
Jun 12 00:07:10 sakura-desktop kernel: [   52.864011] usbcore: registered new interface driver rtl8187
Jun 12 00:07:10 sakura-desktop kernel: [   52.917766] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
Jun 12 00:07:10 sakura-desktop kernel: [   52.925882] usbcore: registered new interface driver cdc_acm
Jun 12 00:07:10 sakura-desktop kernel: [   52.925885] drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
Jun 12 00:07:10 sakura-desktop kernel: [   53.276608] fuse init (API version 7.8 )**edit there is no actual space but does smily so i had to make**
Jun 12 00:07:10 sakura-desktop kernel: [   53.478232] lp0: using parport0 (interrupt-driven).
Jun 12 00:07:10 sakura-desktop kernel: [   53.707887] Adding 3004112k swap on /dev/disk/by-uuid/676be009-9899-4263-a87f-4a8875fe120b.  Priority:-1 extents:1 across:3004112k
Jun 12 00:07:10 sakura-desktop kernel: [   53.985622] EXT3 FS on hdb1, internal journal
Jun 12 00:07:10 sakura-desktop kernel: [   60.743638] No dock devices found.

---

### Post by Cappy on 2007-06-12
Re-install the nvidia driver:
```

cd ~/Desktop
sudo apt-get --purge remove nvidia-glx* nvidia-settings linux-restricted-modules*
sudo rm /etc/init.d/nvidia-*
sudo apt-get install fakeroot build-essential linux-headers-amd64-generic linux-headers-generic gcc pkg-config xserver-xorg-dev linux-headers-`uname -r`
sudo sh NVIDIA-Linux-x86_64-100.14.09-pkg2.run
sudo nvidia-xconfig --no-composite

```

I googled a little bit and discovered that the restricted modules must be removed to compile your own driver.
I also needed to add some packages to be installed.

I've always gotten the "mismatched" error to go away by re-installing the nvidia driver.
As such, if you run this and reboot and it doesn't work I would redo the process again. Maybe it is just mind voodoo.

I would save that code to a file in your Home directory as something like "nvidiainstall.sh" and then
```
chmod +x nvidiainstall.sh
```
(any time before you run it)
then you can run it easily with
```
sudo sh nvidiainstall.sh
```

---

### Post by sataniceaden saklura on 2007-06-13
I would like to say a verybig thank you so much that worked and the driver works perfec thank you sooo much if i could give you a vote i would this has been very help full and now windows has been fully removed we should sticky that as it worked perfect the only thing i had to do was stop the gdm 

sud /etc/init.d/gdm stop



> **Cappy said:**
> Re-install the nvidia driver:
```

cd ~/Desktop
sudo apt-get --purge remove nvidia-glx* nvidia-settings linux-restricted-modules*
sudo apt-get install fakeroot build-essential linux-headers-amd64-generic linux-headers-generic gcc pkg-config xserver-xorg-dev linux-headers-`uname -r`
sudo rm /etc/init.d/nvidia-*
sudo sh NVIDIA-Linux-x86_64-100.14.09-pkg2.run
sudo nvidia-xconfig --no-composite

```

I googled a little bit and discovered that the restricted modules must be removed to compile your own driver.
I also needed to add some packages to be installed.

I've always gotten the "mismatched" error to go away by re-installing the nvidia driver.
As such, if you run this and reboot and it doesn't work I would redo the process again. Maybe it is just mind voodoo.

this part didnt work cause it couldnt find the directory
> 
I would save that code to a file in your Home directory as something like "nvidiainstall.sh" and then
```
chmod +x nvidiainstall.sh
```
(any time before you run it)
then you can run it easily with
```
sudo sh nvidiainstall.sh
```

thank you again =^_^=

---

### Post by Deathwish238 on 2007-06-14
Thanks for all the replies!

> **Cappy said:**
> Here are some more in-depth instructions if you are able to use (recovery mode) to boot:
[http://ubuntuforums.org/showthread.php?t=464513&page=2](http://ubuntuforums.org/showthread.php?t=464513&page=2)This worked like a charm.  My only concern is having to do is after every update?  Is this true?

Also, is there a way to permanently edit GRUB?

---

