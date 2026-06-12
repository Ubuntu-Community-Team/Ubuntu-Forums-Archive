---
title: "HP Pavilion dv2610us Problems"
date: 2008-08-08
forum: x86 64-bit Users
---

### Post by iamdigitalman on 2008-08-08
Hi guys, my girlfriend wanted to try Ubuntu again (last time we had it on her old dell). Now she has a recent dv2610us, one of those HP entertainment laptops, with the quickplay touch buttons, remote, camera, DVD burner with lightscribe, and widescreen.

I downloaded the 64 bit version because the machine has a AMD Turion 64x2 (dual core). It installed and ran flawlessly, except for a few hardware drivers. I was even able to resize the 160gb HD and keep her Windows XP install. This machine has some odd hardware because when I put XP on it for her, (originally it had vista, and was a resource hog.), I had to hunt around and it took me 9 hours to find and install the proper sound drivers and get that working.

First off, the video was defaulted to 800x600, until the restricted drivers came up and I got the right ones for the graphics chipset, and now that works flawlessly. Oddly, the sound worked "out of the box".

The biggest issue I am having is with the wireless card. It is a broadcom, and there were restricted drivers for it, so I installed them, but the wireless is not work, but the ethernet and bluetooth are. It shows up that it is there, I can detect my wireless network, and connect. I get the signal bars, but when I launch firefox, it does not load any page. Oddly, when I click the latest headlines RSS feed, those come up just fine. Currently, I have the machine tethered to my Powerbook and have the internet sharing in OS X turned on. 

As I typed the above paragraph, we tried the wireless again. For some reason it worked for about 5 minutes then it stopped. It seems to not like anything less than a full signal. Any ideas here?

The other problem we are having is with the integrated webcam. It does not show up anywhere. It is a USB based device, and it works just fine with the built in drivers. Any ideas here?

Oh, this is odd too. When the wireless was not working, I went and got NDISwrapper, and the drivers from HP's site for Vista 64 bit. I ran the EXE through wine and extracted the inf. When I installed (using the GUI frontend), it came up with an improper device error.

Also, iTunes 7.7 does not work at all in Wine. It installed fine, and there is a itunes icon on the desktop (as well as a 'iTunes.ink' with a paper icon), but when I double click to launch, it does nothing. Apple Software Update, Quicktime, and other windows apps (even the ones in the XP partition when I mount it ) run just fine. Is there a way to fix this, or is there some software for Linux that allows an iPod to sync? She has a 3rd Generation nano (the black 8gb one), so I need something that will work with that.

Thanks, and I know there is a lot here, sorry if you think it's too long. If I posted this in the wrong section, feel free to move it. Since it's a 64bit computer, I felt this topic best belongs in here. I hope to get this working entirely so we can blow away XP permanently and use Ubuntu full time. I want to use one of my "powered by ubuntu" stickers already!!

Lastly, here are the specs for this beast:

-AMD Turion 64-x2 each core runs at 1.9ghz
-512mb RAM (originally had 1gb, but one of the slots and stick in it failed).
-160gb SATA HD, approx. 120gb for Windows XP, 40gb for Ubuntu 
-Broadcom 802.11b/g wireless
-integrated bluetooth
-integrated webcam
-DVD burner with lightscribe

-digital ;)

---

### Post by Melk79 on 2008-08-09
I did [this]("http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04") on my dad's dv2700 and it worked well.  You need a network connection to perform, but it sounds like you have that.  He had a Broadcom chip as well.

For the webcam, try installing Cheese from Synaptic and see if that picks it up.  You could also try setting up Ekiga, which is installed by default, to see if it picks it up.

Can't offer anything on iTunes/Wine.

---

### Post by iamdigitalman on 2008-08-09
Ah thank you, wireless is working now. It was working with network manager right before I uninstalled it, but that was because I am sitting right next to the modem and had a full signal. I will do a range test and see if it works.

Also, I installed Cheese, the webcam works flawlessly, but the thing we wanted to get working was online websites that can access it, like Youtube (direct upload), and facebook ( profile picture upload). When we go to access those pages, the flash plugin tells us there is no camera available. When we go to have it re scan, it shows "HP Webcam" in the list, but when I click close, it does nothing but tells me it's not found. This may be an issue with the flash plugin, but I installed the Adobe one directly off their site.

Oh, as for the iPod, I did get it working in Rhythmbox. It brought in all the music off it, but the stuff bought off the ITS is unplayable, unless on the iPod. Now I just need to figure out how to uninstall iTunes, it says it is but then it does not go away. We will format the hard drive for good very soon and blow that away though.

-digital ;)

---

### Post by opr8ive on 2008-08-09
Might give gtkpod a try.. Seems to (usually) play a little nicer with ipods than rhythmbox..

-Jason

---

### Post by MatMan on 2008-12-29
Hi Melk, I am about to do a dual install of vista/ubuntu on my dv2700. do you have any more hints and tips or a guy who is kind of a bit inexperienced with linux?



> **Melk79 said:**
> I did [this]("http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04") on my dad's dv2700 and it worked well.  You need a network connection to perform, but it sounds like you have that.  He had a Broadcom chip as well.

For the webcam, try installing Cheese from Synaptic and see if that picks it up.  You could also try setting up Ekiga, which is installed by default, to see if it picks it up.

Can't offer anything on iTunes/Wine.

---

