---
title: "[SOLVED] Black Screen on every 7.10 fresh install attempt (64bit with GeForce 8800)"
date: 2007-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by cowrecked on 2007-10-25
I've heard a lot about Ubuntu, so I decided to try it on my system. However, I've had no success in installing.

Each time I boot off of the installation CD and choose any option (Install or Start Ubuntu, Graphics Safe mode, OEM, CD check, memory test, etc) it displays a progress bar of loading the linux kernel, then goes to a blank screen (sometimes briefly showing a line of text at the top of the screen and a line at the bottom). I've downloaded multiple copies of the .iso's, burned multiple CD's at different speeds, and I even downloaded the FULL dvd and burned that, all with the same results.

I'm trying to install the 7.10 AMD64 version (which I've read should be no problem with an intel Core2Duo).

I've seen a few similar threads, and searched for solutions, but I've been unable to find a clear answer.

System Specs:
intel Core2Duo E6750 @ 3.5GHz
eVGA GeForce 8800GT 640MB
4x1GB G-Skill DDR2 @ 4-4-3-4
500GB Samsung SATA HDD, 120GB Seagate SATA HDD (intended install path for ubuntu, if I can get that far), 400GB Seagate SATA HDD
Samsung IDE CD burner, Samsung IDE DVD burner
Creative Sound Blaster X-Fi XtremeMusic
Samsung SyncMaster 206BW @ 1650x1080

I currently run Windows Vista Home Premium with no issues, and have run Windows XP with this configuration.

---

### Post by Therion on 2007-10-25
Someone else may come along with a better fix, but I have an 8800GTS as well and here's what got me up and running.

