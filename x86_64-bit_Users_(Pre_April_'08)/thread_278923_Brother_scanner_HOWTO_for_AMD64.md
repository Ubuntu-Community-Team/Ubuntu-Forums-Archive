---
title: "Brother scanner HOWTO for AMD64"
date: 2006-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by god of thunder on 2006-10-17
Hello all - 

I realize there are only a billion posts on how to get Brother printer/fax/scanner drivers working on Ubuntu, but doing so on an AMD64 system was harder than just following the instructions on the posts.  I would like to document/plagiarize the way I got my scanner (MFC-640CW) to work in the hopes that it will work for others.  I don't claim that this way is elegant, because it is not.  But it worked.

**CLEAN-UP FAILED PREVIOUS ATTEMPTS**
Remove *sane* and *xsane* if they are already installed.  Remove any other versions of the brscan/brscan2 driver.
```
sudo dpkg --purge sane xsane brscan brscan2
```

**DOWNLOAD BROTHER DRIVERS**
Determine if your printer is covered by brscan driver or the brscan2 driver by loooking for it in the list [here]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html").  I have only tried this with the brscan2 driver.  Download **both** the 32-bit version for Debian **and** the 64-bit version for pretty much everything else.

**TURN THE PRINTER OFF**
Yeah, it's weird.  Just do it.

**FORCE INSTALL 32-BIT VERSION**
Not positive here, but I think there are scripts that get run when the binaries are extracted (*alien* seemed to think there were scripts involved).  Installing this package will run these scripts and generate the symlinks.
```
sudo dpkg -i --force-architecture brscan2-0.2.1-0.i386.deb
```

**INSTALL 64-BIT VERSION**
By default, *file-roller* opens .rpm files and lets you browse the contents.  If your default save directory in Firefox is the Desktop, just clicking on the .x86_64.rpm should open file-roller.  This is a gnome application, so my apologies if KDE doesn't have an equivalent.  Extract everything - it will all be contained within the directory usr/.  Copy over the binary libraries and config files.
```
cd usr/lib64
sudo cp libbrcolm2.so.1.0.1 libbrscandec2.so.1.0.0 /usr/lib/
sudo cp sane/libsane-brother2.so.1.0.7 /usr/lib/sane/
cd ../local/Brother
sudo cp -r sane /usr/local/Brother/
```

**INSTALL SANE**
Just use *apt-get* to download and install sane and xsane.
```
sudo apt-get install sane xsane libsane sane-utils
```

**TURN ON THE PRINTER**
That should be it as far as sane is concerned.  Try running *xsane* as a regular user.  If you get an error like "... Failed to open device ...", the install didn't work.  If instead you get an error like "Error during I/O", your install is great.  Run *sane-find-scanner*, and look for the line like:
```
found USB scanner (vendor=0x04f9, product=0x0197) at libusb:002:002
```
Write down the product number.

**CONFIGURE UDEV**
To configure udev to allow access to the scanner without being root, edit the file /etc/udev/rules.d/45-libsane.rules with your favorite text editor.  I'm actually a *vi* guy, but to make it easier I'll say gedit:
```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```
Make your file look like mine.  Instead of 0197 for the idProduct, use the number (without the 0x) that you wrote down above.  Change the MFC-640CW text to whatever describes your printer.
```
...
SUBSYSTEM!="usb_device", ACTION!="add", GOTO="libsane_rules_end"

[B]# Brother|MFC-640CW
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0197", MODE="664", GROUP="scanner"[/B]
# Hewlett-Packard|ScanJet 4100C
SYSFS{idVendor}=="03f0", SYSFS{idProduct}== etc, etc, etc
```

That should be everything.  Restart the computer and you should be good to go.  It may be possible to avoid restarting by killing udevd with a SIGHUP, but I haven't tried that.

Good luck!

---

### Post by ipa on 2007-01-11
Thanks for this howto Mr God Of Thunder,
I now have a networked scanner MFC-425CN as a regular user on Edgy AMD64!!!

I followed your instructions until:
 ¨That should be it as far as sane is concerned. Try running xsane as a regular user. If you get an error like "... Failed to open device ...", the install didn't work. If instead you get an error like "Error during I/O", your install is great. Run sane-find-scanner, and look for the line like:...¨

and I got the familiar no devices found> So I then followed the advice on the brother web site:

[http://solutions.brother.com/linux/sol/printer/linux/sane_install-net.html](http://solutions.brother.com/linux/sol/printer/linux/sane_install-net.html)

and entered this command in a shell:
sudo brsaneconfig2 -a name=BRSCANNER model=MFC-425CN ip=10.0.0.15
(of course the name model and ip are user specific)
then I tried to open xsane, and got a shock when it did and took over my desktop.

So I never had to enter any UDEV rules... what could be easier!

Once again many thanks!!!
Ivan

---

### Post by Snookered on 2007-02-22
Thanks god of thunder!
Great guide! Now my MFC 420CN is working!
2 things I had to do-
   1.Use Synaptic to install Xarchiver because what came with Edgy won't do .rpm archives.
   And it didn't extract like your tutorial, but it was easy to figure out. Made a folder on the desktop
   and extracted to there!

   2. Not sure if this really matters, but when editing 45-libsane.rules , noticed my lines were-
   
   ACTION!="add", GOTO="libsane_rules_end"  
   SUBSYSTEM!="usb_device", GOTO="libsane_rules_end"
   
   so changed them to match yours- SUBSYSTEM!="usb_device", ACTION!="add", GOTO="libsane_rules_end"

You have also taught me some new commands on top of it all!

---

### Post by btdown on 2007-02-22
Thanks for the help guys...I was able to get my Brother 
MFC-7820N networked printer to work after reading this thread.

---

### Post by kevbro on 2007-02-23
You are a genius - got my Brother DCP-110c scanning away beautifully.  Had a couple of hiccups but after configuring udev all was revealed.  Iam gradually knocking away barriers to Ubuntu for me (6.06) - ONE MORE NAIL IN Mr BG's W----ws coffin.  Thanks a bunch.

---

### Post by roberts3000 on 2007-03-07
i got the scanner working on my mfc-420cn now. anyone get the printer part working in 64-bit.

---

### Post by russell.h on 2007-03-08
Edit: oops, this is about scanners. Nevermind then.

---

### Post by lierodeath on 2007-03-25
Do you have any advice for making the printer section go?

I've followed the usual tuts, and everything works fine - right up until the point where I tell something to print (and nothing happens).

---

### Post by russell.h on 2007-03-26
Ummmm, my network printer I had to go in and change the address. Open the printer manager, right click the printer, go to properties, and on one of the pages is a box that wants the address. But for some reason it had some sort of USB address in there (I don't even know if that works, but thats what it had). Change that to the IP of the printer, and pray that the printer's IP doesn't change.

Hope that helps,

Russell

---

### Post by Richhard on 2007-05-07
Hi god of thunder,

thank you very much: my Scanner (Brother DCP-130c) is now perfect working!!

---

### Post by dsmturbo on 2007-06-05
I gotta try this, I just got the printer part working by following cwmoser how to. I have a 420CN running SimplyMepis 64 bit

---

### Post by dsmturbo on 2007-06-05
Dam, I love you guys  hehe. I just ran Koola and it says 425CN scnner found. Must be a very similar model.
You guys should post these How to's over at Mepis for those people as well.

From a very new Linux user, well I am very old but new to this OS

---

### Post by Dogmeat Jack on 2007-07-13
Good howto, might be a bit out of date. 
I was able to skip the first two steps by downloading the 64bit deb package from [here]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html") and installing it:
```
sudo dpkg -i brscan2-0.2.3-0.amd64.deb
```

---

### Post by Dogmeat Jack on 2007-07-13
To save a restart at the end of the process:
```
sudo /etc/init.d/udev restart
```

---

### Post by nigpow on 2007-07-14
Help me make mfc420 work on Ubuntu. I used dpkg force and it set up okay but nothing will come out of printer when I try to print. The printer says the document is printed but nothing comes out.

---

### Post by CadetD on 2007-08-09
Well, I had gotten so discouraged with Brother support for Linux that I never thought I'd be able to use the scanner from my MFC5440CN. 

Didn't even need all of these steps. 

Downloaded the 64 bit .deb from Brother's site and ran dpkg. 

That was it! No editing anything. XSANE and scanned a pic. 

Except that I had to SUDO xsane. (Is that because I was lazy and didn't follow the directions?)

Thanks for putting me on the right road.

---

### Post by aeruginosa on 2007-09-08
Thank you so much for your help! I spent two weeks trying to install my Brother DCP-110c without any succes untill I found this page. Now I have finally a fully usable Ubunto on my computer and can say goodbye to Windows XP...

---

### Post by Fawlty Towers on 2008-01-02
Thanks God of Thunder for the help in setting up my Brother DCP-130c scanner on my 32 bit system.  Before finding your post I had tried several things that didn't work.  I'd like to know how you figured out all the steps in the process.  Was it trial and error and you got lucky or is there a logical system of steps that you followed to work thru the problem?  I'd like to know because I can't get my Nvidia video to display in 3D.

Thanks....

---

### Post by yetanothersteve on 2008-02-02
Before you start running dpkg with a force on the architecture, check if the brother site has the 64 bit package for your scanner.

For example, I have an MFC-7820N and there is a Brother 64 bit deb that I installed using 
Brother's instructions and I am now scanning.

[http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html")

After downloading, I then read the How To Install, installed, and configured using Brother's how to. I then started Xsane, scanned a document with result type success.

I only found this article when researching why my printing of PDFs is printing an error message.

---

