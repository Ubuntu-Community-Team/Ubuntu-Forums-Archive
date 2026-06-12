---
title: "Epson Scanner V500 and others - new 64 bit drivers available"
date: 2009-03-05
forum: x86 64-bit Users
---

### Post by ArtInvent on 2009-03-05
Good news people. It's only been a year since I last tried this, but Epson seems to have finally released both 64 bit and Deb packages for their newer scanners. Yay. Up to this point it was almost impossible to use my scanner on a 64 bit system. The following worked for me on Intrepid 64. **[UPDATE: All this seems to work about the same in Lucid, Karmic, Jaunty as well. see note.]** I got this scanner to scan color slides and film at higher resolutions so that is mainly how I tested it.  The Epson V500 is a flatbed but it's also an excellent film scanner, it turns on fast, the backlight is LED and comes on instantly, scans are near to dedicated-slide-scanner quality, and using it with 64 bit Linux is now possible. Native Linux scan apps are dicey though, but other options work well with a little effort.

[SIZE=3]Install [/SIZE]

You have to remove the package libsane-extras which has conflicting old Epson drivers. 

Then you can download the drivers from Epson at Avasys Corp.
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do)

If that link doesn't work, just go to the [http://www.avasys.jp/]("http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do") site and click on English and hunt around. Install the iscan deb package first, then the iscan-plugin. I just used the "open with Gdebi" option at download rather than the command line method. Smooth as butta.

[B][NOTE FOR JAUNTY: You have to download NOT the first iscan deb package listed, but the one called 
> DEB 64bit core package [libltdl7] (for Ubuntu 8.10 or later)  	
iscan_2.20.0-6.ltdl7_amd64.deb

If you try to install the first one, you will get a dependency error as in one of my later posts.

Then install the 'iscan-plugin-gt-x770_2.1.1-2_amd64.deb' package. 

The rest of this post seems to be still valid.][/B]

[SIZE=3]Run Linux Image Scan! [/SIZE]

Plug in your scanner, power up. In your Graphics menu there should now be an item called 'Image Scan!' Run this, it should detect a scanner that's called GT-X770. Select that, you should be good to go. Unfortunately Image Scan! is kind of bare-bones. It's fine for a quick and dirty document scan, you can do reflective or transparency, positive or negative in resolutions up to 9600dpi, but there is no DigitalIce or anything for dust removal, and no 48-bit color option. It's a poor second cousin to Epson's Windows scan software.

[SIZE=3]XSane[/SIZE]

XSane seems to work with the V500 alright. There is no ICE or dust removal option for film. The main problem is that the resolution in the X axis is limited to 1600, when the scanner will go up to 6400x6400. Also, I like to scan slides at 3200, but the Y direction is fixed at up to 2400 or 4800 or 6400, but not 3200. What is up XSane? I tried a scan at 1600 x 4800 and sure enough the resolution is is stretched out wacko. You will not be able to scan slides well with XSane, though I've always liked to use it for quick print and sketch scans, and it does multi-page document scans into pdf quite nicely.

[SIZE=3]XP - Epson Scan[/SIZE]

To get the full boat options, I had been using VirtualBox running Windows XP in 32 bit Ubuntu host. I've tried other scan software like SilverFast, and the paid-for VueScan is available for Linux native, but the stock Epson Scan software that comes in the box seems to work best to me. A big advantage is that you can set up 4 slides or six negs, crop and adjust the color for each one, and batch scan them all in one click without having to hang around. (This is actually better than having an expensive dedicated slide scanner with an auto-feeder, which can't do a preview/adjustment of each slide.) Plus you have ICE, Epson's own faster dust removal which I actually prefer, 48 bit color, good resolution choices. And the results seem to look better than any other method I've tried, which is probably the most important thing. I've done about 700 hi-res 35mm & medium format slide and negative scans with this scanner and software in VirtualBox and I'm not really sure that you could do that much better with a dedicated film scanner. (Probably a little more shadow detail.)

Using the scanner in VirtualBox only works if the Linux drivers for the scanner are up and running. If Image Scan! or XSane detect the scanner, you should be fine. (It previously did not work for 64 bit Ubuntu host with a 32 bit Windows XP guest since the Linux scanner drivers were absent.) So I tried again with the new 64 bit drivers. When XP starts you need to make sure in the VM controls that you check the USB devices and enable the Epson scanner. Epson Scan should now detect the scanner and start right up. I was able to scan with full options.

[SIZE=3]Vuescan[/SIZE]

Vuescan is a proprietary scanner app for multiple platforms. The Linux version is 32 bit but currently the website says: 'Built with Ubuntu 8.10 - 32-bit compatibility libraries needed for 64-bit Linux'. This kind of thing can be easy or not so easy. I did not try to install this as I've tried it in the past and it wasn't my cup o' tea, and it costs money, but some people seem to like it a lot. I believe (correct me if I'm wrong) I was unable to set up multiple scans in one shot, as is possible with Epson Scan.

