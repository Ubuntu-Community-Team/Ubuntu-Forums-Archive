---
title: "Installation problem (maybe video)"
date: 2006-02-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Slurm on 2006-02-15
Ubuntu Newbie first post.  

I put together a computer and am having trouble in the installation of Breazy. 
It gets through to the point where my video card comes on board and I get a weird looking screen that reminds me when a refresh on a monitor is not set correctly.  I put the refresh to the factory installation to no avail.  Now I am wondering if the video card is recognized.  I try to 'escape' out of the screen to see if I can get to a prompt to log in and I find my keyboard freezes up.   I have tried using a live Install disk just to get it working and that doesn't work either.  It seems to freeze after it says "registering documentation" and 'checking battery'  after that nothing.   What is going on? 

This is my computer:

MB ASUS A8N-SLI NFsli 939
VGA EVGA 6800GS 256-P2-N389-AX R
AMD 64  3200+
MEM  1G X 2  184 pin
RAID harddrives (set for mirroring)

Also, my motherboard is hyperthreaded and I read on this forum somewhere that my 'smp' and/or 'smt' must be enabled for Ubuntu to support hyperthread.  I cannot find either 'smp' or smt in the BIOS or CMOS to see if it is enabled.  I also tried to run a shell off the liveCD to run the command lspci  -vv to see if Ubuntu recognized all the hardware in my system.  This command is not in the lib it seems.


PLEASE help in this or I have just bought a $1500 boat anchor!!   Also,  I am NOT going to Windows so I will gut this out.  

Thanks in advance..
SLURM

---

### Post by l0cke on 2006-02-15
hi, i am getting the same problem with these specs
 
Foxconn nf4ua-8akkers (or something)
evga 6800gs
1 gig crosair value ram
160gb seatate sata drive
amd 3500+

need help!

---

### Post by RAOF on 2006-02-15
Your graphics cards (6800GS) are probably too new to be properly supported by the open source "nv" drivers that Breezy will by default use on them.

To get a temporary working GUI, boot into "recovery mode", and run "dpkg-reconfigure xserver-xorg".  The defaults should be fine, but when it gives a list of graphics drivers (which should default to "nv"), select the "vesa" driver instead.  This is a fail-safe driver, which will almost certainly work.

Once you've done that, you should be able to boot to a GUI.  Then check out the "nvidia drivers" link in my sig.

@Slurm: I'm not sure what you mean by "my motherboard is hyperthreaded".  "Hyperthreading" is found on some Intel CPUs, and is also known as "Simultaneous Mult-Threading" or SMT.  Nothing to do with motherboards.  Your motherboard may support dual-core processors, but you don't have one.  There's nothing you need to do.

---

### Post by extra SLURMy on 2006-02-15
Would you recommend downloading Dapper Drake (beta) (if they even have that), and do you think that will support this nvidia video card?

---

### Post by Slurm on 2006-02-16
Raof,

Thank you very much for the suggestion and I found out in a weird way that you are right in your assessment.  First, I looked and did not have a 'recovery mode' and could not run 'dpkg-reconfigure xserver-xorg' on my computer at all (it is not on the net).  But here is what I did to get around this.  My nvidia card has a TV line in and it comes with a connector so that you can connect your monitor through your TV line out.  I connected my monitor through my TV line out and it worked!!  Though it is not stunning graphics I can still pull it up.  

But thanks for the suggestion and I will start looking for a driver or something to fix it.  Quoting extra SLURMy,  will Dapper Drake have the driver for this??

Slurm....

---

### Post by RAOF on 2006-02-16
You don't need to have an internet connection to run "dpkg-reconfigure" - it merely allows you to change the configuration of already installed packages.

The driver to fix your problems is the nvidia driver.  Check the "nvidia driver" link in my sig.

I haven't used the nv drivers on Dapper - I use the nvidia binary drivers, as in the "nvidia-glx" package from the link in my sig.  Those will work.  These drivers are in Breezy - there's no need (at least for this ;)) to upgrade to Dapper!

---

### Post by l0cke on 2006-02-19
I tried the nvesa driver and it works! Now i'll be going to install the nvidia ones!

---

