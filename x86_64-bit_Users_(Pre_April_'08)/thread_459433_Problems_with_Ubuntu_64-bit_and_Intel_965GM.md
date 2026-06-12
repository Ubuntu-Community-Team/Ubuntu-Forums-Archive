---
title: "Problems with Ubuntu 64-bit and Intel 965GM"
date: 2007-05-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by mr.snuff on 2007-05-30
Hi,

I bought a new laptop and thought that would be a good opportunity to start using Ubuntu instead of Windows. I had installed a version of Ubuntu before but didn't use it very much. So I would say that I am quite unexperienced with Linux and Ubuntu.

My problem is that I don't get the Intel 965GM Express Chipset with GMA X3100 working. When I change the driver in xorg.conf from "vesa" to "intel" Ubuntu is not able to start the GUI anymore and shows me the following error:
```
GARTInit: Unable to open /dev/agpgart (No such file or directory)
```

I found these instructions and tried to follow them:
[http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)

But when I execute "make menuconfig" and go to Device Driver -> Character devices -> /dev/agpgart (AGP Support), I can't enable it! 

After some testing and trying to get it work I think it is a specific problem with the 64-bit version of Ubuntu.
I installed the 32-bit version and after updating the xserver-xorg-video-intel driver everything worked fine. Also the agpgart option is enabled in the Kernel of the 32-bit version. Again, this option is not available for the 64-bit version! But the intel driver wants it anyway.

After installing the 64-bit version again, I encountered the same problems as before:
- "intel" as driver in xorg.conf is not working, I don't get the GUI (xserver I think) started.
- agpgart is not an option in the kernel, so I can't enable it.
- after all I don't get the intel graphics to work.

So in my opinion there MUST be a difference between the 64- and 32-bit version in view of the intel graphics. I have a brand new Thinkpad T61 with new Santa Rosa platform and the newest intel chipset (Intel 965GM Express Chipset). Maybe the architecture of my pc is not supported yet? I have no idea actually. In my opinion there should be a way to get the intel graphics working for 64-bit as well, but I don't have any ideas how to do that at the moment.

I really hope that someone here has a solution for this problem. After one week only installing and trying to get it work I would really like to start actually working with this laptop.

Thanks for any help!

---

### Post by vitalik on 2007-05-30
Intel 965 and Santa Rosa is very new technology and not a lot of people have yet. It probably was not tested really good or maybe it is not supported by the kernel yet. Anyways Google is your friend use it.

---

### Post by mr.snuff on 2007-05-31
Well, I used Google for the whole last week and wasn't able to find a solution. That is the reason I posted in this forum. I was hoping that I would get some Ubuntu specific support...

I know that the technology of my system is quite new and thus it is not tested very well yet. But everywhere I read that the new Intel driver are supported and so on. And for 32-bit it is working fine, but not for 64-bit...? I just don't understand it.

---

### Post by jespdj on 2007-05-31
Here's a vague answer:

Your new laptop does not contain an AGP graphics card port, yet Linux thinks it does. I remember having seen this before in a post. There's probably a way (maybe a kernel boot parameter?) to make Linux understand that there's no AGP device in your computer.

Try searching for "Intel graphics", "AGP", "64-bit" etc., maybe you'll find something useful.

(I told you it was going to be a vague answer.... :) )

---

### Post by mr.snuff on 2007-05-31
Thanks for your answer! I feel like I have searched for everything already. Unfortunately there are usually just too many results and everything is too unspecific. But that might be because I don't really know what I have to look for. Maybe your hint with the boot parameter helps. I'll definitely try.

---

### Post by rjl6591 on 2007-05-31
You need to have package xserver-xorg-video-intel installed. This supports the 965GM chipset. It is in the Universe repository.

sudo apt-get install xserver-xorg-video-intel

---

### Post by mr.snuff on 2007-05-31
rjl6591, I had installed the package but it didn't work :/

---

### Post by rjl6591 on 2007-05-31
I wonder if you messed something up doing all that low-level stuff, which shouldn't be necessary.

I've been using Linux for 13 years and I gave up building my own kernels and editing X config files years ago. That sort of baroque nonsense just isn't necessary with a modern distro. I'm using Feisty 64-bit with xserver-xorg-video-intel on a 965G (not GM) machine right now. I didn't need to do anything other than install the package and possibly configure the X server with:

