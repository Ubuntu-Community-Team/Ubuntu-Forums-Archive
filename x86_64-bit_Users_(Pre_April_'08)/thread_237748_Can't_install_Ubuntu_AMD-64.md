---
title: "Can't install Ubuntu AMD-64"
date: 2006-08-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by TriZz on 2006-08-16
Ok - here's what happens.

Now, I did post this back in the breezy days and I ended up just installing the 32bit on laptop.  Now, I'm going to be getting rid of my laptop - and want to move my PC to a dual boot (I still rely heavily on iTunes).

...so I boot from the CD.  Click the first choice "install and run".

It uncompresses, and goes through that whole bit with the "loading process name here.......[ok]

The screen goes black - like it's going to run the next thing, and then nothing.  The CD light blinks for a minute or so afterwards and then stops.

I'd really like to get this working - so if anyone has any suggestions, please let me know.

AMD64 Anthlon 3200+
Nvidia GEForce 6800

...I can't imagine it being anything else.

Thanks.

---

### Post by hecato on 2006-08-16
Perhaps help start in safe graphics mode???

---

### Post by John.Michael.Kane on 2006-08-16
What Cd are you running eg: desktop or alternate?

Have you tried booting with acpi=off?

also just listing you an amd cpu,and some nvidia card does not help should the issue be something else. please try to list all your hardware.

also listed any error msg you may see.

---

### Post by TriZz on 2006-08-16
> **hecato said:**
> Perhaps help start in safe graphics mode???

No change when I do that.  Thanks for the suggestion!

---

### Post by TriZz on 2006-08-16
> **SD-Plissken said:**
> What Cd are you running eg: desktop or alternate?

Have you tried booting with acpi=off?

also just listing you an amd cpu,and some nvidia card does not help should the issue be something else. please try to list all your hardware.

also listed any error msg you may see.

I'm running the desktop CD (I think, I'm not sure what the alternate CD is).  It's a boot disk that I assume runs a live session from the CD with the option to install ONLY after you get it to boot from the live mode.

Full hardware specs are as follows:
 - AMD-64 Anthlon 3400+
 - Lan Party UT LP NF3 250Gb Mobo
 - Two Maxtor hard drives (80G w/ windows install + 250G storage  drive)
 - 2 x 512MB DDR RAM sticks (made by Nanya Technology)
 - Sound Blaster Audigy 2 ZS, DR release 2.8.4 - Sound Card
 - Logitech Keyboard and Mouse
 - Daewoo 17in flatpanel LCD Monitor

---

### Post by John.Michael.Kane on 2006-08-16
TriZz can you please try the [**ubuntu-6.06.1-alternate-amd64.iso**]("http://ubuntu-releases.cs.umn.edu/6.06.1/ubuntu-6.06.1-alternate-amd64.iso") it should allow install the os.

---

### Post by TriZz on 2006-08-16
> **SD-Plissken said:**
> TriZz can you please try the [**ubuntu-6.06.1-alternate-amd64.iso**]("http://ubuntu-releases.cs.umn.edu/6.06.1/ubuntu-6.06.1-alternate-amd64.iso") it should allow install the os.

Yeah, I'll give that a shot.

Thanks for your input!

---

### Post by Sebaspi on 2006-08-16
i have the exact same problem, im using desktop 64bit cd on:

asus a8v deluxe
ati x800xt
a viewsonic monitor
160gb hd
amd athlon64 3500+


when i try the first option after starting all the process ok, it goes black and nothing happens, i also tried safe screen mode and all the process load ok but then the screen turns off, and i can hear like the os starting up.