### Post by Slurm on 2006-02-20
1Olocke and RAOF,

I have to tell you both that I failed miserably at installing the NVIDIA driver.  I followed "Method 2" from RAOF's homepage and it went up in smoke on the first command.  The first command is like "getapt -- gcc3.4  gcc" (I know this isn't right)  The problem is that I got a message back "cannot find gcc3.4" which that was it.  Just for laughs I followed the rest of the procedure and watched my computer crash (I was suffering from what only could be called "The Pornography of Despair").  It is maddening that you know that gcc3.4 has to be on the computer and it is not there.  

Also, I tried EasyUbuntu to see if it will install the driver and that didn't work either.  EasyUbuntu can be found on this forum under 'third party software for ubuntu'.

RAOF,  could you tell me in big slow letters where I find gcc3.4 and should I be in root directory when I am executing this method?  

Solitaire works great!

Any help would be appreciated.  Also here is another problem that is quickly becoming imperitive.  I need to load AbiWord on this thing.  Of course Ubuntu will NOT load packages and will NOT load it from Source.  This time, it cannot find gtk.   My office work is BACKING UP badly because I cannot get this up and running.  Can anyone tell me what is going on with this?  I have never heard of a LINUX OS that I could not use tar -xvf and get it to load.  

I wish I was in Australia right now.  I hope you are enjoying your summer!

Slurm

---

### Post by Slurm on 2006-02-20
RAOF,

OK, I am closing in on a killer here. I downloaded your package on how to install programs using apt-get and more importantly using source to get it done.  I also understand the repositories that I need to get the stuff to do all of this.  HOWEVER,  my problem is that as of this moment, my computer is not online!  In fact, I am writing this from work and then copy all I need on a jump and take it home to work on it.  What I would like to do is download all the pckages from the repository, use the apt-get install and all the rest of the computer updated so I can possibly work with it.  The respository even has abiword which is the standard in this office I am working in.  

I looked over the page and could find no place where I can download any of this stuff without apt-get.  It does have a way to set up a place for extra repositories on your computer, but that is the end of it.  Can you tell me or point me to a way to download it and set it up on Ubuntu and then link it so the computer knows to look there for the packages and not try and go online?  

When I get this taken care of (esp the friggin video card),  then I will spring the money and go online.  A cart before the horse?   Maybe, but it is also foolish to invest more money in this if I cannot deal with what I have already.

Constantly mixing metaphors,

Slurm

---

### Post by RAOF on 2006-02-20
You can manually download packages from [packages.ubuntu.com](packages.ubuntu.com).  This, unfortunately, does not automatically resolve dependencies for you.  It will list the dependencies of the packages, but you'll probably have most of those.  If you don't mind downloading more than you have to, you can download all the dependencies.

Once you've got the .deb (and any of the dependencies you think you'll need), you can copy it to your Ubuntu machine, and run "sudo dpkg --install name_of_deb.deb" to install it manually.  Alternatively, copy all the .debs to a directory and run "sudo dpkg --install *.deb" to install them all (in that directory).

Alternatively, apt-zip might be what you're after.  It seems to allow you to go "apt-zip packagename", just like apt-get, and instead of trying to download the packages it creates a script you can run on another machine to get all the packages, then return and install them.

---

### Post by Slurm on 2006-02-27
Hey All,  

I just wanted to say I got everything working.  I finally dragged my computer to a friend's house and got it online.  Everything was fixed that needed to be fixed and the system works great!

I should note to the forum that I had to go to sources.list and decomment all the lines in order to get  'apt-get' to work.  This took a while of poking around to find out.  Why do you think that all the sources.list were commented out so there was no way for the system to look online??  Just curious..

I am having some problems with playing mp3 and sound but I will find a different forum for this.. 

Also, can anyone tell me how does one request to get a package made so to speak??  I need to load Bibus on my comp, but I cannot resolve all the packages since it relies heavily on MySQL 3.4 (yes I loaded it) but there is still some problems.  A greater man than me will have to figure this out or show me how to figure this out.  Plus and bibleography program which can import files from Endnote is a great thing to have.  

Please let me know and I will start kicking around other forums.  

Thanks for the help.. 

Slurm

---

