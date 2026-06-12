---
title: "A Little Trouble, but a Lotta Patience"
date: 2006-03-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Frank65 on 2006-03-21
Hello,

I just registered on the forum and I'm a little nervous, so bear with me.

I have in my possession six Ubuntu CDs which I received free for the asking. Three different platform installs and their respective Live CDs.

I have an old 700 MHz iMac G3 (Model iMac [ver. 33.11]) with 512 ram and 80 GB h/d presently and pleasantly running OS X 10.2.8. I wish to take the Ubuntu Live CD for a spin in the hopes that I can run it full time on the ol' G3. 

I just tried it a little while ago. Unfortunately, after the nice unique start-up tones and some cd-rom drive activity, all I'm presented with is a black screen. I browsed this forum for some help and tried the "reconfigure" suggestion presently on page 3 of the Mac section. Control-Option-F1 in fact gives me the command line so I think this means that the OS just didn't set up the display correctly. But I get spooked to do anything else without a book or manual for reference.

I was hoping one of you mavens can give me a little advice to get me started. I believe firmly that Linux and the open source community are on the right track. I also have an extreme distaste for the Redmond Borg philosophy.

Please help me take the first step.

Sincerely,

Frank65

P.S. - does the desktop background come in any other color besides brown?
  :-)

---

### Post by oswaldkelso on 2006-03-21
Hi Frank65
It is unusual to fail to get the gdm (graphical display manager) working from scratch on an G3 imac. From what I've read and my experiance with my g4 it is usually the xorg file that needs to be set up. I'll install linux on my spare 333 imac latter on so you can borrow the settings if know one helps you while I'm away. I'll be about 5 hours.
When you get the command line interface (clf) type "startx" If it just need a nudge this should give you Gui. Have to go I'm late I'll post later.

oswald

---

### Post by jdp on 2006-03-21
Another very common problem is the Gnome Datee Bug.  Make sure the machien has the date set to something sane.  You may need to replace the PRAM battery to maintain the settings when unplugged.

---

### Post by Frank65 on 2006-03-21
Hello, again

Thanks for your speedy replies.

Firstly, this G3 iMac is always plugged in and used in conjunction with my my other main iMac G5 while it's busy, so I doubt if there is any concern about the PRAM battery or the date and time.

I fired the G3 up again with the Live CD today. After a bit, and at the black screen I mentioned above, I started the command line and typed in "startx". I am then presented with the following:

"xauth: creating new authority file /home/ubuntu/.serverauth.20895

Fatal sever error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock and start again.
Please consult the The X.Org Foundation support at [http://wiki.X.Org](http://wiki.X.Org) for help." 
The quotes are mine.

Please keep in mind that I want to only run the Live CD.

Now Saturday and Sunday nights are my computer "camp-out" nights when I spend many hours cruisin' the Internet, burning cds and other stuff. I could try an actual install on the G3 while I'm on the G5. I've read that the Ubuntu OS install will just partition off a chunk of the existing h/d space and that I won't lose any of my Mac OS afterwards, right? If this is true, then I will ask at another time how to change the startup disk in Ubuntu to reboot into Mac OS on the G3.

Still, I'd like to test drive the Live CD before committing to an install.

Again, I really appreciate the help.

Thanks.

Frank65

---

### Post by linear on 2006-03-21
For an iMac G3, I recommend the following:
 
After booting is complete,
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edits (see below)
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo /etc/init.d/gdm restart (return) to restart Gnome

At the very least you'll need to modify "HorizSync" to 60-60 and "VertRefresh" to 75-117. Both are in the monitors section.

If you restart Gnome and everything is in extreme slo-mo, you'll also need to edit xorg.conf to disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").

---

### Post by Frank65 on 2006-03-22
Finally something different, but it still nothing worth smiling about.

I made the edits as outlined. Changed the horiz and vert in the monitor section, saved the file and restarted. Sonn a grey display came up with a white arrow cursor in the center and the top third of the screen is black. 

You may be on to something here. Please give it another pondering.

Thanks again. I await your reply(ies).

Frank65

---

### Post by 3rdalbum on 2006-03-22
When you start up the Live CD and get the yaboot prompt, type "expert" (I think). The setup program will then ask you EVERYTHING it wants to know. When it asks you if you want video card autodetection, say No and select "ATI". When it asks you for monitor autodetection, say No again. Put in the information that linear gave you above. Try that.

FYI, display problems with the Live CD on iMacs are very very common unless you use the expert mode or edit the xorg file; but the good news is that they're rare when using the install CD.

Is it just a black screen, or has the monitor actually switched off? Mine would switch off. The reason why you can't do startx from a terminal is because the X server is already running - however, it is sending its image data to an address that doesn't exist.

---

### Post by linear on 2006-03-22
Did you try disabling DRI as described? That may be your missing piece.

---

### Post by Frank65 on 2006-03-23
HUZZAH! By Jove you've done it!

The Live CD and "nano" edits ... in addition to the all important MISSING PIECE, disabling DRI did the trick. 

I will run the install disk on the ol' G3 this Sunday, and I will spend some time shaking the trees and kicking the tires in the meantime.

My most gracious thanks to ***linear*** and the others who helped.

In anticipation of the big install, I have just a few more inquiries:

I'm positive that the Ubuntu install will just repartition some space and still leave the Mac OS intact. Is this positively true?

How would I use Ubuntu in conjunction with Mac OS? Select OS on startup? (dual boot?) 

On quitting Ubuntu how do I get back to Mac OS?

Thanks again.

Frank65

---

### Post by linear on 2006-03-23
If you want to repartition, you'd be better off doing it before starting the install.
 
You can either: back everything up, use Apple's Disk Utility to partition the disk (destructively, meaning you'll need a good backup - I like [Carbon Copy Cloner]("http://www.bombich.com/software/ccc.html")), and restore; or back everyting up (just in case), and use the instructions [here]("http://www.ubuntuforums.org/showthread.php?t=89960") to resize the existing partition.

Also read these, they're useful:

[https://wiki.ubuntu.com/Installation/PowerPC]("https://wiki.ubuntu.com/Installation/PowerPC")
[https://wiki.ubuntu.com/YabootConfig...werPCsDualBoot]("https://wiki.ubuntu.com/YabootConfig...werPCsDualBoot")
[http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html]("http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html")
 
Basically, if you've repartitioned first, you can let the installer use the largest free space.
 
After the install, you'll get a text boot menu on each startup. Ubuntu will be the default, but you can change that by following the instructions above.

---

### Post by jdp on 2006-03-23
And by free space, it's meant that you leave space with nothing there, ie. no partition.  Leaving an empty partition is not the same thing.  You can leave a partition there, and remove it inside the installer, but it "might" be less stable to do it there than with "official" Mac OS tools like Disk Utility under OS X.

---

### Post by Frank65 on 2006-03-24
This is wonderful. With all the existing instructions now staring me in the face and a large free block of time on Sunday, I will read and do my homework and do a backup. 

I will repost with results. Talk to you then.

Thanks.

Frank65

---

