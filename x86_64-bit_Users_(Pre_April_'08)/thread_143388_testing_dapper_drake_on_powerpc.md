---
title: "testing dapper drake on powerpc"
date: 2006-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by ssam on 2006-03-12
now might be a good time for people to give dapper drake a test to check that things like hardware recognition work well on powerpc. for breezy quite a few mac users found that things like graphics cards were not correctly configured. the developers only have a limited number of machines to test on, so obvious bugs can easily be missed.

live cds of the latest flight (beta) can be downloaded from [http://cdimage.ubuntu.com/releases/dapper/flight-5/](http://cdimage.ubuntu.com/releases/dapper/flight-5/) . for testing get the live cd, as it will not effect your hard disk, and current installation.

you can write to a cd by right clicking on it and choosing 'write to disk'. its usually recomended to use a low writing speed.

to boot it, put it the drive, restart and hold down 'C'.

hopefully it will boot up, log into gnome and work.

if you have any problems first check they have not already been reported by doing a search [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs) . if they are reported but marked 'unconfirmed' then click on unconfirmed and change it to confirmed, in the comment note that you are seeing the problem too and your hardware. if you can't find the bug then report it at [https://launchpad.net/distros/ubuntu/+filebug](https://launchpad.net/distros/ubuntu/+filebug)

---

### Post by engla on 2006-03-12
umm.. I agree! :-)

I have already grabbed the livecd, and I'm planning to try this later today. 

Did the same thing in the end of february, and basically most things seemed to work even then.
The results back then were basically this:
DRI/3D acc on by default, suspend still working reliably
Sound not working
This was on my ibook G4/1.2GHz.
I've heard that sound is fixed and I'm looking forward to try.

---

### Post by 3rdalbum on 2006-03-13
Is sound-in working in Dapper? It's apparantly an ALSA problem, but I've heard that people have been working on it.

---

### Post by Torrance on 2006-03-13
I'm using an iMac G5 17 inch, and there are two big Dapper issues for me...

Sound card recognition is the biggest problem for me. Not only is there no sound, its loading up "PowermacsAWACS" sound driver which is causing conflicts in the system, so that the mouse and keyboard lock up at the login screen when a sound is attempted to be played. I've been able to override this issue by disabling the ESD sound server on startup (this is what I also had to do with Breezy) but once I'm logged in ANY program that attempts to use sound will once again freeze the keyboard and mouse (whereas Breezy was fine in this resect). Logging out also freezes the system, presumably because it is trying to play sound.

Besides sound, the only other issue is that there is no thermal fan control - they run at full speed and are loud. There are patches around the internet for this, but it'd be nice for us newbies if they we built into the final distro.

Everything else works well, video looks good, the new theme is beautiful and generally it's a top notch job! :-)

---

### Post by spaceballl on 2006-03-13
I have an iBook 12".

Sound works great. Also with some tinkering, Airport Extreme now works great as well.

I really love the system i've got going on. I mount my OS X partition and then I used Banshee to play my iTunes music library songs in Ubuntu.

I have two main problems that I can't seem to get fixed.
1. BLUETOOTH MOUSE / KEYBOARD - oddly enough, when my computer boots up, I can use my bluetooth keyboard to select my OS. Then when the mouse cursor first shows up as X boots up, I can move the mouse with my bluetooth mouse. Then unfortunatley, as soon as GDM comes up, the bluetooth mouse/key lock up and I'm stuck using the laptop keyboard and trackpad. I've reported the bug here:
[http://ubuntuforums.org/showthread.php?t=134910](http://ubuntuforums.org/showthread.php?t=134910)
and here:
[https://launchpad.net/distros/ubuntu/+source/bluez-utils/+bug/32415](https://launchpad.net/distros/ubuntu/+source/bluez-utils/+bug/32415)
I can't get any responses about what the problem is though. If you depend on bluetooth keyboard/mouse, might want to wait.

The only other problem I've had which I describe here:
[http://ubuntuforums.org/showthread.php?t=143748](http://ubuntuforums.org/showthread.php?t=143748)
is trying to get XGL/Compiz to work on the iBook. So far, i've been met with no success.

Besides those two problems, The newest flight has been a pretty amazing release for me. Right now i still use OS X probably 70% of the time, but back when breezy was released, it was more lik 90%. Each release wins me over more and more. I really look forward to the next big release :-).

---

### Post by eidex on 2006-03-13
[QUOTE=spaceballl]
Sound works great.
[/QUOTE]

Sound does not work for me, tried all settings in alsamixer without success, did it work "out of the box" for you?

---

### Post by spaceballl on 2006-03-13
Yah it worked "out of the box" for me. Well for me, sound came muted. So the volume control in the upper right has like a little red X on it. Right click it and then go to volume properties and I think you'll find that you need to unmute something. Not sure why it ships like that. Let me know if that was your problem.

Edit: Right clicking by default is either f10 or f11...

---

### Post by ssam on 2006-03-13
good work people :-)

the sound was reported to be fixed with
[https://launchpad.net/distros/ubuntu/+bug/32151](https://launchpad.net/distros/ubuntu/+bug/32151)
that fixed it for me. if its still not working the file a new bug

i can't see any open bugs about fan control in macs. please file one linking to the source of these patches.

does anyone else get the bluetooth problem? if so can they confirm the bug, that gives it a higher chance of being worked on be the developers.

---

### Post by ThomHolwerda on 2006-03-13
Hi all!

Magnificent work you guys've done on Ubuntu/PPC. I made it the subject of my [last column](http://www.osnews.com/story.php?news_id=13955) on OSNews-- I was really surprised by the quality. Still, there were a few glitches, and I'll dive into launchpad asap to see if they're filed or not-- if not, I'll report them. I'll mention them here too now. I'm testing on a G4 iBook 12".

A lot of problems when installing packages-- a lot of them seem to be missing. Dependencies of xine-ui, vlc, some libs needed for dvd playback, etc. are missing. It happens just a little too often to be coincidence. The weird thing is this: I can find some of the missing packages in the debian archives, with ppc versions, and more often than not, I can find them via the web in Ubuntu's archive too! 

I'm being a bit too generic here, I know, but I haven't made any notes during my attempts at getting xine/vlc/dvd playback. I'll attempt at this again, and then I'll be sure to remember the details.

Another issue is sound: playback works, but is very jerky.

Also, network manager is kinda... Broken. I can only apply my configuration options for my Airport card the hard way (I've set up a script), but not via network manager. This is annoying: netw. manager now keeps insisting eth0 (my airport card) isn't configured-- even though I really am browsing the web wirelessly thanks to my script. Applying the same settings as in the script via netw. manager is impossible-- the 'activating' dialog keeps going forever.

Those are the major issues I encountered. I'll be sure to dive into launchpad to see if they're known or not!

Note: all these issues apply to the install CD-- NOT the live CD.

---

### Post by spaceballl on 2006-03-13
[QUOTE=ThomHolwerda]I can only apply my configuration options for my Airport card the hard way (I've set up a script), but not via network manager. This is annoying: netw. manager now keeps insisting eth0 (my airport card) isn't configured-- even though I really am browsing the web wirelessly thanks to my script. Applying the same settings as in the script via netw. manager is impossible-- the 'activating' dialog keeps going forever.[/QUOTE]
I have the exact same issue. I make a script for my airport extreme card, but it definitely cannot be handled by the GUI yet. I figure this is probably just due to how new the drivers are

---

### Post by Xappe on 2006-03-13
sound is not working on g3 ibook 2 rev. 2 700 MHz on up to date dapper.
the soundcard is not recognized by the kernel/alsa:

[https://launchpad.net/products/alsa-utils/+bug/30963 ]("https://launchpad.net/products/alsa-utils/+bug/30963")

I also find X to be quite unstable as in slowdowns and lockups. I can't see the cause yet, though.

Sleep seems to work quite well from start (on breezy some scripts and patches were needed to get this to work).

---

### Post by Torrance on 2006-03-13
I put the iMac thermal fan problem on Launchpad, but I'm not sure its in the right place: [https://launchpad.net/distros/ubuntu/+bug/34723](https://launchpad.net/distros/ubuntu/+bug/34723) ???

Also, if anyone else has an iMac G5 can they please confirm the bug?

With regards to the iMac sound conflict freezing the keyboard and mouse, that bug is here: [https://launchpad.net/distros/ubuntu/+source/gdm/+bug/29368](https://launchpad.net/distros/ubuntu/+source/gdm/+bug/29368)

---

### Post by eidex on 2006-03-14
[QUOTE=spaceballl]Yah it worked "out of the box" for me. Well for me, sound came muted. So the volume control in the upper right has like a little red X on it. Right click it and then go to volume properties and I think you'll find that you need to unmute something. Not sure why it ships like that. Let me know if that was your problem.

Edit: Right clicking by default is either f10 or f11...[/QUOTE]

After patching to flight5 sound is working!

---

### Post by eidex on 2006-03-14
[QUOTE=ssam]

does anyone else get the bluetooth problem? if so can they confirm the bug, that gives it a higher chance of being worked on be the developers.[/QUOTE]

As I posted 2 weeks ago ([http://ubuntuforums.org/showthread.php?t=134910](http://ubuntuforums.org/showthread.php?t=134910)) I have to manually start the bt mouse:

```
paul@wolf:~$ hidd --search
Searching ...
        No devices in range or visible
paul@wolf:~$ hidd --search
Searching ...
        No devices in range or visible
paul@wolf:~$ hidd --search
Searching ...
        No devices in range or visible
paul@wolf:~$ sudo hidd --search
Password:
Searching ...
paul@wolf:~$ sudo hidd --search
Searching ...
paul@wolf:~$ sudo hidd --search
Searching ...
paul@wolf:~$ sudo hidd --search
Searching ...
paul@wolf:~$ sudo hidd --search
Searching ...
        Connecting to device 00:0A:95:0A:3E:6C
paul@wolf:~$


```

The mouse (Apple Bluetooth) was always on but could only be found after several tries!

---

### Post by ssam on 2006-03-14
[QUOTE=Torrance]I put the iMac thermal fan problem on Launchpad, but I'm not sure its in the right place: [https://launchpad.net/distros/ubuntu/+bug/34723](https://launchpad.net/distros/ubuntu/+bug/34723) ???

Also, if anyone else has an iMac G5 can they please confirm the bug?

With regards to the iMac sound conflict freezing the keyboard and mouse, that bug is here: [https://launchpad.net/distros/ubuntu/+source/gdm/+bug/29368](https://launchpad.net/distros/ubuntu/+source/gdm/+bug/29368)[/QUOTE]

the fan bug report looks good. the link to Benjamin Herrenschmidt's debain post is good. i set the package to kernel so the right people should spot it.

i dont have blue tooth so i can't confirm the that one.

---

### Post by Xappe on 2006-03-15
the "no soundcard" bug is updated and is now labelled as a kernel bug.

[https://launchpad.net/products/alsa-utils/+bug/30963]("https://launchpad.net/products/alsa-utils/+bug/30963")

---

### Post by qball on 2006-03-15
I run dapper on my mac mini and I have 2 problems:
1. My usb system is _very_  unstable. unplugging a device, or pluggin in devices makes it not regonize any new hardware anymore, and after a while the mac locks.

2. Less serious, X often uses 100% cpu, making everything unresponsive, for 5-30 seconds.. this mostly happens on switching Virtual desktop or creating a new window.

for the rest I have little problems left...
(usb-audio 1.1 through an usb 2 hub isn't supported on ppc, but that is a kernel problem, not a ubuntu problem I guess.

---

### Post by autocrosser on 2006-03-16
Well--
I've been running Dapper from about a month into the testing & onlt have one MAJOR issue--All the Dual-processor kernels after 15-11-smp have a timing sync problem that makes Gnome-panel, Xscreensaver, Gkrellm & Time/Date pref go "crazy". Yes-I've talked to Ben via Email several times & filed several bug reports--no answers yet--

I'm currently running a single processor kernel (no problems with the singles) & am waiting for the next Dual kernel (should be 15-19-smp). Running a Dual 1.25 Mirror-Door. I've thought about "cooking" my own, but want to test with only Ubuntu stuff so my bug reports reflect "truth"

---

### Post by ThomHolwerda on 2006-03-16
Btw, is it normal that since I installed Flight 5 (Sunday), there haven't been any updates of any kind? On x86, I remember heavy updates each day up until the release of -final (previous release cycles).

Someone on OSNews also said he already got the updates for GNOME 2.14-final...

---

### Post by keifer on 2006-03-16
Indeed, I belive that the Gnome 2.14 has hit the repos, or atleast parts of it. The package I looked up (gnome-desktop) had a ppc .deb available.

Unfortanatly, I haven't been able to install/boot dapper on my machine (see bug [#34508](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508)), due to a problem with the kernel.

---

### Post by spaceballl on 2006-03-16
Booted up a fresh install of Kubuntu to see if the bluetooth keyboard/mouse issue is related to GDM. It's not as the problem exists in Kubuntu as well. I've tried to initialize everything manually but w/ no success

---

### Post by spaceballl on 2006-03-18
[QUOTE=ssam]does anyone else get the bluetooth problem? if so can they confirm the bug, that gives it a higher chance of being worked on be the developers.[/QUOTE]
Confirmed the bluetooth bug here:
[http://ubuntuforums.org/showthread.php?t=142987](http://ubuntuforums.org/showthread.php?t=142987)
Also, there is a workaround posted.

Basically, bluez kills the keyboards / mice so by removing the bluez* packages, we restore bluetooth keyboard / mouse functionality. This problem is not PPC specific.

---

### Post by paulsomm on 2006-03-19
Consider me a Dapper tester now :)

So far, loving it (Ubuntu has to be the best linux distro I've ever used, and I've used RedHat, Suse, YellowDog, and the now-defunct LinuxPPC).  I do have a few issues:

1. MOL - After installing the latest drivers within the OSX session, MOL now dies on starting with the error "Out of memory".  As I only specified 256M in the molrc.osx file, and I have over 600M free when launching MOL, I don't think that error is correct.

2. I have no sound anymore, aside from system beeps.  Playing with the settings, I can't seem to coax any sound to work.

3.  My airport extreme is recognized, and enabling it appears to work, but it doesn't get an IP address from my access point.  Also, booting with the Airport Extreme enabled AND my Orinoco WaveLAN card inserted (pcmcia 802.11b card I've been using in lieu of the AE) causes all networking to not work.  By this I mean even my wired connection.  Any attempts to ping return "ping: sendto: operation not permitted" even if I disable all but the wired.  I had to disable all but the wired and then reboot.

On the plus side, XSANE now works for me, whereas it was dieing before if my scanner was plugged in.

---

### Post by smileyme on 2006-03-19
Has anyone tried Dapper on Old World Mac. I thought I would try it, but BootX doesn't seem to be able to do it.

Rick :)

---

### Post by virgule on 2006-03-19
About OldWorld:  I am fairly high on free time today.. If the oldworld-standard way  fail I will use the same steps as Breezy (reconfigure linux-image...)

---

### Post by erniewinner on 2006-03-19
i hope it someone gives some feedback on this! is there a dapper ppc test disk. i've got flight 5 on my pc. but i'd love to see my mac do something productive.

---

### Post by paulsomm on 2006-03-19
There are the LiveCDs, fully bootable CDs of Dapper.  Just download, burn, and boot and you'll see what is and isn't working on your system.  The LiveCDs are available at the same location as the full install CDs.  There is an forum post in the PPC section on testing Ubuntu PPC with a link to the downloads, if you need.

---

### Post by erniewinner on 2006-03-19
ha ha! got it. it wasn't very well sign posted though. [http://cdimage.ubuntu.com/releases/dapper/flight-5/](http://cdimage.ubuntu.com/releases/dapper/flight-5/)

---

### Post by virgule on 2006-03-19
Its not loading at all from an OldWorld Mac. I really mean nothing as in *nothing*. Past BootX, the screen used to turn black and show loads of white texts but this one won't even reach this state. The BootX dialog disapear then nothing. Total idleing.

---

### Post by smileyme on 2006-03-19
I'm assuming there will need to be a new version of BootX, but I am a complete noob, so it may be something different.

Rick :)

---

### Post by virgule on 2006-03-19
In fact, I am sure its initrd.gz and/or vmlinux fault. They must be missing some important parts for oldworld ppcs to run. I am hunting for the kernel config file they used I aint finding much so far :(

---

### Post by smileyme on 2006-03-19
I tried an experiment by booting using the 6.04 vmlinux and the 5.10 initrd.gz, just to see if it would get past the Mac OS screen. It didn't. I then tried the opposite with the 5.10 vmlinux and the 6.04 initrd.gz. This time it moved to the dialog screen of 5.10. I didn't try to go any further \\:D/ 

In my opinion this indicates the problem is with the 6.04 vmlinux, not the initrd.gz.

Rick :)

---

### Post by virgule on 2006-03-19
Ok. Thanks fot that. I had to write my own initrd for breezy to boot. I used these instructions: [Linky to Wiki]("https://wiki.ubuntu.com/Installation/OldWorldMacs"). I am goint to try various combinations. I have 4 different vmlinux and initrd known to work besides the dapper not working twins. There is hope I only wish it will be better in the release version.

---

### Post by virgule on 2006-03-19
Im back from Hit-a-Wall Land. :) 
I played with everything I could think of. I only seam to reach as far as you.

-=-=-=-
With Breezy vmlinux and Flight 5 initrd:
There is a TON of
```

modprobe: FATAL: Could not load /lib/modules/2.6.12-10-powerpc/modules.dep: No such files of directory.

```
these sliped in here and there:
```

-request_module: runaway loop modprobe net-pf-1
-udevd[650]: init_udevd_socket: error getting socket: Address family not supported by protocol
-udevd[650]: main: error initializing udevd socket: Illegal seek

```
-=-=-=-
With Flight5 vmlinux and Breezy initrd:
```

(...) Congratulation! You have got yourself a 1000$ power-bill enhancer device!
(this mean nothing is going on..)

```

I guess it only make sense since the two are of a different version, thus, not meant to play together.

---

### Post by smileyme on 2006-03-20
I didn't expect it to run. I just wanted to know which was the offending file; the vmlinux or the initrd.gz. That being determined, maybe someone with some programing experience can modify the vmlinux kernel. That won't be me[-( 

Rick :)

---

### Post by Torrance on 2006-03-22
This is a vague question, but I was just wondering if anyone has an inkling if sound will be working on any of the newer Apple machines when Dapper finally comes out, ie. the G5 iMac and Powermacs. I'm guessing this has more to do with ALSA???

It's the last thing holding me back from making the final switch to linux....

---

### Post by RIVE on 2006-03-24
Dapper in iBook G3 500 mhz dual USB works almost perfect, first I install hoary from a original cd then make a dist-upgrade for dapper.

Problems.-
Most of the problems are from audio.
-The integrated microphone is not detect, when i try to record something this message of error apears "Your audio capture settings are invalid. Please correct them in the Multimedia settings."
-Sound does not start when booting, have to open audio control and check the sound box.
-Mp3's and ogg files sound pretty bad when played in xmms or any other program, tried to change the setting to OSS or esound with the same results.
The dvi to vga port don't work, can't make it work, this is important for me because sometimes have to make presentation in public.

Icons in the Gnome 2.14 desktop always move when booting, doesn't stay where i put them.

---

### Post by AlphaMack on 2006-03-24
I would avoid a dist-upgrade from older versions to Dapper.  After clean installing for Dapper Flt 5, many of my issues disappeared (I did a dist-upgrade from Breezy).

I do have one huge problem in Dapper.  Wireless.  Then again, it isn't Dapper's fault. ;)

---

### Post by paulsomm on 2006-03-24
I too have no sound since upgrading to Dapper.  Wireless doesn't work, but didn't expect my AE to, although what is odd is I have to disable all nics except my ethernet and reboot.  If I try to change any of the networking settings, even if I just go in and save teh same config, I loose all connectivity and receive "ping: sento not allowed" if I try to ping anything.

Those, however, are the only things not working so far.  It's otherwise working quite well.

---

### Post by bgmccollum on 2006-03-24
[QUOTE=RIVE]Dapper in iBook G3 500 mhz dual USB works almost perfect, first I install hoary from a original cd then make a dist-upgrade for dapper.

Problems.-
Most of the problems are from audio.
-The integrated microphone is not detect, when i try to record something this message of error apears "Your audio capture settings are invalid. Please correct them in the Multimedia settings."
-Sound does not start when booting, have to open audio control and check the sound box.
-Mp3's and ogg files sound pretty bad when played in xmms or any other program, tried to change the setting to OSS or esound with the same results.
The dvi to vga port don't work, can't make it work, this is important for me because sometimes have to make presentation in public.

Icons in the Gnome 2.14 desktop always move when booting, doesn't stay where i put them.[/QUOTE]

I also have a 500Mhz G3 iBook, and doing a fresh Flight 5 install goes without a hitch. But when I get to the login screen, everything is garbled. There is a dialog box that pops up, but I cannot read it. What log file should I look at for potential problems?

---

### Post by ssam on 2006-03-25
[QUOTE=bgmccollum]I also have a 500Mhz G3 iBook, and doing a fresh Flight 5 install goes without a hitch. But when I get to the login screen, everything is garbled. There is a dialog box that pops up, but I cannot read it. What log file should I look at for potential problems?[/QUOTE]

Xorg logs in /var/log/Xorg.0.log and you should probably also include /etc/X11/xorg.conf in a bug report.

---

### Post by JackosKing on 2006-03-25
So my computer is an iBook G4 1Ghz AE.
Result: No sound, no Wifi available (WEP 128bits HEX).
Bad keymap loaded.
This was with the cd live.

---

### Post by jdp on 2006-03-27
Dapper Flight 5 on an iBook 2 rev. 2 (600MHz 16VRAM)

On initial boot, the Xserver came up in 640x480 only.  I opened a Terminal in Gnome and ran **sudo dpkg-reconfigure xserver-xorg** and went through the options.  It detected the video and LCD fine.  Then I just pressed **Ctrl-Opt-Del** to kill the Xserver, and it restarted on it's own, and into 1024x768.  Whew!  Then I found that the Orig Airport card wasn't found yet so I opened another Terminal and ran **sudo modprobe airport** to get the card detected.  I opened the Networking Admin panel and setup for my networks SSID and activated DHCP.  After a minute it finished configuring and was detected and online.  Woo!  The problems are that both of these *should* have worked out-of-the-box, as ISTR the AP detected fine from Breezy, and there was no real playing that had to be done to get the video working right.

Overall though, it's looking fine, albeit I haven't tried getting the audio to work.

Also, sleep works great!  It's just that it keeps resetting the brightness settings to max whenever it wakes up or the Xserver is restarted.  I can turnt eh brightnesss down with **Fn-F1** and it'll turn off the backlight if I keep going down.  Then it takes two presses of **Fn-F2** to turn it back on.  I can turn it back down one notch and it stays on.  Odd.

EDIT: (After ssam's post below) I've been able to **sudo modprobe snd-powermac** and have sound stuff show up in **lsmod** but I haven't got Gnome finding it yet.  Maybe an Xserver restart is in order agian...  And I'll try to remember to post some bugs, or confirm others when I get back to an install with my Launchpad login setup. :)

---

### Post by ssam on 2006-03-27
please file bugs. things not working 'out of the box' count as bugs too (usually)

---

### Post by paulsomm on 2006-03-27
[QUOTE=paulsomm]Consider me a Dapper tester now :)

2. I have no sound anymore, aside from system beeps.  Playing with the settings, I can't seem to coax any sound to work.
[/QUOTE]

Yay, I found out how to get sound back.  Playing with Volume Control I went to "Preferences", scrolled down and checked "DRC".  Then, in the main Volume Control program, I clicked on "Switches" and from there UNCHECKED DRC.  After doing that, I have sound :)

Not sure why this works/is a problem/whatever but 'slong as I have my sound . . .

---

### Post by jhupiter on 2006-03-28
Attempted install on Powerbook G3 Firewire Pismo 400 MHz 1 GB. Get half/half black and white screen with horizontal gray strip about 2/3 down screen. LiveCD gets me a hang with lots of errors.

---

### Post by ssam on 2006-03-28
[ Bug #27862 in casper (Ubuntu): "sound does not work any more on ppc live CD"]("https://launchpad.net/distros/ubuntu/+source/casper/+bug/27862")

is marked as fixed. it might take a day or two for this to get into the [live cd images]("http://cdimage.ubuntu.com/daily-live/").

jhupiter
that screen issue sounds a bit like
[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/29540](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/29540)
could you add a comment there.

---

### Post by fraterf93 on 2006-03-29
I have tried Kubuntu Dapper on my iMac G3 600 MHz, and I get the same login freeze issue that was present in Breezy. In Breezy I fixed it using the advice from this fellow: [HTML]http://www.ubuntuforums.org/showpost.php?p=501386&postcount=4[/HTML]   This fix does not work in Dapper.  Still login freeze.

---

### Post by ssam on 2006-03-31
a couple of new bugs, possibly powerpc specific
[can't connect to WEP networks with NM 0.6.1]("https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/37396")

[f-spot crash on colour adjustments]("https://launchpad.net/distros/ubuntu/+source/f-spot/+bug/37412")
can anyone confirm this?

---

### Post by dhirsch on 2006-04-03
I just installed Flight 6 onto my 800mhz ibook (pearl book style, not clamshell).

According to the volume applet and sound preference gui, there is no sound device found. 

Also, the system isn't suspending when I close the lid. 

:(

---

### Post by Xappe on 2006-04-03
[QUOTE=dhirsch]I just installed Flight 6 onto my 800mhz ibook (pearl book style, not clamshell).

According to the volume applet and sound preference gui, there is no sound device found. 

Also, the system isn't suspending when I close the lid. 

:([/QUOTE]

The "no soundcards found" bug is in malone (I have the bug myself on my ibook g3 700 MHz): [https://launchpad.net/products/alsa-utils/+bug/30963]("https://launchpad.net/products/alsa-utils/+bug/30963")

I could get my ibook to suspend, when closing the lid, after enabling it in system --> preferences --> power management.

---

### Post by dhirsch on 2006-04-03
> I could get my ibook to suspend, when closing the lid, after enabling it in system --> preferences --> power management.

I don't have to patch the kernel anymore? Yay!

Thank you <3

---

### Post by RIVE on 2006-04-05
I did a fresh install of flight6 in a iBook G3 500mhz dual USB and this are the problems I have:

1.- Sound doesn't work if didn't turn on PC Speaker in Volume Control App first.
2.- The integrated microphone isn't detected, so can't test ekiga :-(
3.- Mp3's and Oggs files plays horrible, every one is playing with cuts, like if you were moving up and down the volume.
4.- In Nautilus can´t select more than one file with ctrl key push, it´s very anoying make that with the mouse. 
5.- The vert and Horiz sync isn't detected on install so I have to edit the xorg.conf with the correct parametres:
Section "Monitor"
Identifier "Color LCD"
Option "DPMS"
[B]HorizSync 28-51
VertRefresh 43-60[/B]
EndSection

Can I report this like bugs? don´t undernstand very well the way to make a report.

I keep testing :-D

---

### Post by Rxke on 2006-04-07
:D I did a dist-upgrade from Breezy, which itself was already a dist-upgrade from Hoary, and... I have sound, heehee! So far, I see no problems, except that I noticed Oo having disappeared from the menu (don't use it anyways...) But that can be me, not sure I removed it myself before, heh.

(Clamshell iBook)

Got an error during boot that it couldn't acces the Hardware clock "by any known means", but the clock is set correctly. 

Impressive work, guys and girls!

---

### Post by projectle on 2006-04-07
Is there any word on whether there is going to be mouse button emulation support in Dapper? 

Right now, it is impossible (atleast with my current knowledge) to use a right click on my 17" Powerbook G4 5,9's touchpad under Linux.

Even the new Intel Macs using Boot Camp and Windows XP have my trusty CTRL-Click.

It would sure be nice if us non-sellouts wanting to use something not quite as craptastic as XP would be able to use contextual clicks in our operating systems.

---

### Post by Rxke on 2006-04-08
You mean pressing F11 doesnt work for you; or is too cumbersome?

---

### Post by seatea on 2006-04-08
I just started up with the Live CD for Dapper Drake Flight 6. I was a little concerned initially that I wouldn't even be able to burn a CD when I tried making a CD with GnomeBaker. I kept getting  the message that the ISO image was too large for my CD. I think the ISO came in at 689MB and my CD is 700MB. I then installed the  KD k3b software and it  burned without a hitch. I started  up from the Live CD without  a problem. I do not appear to have sound even after tinkering with the controls. The  Live CD for Dapper seems  faster  than the Breezy Live CD. It is interesting that the  Live Cd has an installer. I like that option. When will the final release be  available?

I need to add that  I am using  a PM G4 400 Gigabit.

---

### Post by seatea on 2006-04-08
I fixed my sound problem.

sudo chmod 666 /dev/dsp

---

### Post by halvor on 2006-04-10
live cd no6 does not work on a pismo, something with no framebuffer on video, it does not work on a blue white g3, hangs on loading root filesystem ...

---

### Post by dpny on 2006-04-10
[QUOTE=halvor]live cd no6 does not work on a pismo, something with no framebuffer on video, it does not work on a blue white g3, hangs on loading root filesystem ...[/QUOTE]

Hmm. . .

I see this message when I boot 5.10 on my Pismo,  but the machine proceeds through to boot.

---

### Post by pauljwells on 2006-04-12
I just did a dist-upgrade from breezy - seemed to go ok except that now at the gdm screen my keyboard is not fully recognised. Only numerals seem to respond. As a result, I can't login! I can get to a terminal (ctrl-alt f5) and login there ok so I can get at any files to fix stuff, if I only knew where to start...

well, I started with editing /etc/gdm/gdm.conf to auto log me in...

---

### Post by RaSa on 2006-04-13
Hello,

I'm testing Dapper Drake on an iMac G3/400 and an iMac G3/500. Last Update solved some strange problems with pakets. Sound works with Gnome.

Problem is sound and kde. It worked at start. I tried to set up amaroK to play some sound and altered the sound system presets. Bad bad idea. After I tested esound I get the normal sound for a fraction of a second to bust my ears for the rest of the time with ugly and loud white noise. I tried a lot, set everything back, loaded defaults, tried every other setting and searched a lot, but still in vain. One thing more, when a sound has to be played, I notice that the mouse (usb) freezes for a second, then comes the white noise.

Is there any other solution than a clean re-installation of kde / Dapper Drake? This does look like a problem you usually found in windows, but nor on linux. ](*,)

---

### Post by stmiller on 2006-04-13
Problems with the live dapper cd on Powermac G5.

Loaded live-powerpc64

The fans come on full blast; no thermal support. Trying to exit the gnome desktop led to the entire computer freezing. Did not try sound, as the computer was as loud as an airplane by the time it got to the desktop; just went to shut it down immediately.


Specs:

  Machine Name:	Power Mac G5
  Machine Model:	PowerMac7,3
  CPU Type:	PowerPC G5  (3.0)
  Number Of CPUs:	2
  CPU Speed:	2 GHz
  L2 Cache (per CPU):	512 KB
  Memory:	1.5 GB
  Bus Speed:	1 GHz
  Boot ROM Version:	5.2.4f1
  Serial Number:	xxxxxxxxxxxxx

---

### Post by Rikostan on 2006-04-14
I just had an older blue G3 delivered about 2 hours ago... I'll try dapper on it and see how it goes. It will be my first dual boot with a mac.

---

### Post by Peter76 on 2006-04-15
See this thread: [http://ubuntuforums.org/showthread.php?t=160593](http://ubuntuforums.org/showthread.php?t=160593)
For the rest, after a week of using dapper on my iBook 900 600MB, it looks great

---

### Post by nkbj on 2006-04-28
[QUOTE=virgule]In fact, I am sure its initrd.gz and/or vmlinux fault. They must be missing some important parts for oldworld ppcs to run. I am hunting for the kernel config file they used I aint finding much so far :([/QUOTE]

I've hit the same problem. :-( Has this been reported as a bug in launchpad?

Regards,
Niels Kristian

---

### Post by glennric on 2006-05-01
I am running Dapper Beta with all updates on a G5.  I have lots of problems.  First, no sound.  I have to disable the snd_powermac module entirely to prevent system lockups.  Second, no second and third mouse button emulation.  The pbbuttonsd fails on boot up and says there are no keys dev. mac_hid.mouse_button_emulation and no /dev/pmu.  Third, I can't get my HP Laserjet 1022 printer to work for anything.  It shows up with lsusb, but I can't get anything to print to it.  hp-makeuri can't find it.  /dev/usblp0 is there, but it doesn't seem to work.  Any suggestions for any of these problems would be welcome.

---

### Post by Doobie9 on 2006-05-01
Testing Dapper Drake on a G3 iMac (Installed) and on a G4 iMac (LiveCD).

The two biggest issues with these machines is the lack of sleep mode funcionality and Direct Render support. I've filed a few bug reports and I really do hope that these issues are resolved because I can't use Ubuntu unless I can put it to sleep, and Direct Render would be nice for Xgl :(.

](*,)

---

### Post by woopie49 on 2006-05-01
Hi guys, the link

[http://cdimage.ubuntu.com/releases/dapper/flight-5](http://cdimage.ubuntu.com/releases/dapper/flight-5)

seems broken, I get a 404, could someone please point me to a working link. I'm on a dual 1.42 G4.

Thankyou

---

### Post by ssam on 2006-05-02
flight 5 is quite old now.

there is the beta 2 cd [http://releases.ubuntu.com/6.06/](http://releases.ubuntu.com/6.06/)

or if you want the very latest:

the latest unstall is at [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)
the latest live is at [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by woopie49 on 2006-05-02
Thanks for the links ssam

---

### Post by megabenman on 2006-05-02
Question: Does dapper drake flight 6 beta 2 have iMac G5 fan and sound support? I've been debating between breezy or dapper drake but if dapper drake has fan and sound support I will use it instead.

---

### Post by Torrance on 2006-05-03
Dapper does not have fan control still (despite it being an option for the PPC kernel compile). Also, neither will run first time with some under the hood changes to disable ESD Sound Server - another bug that remains unresolved in Dapper. This also means there's no sound.

Personally, if you're using an iMac G5, I recommend openSUSE 10.1 (about to come out) because it has fan control and doesn't require disabling of ESD (though still has no sound support).

---

### Post by megabenman on 2006-05-03
[QUOTE=Torrance]Dapper does not have fan control still (despite it being an option for the PPC kernel compile). Also, neither will run first time with some under the hood changes to disable ESD Sound Server - another bug that remains unresolved in Dapper. This also means there's no sound.

Personally, if you're using an iMac G5, I recommend openSUSE 10.1 (about to come out) because it has fan control and doesn't require disabling of ESD (though still has no sound support).[/QUOTE]
Ok.... I just hope it isn't complicated.

---

### Post by moonaust on 2006-05-03
Running DaPPER on a Powerbook G3 233 with no problems at all, except no hardware acceleration w/video.

---

### Post by szim90 on 2006-05-04
I have just upgraded to Dapper from Breezy using the gksudo "update-manager -d" command. When I start the computer, it goes through two prompts, and then the screen completely changes to white. After a minute or so, the login screen loads. Also, when I shutdown, I get a similar problem (this screen is gray). Is there a way to prevent the screen from going to white, and use the splash screen during startup and shutdown? If not, is there a way to force it to do a text start and shutdown? 

I am using a Nvidia GeForce2 MX/MX 400 with the nv driver.

---

### Post by hotani on 2006-05-05
I have been working with Dapper on a dual G4 867 with a GeForce Ti 4600, M-Audio Revolution 5.1 soundcard and a 1920x1080 display.

The good:
It boots.

The bad:
sound is there, but really bad. When I log in, it is full blast. If I turn it down, I lose sound on the left side. The alsa mixer is a complete joke, there are about 25 columns that aren't human readable and changes I make to it don't stick.

The ugly:
My display, once I edited the xorg.conf file to show full res instead of blurred and distorted 1280x1024 (can we have our monitor resolution gui tool upgrade now?), hangs off the right side about 10 or 20 px, then on the left side there is a vertical bar about 10px wide which is the leftover image from the right side. *Most* of the display is fine though. I thought I'd try installing the real nvidia driver rather than using 'nv' but when I added it to xorg.conf Gnome wouldn't start so I had to revert back.

Overall, it isn't pretty. I opened a movie in mplayer and it seemed to play, albeit with crappy sound from my apparently unsupported sound card. However, when I went fullscreen with the movie, it was squished too thin. WHere it should have fit the full screen 16:9, it was compressed vertically to about 2.5:1 which is not the dimensions of the video.

Other movie players either A) did nothing or B) showed video but no sound. This is after installing all the restricted codecs such as XviD, AC3, mp3, etc...

Also, when I reboot back into OS X, something has jacked with the vid card because the monitor switches off and on again 2 times during boot up. When I'm back in OS X, the colors have changed to "thousands" even though the Displays dialog says "millions." The only way to fix it is to switch to thousands, then back to millions. It is very disturbing that Ubuntu is messing with system-level settings that affect the other OS. 

I know my hardware is odd, but it is still frustrating to not have fully functioning sound and video.

---

