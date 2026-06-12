---
title: "Adobe Flash 10 For Linux 64 Bit"
date: 2009-10-13
forum: x86 64-bit Users
---

### Post by lastoneleft07 on 2009-10-13
This is less a tutorial and more of a tip and usefull information, I couldn't find this info any where here and finding out how to get Adobe Flash 10 working on your 64 bit Linux system. 

Adobe has kept this a secret pretty much but there is a download here on the Adobe Labs page for the plugin

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Scroll to the bottom of that page to see the Download

Step 1: Download the file 
Step 2: Extract the file with whatever extractor you have or with Ubuntu's Archive manager by right clicking on the folder and select open with Archive Manager, then choose extract and choose your destination.
Step 3: Find your folder for plugins on the Browser you use :

Opera 10: /usr/lib/opera/plugins

Copy and paste the file into the folder, make sure you have ownership of that folder.

Restart your browser and check the plugins loaded

---

### Post by darco on 2009-10-14
> **lastoneleft07 said:**
> I couldn't find this info any where here and finding out how to get Adobe Flash 10 working on your 64 bit Linux system.

You didnt look very hard...at the top of this forum is a how-to which includes a simple script that handles everything...


darco

---

### Post by nzadLithium on 2009-10-14
plus u can just run 
sudo apt-get install flashplugin-nonfree
At least i could anyways :D

---

### Post by falconindy on 2009-10-14
> **nzadLithium said:**
> plus u can just run 
sudo apt-get install flashplugin-nonfree
At least i could anyways :D
That installs a 32-bit plugin, not 64.

---

