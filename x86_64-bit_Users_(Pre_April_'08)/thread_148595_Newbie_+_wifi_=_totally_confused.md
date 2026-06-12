---
title: "Newbie + wifi = totally confused"
date: 2006-03-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by The_Tankengine on 2006-03-22
I've read through a few threads about setting up an internal wireless card, but all have started after compiling ndiswrapper.

I am a total n00b here, and I am wondering if someone could start from scratch with me on how to get it working.  I have a Compaq Presario R3000 Athlon 64 3000+ with 54g integrated Broadcom 802.11b/g WLAN & Bluetooth.  I've checked my hardware properties, and the only networking related thing listed is the LAN card, at eth0.  I've read that it should list 'wlan0' to recognize wifi, but I dont know how to get that up.

Thanks for any help! :mrgreen:

---

### Post by NetMatrix on 2006-03-22
My wireless card is listed as eth1 and not wlan1.  You should be able to set everything up from the networking GUI tool.  If you are using WEP encryption you have to enter it in ascii or hex.  Passphrases don't work.  You will also need to enter the SSID of the network you want to access.  Use the GUI tool and everyting is pretty self explanitory.

System / Administration / Networking

Good Luck

---

### Post by The_Tankengine on 2006-03-22
So I dont have to use the ndiswrapper thing at all?

Also, my wireless card is not listed at all, only eth0 is.

---

### Post by raphy3 on 2006-06-14
[QUOTE=The_Tankengine]So I dont have to use the ndiswrapper thing at all?

Also, my wireless card is not listed at all, only eth0 is.[/QUOTE]

Hi,
I don't know if you ever solved your problems or not, or if you monitor this thread still, but I have the same laptop as you, an r3000z, and I have the wireless working pretty well.
What you need to do is apt-get install ndiswrapper and then grab the windows drivers for your wireless card.  I'm assuming it's a broadcom card like mine.  You can go straight to HP's website, go to their support section, and download the latest windows drivers for the broadcom card that way.  Extract the files, either in windows or in linux (in linux you can use cabextract, not sure if that's the exact name of the utility), after that you go to the directory you extracted them to and type
sudo ndiswrapper -i *.inf (or whatever the inf file you have in there is, probably bcwmX.inf or something).
That's a one time thing.  After that you modprobe ndiswrapper and your wireless card should now show up as wlan0 in the wireless networking control applet in gnome.  If you need to use wpa encryption, you need to go a step further and use wpa_supplicant.  Let me know if you need that.  If you just use WEP, the gnome controls will suffice.

I would be very very interested in knowing how you got xgl+compiz running (seen in your sig) on your r3000... I'm having a hard time of it myself.  Do you have a post anywhere where you maybe mention some of the trials and tribulations of that?  Thanks a bundle.
raphy

---

### Post by John Jason Jordan on 2006-06-14
[QUOTE=The_Tankengine]So I dont have to use the ndiswrapper thing at all?
Also, my wireless card is not listed at all, only eth0 is.[/QUOTE]
I have a Compaq R3240 and know exactly what you are going through. Been there, got the t-shirt, etc. But I've got mine working and I'm sure you can get yours working too. It's just a question of installing some extra stuff and fiddling with it.

First, your Broadcom wifi will not be listed until Linux sees it, which hasn't happened yet. And it hasn't happened because it can't find a driver for it. The first thing I would suggest is that you reboot your laptop and watch the screen carefully while it is booting (the text displays that scroll by before the GUI screen comes up at the very end). You may see an error message in there that will say something about your Broadcom wifi -- like "wifi not installed, unable to find driver" or something along those lines. If you don't see any error messages, don't worry. 

What you need to do is install a utility called ndiswrapper. Ndiswrapper is a Linux fake utility that tells Linux that the Windows wireless driver for your Broadcom chip is really a Linux driver, and also "translates" the Windows driver data to what Linux is expecting, and vice-versa.

It took me a couple weeks to get it working the first time, but I was a n00bie then. And when I upgraded from Ubuntu Hoary to Breezy last November the upgrade broke ndiswrapper and I had to go through it all over again. Unfortunately, it had been so long since the first time that I had forgotten how I finally got it working. So after it took me a week to get it working again I resolved that I would never go through that again. I took all the e-mails from Linux friends who helped me get it back running again and amalgamated them into a document that I posted on:

[http://prinsig.se/weekee/index.php/Ndiswrapper64]("http://http://prinsig.se/weekee/index.php/Ndiswrapper64")

If you go there look for my post, which is about the bottom half of the page. 

While you are there, sign up for the R3000 Linux e-list. There are lots of us out there and it's cool to have people to turn to when something blows up and you can't figure out how to fix it.

If you still can't get it working, holler back and I'll try to help. I check the AMD-64 forum here several times a day.

---

