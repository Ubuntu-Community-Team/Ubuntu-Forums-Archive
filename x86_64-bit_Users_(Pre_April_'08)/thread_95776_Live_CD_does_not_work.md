---
title: "Live CD does not work"
date: 2005-11-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by korakde on 2005-11-27
Hi,
I am  writing this so  that I may get some help to get my Linux up and running.  Firstly,  I am a rank beginner as far as Linux goes. I downladed my copy of Ubuntu 5.10 from the net and gave the live CD a spin.  Everything seemed to  be going OK. The OS asked me for  the screen resolution and I filled it up.  Then after some time, I get a fatal error message that X11 server could not load.  The system just sort of  freezes. When I press the power button on my CPU, the system shuts down like  a Linux system  should.  
The following message comes when the X11 hangs. 


Window System Version 6.8.2(Ubuntu 6.8.2-77 20051010174819 root @ crested.warthogs.hbd.com.
Release Date 9 Feb 2005]
X Protocol version 11, Revision 0, Release 6.8.2
Build OS: Linux 2.6.8.1 X86_64 [ELF]
Current OS:Linux Ubuntu 2.6.12-9-amd64-generic #1 Mon Oct 10 13:27:39 BST 2005 X86_64

Module Loader Present
OS Kernel: Linux ver 2.6.12-9-amd64-generic (buildd@king)(gcc version 3.4.5 20050809 (prerelease)(ubuntu 3.4.4-6ubuntu ) #1 Mon Oct 10 13:27:39 BST 2005

it shows the markers (didnt copy thoes down..)

(==)Log file:"/var/log/xorg.0.log" Time wed 2 nov 2 7:52:58
(==)Using Config file:"/etc/x11/xorg.conf"
Skipping
"usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o": no symbol found
Skipping
"usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o": no symbol found
Skipping
"usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o": no symbol found
(EE) RADEON(O): [dri] DRI ScreenInit failed.  Disabling DRI.
(EE) RADEON(O): XAA Init Error
Fatal server error: Caught signal  11.  Server aborting. 

I browsed through various posts and one post of Nella 89 " [http://ubuntuforums.org/showthread.php?t=85295](http://ubuntuforums.org/showthread.php?t=85295) "  was quite similar, though she seemed  to have first loaded Ubuntu on her PC  before experiancing this problem. My problem is right at the Live CD stage.  
Now, when I went through this post, Teroedni suggested that she write:

sudo nano /etc/X11/xorg.conf

You get a text file
Scroll down to where it stands section device
and then you se a subsection driver "xxx" i write xxx since i dont know what you hav there. SAnyway remove whatever stands there and put in either ati or vesa
after you done that
press ctrl+0 
thebn you save your file
 
 Then restart and you should be able to get into Ubuntu
and then its get easier to fix the problem(i guess you want 3d)

I don't think  I can do this  with the live CD.  
Another post by yellowguy " [http://www.ubuntuforums.org/showthread.php?t=93553](http://www.ubuntuforums.org/showthread.php?t=93553) " documents  a similar problem.  There  don't seem to be  any solutions  up until now. So I was   really tempted  to start a new thread. 
Can someone  help me.
 My system specs:
AMD64 939 pin 3000+
MSI RS482 IL motherboard with integrated ATI Xpress200 graphics driver. 
A 40GB Seagate HDD as master and a Hitachi  80GB as slave. Both IDE.  I was  planning to load Ubuntu on the primary partition of the Hitachi HDD and have a unformatted partition of 16GB earmarked  for it.  My comp is used by other users in my family and I am quite paranoid about inadvertantly ruining their data. So, I found it safer to load Linux on the slave HDD. 
My system has Windows OS on the C: drive which works OK.
ASUS  52X CD writer.
Hynix DDR 400 RAM 512MB
I assembled the system myself. 
Please,  I am desparate to get  Linux going on my system. So pleeeeeeease help.

---

### Post by jluquette on 2005-11-28
Got exactly the same error message you did.  If this helps you avoid some wasted time, it  will also happen if you use the install version too.  It just happens later - after the install.  I went to X.org website and found, down on the page, a place for bug reporting.  This took me to freedesktop's web site where I could do a search using bugzilla.  There I found dozens and dozens of bug reports about not being able to start X after install.  But I don't think there was any info that could help me.  Maybe you can get something from there.  I think one needs to know more about Linux (Unix) to really understand what they are talking about - although many of these people did say that they were newbies.  If you figure something out please let me know as I am in exactly the same place as you (note my thread right after yours).
PS   Never could make it work.  Had to go back to Windows XP (which loaded just fine).
PSS   I'm using a new GigaByte MB with built in PCI Express like yours.  Not using an add-on video card.  Also, if you read the reply to my thread, I tried the suggestions that he gave me and it didn't work.  Maybe someone else will have another suggestion.

---

### Post by jvictor on 2005-11-29
Looks like ur ATI card is the villain. Can u just boot in from the CD and let knwo what exactly is the driver used in the Device section of /etc/X11/xorg.conf ? ATI cards are bit a pain .. Now coming to the core of the problem, 
I see that 

[I]"usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o": no symbol found
Skipping
"usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o": no symbol found
Skipping
"usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o": no symbol found[/I]

which makes me assume that ur xorg.conf maybe having lines 
load GLCore 
....
.....

try commenting off that GLCore line and change the driver to **vesa** instead of **ati** in xorg.. it should be possible to edit xorg.conf even on a Live CD ..( eventhough ivent tried it :rolleyes: ).. Can u plz tell us what prevents u from editing that file ?

can u run

sudo nano /etc/X11/xorg.conf ?

---

### Post by victor_c26 on 2005-11-29
The problem with trying to edit the xorg file victor is that we can't get into Ubuntu, at all. It crashes right when Ubuntu tries to start.

Isn't there a boot command that lets us use the VESA drivers right from the start? I really just want to use the live cd for now, since I don't have a spare FAT32 fomatted HD at the moment.

EDIT: Also, is there anyway to pre-set the monitor's refresh rate too? I get a headache trying to run my monitor at 60 Hz

---

### Post by victor_c26 on 2005-11-30
Anyone?

EDIT: Honestly, I seriously doubt setting the system to use VESA on the live disc is impossible.

Does ***anyone*** know?

EDIT 2: How do you configure the xorg.xonf file on the live cd though. I've been trying to use the live cd for a couple of months now with no luck.

Is there a command that I have to enter at the boot screen in order to be able to edit the xorg.conf file. I know what to do in order to edit the file so ubuntu uses the VESA drivers, but when I try to run the live cd, it just loads the OS without even giving me a choice as to which graphical driver I want to use.

I'm really close to giving up on linux all together guys. It's a shame really, it feels like a great OS, but damned if the ati issue isn't incredibly frustrating.

I'm writing this post on Ubuntu right now on an old laptop with the live cd running, and also installed Ubuntu on an old computer I have (Old Celeron with 128 MB of RAM). But I'd really like to use the live CD on my most powerful rig (Athlon 64 3500+ Venice core with 1 GB of DC DDR RAM). But it happens to have an ATi card. I'm still rather surprised this hasn't been fixed a long time ago, both on the ATi front, and the Ubuntu front.

Instead of using the ATi drivers that come packaged in the live CD, why not switch the xorg.conf setting to VESA upon detecting an ATi card?

---

### Post by korakde on 2005-12-01
Hi,
Here's the latest post on my problem:
During bootup with the live CD
1. I wrote:
sudo nano /etc/X11/xorg.conf ? 
and got a reply 'cannot find kernel sudo'
2. Then I tried writing:
/etc/X11/xorg.conf ? 
and got a reply ' cannot find kernel X11'
3. I then tried booting by writing:
live X11=off 
and got the same results of before. The system just hanged at XServer stage after seeming to load beautifully till then.

Any more idea's anyone. Like victor c26 said, I guess the solution to the problem would be to load VESA drivers right at the start, but the problem is how. 

Now, here's something that would interest a geek:
When the system hangs up, part of the message says 'Please also check the log file at "/var/log/Xorg.0.log"
Then when I press enter, I get a message, 'Do you want to see the Detailed XSever output'. I pressed yes, and I got a mesage which was atleast a few hundred lines. It seemed like the log file mentioned above. Amongst the contents of these hundreds of lines I saw:
ATI: ATI driver (version 6.5.6) for chipsets: ati, ativga
Then in the list, I saw the name of my display chipset 'ATI Radeon Xpress200'.
I dont know any way I can save this file to HDD. I guess that would be useful.

---

### Post by korakde on 2005-12-01
.

---

### Post by Mr_Grieves on 2005-12-01
I got exactly same problem, trying to install on a friends amd-box. Amd Athlon 64 Processor (3000+), and a Radeon X800 (256 mb).

I've tried both the AMD64 live CD and the general i386 live CD.

---

### Post by RAOF on 2005-12-01
[QUOTE=victor_c26]...
Instead of using the ATi drivers that come packaged in the live CD, why not switch the xorg.conf setting to VESA upon detecting an ATi card?[/QUOTE]
Because all but the very newest ATI cards actually **work** with the driver on the live CD ;)

But after it has booted, and failed to load the X server, does it really hang?  If you press Ctrl-Alt-F1, do you get to a terminal?  If so, you should be able to change the X driver to vesa from there and then restart X.

@Mr_Grieves - If you've got it installed, and the X server doesn't start, you could just boot into "recovery mode" and change the X driver to vesa.

---

### Post by victor_c26 on 2005-12-01
[QUOTE=RAOF]Because all but the very newest ATI cards actually **work** with the driver on the live CD ;)

