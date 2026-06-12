---
title: "Upgraded to Hardy and Nvidia problems."
date: 2008-05-04
forum: x86 64-bit Users
---

### Post by JudasReanimated on 2008-05-04
Well I've upgraded to Hardy from Gutsy, and apparently lost my graphics driver update in the process in favor of the older versions. So I was stuck in 800x600, and when I tried to update my drivers, everything loads fine, then doesn't save, nor work. 

Shutting down the computer and restarting it doesn't save the configuration. 

I've tried Nvidia's .run file with xserver shutdown, and still nothing, I've tried Envy, Restricted Driver Manager, and all yeild the same, it's installed, but when I click Nvidia-Settings it tells me to configure the xserver. So I,

```
Sudo nvidia-xconfig
```

Which meets with success and doesn't change a thing.

Any ideas?

---

### Post by warpuck on 2008-05-04
I have had the same experience. I got 2.6.22-14 to go to desktop. it lost some thing that 2.6.24-16 shares. I thought the latest update might have it in jockey-gtk and jockey-common....well now I got 2.6.24-17 stuck @ (initramfs). 
I think it may have something to do with Driver 'sr' needs updating-please use bus_type methods. I keeping digging on that even though I have a hard time with installing flash player. At least that is what I see when I tried the recovery mode. (24-16)

Use the 22-14 recovery mode when you get the 800x600 or 640x480 screen only choice. it should offer to init Xorg repair settings or something like that. When it is done reboot run 22-14 and open synaptic package manager and search for nvidia and pick the right ones. note if it says crossfire and you dont have ati skip it. my board (abit an 52) is nvidia chipset and a nvidia graphics card. I needed to make 3 choices and three boot cycles. I did them 1 at time so could know it needed to be removed. it works now (1024 x 768) even got my sensor panel back. I doubt that core O is running at -16C, but at least is is doing something.

---

### Post by JudasReanimated on 2008-05-04
Well I did the repair option and nothing still. It doesn't seem to take any of the settings even though they go through without a hitch or error.

---

### Post by Nubsauce on 2008-05-04
Maybe my meds are messing up my thought process at the moment...  but are you having problems with your screen resolution staying, the drivers functioning or both?  heh

/kicks the flu..

---

### Post by KillaKurt on 2008-05-04
> **JudasReanimated said:**
> Well I've upgraded to Hardy from Gutsy, and apparently lost my graphics driver update in the process in favor of the older versions. So I was stuck in 800x600, and when I tried to update my drivers, everything loads fine, then doesn't save, nor work. 

Shutting down the computer and restarting it doesn't save the configuration. 

I've tried Nvidia's .run file with xserver shutdown, and still nothing, I've tried Envy, Restricted Driver Manager, and all yeild the same, it's installed, but when I click Nvidia-Settings it tells me to configure the xserver. So I,

```
Sudo nvidia-xconfig
```

Which meets with success and doesn't change a thing.

Any ideas?

I too had this problem (but I wasn't upgrading or anything, it was my first linux OS install and it was Gutsy, not Hardy).  Same thing you're saying, the nvidia-xconfig seems to run okay and then it still won't use the driver correctly and it kept trying to run in safe-graphics mode...

A few questions:

Did you enable the restricted driver for nvidia?

What kind of monitor are you using? (I was using a 32" Sharp 1080p LCD...I'm using a Samsung 22" LCD now and the driver works fine, upgraded to Hardy too)

---

### Post by JudasReanimated on 2008-05-05
Well I found out something interesting.

I deleted every instance of Nvidia on my Distro, and then,

```
Sudo /etc/init.d/gdm stop
```

Then I,

```
Sudo sh Nvidia.run "what I named the 169.12 Driver"
```

It loads the driver ok until it comes up with an error trying to replace the I believe it's called tthe libswb.so or something similar "I'm at work at the moment". 

So I click continue anyway, and it's still in safe graphics mode, so I,

```
Sudo rm blahblah.so
```

Retry the install, it goes without a hitch, yet still in safe graphics mode.

So I try something else, and redelete every instance of Nvidia again, well I forget to get rid of the libsomething.so and I'm doing the install and it gives me the error about being unable to replace the file, so I click cancel and restart to get rid of the file again, and my resolution is fine and everything is connected properly, except my computer is moving extremely slow, and has like 75+% on each core running constantly.

That's where I'm at now at least.

Also I'm running on a Clevo Laptop with a 8400 Nvidia card. Monitor is a 17" with 1440x900

---

### Post by philinux on 2008-05-05
What does system>admin>"hardware drivers" come up with?

---

### Post by JudasReanimated on 2008-05-05
I have uninstalled the Hardware Driver Manager, but before it just had the Nvidia listed as enabled whenever I installed the drivers.

I removed it cause it created a lot of issues.

---

### Post by soxs on 2008-05-06
Did you allready try envyng-gtk from the repos? Try installing (first remove your old garbage drivers) your driver with envyng(-gtk)

---

### Post by JudasReanimated on 2008-05-06
My first post states that I tried Envy, but yes I've tried the GUI frontend.

---

### Post by peakshysteria on 2008-05-06
Uninstall the driver via Envy. Then uninstall Envy. Then reinstall the Hardware drivers manager. Reboot. Check that the Hardware drivers manager don't have the proprietary driver checked (if it's present at all).

