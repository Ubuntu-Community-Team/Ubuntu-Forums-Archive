---
title: "32 bit apps under 64 bit OS"
date: 2008-11-27
forum: x86 64-bit Users
---

### Post by putz3000 on 2008-11-27
I decided to try the 64-bit release this time - so I installed it.  My first obstacle was 64 bit flash.  I did not find 32 bit easy to force in which has me thinking a bit.  Can any one tell me installing a 32 bit app from apt-get or the gui package manager will grab and install all the needed 32 bit library's for the desired application?  If not then I am thinking I should probably drop down to 32 bit to make my life easier.S

---

### Post by nikgare on 2008-11-27
Just install **flashplugin-nonfree** from synaptic!

---

### Post by wfp on 2008-11-27
You could try flash 10. For 64 bit Users

Thanks to Alejandro for this nice script.First you need to Download shell script from here
Using the following command from the terminal: just copy and paste this to your terminal: wget [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh)

Now you need to give execute permissions using the following command

sudo chmod +x flash10_en.sh

Run the script now

sudo sh ./flash10_en.sh


You can find it all here> [http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html)

---

### Post by jespdj on 2008-11-27
> **putz3000 said:**
> I decided to try the 64-bit release this time - so I installed it.  My first obstacle was 64 bit flash.  I did not find 32 bit easy to force in which has me thinking a bit.  Can any one tell me installing a 32 bit app from apt-get or the gui package manager will grab and install all the needed 32 bit library's for the desired application?  If not then I am thinking I should probably drop down to 32 bit to make my life easier.S
You're making it much more difficult than necessary. As nikgare says, if you install flashplugin-nonfree, then you automatically get nspluginwrapper and other necessary stuff installed to make 32-bit Flash work on 64-bit Firefox.

You don't need to do difficult things to install Flash on a 64-bit system.

**wfp**: Using that script is not necessary anymore, the version of Flash in the Ubuntu repository is already Flash 10.

---

### Post by Bucky Ball on 2008-11-27
There is a 64 bit .tar for Flash 10 available from Adobe at the bottom of this page:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by Izek on 2008-11-27
> **Bucky Ball said:**
> There is a 64 bit .tar for Flash 10 available from Adobe at the bottom of this page:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

But it's no use if Firefox itself is 32-bit I believe.

---

### Post by m_l17 on 2008-11-27
> **putz3000 said:**
> I decided to try the 64-bit release this time - so I installed it.  My first obstacle was 64 bit flash.  I did not find 32 bit easy to force in which has me thinking a bit.  Can any one tell me installing a 32 bit app from apt-get or the gui package manager will grab and install all the needed 32 bit library's for the desired application?  If not then I am thinking I should probably drop down to 32 bit to make my life easier.S

If you want to use the 32bit flash plugin follow the instructions on this thread: [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

If you want to use the native 64bit alpha read from the post from H4rold and vanadium101:

[http://ubuntuforums.org/showthread.php?t=772490&page=46]("http://ubuntuforums.org/showthread.php?t=772490&page=46")

I would use the native 64bit. I have being using since it came out with no issues so far.

Keep using 64bit no need to go back to 32bit.

---

### Post by steveneddy on 2008-11-27
> **Bucky Ball said:**
> There is a 64 bit .tar for Flash 10 available from Adobe at the bottom of this page:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

This is the way I went and it works very well.

There is already 64 bit Flash from Adobe from that site.

I can think of no other 32 bit app that you will need.

If so, then please tell us.

read this:

[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

read the entire first post to the thread.

This may answer most of your questions.

---

### Post by jespdj on 2008-11-28
> **Izek said:**
> But it's no use if Firefox itself is 32-bit I believe.
But the Firefox on 64-bit systems is a native 64-bit executable, it is not 32-bit. (see [this](http://ubuntuforums.org/showthread.php?t=994798)).

---