But after it has booted, and failed to load the X server, does it really hang?  If you press Ctrl-Alt-F1, do you get to a terminal?  If so, you should be able to change the X driver to vesa from there and then restart X.

@Mr_Grieves - If you've got it installed, and the X server doesn't start, you could just boot into "recovery mode" and change the X driver to vesa.[/QUOTE]

Oh, I see. Blast, I had a Radeon 7500 installed on my old Celeron (The one I installed Ubuntu on), but I removed it and used it's Intel Integrated chip. Can one easily install the ati drivers again if I ever want to install the 7500 back?

About the live CD on my A64 machine: The thing is, the end result varies. Sometimes it takes me to a command prompt display of the loading splash screen (Where it tells you if something loaded or failed). But I can't enter anything with the keyboard, as the keys are unresponsive. Sometimes it just takes me to the dreaded flashing prompt underscore (Keys unresponsive). Onetime I got to the command prompt, but that was when I wasn't aware of the actual procedure to edit the xorg.conf file.

Isn't there a boot command that lets me start Ubuntu without starting X? That way I can edit the xorg.conf file without trying to wait for the prompt like a lottery.

---

### Post by RAOF on 2005-12-01
[QUOTE=victor_c26]...
Isn't there a boot command that lets me start Ubuntu without starting X? That way I can edit the xorg.conf file without trying to wait for the prompt like a lottery.[/QUOTE]
There should be, yes, but I'm not familiar with the livecd.  You could try "linux single"?  That should boot it into single-user mode, which won't load X.