Then in terminal: 

Sudo displayconfig-gtk (or without -gtk in Kde if i remember right).

Restart x (ctrl + alt + backspace) or reboot.

Then in terminal (as root):

sudo dpkg-reconfigure -phigh xserver-xorg

Restart x (ctrl + alt + backspace) or reboot.

And if you're sure your sure you're rid of all bits and pieces of the driver start fresh:

Either; Envy, Hardware driver manager/the proprietary driver or manuall install.

---

### Post by Saubazi on 2008-05-06
I also had problem the graphical interface starting with 800x600. However, I noticed that for some reason the machine was still booting with Gusty kernel 2.6-22-14 - I noticed that there was never kernel under /boot - was it 2.6.24-16 or whatever - I manually edited menu.lst to the highest version and after that the desktop came up normally...

---

### Post by neolithicsilence on 2008-05-06
There was an option called Screens and Graphics under Administration in 7.10.. I dont see it in 8.04.. I'm unable to select my monitor type.. Any help on this?

---

### Post by peakshysteria on 2008-05-06
As mentioned above: run sudo displayconfig-gtk from a terminal

---

### Post by JudasReanimated on 2008-05-07
Sorry man that's basically what I've done all along, but to humor you, and myself I tried it with a restart after every move, and still 800x600. 

I used EnvyNG, Manual, and tried Restricted again, and no go man.

---

### Post by peakshysteria on 2008-05-08
Have you tried Saubazis suggestion above as well? And have you uninstalled the driver via Envy after you have enabled it with Envy, then uninstalled Envy and rebooted before you proceed?

Or:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI?action=fullsearch&context=180&value=nvidia&titlesearch=Titles](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?action=fullsearch&context=180&value=nvidia&titlesearch=Titles)