Install from the LiveCD and boot.
When the GRUB menu comes up, hit Escape and select "Recovery Mode".
You'll end up at a command prompt.
from the command prompt:
```
nano /boot/grub/menu.lst
```
Scroll down using the arrow keys until you find the first line that begins with Kernel.  It's a looong line of code that will go off the end of your display.  At the end of that line you'll see the word "splash".  Remove "splash" from that line so it looks like this:
```
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=43a49820-eae9-4b96-9f94-a81a2aadcb2c ro quiet
```
Use Ctrl+X to Save the change, okay the file over-write when prompted and reboot.
That should get you to your desktop.  From there install the restricted driver (you'll be prompted about this automatically) and you should be good to go from there.

That's what did it for me.

---

### Post by cowrecked on 2007-10-25
Maybe I'm missing something, but I can't get to a Linux desktop or menu other than the one off of the install CD/DVD.  Hitting escape only exits the installer, which doesnt seem to help, but I'll try it again.

---

### Post by cowrecked on 2007-10-25
hitting escape goes to the text based installation menu, where I have a command prompt of "boot:"

entering in that nano /boot/grub/menu.lst returns a "could not find nano in kernel" or some such error (different from the unrecognized command error)

---

### Post by cowrecked on 2007-10-25
again, my problem is that I cannot install from the LiveCD in the first place

this is the first attempt to install any linux OS on this system, I'm not coming off of any previous installations

but thanks for that suggestion!

---

### Post by Therion on 2007-10-25
Sorry, I was understanding your LiveCD was bringing you to the install menu at least.  You may need to use the text-based installer, but I'm not able to help you with that.  I'll see if I can't find you something that will help with that though...

Hopefully someone else will come along that can help you in the meantime.

---

### Post by Therion on 2007-10-25
Okay, I think the solution to your problem lies in using F6 from the boot menu.  You do get THAT far right?  You can at least see the options menu?  From that menu use F6 and remove the "quiet splash" boot option  and replace it with "nosplash".

That should allow you to do your install.  Then go back to my first post about editing the GRUB menu.  You'll need to do both.

If it makes you feel any better this is a known bug.  I had these same problems, sort of, when I installed the 64bit version myself.

---

### Post by Bannor on 2007-10-25
try adding naopic nolapic to the end of your boot line

---

### Post by chameleon_789 on 2007-10-25
I had the same problem. I got round it by pressing F6 at the menu and adding **noapic** to the second line down. If that doesn't fix it removing **quiet** can sometimes give a better insight into what's going on.

Alternatively, it could just be that both the "splash" screen and the window system of Ubuntu itself are set to a resolution your LCD can't handle. Signs of this would be the monitor going to standby but the CD / hard-drives are still spinning after the screen goes blank. If that's the case try setting the VGA option (F4, I think) to a resolution more likely to work with your monitor, eg 1024x768x32. It'll go blank at first but hopefully you'll get a picture when it boots into X. (From your specs you seem like you know your stuff, but I thought I'd spell it out for anyone else who happens on this thread)

---

### Post by cowrecked on 2007-10-25
thanks to both of you, all I have to do is change **splash** to **nosplash** in the F6 menu


heh, thats one issue down...since then, I've installed twice, only to get the Grub error 17 both times, I finally fixed the mbr on my main drive, so I'm finally back with a working OS...just not ubuntu yet

---

### Post by rob40wilson03 on 2007-10-26
i had the exact same problem as cowrecked, and changing splash to nosplash fixed that... so i went on with the install, install completed

now, however, when the GRUB menu comes up (i think that it's the grub menu, it's the menu where i can choose ubuntu 7.1, 7.1 recovery, memtest, etc. (please forgive my linux nubie-ness)) and i choose the first option, the screen goes blank just like before

i tried editing the boot line and removing the word splash, just like in Therion's first post, but that didnt work

i tried booting into recovery mode, no dice there either

What else can i do??

Thanks in advance!


Im running:

Core2Duo 6420
Geforce 8800 GTS (320MB)
Asus P5B-Deluxe

---

### Post by Therion on 2007-10-26
Now that you've done the install you need to go back and edit the menu.lst file again.  You fixed things the first time so you could get Ubuntu installed.  Now that it's resident and booting from your hard drive, you need to configure the actual menu.lst file ON your hard drive:

Boot from the hard drive.
When the GRUB menu comes up, hit Escape.
Select "Recovery Mode".
You'll end up at a command prompt.
From the command prompt:
```
nano /boot/grub/menu.lst
```
Find the Kernel line down near the bottom of the file, same line just like before, but it's going to be a looong line that runs off the end of your display, so you'll have to look for it.  Scroll all the way down to the bottom and make sure you edit the first instance of the Kernel line.
Remove "Splash".
Ctrl+X to Save.
Enter "Y" to overwrite the file.
Cross fingers.
Reboot.

---

### Post by rob40wilson03 on 2007-10-28
well when i boot my machine, the boot menu that comes up (grub menu? idk) gives me the choice of:

ubuntu 7.1
ubuntu 7.1 recovery mode
memtest
*something else*
OTHER OS's:
Win XP

if i hit escape here, nothing happens, and when i got to recovery mode on this same screen, it lets me edit the code, but never allows me to save anything

also the line that you say to edit is like the second line i believe, there is no scrolling all the way down, there are only maybe 4 lines total

i apologize for being a newbie at all this, but i guess i gotta start somewhere


thanks for all the help!!

---

### Post by cowrecked on 2007-10-28
I think you need to hit escape before the GRUB menu finishes loading.   I have mine set up with vista on one hard drive and ubuntu on a separate one; my motherboard allows me to choose which Hard drive to boot from.  I ended up installing ubuntu while my other hard drives were disconnected to resolve boot table issues.  Now, when I boot I need to hit ESC as the GRUB menu loads so that I can change the "splash" to "nosplash".  I don't remember what the menu options are, but I think I had to select the 2nd option.

I hope that helps and/or makes sense.

---

### Post by Therion on 2007-10-28
The GRUB menu only gives you a few seconds, right after the BIOS finishes loading.  You'll see it doing it's countdown and you don't have long to hit Escape before it goes into normal boot.  If you miss that opportunity, you'll need to reboot.  There might be other ways to edit the menu.lst file, but the procedure I outlined is what worked for me.

---

### Post by cowrecked on 2007-10-29
After you've hit escape, you see a menu with a few options, to run ubuntu, to run it in safe mode, etc.  You can hit "e" to edit the boot options of 7.10, which brings you to another menu, where you highlight the 2nd option (for me), hit "e", and change "splash" to "nosplash", then hit enter, then hit "B" to boot with that option.

Then once you've booted, you can edit the /boot/grub/menu.lst file by opening terminal and typing "sudo gedit /boot/grub/menu.lst", and changing the "splash" to "nosplash" towards the bottom.

Same basic idea as Therion, just gives you a GUI to work with.  Worked for me, at least.

---

### Post by rob40wilson03 on 2007-10-29
thanks for the good tips guys, soon as i get back from class im gonna give that a shot

..... i need to just buy a second HDD to run ubuntu on......

---

### Post by cowrecked on 2007-10-29
When I installed Ubuntu, I kept coming up with boot table errors and irregularities.  I'd suggest unplugging the hard drive of your existing OS (and any other drives) before installing Ubuntu.  This way, you can use the default install options for the boot table (as in not worry about it), and you'll always be able to run Ubuntu from that hard drive.  The only downside is that it will force you to manually select which hard drive to boot from as your BIOS loads.

Worst case scenario, this means a few keystrokes and a soft reboot. However, your motherboard might have a boot menu separate from the main BIOS Settings menu settings that will allow you to choose which HDD to boot from. You can also set in your BIOS which HDD you want to be the default booting device, usually.  For example, when I boot, hitting (F2) opens my BIOS settings menu.  Any changes here require a soft reboot afterwards, i.e. a few extra seconds.  If I hit (ESC), however, I can choose which device to boot from, and the system doesn't need to reboot or re-POST.

Try this, it worked for me.  Best part is that it doesnt interfere with your other hard drive(s) at all, so there's no risk.

---

### Post by Saint Angeles on 2007-10-29
> **rob40wilson03 said:**
> well when i boot my machine, the boot menu that comes up (grub menu? idk) gives me the choice of:

ubuntu 7.1
ubuntu 7.1 recovery mode
memtest
*something else*
OTHER OS's:
Win XP

if i hit escape here, nothing happens, and when i got to recovery mode on this same screen, it lets me edit the code, but never allows me to save anything!

go to recovery mode

type:```
sudo vim /etc/usplash.conf
```

it will ask you for root pass word.

set the correct resolution

reboot

---

### Post by netbandit on 2007-10-30
Try pressing F6 during the CD boot menu and adding this to the end of the line:

```

acpi=off

```

worked for me
-nb

---

### Post by Bart Ellebaut on 2007-11-05
Hello,

tried to install Kubuntu 7.10 with livecd.

Got the black screen problem, no splash.

First tried what was posted in this thread and nothing worked.

Then I tried the solution from [https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930](https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930)

```
edit /etc/initramfs-tools/modules
add the following

    * vga16fb
    * fbcon
    * vesafb

edit /etc/modprobe.d/blacklist-framebuffer
comment out the following (prefix with #)

    * blacklist vesafb
    * blacklist vga16fb

last but not least, run the following in a terminal

    * sudo update-initramfs -u
```

Now I get the splash screen, but it is followed by another black screen instead of my login screen!! What now??

---

