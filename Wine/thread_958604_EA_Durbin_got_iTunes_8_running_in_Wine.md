---
title: "EA Durbin got iTunes 8 running in Wine"
date: 2008-10-25
forum: Wine
---

### Post by darkxman on 2008-10-25
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13739](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13739)

Can anybody explain how the hack works in English? :)

---

### Post by DoktorSeven on 2008-10-26
It's a patch to the sourcecode of Wine.  You would need to download wine's source, patch, then build and install it.  There's no way to apply this to a binary package of Wine you might already have.

---

### Post by darkxman on 2008-10-26
> **DoktorSeven said:**
> It's a patch to the sourcecode of Wine.  You would need to download wine's source, patch, then build and install it.  There's no way to apply this to a binary package of Wine you might already have.That's what I needed to know. Thanks!

---

### Post by robinlennox on 2008-10-31
Is there any chance anyone could compile this with the fix...?

Cheers

Robin

---

### Post by huanix on 2008-11-07
working on it. if i can make it work i'll distribute it as a download/build/install script.

---

### Post by ColinZeal on 2008-11-07
Yeah, please make this work so I can switch from Vista 64bit to Ubuntu.. :)

---

### Post by huanix on 2008-11-07
Here's the progress and a screenshot of the script for installing iTunes 8 in Ubuntu 8.10 through wine.. still working on iPhone support.

[http://www.huanix.com/2008/11/07/itunes-8-running-natively-in-ubuntu-810-with-wine/](http://www.huanix.com/2008/11/07/itunes-8-running-natively-in-ubuntu-810-with-wine/)

---

### Post by huanix on 2008-11-08
I finished the script to download/build/compile a version of Wine that will run iTunes 8.0.1 in Ubuntu 8.10 (Intrepid Ibex). 

I haven't been successful with recognizing devices yet (iPhone/iPod), but that may come in time.

I'd love to know if this works for you, or what i need to fix!

[http://www.huanix.com/2008/11/07/itunes-8-running-natively-in-ubuntu-810-with-wine/](http://www.huanix.com/2008/11/07/itunes-8-running-natively-in-ubuntu-810-with-wine/)

---

### Post by ntetreau on 2008-11-10
Thanks for you work, good luck on getting the iphone working, that would be a blessing!

---

### Post by huanix on 2008-11-22
I posted the newest version of the script, it will now detect and install the correct version of Virtualbox-2.0 (by adding the repository to your sources) and create a correct /etc/fstab listing for usb - that will assign the usb to the vbox group thanks to tauchris.

[www.huanix.com/2008/11/22/itunes-8-running-in-virtualbox-20-allows-usb-sync-with-iphone-and-ipod-touch/](http://www.huanix.com/2008/11/22/itunes-8-running-in-virtualbox-20-allows-usb-sync-with-iphone-and-ipod-touch/)

---