[http://www.funnestra.org/ubuntu/hardy/#nvidia-driver](http://www.funnestra.org/ubuntu/hardy/#nvidia-driver)

[http://ubuntuforums.org/search.php?searchid=40794148](http://ubuntuforums.org/search.php?searchid=40794148)

[http://tuxicity.wordpress.com/2008/03/05/ubuntu-hardy-nvidia-and-craziness/](http://tuxicity.wordpress.com/2008/03/05/ubuntu-hardy-nvidia-and-craziness/)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by JudasReanimated on 2008-05-08
I know all the Howto's and yes I've done it 100% the way it was supposed to be done, multiple times. When I did it for Gutsy it worked fine, right off the bat. Hardy just seems to not save config properly, or configure it properly it's self.

So I need some info outside of the basic Howto range, and more into the glitch , or miss configuration range.

If you look above it will only work if I cancel on the error while manually installing it, but then my GUI runs like a dieing slug on meth.

---

### Post by JudasReanimated on 2008-05-09
bump

---

### Post by maramot on 2008-05-09
> **Saubazi said:**
> I also had problem the graphical interface starting with 800x600. However, I noticed that for some reason the machine was still booting with Gusty kernel 2.6-22-14 - I noticed that there was never kernel under /boot - was it 2.6.24-16 or whatever - I manually edited menu.lst to the highest version and after that the desktop came up normally...

Thanks a lot mate, that did the trick for me. And I can even tell you what that "some reason" that you mention is. Here's my case:

I was joyfully running Gutsy until two days ago when I updated (over the net, not from a CD) to Hardy. Somewhere around the end of the installation after it had downloaded all the 1200+ packages (it took the damn thing about 2 hours to download them) I was asked what I want done with my menu.lst file -- do I want it changed, replaced, left unchanged etc. There was this drop down list I had to choose from.

Now, mentioning changes of my menu.lst made me jump because I had tuned it just right, so I could launch XP when I feel like playing some games (the only thing this OS is good for). Naturally I chose the option of leaving my menu.lst unchanged. That's how it was left with the old kernel version.

So for the last two days I've been banging my head in this resolution/driver/display problem, I had even glanced at your post the other day and the funniest thing - I even checked my /boot/ dir but I didn't see I have two kernels there, so I thought that since I was running ubuntu I could only be running it with the right kernel -- so my menu.lst was all right and I didn't look inside it until right now. :D

After I changed the entry in menu.lst (which the hardy installer would have done on its own if I had allowed it to), I enabled my proprietary driver through "jockey-gtk" (or simply System->Administration->Hardware Drivers), I did a reboot and the first thing I noticed was that my login screen was running both with the nvidia driver and in a good resolution. After logging in though I was returned to 800x600 but this time I knew something was up. I opened nvidia-settings and this time it didn't greet me with an error and there were many more (obviously, the standard amount ;) ) options available, among them - resolution settings. I set it to the maximum 1650x1050, and that's the resolution under which I'm writing you this.

Other people stuck in 800x600 while using the nvidia 169.12 driver -- check your /boot/grub/menu.lst file and make sure you have lines similiar to these:

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-[COLOR="Red"]2.6.24-16[/COLOR]-generic root=UUID=060b8e23-1393-46fe-b749-44f9010398dd ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=060b8e23-1393-46fe-b749-44f9010398dd ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

The first paragraph is the kernel you're starting ubuntu with and the version numbers should be those highlited in red in the example here. The version number in the "title" isn't important since that's just the label for the actual kernel you'll load. As you see mine still says Ubuntu 7.10 and so forth, even though I'm loading the newer 8.04 version with the newer 2.6.24.16 kernel. The second paragraph is for the kernel to be loaded when you're running in recovery mode. You should change that to the new kernel as well.

Make sure you have the new kernel, then try this method and post comments.

Thanks again to Saubazi :)

---

### Post by JudasReanimated on 2008-05-09
I cleaned my old Kernel out first thing, I'm using the latest 64 bit generic kernel.

---

### Post by maramot on 2008-05-10
If you're using the 64 bit kernel maybe you should check this guy's threads, Nebelhom's. He's also using the 64 bit kernel and has the same problem.
[http://ubuntuforums.org/showthread.php?t=785963](http://ubuntuforums.org/showthread.php?t=785963) -- His second thread
[http://ubuntuforums.org/showthread.php?t=776389](http://ubuntuforums.org/showthread.php?t=776389) -- His first one

Check them out if you haven't yet, they may suggest you something that will get you to the solution. Also, what is your xorg.conf like? Or it's being overwritten with the failsafe version every time you boot?

---

### Post by tenmoi on 2008-05-10
One thing that I have learned is that I should NEVER use the Nvidia driver provided by Ubuntu. The second thing is I should NEVER do a dist-upgrade.

In your case I think you forgot to remove everything that is **linux-restricted-***.If any trace of them is left over you will have to log in using the failsafe mode. For me I always have 4 packages to remove. After that I compile the driver and am ready to go.

P.S

Because you said you could still log in to a GUI I think there's nothing wrong with the monitor.

---

### Post by Zorael on 2008-05-10
Make sure you haven't blacklisted the nvidia module.
```
zorael@sunspire:~$ grep nvidia /etc/modprobe/blacklist*
blacklist-framebuffer:blacklist nvidiafb
```
It should *only* output that line in blacklist-framebuffer. If there are more lines, open that file up in a text editor with superuser permissions, find the line, and comment it out.

---

### Post by JudasReanimated on 2008-05-10
Yeah there isn't anything wrong with my monitor, it's a Clevo Laptop by the way, but other OSs work, Windows, Solaris, Linux distros, etc. The Laptop it's self is fine.

I check out what you said, but since my internet is toasted as well, per my other thread. I have to check from this OS then switch and give these a whirl. 

Thanks and more suggestions the better.

EDIT: Well I managed to get the driver loaded, but with another fun problem. What I did was.

```
sudo rm -rf *Everything named Nvidia, sans the install driver file.
```

```
sudo rm -rf *Everything Linux-restricted*
```

and finally the problem child it's self.

```
sudo rm -rf /usr/lib/xorg/modules/libwfb.so
```

Then I,

```
sudo /etc/init.d/gdm stop
```

```
sudo sh Nvidia.run
```

Everything went smoothly and the Driver installed, but I told it no on the question to auto update Xorg.

When it finished I,

```
sudo nvidia-xconfig
```

It backedup the file and everything, then of course for kicks I,

```
sudo rm -rf /etc/X11/xorg.conf.backup
```

To make sure that there was no way that blasted backup could be used anymore. Then I restarted the xserver.

Started Ubuntu backup and logged into the GUI, BAM the resolution was 1440x900 like I wanted.

Now for the next problem.

The system is crawling, and I do mean crawling. It takes about 30 seconds to open the terminal. 

Everything is moving at a standstill, and compiz is taking 45% of my cpu power, and my Duals are both running about 75% average and my ram is maxed out almost according to the system monitor.


So any ideas on this one, also I'm pretty sure it's that damned libwfb.so's fault somehow. <_<


Final Edit.....I think: I checked the blacklist and it was all well. Just so you know I followed everyone's advice.

---

### Post by tenmoi on 2008-05-10
Your system is kind of screwed up. I recommend doing a clean reinstall. Then remove everything linux-restricted and install build-essential and libxft-dev - the only things that I need to compile the module. I have never let the Nvidia compile and install 32 bit OpenGL compatibility library on my 64 bit system. 

And one more question, did you compile any programmes and upgrade the kernel without recompiling those against the new kernel?
I used to have my CPU running at full load when I opened UNikey, the Vietnamese virtual keyboard, which I compiled under .16. When I uninstalled and recompiled it for the new .17 kernel, things went smoothly. So I think you should consider this.

---

### Post by JudasReanimated on 2008-05-10
Thanks for the input, but I'd prefer to fix the issue at hand, and not take the simple clean and reinstall, though I seriously doubt that would fix my issue.

Also everything has been upgraded and I recompiled every program that I have issues with.

---

### Post by tenmoi on 2008-05-11
I notice now that you did "sudo rm -rf *Everything Linux-restricted*", which I doubt is the correct way to uninstall the modules. I recommend reinstalling the modules and then sudo -PURGE REMOVE them from the terminal or synaptics. DON'T **sudo -rf**.
The second thing I think is you open synaptics and then find the xserver-xorg-video-fbdev and see whether it is installed or removed. And then you should remove all the xserver-xorg-video-* drivers which are not necessary for your system. 

I did a file like this and the result is:
nam@ubuntu64:~$ file /usr/lib/xorg/modules/libwfb.so
/usr/lib/xorg/modules/libwfb.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), not stripped

So you perhaps deleted one important shared library. I did some goggling and found out that libwfb.so is provided by xserver-xorg and the Nvidia installer must make the symlink libnvidia-wfb.so.1 to libwfb.so if it is already in place. Here is the files in my usr/lib/xorg/modules

So this is all that I can help. My last recommendation is unless you now how to compile xorg server you should do a clean install. Or supply the modules folder with the files you can see in the attachment.

Bie.

---

### Post by JudasReanimated on 2008-05-11
Too be truthful I removed it via Synaptic, then got the left over files, ie: amd64.deb files, etc. So that should be fine.

The libwfb.so seems to be a concern for a lot of people, and for me you have to sudo rm -rf it in order to get the drivers to even install, and that's been that way since I upgraded to Hardy. 

I'm thinking about downloading the 8.04 Live CD, and installing it on another partition as a test OS, and see if I can get it working from there, then recompile my other setup in the same way.

I'm still convinced this is just a bug that should be fixable, and not a system fault that needs a complete reinstall.

---

### Post by JudasReanimated on 2008-05-13
bump

---

### Post by tenmoi on 2008-05-13
take a look here [http://www.nvnews.net/vbulletin/showthread.php?t=97998](http://www.nvnews.net/vbulletin/showthread.php?t=97998)

---

### Post by JudasReanimated on 2008-05-17
Alright I should've thought of this, but outside of working and what not my mind has been a bit off course, but I went ahead and disabled Compiz-real and that took care of the sluggishness, and High CPU/Ram pulling.

However I can no longer shutdown my GDM. When I attempt to it just shows some text about modules loaded properly, and does nothing else.

```
sudo /etc/init.d/gdm stop
```

Also in the wrong resolution if that means anything.

Any more suggestions?

---

### Post by JudasReanimated on 2008-05-18
bump

---

### Post by JudasReanimated on 2008-05-20
Bizumptiy bump bump

---

### Post by mudlogger on 2008-05-21
I had exactly the same problems on a clean install. I had to manually edit the xorg.conf file to get things to work. I'm using the nvidia-glx 1:96 drivers. No matter what I tried I wound up at 800 x 600 with an xorg.conf file that said configured device.

Not sure if this will help, but it worked for me.

---

### Post by tenmoi on 2008-05-22
> **JudasReanimated said:**
> Bizumptiy bump bump

What if you remove the nvidia driver and

sudo apt-get -P remove xserver-xorg xfonts* gnome

and 

sudo apt-get install xserver-xorg xfonts* gnome

and then you install the nvidia driver as suggested in the previous posts.

Hope this may help.

---

