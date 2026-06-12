---
title: "Corrupt Jaunty Boot Graphics"
date: 2009-06-07
forum: x86 64-bit Users
---

### Post by DitchingMS on 2009-06-07
Hi All

Recently installed 64 bit Jaunty with success, got my Speedtouch 330 working, got my wireless network up, everything going great so decided to go through the add/remove programs list and get myself some new apps and games. Can't remeber the last thing I did before I shut down but now when I start up I'm confronted with a corrupt display and can't go any further. The PC boots fine, loads the 'ubuntu' loader with the moving line, takes about 20 secs as usual, then just as it's about to go to the desktop the graphics corrupt. There seems to be random graphical elements of the BIOS, the boot loader, and random lines of colour. It's as if the random elements are still hanging around in graphics memory somewhere. A few seconds later, there is a momentary blackout then it goes back to curruption. This repeats a few times and then the system just seems to hang. It behaves as if the graphics know they're corrupt and are trying to reboot, or perhaps the OS is loading in the background and things are just running normally behind the corruption. I managed to load the recovery options, and did every option available, such as repair etc. Nothing has worked. I tried to boot the Live CD for a Windows-esque Repair Install type function, but no luck. The Live CD boots fine, everything working 100%, I just don't know what to do. It appears that the Live CD does not interact with the base installation, so I don't know if I can repair from here.

I just want to repair the install if at all possible, as I downloaded so much data and tweaked the system so much I am loathe to lose it all. Perhaps I could simply uninstall selected items one at a time or carry out some other systematic repair? Or reinstall the default graphics drivers? I did not intentionally try to install any replacement graphics drivers, although this is not an impossibility. By the way I'm running an ATI 2900 Pro. I'm aware they can be buggy but for the time being I just want a basic email/Internet/WP machine.

I am a total noob so please don't ask me to do anything tricky.

Thanks all in advance, I'm sure someone can help me out. I'm very impressed with this whole open source community idea!

---

### Post by lozanoa11 on 2009-06-07
have a similar problem also only on just one of my monitors.

---

### Post by DitchingMS on 2009-06-09
Hi,

Tried a huge list of possible fixes but no luck yet. I watched Grub loading and it had a black screen with a long string of white text then 'Loading...` and then it corrupted. I tried using key combinations to exit the GUI, reboot, get to a command line, etc., but it is completely frozen save for a few occasional short blips on the HDD. I waited for about a minute and nothing, then I did a hard reset.

I've managed to boot into the Grub recovery menu and tried every one of the menus in it, such as recover/repair etc. I tried numerous times to select the command prompt so that i could try to uninstall suspect drivers but when I try to get in I have to input a Root password and for some reason my password does not work. The keyboard is completely inoperative and although the caps lock and scroll lock lights will go on and off, text does not appear when I type and the cursor does not move. When I hit Enter it says password not valid. I don't even know if it's accepting the password I'm typing somehow, or if it can't read the keystrokes at all. No keys work except the light up ones and Enter.

The only other alternative I have tried is to boot from the Jaunty Live CD. If I boot to the command line from the CD it works ok but it looks like a limited set of commands and I couldn't do what I wanted to. I therefore booted into the Live CD proper, and tried to use the GUI to do some digging, but no luck. I edited the xorg.conf as many people suggest but it doesn't seem to work. It seems that xorg.conf is not really designed to define the driver and I need to edit something else. I have tried uninstalling, reinstalling and many other things but as I said I'm a total noob and have no idea what I should be doing. When I tried to uninstall and reinstall packages I couldn't tell whether it was doing it to my HDD install or the Live CD version.

Latest is it's still knackered.

HELP?!

---

### Post by cariboo on 2009-06-10
It would help if you told us what graphics chipset your computer has.

I have Jaunty installed on three different computers, an HP laptop with an ATI chipset, a media center pc with an Intel chipset and My main system with an Nvidia chipset.

Of the three, my main system is the only one that worked with the restricted driver suggested in System-->Administration-->Hardware Drivers. My laptop has an ATI chipset that isn't supported anymore, but using the open source radeon driver works, even with full visual sffects enabled.

My media center pc, I use for watching full screen video on my 32" LCD HDTV, I used the drivers from [here]("https://launchpad.net/~intel-gfx-testing/+archive/ppa") to get rid of video tearing problems. I'm not sure how good they are for gaming, but I am happy with the playback quality of the videos.

My main computer has a Nvidia 8500GS with 512Mb and uses the 180.44 restricted driver. It installed with no problems and I'm very happy with the performance.

Oops I forgot which forum I was in, both my main system and my media center pc are using the 64-bit versions, while the laptop is running the 32-bit version.

---

### Post by DitchingMS on 2009-06-10
My card is an ATI 2900 Pro I think, R600? I'm not looking for graphics upgrades and performance right now, I just need to find a way to get into the OS. The Live CD works fine. The install used to work fine before I did some 'updates' and 'add/remove programs'. Trouble is, I don't know what driver the CD loads and how to get back to it. 
 
I might be able to work through a command prompt but there's the problem with the keyboard not working properly (read my previous posts)! Last thing I tried was to go through Grub, edit one of the lines to add 'xforcevesa' (recommended elsewhere on the net) because I though this might force the vesa driver, but this didn't work either.
 
Most of the threads recommend editing xorg.conf to add in the vesa driver reference but apparently from Heron onwards the xorg.conf doesn't work this way. Therefore I need to modify the 'x' configuration using another method. Or at least that's my understanding of it.

---

### Post by stephan0h on 2009-06-11
Hi,

You apparently already checked out my thread about a similar problem ([http://ubuntuforums.org/showthread.php?p=7435550](http://ubuntuforums.org/showthread.php?p=7435550)). What I did to fix it was the follwing:

Try to login to the machine somehow - on my PC the keyboard was locked due to this graphics problem, so I logged in from another machine via network with ssh (ssh user@ip-address). You can also try to start ubuntu in repair mode (or whatever it is called). To do this you have to get into the grub menu when the system starts up. (I tried - but it was not allowing me in with the password i provided ...)

Once you're logged in try to remove your current ati-driver. You don't need to edit xorg.conf for this, just enter 'sudo dpkg remove <whatever>'. See my thread.

Restart your machine - now you should be able to login in some basic graphics mode.

Finally install a working graphics driver. I used the open ATI-driver.

Hope that helps,
stephan

---