---

### Post by RAOF on 2005-12-01
[QUOTE=victor_c26]Oh, I see. Blast, I had a Radeon 7500 installed on my old Celeron (The one I installed Ubuntu on), but I removed it and used it's Intel Integrated chip. Can one easily install the ati drivers again if I ever want to install the 7500 back?...[/QUOTE]
The ATI drivers won't have been removed.  If you ever put the Radeon back in, the ati drivers will be only a "sudo dpkg-reconfigure xserver-xorg" away. :)

---

### Post by cvcaelen on 2005-12-02
downloaded the life cd-iso
burned onto a cd
booted from cd
.
.
.

and all went well=D> =D> 

I'm feeling like a kid who found Santa-stuff on Xmas morning:) 

time to experiment

Christiaan

---

### Post by Robocoastie on 2005-12-04
You're ATI card is the culprit. Just get to the command line and use vi to edit your /etc/X11/xorg.conf to say driver=vesa save, and startx and you'll be good to go. If you choose to install ubuntu there's an excellent howto here for installing the latest ATI driver.

vi guide for those unfamiliar with this simple yet powerful editor:
[http://acs.ucsd.edu/info/vi_tutorial.php](http://acs.ucsd.edu/info/vi_tutorial.php)

---

### Post by korakde on 2005-12-06
cvcaelen, you seem to be the luckiest guy on this planet. Wish I get some of your luck while running my live CD. 
Robocoastie, I'll try implementing your idea. Hope it works. Same for RAOF 
 This forum seems to be flooded with problms concerning ATI compatability issues. Hope the bigwigs in ATI are watching. I guess, I'd do womething to solve these problems in a hurry if I was a research head at ATI. It's not good publicity.

---

### Post by korakde on 2005-12-08
A few link's to other users with trouble with their ATI graphic chipsets:
[http://www.ubuntuforums.org/showthread.php?t=99725](http://www.ubuntuforums.org/showthread.php?t=99725)
[http://www.ubuntuforums.org/showthread.php?t=98687](http://www.ubuntuforums.org/showthread.php?t=98687)

---

### Post by rengens on 2005-12-08
Well, I'm sorry I started a new topic. Just did not find this at the begining... 
Now I am on ATI suffers club:)

I hope we find something better than Vesa soon ...

---

### Post by TheGame619 on 2005-12-09
Well I just downloaded Live CD yesterday, but i have a problem: 

I burned the image to a cd, but whenever i restarted my computer, it would attempt to read the cd, but then it restarts again. Only when I press F8 while it posts does it read the cd without restarting,but then it asks me questions like single step such and such and after all that, it brings me to an actual dos prompt and it starts with A:\. I'm kind of a noob when it comes to dos and linux, so if you can help me out, please explain what to do in a language ill understand. If this helps any, i downloaded the AMD version and my computer specs are listed below: 
Biostar NF4ST-A9 motherboard 
AMD 3200+ socket 939 
1 gig of ram 
WD 250 gig Cavier SATA hard drive 
Evga 6600 256 mb video card 
onboard audio: Realtek AC'97 codec

---

### Post by TheGame619 on 2005-12-09
Well every1 i have a question to ask before i give up on Live CD.................Do you think the regular install version have the same problem or not because i am getting fed up with trying to make Live CD work:mad:

---

### Post by vladnl on 2005-12-10
Okay guys here is solution for booting up Live CD on problematic PC's with ATI graphics cards.
I have Compaq R4000 with ATI X200, so I was also looking for a while at forums, but no luck. In meanwhile I was trying different settings on my laptop, and solution is quite easy.
When you get to the boot screen type in:

**live-expert**

You will get bunch of setting options, and usually you should choose whatever system offers you, until we come across your vga detection. You should choose No for the auto detection and manually select **VESA** driver, resolution and monitor depending on your hardware. When you come acros modules that would be loaded, mark off DRI, as I've read somewhere that DRI causes hanging problems also. Lastly, when we get an option to choose in which init level system should be booted, we choose **5**, we want our GUI desktop, don't we? :)

That's it, it should work, only nightmare is to find a way how to save default settings on USB key, or whatever removable media, as it would be pain in arse to go through this process every time you want to boot Live CD.

Cheers, and I hope this will help you too.
Vladimir

---

### Post by korakde on 2005-12-13
[QUOTE=vladnl]Okay guys here is solution for booting up Live CD on problematic PC's with ATI graphics cards.
I have Compaq R4000 with ATI X200, so I was also looking for a while at forums, but no luck. In meanwhile I was trying different settings on my laptop, and solution is quite easy.
When you get to the boot screen type in:

**live-expert**

You will get bunch of setting options, and usually you should choose whatever system offers you, until we come across your vga detection. You should choose No for the auto detection and manually select **VESA** driver, resolution and monitor depending on your hardware. When you come acros modules that would be loaded, mark off DRI, as I've read somewhere that DRI causes hanging problems also. Lastly, when we get an option to choose in which init level system should be booted, we choose **5**, we want our GUI desktop, don't we? :)