---

### Post by BetterSense on 2009-03-06
Wow good news. I run Intrepid 64bit, and just bought a V500 photo thinking I'd just use it in my 32bit XP virtualbox. I didn't know it was going to be more complicated than that, and this post has been very helpful. It gives me great hope that you are using the scanner on 64bit Intrepid, so that means I should be able to as well. When I attempt to follow your instructions, I run into a snag at installing the iscan .deb package. Gdebi says that a dependency libltdl3 is not satisfiable, and I cannot apt-get it either. Thus I don't know what to do or whether to take the scanner back or what.

---

### Post by BetterSense on 2009-03-07
[http://packages.ubuntu.com/hardy/libltdl3](http://packages.ubuntu.com/hardy/libltdl3)

If anyone else has the dependency problem, you can get the package there. It worked fine and I was able to install the packages and use Image Scan.

I'm having trouble, however, with installing Epson Scan in my Virtual XP, perhaps because I'm such a stranger to Windows-land. The CD does not autostart. When I enable the scanner in virtualbox, the new hardware wizard starts, but fails because it "could not find the necessary software" even though the CD is inserted and I told it to look in removable media. In Windows Explorer, the CD is detected as EPSON and there is an Epsetup icon on the root of the CD, but clicking on it pops up a warning that "windows cannot access the device because I might not have permissions to access it". Help with this issue would be appreciated.

---

### Post by BetterSense on 2009-03-07
The balky windows issue was bypassed by some combination of restarting the virtual machine, power cycling the scanner, and dis- and re-connecting the virtual USB connection as well as the host DVD drive.

---

### Post by margolism on 2009-04-02
I posted this in another forum, but I thought it was appropriate to repost here, since this addresses some of the issues being discussed.

Here's a simple solution I just came up with, and I am far from being a Ubuntu or linux expert. Note that I have an Epson V500 scanner, but I imagine this works for all Epson scanners with drivers on the Avasys website. I am running Ubuntu 8.10 64-bit version. 

My issue was that I wanted to be able to run VueScan, iscan, and gscan2pdf. The other solutions I have seen let me either run VueScan (which requires 32 bit scanner libraries) OR software that requires the 64 bit scanner libraries, but not both. This simple solution lets me use my scanner with all scanning apps, regardless of which libraries it needs.

First, I installed the AMD64 bit versions of iscan and iscan-plugin, which I got from the Avasys website. No force architecture stuff needed, since these are built for the 64bit platform.

I also downloaded (but did not install) the 32 bit version of the iscan-plugin from the Avaya website. (iscan-plugin-whatever-i386.deb)

Don't install the 32 bit version DEB using the package manager. Instead, open this as an archive , go to data.tar.gz, and go to the /usr/lib/iscan folder.

Extract the file libesint7C.so.2.0.1 (might have a different name if using a different scanner, I don't know.) This is the 32bit file that VueScan needs to run. You don't need anything else from this package.

I renamed this file driver32 and copied it to the /usr/lib/iscan directory.

I then went to the /usr/lib/iscan directory and made a copy of the 64 bit version of libesint7C.so.2.0.1 already there, from when I installed the 64 bit iscan-plugin DEB package. I called this file driver64

So now I have driver32 (the 32 bit scanner libraries VueScan requires), and driver64 (the 64 bit version all the other scanner apps I use require.)

Basically, I wrote a super simple bash script that copies driver32 to libesint7C.so.2.0.1 when you run VueScan, and restores the 64bit version once you quit VueScan. Here it is:

rm /usr/lib/iscan/libesint7C.so.2.0.1
cp /usr/lib/iscan/driver32 /usr/lib/iscan/libesint7C.so.2.0.1
/usr/VueScan/vuescan
rm /usr/lib/iscan/libesint7C.so.2.0.1
cp /usr/lib/iscan/driver64 /usr/lib/iscan/libesint7C.so.2.0.1

I called this script vuescan.sh, and I simply run this script to run VueScan.

If there are any other scanning apps that can only work with the 32 bit libraries, I would assume this approach would work for them too.

Note that I had to change the permissions of the /usr/lib/iscan directory, but other than that, it's working great!

Hope this is helpful to someone!

Cheers,



Mark

---

### Post by ArtInvent on 2009-04-29
For 9.04 Jaunty, the drivers don't work. The iscan deb package complains that 'libltdl3' is not installed. I checked in Synaptics, and libtdl7 is installed and there is no package libltdl3 available.

Looks like Epson needs to update their packages. 

If they would just open source this stuff they would realize that someone would just put the drivers in the kernel and be done with it, and they would never have to deal with it again. Oh well.

---

### Post by ArtInvent on 2009-07-01
After just waiting awhile for Epson, I've got the scanner working again under Jaunty 64. 

I've updated the top post with new instructions for Jaunty.

---

