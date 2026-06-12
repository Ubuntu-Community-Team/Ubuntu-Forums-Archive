---
title: "Beginners beginner"
date: 2009-06-20
forum: Za Team - South Africa
---

### Post by mcnaugg on 2009-06-20
Hi there

I have been using windows since its inception so I am, I think, reasonably at home with windows and its workings (as an end user) etc but I know nothing about Linux and Ubuntu other that the names.

Some time ago I updated to Vista and as a result became totally ********** off with the system.  So I have obtained a copy of Ubuntu 9.04 Desktop Edition from Canonical and have installed it on a spare PC which has XP installed.  I chose to install Ubuntu inside windows as I didn't want to clean the PC just yet.

The PC is a P4 Celeron with 1m Ram, 80meg HD and DVD.  I use Iburst Wireless to connect to the Internet via UTD Desktop Modem.

I have loaded Ubunu with out any problem and those programs that were installed by default seems to run OK. However I cannot get the modem to connect, in fact I'm not sure if the modem is recognised.  From searches on the net, from my main PC, it seems that the Modem should use the RJ45(ethernet) connection rather than the USB.  I have changed from USB to RJ45 and I am still able to connect to the Web via windows so the modem connection is working.
From the “How to” directory on the Wiki.Ubuntu-za web site I have read the article on setting up an Iburst modem on Ubuntu _Intrepid._  Is Intrepid the same as 9.04 and are the instructions still valid?
 

 I realise that the Linux systems use a completely different approach than windows so I am struggling to understand some of the commands which seem to be simialar to Windows Command line instructions. For instance in the Iburst Modem How To set up, it says - “sudo apt-get install linux-headers-2.6.27-7-generic'.
 

 Question: from where do I do this command?
 

 Any help would be gratefully accepted.
 

 Gareth

---

### Post by lisati on 2009-06-20
I'm not familiar with the iBurst modem but found this thread which might be helpful: [http://ubuntuforums.org/showthread.php?t=1145369](http://ubuntuforums.org/showthread.php?t=1145369)

---

### Post by mcnaugg on 2009-06-20
I have just found a local (South African) web site for Ubuntu so I have posted a message there as I suspect that the modem I use maybe peculiar to South Africa.

Many thanks for the reply.

Gareth

---

### Post by SabreWolfy on 2009-07-04
Any luck with this yet? Are you using a normal dial-up modem?

---

### Post by Flash858 on 2009-07-04
This may be a moot point, but as no one has answered your specific question yet, the place you enter commands is the "terminal". It is the Linux equivelent of the "command prompt" in Windows, and can be found by selecting the Accessories menu...

---

### Post by mcnaugg on 2009-07-06
Hi there 

I have had a number of replies to my original query but so far I have not been able to get my Iburst modem connected.
I think the main problem is that I have been brought up on Microsoft (XT, AT etc) and have become blinkered when trying to use another system.  I have no doubt that Ubuntu/Linux is a viable system but I am an end user, not a computer technician, and also there are no Linux users in my small circle of friends on whom I can prevail.  Forums like this are great but there comes a time when you need to be able to plonk the PC on somebodies desk and say "Fix it".  

Please don't get me wrong since I have a quite a few replies trying to help but I think that what I should perhaps do is to obtain a basic book on Linux because I don't understand expressions such as sudo and pppoconf and therefore don't have a clue.

Again thanks to all those who have tried to help.

Gareth

---

### Post by SabreWolfy on 2009-07-06
How is the modem connected to the PC? You mentioned earlier something about an ethernet connection or a USB connection?

---

### Post by carml on 2009-07-06
> **mcnaugg said:**
> 

Please don't get me wrong since I have a quite a few replies trying to help but I think that what I should perhaps do is to obtain a basic book on Linux because I don't understand expressions such as sudo and pppoconf and therefore don't have a clue.

Again thanks to all those who have tried to help.

Gareth

Sudo is the command you use for administrative tasks,pppoeconf is a wizard to set up a PPPoe Modem i.e. to establish a connection in which Username and Password is required,this kind of connetion is the one used frequently at home.
If someone asks you to type something in a terminal,just go to Applications->Accessories->Terminal and type there what they ask you.
I hope I clarified you some doubts,if there are any more,just ask and someone will answer you. ;) ):P

---

### Post by mcnaugg on 2009-07-06
Hi there SabreWolfy

The modem is a IBurst wireless broadband modem, which is normally connected via USB in windows.  There is also a RJ45 (Ethernet) connection which can be used.  When used in windows there is a piece of software supplied which puts a "Dashboard" on the screen which is used to connect to the wireless broadband and also gives an indication of the amount of "Data" remaining, in my case I have a 1Gig package.

When I contaced IBurst regarding a Linux driver they were not very forth coming except to say that due to all of the various versions of Linux I should visit Sourceforge for a driver.

---

### Post by SabreWolfy on 2009-07-06
Open a terminal window (Applications --> Accessories --> Terminal) and type

```

lsusb

```

and then copy the output and paste it into a new message here.

I presume you are using Wireless iBurst, not ADSL iBurst?

---

### Post by mcnaugg on 2009-07-07
Hi

done as requested:

gmc@linux:~$ 1susb
bash: 1susb: command not found
gmc@linux:~$ 


I am using an Iburst Wireless Modem connected to the PC via the USB port.  According to the lights on the modem it is connected to the PC.  Ubuntu is installed as a dual boot.

Gareth

---