sudo dpkg-reconfigure xserver-xorg  

I'm not even sure I needed to do that. But everything is there in Feisty 64-bit, it just needs installing and configuring. AIUI the only difference between the 965G (X3000) and 965GM (X3100) is that support for the latter was specifically added to the newer driver, whereas the 965G works (after a fashion) with the old i810 driver that is installed by default.

---

### Post by rjl6591 on 2007-05-31
A couple of extra thoughts since my previous post:

1. Looking in my own xorg.conf, I see the driver is still "i810" even though I'm using the intel driver not the i810 one.

2. Have you tried loading the intel_agp kernel module manually and then restarting X?

sudo modprobe intel_agp
sudo /etc/init.d/gdm restart

---

### Post by mr.snuff on 2007-05-31
I didn't compile the kernel since I couldn't enable the agpgart module in the 64-bit version (it is enabled in the 32-bit version and for me that seems to make the difference!). I have installed the new driver as you described it but it just isn't working for the 64-bit version. I don't get the correct resolution. For the 32-bit version it is working. Although there my system freezes when I activate the gnome desktop effects or try to use Beryl. All in all VERY annoying since nothing is working really well when it comes to the graphics.

For me it seems that the new intel driver is just really bad. It's quite sad that I can't use Ubuntu the way I want it since I really wanted to switch to it and go away from Windows.

However, I still hope that there is a solution...

> **rjl6591 said:**
> A couple of extra thoughts since my previous post:

1. Looking in my own xorg.conf, I see the driver is still "i810" even though I'm using the intel driver not the i810 one.

2. Have you tried loading the intel_agp kernel module manually and then restarting X?

sudo modprobe intel_agp
sudo /etc/init.d/gdm restart

I tried it and it didn't work. I think our different experiences are based on the different chipsets/drivers we are using.

Could you tell me if Device Driver -> Character devices -> /dev/agpgart (AGP Support) in your Kernel is enabled for the 64-bit version?

---

### Post by rjl6591 on 2007-06-01
> Could you tell me if Device Driver -> Character devices -> /dev/agpgart (AGP Support) in your Kernel is enabled for the 64-bit version?

Where are you looking so see Device Driver -> etc?

But . . .

~$ ls -l /dev/agpgart
crw-rw---- 1 root video 10, 175 2007-05-31 18:10 /dev/agpgart
~$

I think that means yes.

---

### Post by mr.snuff on 2007-06-01
You should find 
Device Driver -> Character devices -> /dev/agpgart (AGP Support) 
in your kernel configuration that you open with "make menuconfig".

---

### Post by rjl6591 on 2007-06-03
OK. I've never built an kernel under Ubuntu. I'm using the stock one (linux-image-2.6.20-16-generic).

---

