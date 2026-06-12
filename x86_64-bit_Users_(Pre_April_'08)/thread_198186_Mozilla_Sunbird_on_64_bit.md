---
title: "Mozilla Sunbird on 64 bit"
date: 2006-06-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Neuros on 2006-06-16
I've heard that the calendar sub-software for Seamonkey does not work well in 64x Ubuntu Dapper Drake.
Anyone know about the compatibility of Mozilla Sunbird? - I'm asking because I know that much (actually almost all) of the code for Sunbird is directly from Seamonkey/Mozilla Suite.

Thanks for your help.

---

### Post by salmanal on 2008-02-08
I tried to install Sunbird yesterday using the instructions here:

[http://ubuntuforums.org/showthread.php?t=278206](http://ubuntuforums.org/showthread.php?t=278206)

I get the icon in my APPS folder, but I click on it and nothing
executes. I'm wondering if the version I downloaded was 32-bit only.

I'll try again shortly........

---

### Post by Antonlacon on 2008-02-08
Yes the sunbird from the link is 32bit.

If you're already using thunderbird, you can use the 64bit add-on.

[Mozilla Lightning](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.7/contrib/linux-x86-64/)

---

### Post by Kilz on 2008-02-08
Why not just use ```
sudo apt-get install sunbird
```. [Sunbird is in the repositories ]("http://packages.ubuntu.com/gutsy/web/sunbird")with a 64bit version for Gutsy

---

### Post by timzak on 2008-02-12
> **Kilz said:**
> Why not just use ```
sudo apt-get install sunbird
```. [Sunbird is in the repositories ]("http://packages.ubuntu.com/gutsy/web/sunbird")with a 64bit version for Gutsy

The 64bit version of Sunbird in Synaptic is version 0.5.  The latest version is 0.7.  There are significant differences between the versions, especially in the integrated Lightning.  If you could show me how to use version 0.7 of Lightning in Gutsy 64, I would really appreciate it.

Edit:  nevermind, just noticed the link that Antonlacon posted, download, and installed from within Thunderbird (it works!).  What are potential problems for doing this rather than from Synaptic?

---

### Post by Kilz on 2008-02-12
> **timzak said:**
> Edit:  nevermind, just noticed the link that Antonlacon posted, download, and installed from within Thunderbird (it works!).  What are potential problems for doing this rather than from Synaptic?

It wont automatically upgrade with the rest of the operating system. But Mozilla might update it.

---

### Post by timzak on 2008-02-12
Thanks, Kilz.  This is worth the minor inconvenience of having to possibly manually update.  I prefer Lightning (Sunbird integrated into Thunderbird), but had been forced to use the standalone Sunbird because of missing features in the 0.5 version.

---

### Post by jonnywombat on 2008-02-14
I use sunbird by downloading the x86 version from mozilla [ -link. ]("http://www.mozilla.org/projects/calendar/sunbird/download.html") 

I then simply unzipping the folder and creating a launcher for the executable and have never had an issue on my either of my amd 64 gutsy systems

---