### Post by SabreWolfy on 2009-07-07
The code you needed to paste was "lsusb" -- that is "EL" -- the lower-case LETTER "L", not the digit "1". Please try again and post the output here.

The second part of your reply may have answered my question though. The "lsusb" command will list the devices attached to your USB ports. I wanted to check if Ubuntu was at least detecting that the modem is connected.

Do you have any network/connection icon/s in the system tray in the top-right of the screen? Have you tried left- or right-clicking these to see if there are any other connection options there.

---

### Post by mcnaugg on 2009-07-07
I wondered if it was a "1" or an "l" however I have inputted the command again and get :

	 	 gmc@linux:~$ lsusb
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 002 Device 002: ID 0482:0204 Kyocera Corp. iBurst Terminal
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 gmc@linux:~$ 



So the modem is being seen.  As far as any indications in the system tray all I can see is a "bargraph" 



I do not have a printer connected to this pc yet.



Gareth

---

### Post by SabreWolfy on 2009-07-07
Yes, the modem is being detected -- or at least the modem is telling Ubuntu that it is there.

A blue bargraph? That's the network icon -- are there any options available if you left- or right-click it? I know the Ubuntu supports 3G and some mobile devices, so I'm wondering if the same applies in your case.

Did you have any luck with the reply [here]("https://lists.ubuntu.com/archives/ubuntu-za/2009-June/003522.html")?

There is a driver on SourceForge [here]("http://sourceforge.net/projects/ibdriver/").

Found a tutorial [here]("http://blog.hostinghabitat.com/2009/02/iburst-usb-modem-installation-tutorial.html").

---

### Post by mcnaugg on 2009-07-08
Hi there SabreWolfy

I am please to say that I am now able to connect via my IBurst modem.  Following your info and the feedback from Arnold plus the tut listed I have connected.  I have to admit that I am not excactly sure what I did differant this time but it has worked in the end. I have now to learn the rudiments of Ubuntu/Linux to see if it is was I want.

I understand that downloading of software is via "repositories".  How does that work?  Can I still have software on a CD etc and load from it?  If so how?

I have been using Open Office (windows) for some time and would like to use it via Linux.  I see that Writer and Calc has been loaded with Ubuntu but not Base.  Is there a reason for this as I use Base for a number of simple DB's.

Gareth

---

### Post by SabreWolfy on 2009-07-08
Great stuff! I'm so glad that you managed to get it to work!

Ubuntu is a Debian-based distribution and we have access to all the packages (applications) in the Debian repositories -- some 25000+ applications or something. Typically these are installed via apt or aptitude at the command line or via the Synaptic GUI if you don't like the commandline. Have a look under System --> Administration --> Synaptic Package Manager.

It is also possible to install software from anywhere else (CD, Flash drive, etc.). If this software is packaged as a .deb file, then it is really easy: at the command line you would enter

```

sudo dpkg -i FILENAME.deb

```

to install the package from a .deb file. What are you trying to install from CD?

I'm not sure about Base being installed by default, but you can install it easily via the Synaptic Package Manager I mentioned above.

---

### Post by mcnaugg on 2009-07-08
I think I spoke too soon.  Last night everything was connected and I could send and receive mail and I could also connect via Firefox to the net.

This morning when I switched on it was back to sq one.  I tried lsusb again and it showed that the Iburst modem was being seen.  I tried sudo pon dsl-provider and got the following:
 gmc@linux:~$ sudo pon dsl-provider  
 Plugin rp-pppoe.so loaded.  
 RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5  
 gmc@linux:~$  
 
but there is no connection to Iburst.

The two progs (ibdriver and rp-pppoe) were loaded from my windows PC onto a mem stick.  This was plugged into the Ubuntu PC.  The stick was found and shown on the Desktop.  When I opened up the stick I then double clicked on the progs.  I was asked where I wanted to put the extracted progs and I choose the desktop. Each program was then shown on the Desktop without the gz ext.
I have gone through the process again but no luck.

As regarding loading software via cds etc it was a general question really.  I have a habit of storing various progs on CD/DVD etc so I don't have to download them again and using up my data allocation.  So it was a case of ensuring that there was no problem in loading my backups etc.

Gareth

---

### Post by carml on 2009-07-08
Are you sure you typed the correct command?

---

### Post by mcnaugg on 2009-07-08
Yes, as far as I can tell.  I tried the process twice with the same result.

Gareth

---

### Post by cody barth on 2009-07-08
i am having the same problem but i am using a verizon, actiontec gateway. when i go to the network manager there are no options besides vpn connections and under. I tried everything in the help next to firefox but it told me to reboot but no luck. worked fine with vista yesterday but now today with 9.04 its not...

---

### Post by roach33 on 2009-11-02
did you by any chance do any system updates before shutting down for the night? the updates threw my installation out the window as well, and I am yet to find out which update causes the conflict. 

hang in there with command line - eventually one gets the hang of a few basic commands, and the rest is doable through the package manager or add/remove programs.

---

### Post by mcnaugg on 2009-11-03
Hi there

I'm sorry to say that I have given up on Ubuntu.  I made several attempts to connect via my Iburst Modem and only succeeded the one time.  Next time I switched on it was all back to square one.  Unfortunately being an oldie my brain no longer works on the level needed for all this new technology so I have realised that I have reached my limitations.  I am still using open source programs where possible but with MS as the operating system.

Many thanks to all who tried to help.

Regards

Gareth

---