i guess ill have to download alternate :( gotta wait 7hours.

---

### Post by clevershark on 2006-08-16
This is probably due to your graphics card. ATI x?00 cards are apparently not compatible with the standard ati/radeon drivers that come with Xorg. I've had the same problem when I tried out Fedora on one of my PCs (I have an x700 card).

---

### Post by Sebaspi on 2006-08-16
> **clevershark said:**
> This is probably due to your graphics card. ATI x?00 cards are apparently not compatible with the standard ati/radeon drivers that come with Xorg. I've had the same problem when I tried out Fedora on one of my PCs (I have an x700 card).


thats bad :( so do you know if i download alternate cd and install that would i be able to enter the os after the installation? i hope there is some way to fix this beacause i really wanted ubuntu. im going to leave alternate cd downloading tonight so i hope i can install it tomorrow ill tell you what happend later. thanks for your help everyone.

---

### Post by clevershark on 2006-08-16
The alternate CD works!! It's not nearly as easy to use as the live CD, but it's doable, and you get 3D support (yay!).

1- Install in text mode from the alternate CD. Make sure your network is up and running, as the installer does inline updating.
2- Boot in recovery mode
3- Update the /etc/apt/sources.list to include the universe repository. Just to be on the safe side I also copied the lines that point to universe and changed "universe" to "multiverse" on both. I'm not sure if that actually did anything though. 
4- Follow the instructions provided by [Kilz]("http://www.ubuntuforums.org/member.php?u=78588") on [this page]("http://ubuntuforums.org/showthread.php?p=1372283#post1372283").

When your computer reboots your display should work, as the X800 cards are supported by the driver.

Hope this works for you!

---

### Post by TriZz on 2006-08-17
> **clevershark said:**
> The alternate CD works!! It's not nearly as easy to use as the live CD, but it's doable, and you get 3D support (yay!).

1- Install in text mode from the alternate CD. Make sure your network is up and running, as the installer does inline updating.
2- Boot in recovery mode
3- Update the /etc/apt/sources.list to include the universe repository. Just to be on the safe side I also copied the lines that point to universe and changed "universe" to "multiverse" on both. I'm not sure if that actually did anything though. 
4- Follow the instructions provided by [Kilz]("http://www.ubuntuforums.org/member.php?u=78588") on [this page]("http://ubuntuforums.org/showthread.php?p=1372283#post1372283").

When your computer reboots your display should work, as the X800 cards are supported by the driver.

Hope this works for you!

Ok, did the alternate CD (God Bless bit torrent with it's 550KB/sec downloads) - at any rate, it's the same story different disk.  Loads right past the processes then nothing but a black screen. more info: No network connection until I get a wireless connection.  I'm in the basement - the modem/router is all upstairs.

---

### Post by Sebaspi on 2006-08-17
> **TriZz said:**
> Ok, did the alternate CD (God Bless bit torrent with it's 550KB/sec downloads) - at any rate, it's the same story different disk.  Loads right past the processes then nothing but a black screen. more info: No network connection until I get a wireless connection.  I'm in the basement - the modem/router is all upstairs.


i think i will have the same problem as trizz, i wont have inet conection i think, i have an adsl connection, this is too bad i have been having lots of problems to install linux, its is not ubuntu fault, i guess its bad luck many things gather.

i have an old 5.10 ubuntu live cd an i try that one and it works fine, why an newer version isnt compatible with the same hardware?

---

### Post by hecato on 2006-08-17
> **Sebaspi said:**
> 
when i try the first option after starting all the process ok, it goes black and nothing happens, i also tried safe screen mode and all the process load ok but then the screen turns off, and i can hear like the os starting up.

i guess ill have to download alternate :( gotta wait 7hours.




Hi there...

If after loading the screen goes black, and the led-light-ofTheMonitor or indicator blink for indicate out of rate or not valid resolution.... then you just need hit **CTRL**+**ALT**+"**+**" or **CTRL**+**ALT**+"**-**"... that will switch (rotate... like a barrel of a gun) between the modes that the X server "has thinked" that are correct for your screen.


If after hit much times, you dont are able to see a good or fine resolution or even a lower resolution, then try to hit **CTRL**+**ALT**+**F1** that will switch you to terminal-1 (by the way, the graphic "terminal"/session [dont know how to call it] is in  **CTRL**+**ALT**+**F7** or **F8** sometimes).

In the terminal-1 try to see if you are able to output

```
xrandr
``` 
 that you will see the available modes and rates (you are only able to use one of the listed there... tought there exist other graphic modes... available for your card.. calculated at startup of the X server and validated/provided modes againts the file **/etc/X11/xorg.conf**)

There  in you **/etc/X11/xorg.conf** can indicate extra resolution/modes like for example **"1024x768_60"** included the **"**, if you dont know wich modes your screen is able to use... try modifying for example **/etc/gdm/gdm.conf** and search the general/basic/DontRemember a line that startx... search for the one that **should be the default** (there are a lot of lines that launch X in different ways/setups)...[LIST]
[*]Copy the line
[*]Paste it again
[*]Comment with "_**#**_" one of the lines
[*]Delete the arguments to X of the other line
[*]Add like arguments "**-- --logverbose 6**" without the quotes
[*]Switch to graphic terminal/session with **CTRL**+**ALT**+**F7** or **F8** and then hit **CTRL**+**ALT**+**BACKSPACE** (for restart the X server).[LIST]
[*]The black screen _will stay_, but now you will have a **logverbose output** (the log is in **/var/log/Xorg.0.log**)) of the xserver _waiting for be analized_ for see the **valid modes** a **pool of valid modes** that the X server has **determinated** **automatically** and that **will** match against for validation and elimination of extra modes (only the modes that the user whant) to the  **/etc/X11/xorg.conf** file[/LIST] 
[*]Search for **valid modes** or **pool of valid modes** and there you will see the modes like **"1024x768_60"** you will see a section where it display the requested modes (the ones inside **/etc/X11/xorg.conf**) and the discard of them if they are out of range
[*]Now with this info modify **/etc/X11/xorg.conf** and add a valid mode that is validated but not included in your cfg file[LIST]
[*]go to the terminal7 or graphical session and restart again the X server
[*]Rotate between the modes with the key combination.
[*]If this dosent work (you hit and hit and hit), try the last thing I know... go again to terminal-1, see again the output of xrandr (you should see there your added valid configuration) and type **xrandr -s XResolutionxYResolution -r ValidRate** (this is because the combination of keys aparently dosent setup correctly the xrandr values... or some like that... dont know, but have happened me), switch again to graphical session and see if that worked.[/LIST] [/LIST]
Hehe, see if that help. (I will edit it later for be more descriptive in the repetitive task... like switch restart and so on... perhaps or no soon).

---

### Post by TriZz on 2006-08-17
I hit the ALT+CTRL+"+" once and it brought up the login screen!

Ok, so I logged in - and all I could see was my mouse pointer and the brownish background.  I was getting frustrated until I moved the mouse and it automatically scrolled to the edge where the "applications places system" menus are.

...how to I fix the resolution?  How do I make sure it uses a working resolution on startup?

Thank you for your God-like advice Hecato!

---

### Post by clevershark on 2006-08-17
Something I did when rebooting -- and which may have helped, but I'm not sure -- was to set the correct VGA mode for my monitor in grub by appending "vga=795" to the line that specifies the kernel location. This *may* have provided a hint when the original xorg file was created.

re: the mouse problem -- this can happen if you have multiple mouses/mice connected to your system. Also some Logitech mouses don't work correctly with xorg (some of the laser ones). If you can, try connecting a cheap $5 mouse to your system and see if that works.

---

### Post by hecato on 2006-08-17
> 
Ok, so I logged in - and all I could see was my mouse pointer and the brownish background. I was getting frustrated until I moved the mouse and it automatically scrolled to the edge where the "applications places system" menus are.
 
A yea... I forget to say that :P... hehe.

In that graphic mode you should follow the step I describe before (about modify gdm.conf)... byt the way...

in **/etc/gdm/gdm.conf**
```

# Definition of the standard X server.
[server-Standard]
name=Standard server
[COLOR=Green] command=/usr/bin/X -br -audit 0[/COLOR]
[COLOR=Blue] #command=/usr/bin/X -logverbose 6[/COLOR]

``` 
The [COLOR=SeaGreen]uncommented line[/COLOR] is the default line
The [COLOR=Blue]commented line[/COLOR] is for get a verbose output in /**var/log/Xorg.0.log** file

See the .log file and search for this part

> 
(II) **Setting vga for screen 0**.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce 6100 at PCI:0:5:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.22.22.05
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6100 at PCI:0:5:0:
(--) NVIDIA(0):     Samsung (CRT-0)
(--) NVIDIA(0): Samsung (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): [COLOR=Red]_**Validated modes**_[/COLOR]:
(II) NVIDIA(0):     "**1024x768_60**"
(II) NVIDIA(0):     "1024x768_75"
(II) NVIDIA(0):     "1024x768_70"
(II) NVIDIA(0):     "1024x768_87i"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "720x400"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(WW) NVIDIA(0): No size information available in CRT-0's EDID; cannot compute
(WW) NVIDIA(0):     DPI from EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
 
Then those Valid Modes are the ones you can select...




A brief explanation (like I understand)..
[LIST]
[*]**xrandr** list the _user available sizes and rates_.[/LIST][LIST]
[*]The _user available sizes and rates_ is obtained with a **Insersection of modes** between the **modes in /etc/X11/xorg.conf** and the **modes calculated when the X server is started/restarted** those can be watched with the *logverbose* output.[/LIST]The X server will always (I guess)[LIST]
[*]Read the config file (default is **/etc/X11/xorg.conf**)
[*]Do the automated calculations and loadings[LIST]
[*]Validate screen modes from EDID (the source is the monitor I guess), vesa modes and others.
[*]Load extensions
[*]Enable things
[*]Other X server things[/LIST] 
[*]Do an **intersection** of **modes** between the **calculated at start** and the** readed from the config file**.[LIST]
[*]That intersection of modes and rates is the displayed with **xrandr** programm.[/LIST] [/LIST]With that you will see now what is xrandr and how it get the modes and rates...






Notes in my experience[LIST]
[*]You can have more control with xrandr  than switch resolution (**CTRL**+**ALT**+"**+**" or "**-**") use _directly_ the **xrandr** application if possible.
[*]In the modes in the config file, you should write the **name** of the mode like is detected in the **Xorg.0.log** file for example in my case... and [COLOR=Red]note[/COLOR] that it all the modes work like spected (dont know exactly why)[LIST]
[*]1**024x768_87i** work OK (tought my monitor is supposed to not support interlaced mode I guess from the manual I found online)
[*]**1024x768_75** put the scren at black and led blinking (indicating a out of rate... like the manual say it dosent support this rate at that resolution... like I understand the manual)
[*]**1024x768_70** put the scren at black and led blinking (indicating a out of rate... like the manual say it dosent support this rate at that resolution... like I understand the manual)
[*]**1024x768_60** work like spected (the only oen that work nice and is like I understand the manual the case of my monitor).[/LIST] [/LIST]My xrandr say

> 
~$ xrandr
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 347mm x 260mm )  *60   75   70   87
 1    832 x 624    ( 347mm x 260mm )   75
 2    800 x 600    ( 347mm x 260mm )   85
 3    720 x 400    ( 347mm x 260mm )   85
 4    640 x 480    ( 347mm x 260mm )   85
 
you use it like[LIST]
[*]xrandr -s **XPixels**x**YPixels** for change the resolution
[*]xrandr -r **ValidRate** for change the rate of the actual resolution[/LIST]
> 
...how to I fix the resolution?  How do I make sure it uses a working resolution on startup?

the anterior have worked for me, only you need to put in xorg.conf the resolution name detected that work for you... in my case the config file  have some like

> 
ubSection     "Display"
        Depth       16
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768_60" "1024x768_75" "1024x768_70" "1024x768_87i" "832x624" "800x600" "720x400" "640x480"
    EndSubSection

 See that the default is **24** dept, then it will take like first resolution the one **1024x768_60**, if the default was **16** depth then it will take the default value (the max valid guessed/aprovated by the X server.. is like an Alias for 1024x768_75)

---

### Post by Sebaspi on 2006-08-17
Thanks hecato, thanks everyone im going to follow your instructions and let you know how it went.

---

### Post by zzarr on 2006-10-04
Hello!

When I boot my ubuntu amd64 6.06.1 desktop (live-cd)
the monitor go into the sleep mode when it should be
showing the desktop.

[http://home.astrakan.hig.se/zzarr/ubuntulog/]("http://home.astrakan.hig.se/zzarr/ubuntulog/")
This is /var/log on my failing ubuntu session.

Greetings Zzarr

---

### Post by zzarr on 2006-10-04
One thing I didn't think of is there I'm useing the digital output on my graphics card, but I don't think that matters?

An interesting thing is that the graphic is working fine in the startup
menu system until it shuts the x-server down to start the real one. (which
don't work with my computer)

I hope this leeds anywhere. ;)

I'm looking forward to be running ubuntu on my computer! :)

Greetings Zzarr

---

### Post by xstaticxgpx on 2006-10-04
> **clevershark said:**
> This is probably due to your graphics card. ATI x?00 cards are apparently not compatible with the standard ati/radeon drivers that come with Xorg. I've had the same problem when I tried out Fedora on one of my PCs (I have an x700 card).

not true, my x800xl worked fine with default Xorg drivers.

---

### Post by confusimo on 2006-10-04
That's weird.  I installed 64bit without any hitches on an Intel Celeron D 3.06 GHZ despite having AMD listed there and not intel.  And Nvidia BFG 256ddr card.  But Suse and Ubun tu 64bits would only install.  Fedora and Xandros wouldn't install.  Weird how some distros work and some complain eventhough the same card is used.

Thanks,
Confusimo

---

### Post by zzarr on 2006-10-04
Hello again!

Can someone tell me exactly how to do if I want to
install ubuntu?

Some computer specification:
cpu: AMD Ahtlon 64 3200+
memory: 2048 Mb
cd-rom reader: 48x
graphics card: ATI Radeon X800 XT PE
mainboard: MSI K8T Neo
disks: one 250 Gb PATA + one 250 Gb SATA + three 250 Gb USB 2.0

the logfiles from a live-cd start with graphics problems:
[http://home.astrakan.hig.se/zzarr/ubuntulog/]("http://home.astrakan.hig.se/zzarr/ubuntulog/")

Greetings Zzarr

---

### Post by John.Michael.Kane on 2006-10-04
zzarr what issues are you having?

Also have you tried to install without having your sata drives connected?
There's a known bug in dapper that affects some users with mixed hard drive setup's. not sure if this is still the case for edgy users.

---

### Post by zzarr on 2006-10-05
> **SD-Plissken said:**
> zzarr what issues are you having?

Also have you tried to install without having your sata drives connected?
There's a known bug in dapper that affects some users with mixed hard drive setup's. not sure if this is still the case for edgy users.
Hi!

The main problem is there I haven't got the graphics working on my computer. (except knoppix and looking glas live cd's, nither is 64 bit)

So the problem is that I want to swith os from win xp to ubuntu totaly (no dualboot), but there dosn't seem to be any garanti
that it will work.

When I boot the live-cd the menu looks fine, but then when it's
trying to display the desktop the monitor turn into standby.

And I remember that I was sitting for hour trying to get the
graphics work in debian (debian is a parent to ubuntu so to 
speak) without any result.

I know... it was XFree86 and not Xorg like it is now.
But in any way, if the live-cd was working I could test
the operating system too before I make any big decision.

I guess it's me, afraid of not getting the graphics to
work.

Greetings Zzarr

---

### Post by pay on 2006-10-05
I get the same problem zarr but it only occurs with the amd64 cd not the i386 cd. The amd64 cd works on another computer so I don't think that its a damaged cd. I could probably try the alternate cd but I don't think I will instead I'm probably going to install Gentoo or something. I think that it's a bug or something. I have a ati x800 pro with an nforce4 board and a amd64 3000+ cpu.

---

### Post by hecato on 2006-10-08
Have you tryied hit CTRL+ALT+"+" or "-" ???

Watched the output of xrandr???

Checked the modes in your log file (with logverbose)?? and know what modes are supported by your card and what are discarded (when compared/matched) via the config file?

---

### Post by pony-tail on 2006-10-09
I have found the same thing !
System AMD 64 4600+ X2
       Asus AN8SLI premium  
       Corsair 2 x 512 DDR400
       Radeon X850XT-PE
       2 x SATA HDD
       LG DVD burner
Using any of the Ubuntu / Kubuntu 64bit installers results in X failures of various kinds
I have tried configuring X after install using VGA VESA ATI modules but cannot get X up it either locks up totally or the monitor just switches off.
Prior to having attempted to install Kubuntu 64 the machine had Mepis 6 ( 32 bit ) installed with fglrx drivers I have had Gentoo 64 on the machine but had ( many ) other issues . I have , for the moment , put Mepis back on . I would like to run K / Ubuntu 64 so I will keep an eye on this thread to see if a soloution presents itself ( I am posting this from the machine )
It just seems strange that one disto will work out of the box and another not at all . I am going to try Edgy on it tomorrow on a spare drive and see if I can get that running .

---

### Post by pony-tail on 2006-10-09
Edgy worked after installing fglrx and reconfiguring xserver-xorg.
My method may work on 6.06 too ! 
Here is what I did.
I installed Ubuntu as per normal from the alternative install cd.
Then booted it up and waited for the log in to crash.
Then I did Ctrl + Alt + F2 to bring it back to a text log in
Then I logged in and edited my apt-sources (removed the hash symbols from infront of the universe and multiverse entries and saved .
Then I did an "apt-get update"
Then "apt-get install xorg-driver-fglrx"
Then "dpkg-reconfigure xserver-xorg"
Then "reboot -n"
I have my system setup with both root account and root login so you would have to ad sudo infront of each command .
If you have an nVidia card you would have to use "xorg-driver-nvidia" or something like that.
It worked for me - Hope it works for you.
Someone with a bit more experience may be able to do it more elegantly - If so please do so
Can verify that it does work on Dappa 64 as well !

---