### Post by handband2 on 2007-06-05
I have a Dell Latitude D630 and had problems with the intel 965 graphics chipset. The following helped me to solve my graphics problem:
[http://ubuntuforums.org/showpost.php?p=2754506&postcount=4]("http://ubuntuforums.org/showpost.php?p=2754506&postcount=4")

Note* - I chose the video driver "intel" and until the driver is upgraded ([http://www.intellinuxgraphics.org/download.html]("http://www.intellinuxgraphics.org/download.html")) the resolution appears blurry.

---

### Post by mr.snuff on 2007-06-05
and you are using the 64-bit version? When I use the 32-bit version and install the driver I get the same result as you. It is working but appears blurry. However, if I use the 64-bit version of Ubuntu I get the message about the missing agpgart module.

Could you both check if agpgart is enabled in your current kernel configuration?
Just do the following:
bash# grep CONFIG_AGPGART /boot/config-<<your_kernel_version>>

"uname -a" can show you your current kernel version.

---

### Post by handband2 on 2007-06-05
mr.snuff,

I'll check mine out later and get back to you.  Till then see if this helps... According to [Intel Linux Graphics Driver Installation Guide]("http://www.intellinuxgraphics.org/install.html"):
> 4. Configuration
4.1 Load kernel modules

If agpgart and drm are not compiled into kernel, when system boot up you need load these kernel modules: agpgart, intel-agp, drm and i915.

To automatically load kernel modules when system boot up, you can edit file /etc/modules to add modules' name (on Debian/Ubuntu); or edit file /etc/rc.local to add lines such as: modprobe agpgart.
4.2 Enable Intel driver

Make sure intel driver is used in Xorg configure file (usually is /etc/X11/xorg.conf):

Section "Device"

               Identifier "name"

               Driver     "intel"

               Entries...

               ...

EndSection

Note: The old name i810 has been deprecated now.
4.3 Enable DRI

DRI (Direct Rendering Infrastructure) is a framework for allowing direct access to graphics hardware under the X Window System in a safe and efficient manner. You need enable DRI in xorg.conf.

Firstly, make sure the GLX and DRI modules are being loaded:

Section "Module"

    # ...

    Load "glx"

    Load "dri"

    # ...

EndSection

Then, set the permissions for DRI appropriately. To allow anyone to use DRI, do:

Section "DRI"

    Mode 0666

EndSection

After restart X server, you can check whether direct rendering is enabled by running glxinfo, the output of glxinfo should show:

direct rendering: Yes


I also found this on launchpad:  [Fiesty i965 graphics support]("https://answers.launchpad.net/ubuntu/+source/xorg/+question/7274")

---

### Post by UBfusion on 2007-06-05
I don't know if this will help, but I was stuck too some hours ago when installing my Feisty x64 on my Asus P5B-VB featuring 965G (aka G965): [COLOR="Red"]don't enter any memory value during the configuration of the intel driver![/COLOR]

Details: After installing feisty, I changed the default driver to intel and ran dpkg-reconfigure. At the point where it asked for the AGP video memory I was absent-minded and entered 256 MB.  Starting X immediately complained about not being able to find the memory, so I reran dpkg-reconfigure, this time leaving the memory setting blank (if you read the help text, it says that the driver can figure that out for itself). The intel driver worked like a charm, even desktop effects.

My guess is that people struggling to force their 965G to work with 384 MB of memory as advertised in the specs, will be very sorry and as a bonus during the process their X will crash. There are many flavors of 965G and certainly mine is not a true X3000 that can do 384 (a lot of users weep over the issue in the Asus forums...).

---

### Post by mr.snuff on 2007-06-05
Handband2, thanks for checking later. I tried the installation guide but it didn't work. The guide describes that I should enable agpgart in the kernel and I can't do that since it is disabled.
As for the discussion on launchpad I think they are speaking about the 32-bit version and this one is running fine for me.

UBfusion, I think I tried to reconfigure it with both 128000kb and no value. But I will try again to be sure.

---

### Post by mr.snuff on 2007-06-08
I upgraded to the Gutsy kernel that solved some problems but also created new ones :(

You can find a description of the new problem here:
[http://ubuntuforums.org/showthread.php?t=467036]("http://ubuntuforums.org/showthread.php?t=467036")

If someone has an idea...

---

### Post by handband2 on 2007-06-19
I want to thank user cnshzj007 for helping me. cnshzj007 did his on Feisty I did the same thing for Gutsy. This seems to fix it on both. Now I got the blur gone on my Latitude D630 with the Intel 965GM X3100.  Everything looks crisp and clean. Here is the steps cnshzj007 shared with me:

Log in as root
```
$ su
```
Install dependencies
```
# apt-get install build-essential xorg-build-macros xorg-dev mesa-common-dev libdrm-dev x11proto-video-dev libxv-dev libxvmc1 libxvmc-dev x11proto-fonts-dev x11proto-xf86dri-dev libdrm-dev x11proto-gl-dev xserver-xorg-dev gawk
```
Download source files:
```
# apt-get source xserver-xorg-video-intel
```
Move to xserver-xorg-vidoe-intel directory
Feisty
```
# cd xserver-xorg-video-intel-1.9.94/
```
Gutsy
```
# cd xserver-xorg-video-intel-2.0.0/
```
Change i830_lvds.c file
[COLOR="Red"]**Goto line 230 and delete (PFIT_ENABLE | VERT_AUTSCALE ....) and replace with (0)**[/COLOR]
```
# vim src/i830_lvds.c
```
save and quit vim
Make .deb file
```
# dpkg-buildpackage -rfakeroot -uc -b -d
```
Go back one file
```
# cd ..
```
Install .deb file
Feisty
```
# dpkg -i xserver-xorg-video-intel_1.9.94-lubuntu3_i386.deb
```
Gutsy
```
# dpkg -i xserver-xorg-video-intel_2.0.0-1ubuntu2_i386.deb
```

I'm attaching the .deb's built for those who might want to try it for Gutsy Gibbon and/or Feisty Fawn.

Sources:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61)
[http://ubuntuforums.org/showthread.php?t=464907](http://ubuntuforums.org/showthread.php?t=464907)
[http://ubuntuforums.org/showpost.php?p=2860877&postcount=9](http://ubuntuforums.org/showpost.php?p=2860877&postcount=9)
[http://ubuntuforums.org/showpost.php?p=2860913&postcount=34](http://ubuntuforums.org/showpost.php?p=2860913&postcount=34)

---

### Post by mr.snuff on 2007-06-19
Hi!

Thanks for the reply! I also found the thread describing this approach and tried it. It solves the blurry screen problem but didn't solve the resolution problem. When I use Gutsy I still have this problem:

[http://ubuntuforums.org/showthread.php?t=467036](http://ubuntuforums.org/showthread.php?t=467036)

I installed Feisty again, did the steps you described and now the resolution is working. But now Beryl is not working anymore. As soon as I start it and click something my system freezes. It seems that I don't get working everything (resolution AND Beryl). :(

However, maybe there will be a solution for Beryl in the next time. Do you use Beryl?

Anyway, thanks a lot!

---

### Post by handband2 on 2007-06-20
mr.snuff,

Using Beryl and Compiz freezes my system also.  I guess we'll have to wait till an update to the driver with fixes to these problems.  

At least now we can view our desktops with getting a headache from the blur :)

---

### Post by mr.snuff on 2007-06-20
yeah, that's right. But it would be really nice to use Beryl. The weird thing is that Beryl was working with Gutsy but then I had other problems...

So far I couldn't set up an installation that had everything working :(

---

### Post by digitaldoug on 2007-06-22
> **mr.snuff said:**
> Handband2, thanks for checking later. I tried the installation guide but it didn't work. The guide describes that I should enable agpgart in the kernel and I can't do that since it is disabled.
As for the discussion on launchpad I think they are speaking about the 32-bit version and this one is running fine for me.

UBfusion, I think I tried to reconfigure it with both 128000kb and no value. But I will try again to be sure.

SUCCESS!!  I would like to thank the people posting to this forum.  I was just about to
give up on feisty.  I have a HP Pavillion DW6500t 4GB with:
Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz
and GM965 (X3100). 
 I am running 64 bit OS "stock" kernel (no recompile necessary).
The trick was to configure with "no value" and then change the xorg.conf file to contain
the correct resolution.  Mine is 1280x800. Possibly the adding the "Modeline" helped.
X has worked flawlessly for about a week.
Now I just need to get "network manager" to work.

Misc data, sorry I do not know how to "box" it up, this is my first post.

$uname -a
Linux ubuntu 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux 

$lsmod | grep -i intel
snd_hda_intel          24224  2 
snd_hda_codec         262528  1 snd_hda_intel
snd_pcm                92808  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    68904  14 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              29504  1 
snd_page_alloc         11792  2 snd_hda_intel,snd_pcm

$cat /etc/X11.xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc101"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "PS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
        Option          "MaxTapTime"            "0"
        Option          "MaxTapMove"            "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel 965GM (3100)"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
#       HorizSync       28-49
#       VertRefresh     43-72
        Modeline        "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel 965GM (3100)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

$grep CONFIG_AGPGART /boot/config-2.6.20-16-generic
$<nothing>

---

### Post by mr.snuff on 2007-06-22
Yes, the resolution is working :)

But what about Beryl or Compiz? Is that working for you as well? Some eye candy would be really nice...

---

### Post by thesnowgoose on 2007-06-28
I have another problem on X3100 - Amilo Pi2515 Santa Rosa.

I have applied patch that corrects fonts displaying. But there's a big problem with smooth gradients.

Let's see : [http://rael.rohan.one.pl/shots/display.png](http://rael.rohan.one.pl/shots/display.png)

Drivers from git repositories on intellinuxgraphics.com , I'm not Ubuntu, but Gentoo user - but it makes no difference in this topic I think.

Cheers

---

### Post by otaviofcs on 2007-09-02
thanks digitaldoug. I had the same problem and solve it with your post!

---