That's it, it should work, only nightmare is to find a way how to save default settings on USB key, or whatever removable media, as it would be pain in arse to go through this process every time you want to boot Live CD.

Cheers, and I hope this will help you too.
Vladimir[/QUOTE]


Vladimir, your's seems to best solution to all ATI user's troubles. This seems the best solution. Only I'll be out of town for the next 50 days and will not be able to try this. RAOF seems to have already started spreading the message to others.
Cheers

---

### Post by jim-fwb on 2005-12-25
I just tried Vladni's solution and got a working X11 desktop.  Thanks! Now I'll not worry about doing an actual physical insatll.  Just got that new box.  The Window EULA-stuff makes me want to puke.  Fortunately, I already had the live CD burned.   Ubuntu,like Debian, is cool.

---

### Post by antjenkins on 2006-01-13
[QUOTE=vladnl]Okay guys here is solution for booting up Live CD on problematic PC's with ATI graphics cards.
I have Compaq R4000 with ATI X200, so I was also looking for a while at forums, but no luck. In meanwhile I was trying different settings on my laptop, and solution is quite easy.
When you get to the boot screen type in:

**live-expert**

You will get bunch of setting options, and usually you should choose whatever system offers you, until we come across your vga detection. You should choose No for the auto detection and manually select **VESA** driver, resolution and monitor depending on your hardware. When you come acros modules that would be loaded, mark off DRI, as I've read somewhere that DRI causes hanging problems also. Lastly, when we get an option to choose in which init level system should be booted, we choose **5**, we want our GUI desktop, don't we? :)

That's it, it should work, only nightmare is to find a way how to save default settings on USB key, or whatever removable media, as it would be pain in arse to go through this process every time you want to boot Live CD.

Cheers, and I hope this will help you too.
Vladimir[/QUOTE]

*OF COURSE* I just found this after having to figure that out for myself.

By the way, you can just hit enter with a blank field for the Run Level.

Now my only problem is that I have to unplug all my USB devices or it will freeze during install...

---

### Post by linux123 on 2006-01-13
[QUOTE=korakde]Vladimir, your's seems to best solution to all ATI user's troubles. This seems the best solution. Only I'll be out of town for the next 50 days and will not be able to try this. RAOF seems to have already started spreading the message to others.
Cheers[/QUOTE]

also i have this problem with my pavilion laptop! nice question! never brought that type of laptop again!
nice day fool.!

---

### Post by korakde on 2006-02-06
A big hello to all Ubuntu users. Finally I got my live CD working. The Idea to use a VESA driver instead of ATI was wonderful. Will there be any performance reducion? 
Now there are other issues though but I guess I should start a new thread for them. I guess, when using a live CD, Ubuntu cannot see FAT32 partitions on the Hard Disk. Someone please correct me if I am wrong. My USB flash memory is working fine though. Thanks everyone for all the help.

---

### Post by RAOF on 2006-02-06
[QUOTE=korakde]A big hello to all Ubuntu users. Finally I got my live CD working. The Idea to use a VESA driver instead of ATI was wonderful. Will there be any performance reducion? 
Now there are other issues though but I guess I should start a new thread for them. I guess, when using a live CD, Ubuntu cannot see FAT32 partitions on the Hard Disk. Someone please correct me if I am wrong. My USB flash memory is working fine though. Thanks everyone for all the help.[/QUOTE]
There will be a performance reduction from ATI to VESA - the VESA driver uses none of the hardware acceleration the card is capable of.  On the other hand, it works, and a slow, working driver still performs better than a fast, non-working driver :)

The livecd should be able to see FAT32 partitions, but it's possible that they aren't mounted automatically.

---

### Post by victor_c26 on 2006-02-18
Do we type in init5 in full or do we just enter the number 5?

The system keeps hanging right when ICE loads. Don't know if it's because I keep entering init5 in full/entering the value wrong, or if it's because I'm running a mouse through USB.

---

