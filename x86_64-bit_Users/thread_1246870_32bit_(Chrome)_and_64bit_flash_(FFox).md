---
title: "32bit (Chrome) and 64bit flash (FFox)"
date: 2009-08-22
forum: x86 64-bit Users
---

### Post by zelhar on 2009-08-22
Hi all,

I have installed 64bit flash using the script posted on this forum, which erased any previous flash version. 

Now I also want to use google Chrome. How can I install flash 32bit just for this browser ?

---

### Post by Gen2ly on 2009-08-22
[http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/)

look at amd64

---

### Post by zelhar on 2009-08-22
Thank you for the link. But I have some follow ups:
Can I install chromium 64bit from a repository ?
Do I need to manually install flash or does it come with it. I installed flash 64 using the script, which is essentially a manual install.

---

### Post by sebastianabate on 2009-08-22
> **zelhar said:**
> Thank you for the link. But I have some follow ups:
Can I install chromium 64bit from a repository ?

I use this repos whith Jaunty 64:

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free

> Do I need to manually install flash or does it come with it. I installed flash 64 using the script, which is essentially a manual install.You cant use the 64 bit version of flash, you must download the 32 bits version from Adobe and copy it to /opt/google/chrome/plugins. Then run chrome whith

google-chrome --enable-plugins

---

### Post by darco on 2009-08-22
Chromium is now native 64 bit build....it does utilize the x64 flash player....not sure about Chrome

darco

---

### Post by zelhar on 2009-08-22
Thank you all, I have it working now. 
For future reference here is the full detail of what needs to be done:
The launchpad repository installs the 64bit version.
> deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) intrepid main 
with key:
> sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5
Then I downloaded flash 64 bit for linux from 
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

and unpacked it (a single file, not install needed) to 
> /usr/lib/chromium-browser/plugins.

then all that is left is to run chrome with plugins enabled by:
> chromium-browser --enable-plugins

For google chrome the process is very similar. But since I have the 32bit version, downlowad the 32bit flash player (the tgz format), and unpack to  
> /opt/google/chrome/plugins/ (../plugins dir must be created)
then run with chromium-browser --enable-plugins.
But I'm no

---

### Post by darco on 2009-08-22
Its fast ain't it?
:guitar:

darco

---

### Post by zelhar on 2009-08-22
yes it is.

---

### Post by Blakefreak on 2009-09-03
Two things
One:

When I attempt to copy/cut/extract the file to /usr/lib/chromium-browser/plugins I am told that permission is denied.

Two:

Where do I enable plugins?

---

### Post by Blakefreak on 2009-09-03
Two things
One:

When I attempt to copy/cut/extract the file to /usr/lib/chromium-browser/plugins I am told that permission is denied.

Two:

Where do I enable plugins?

---

### Post by darco on 2009-09-04
> **Blakefreak said:**
> Two things
One:

When I attempt to copy/cut/extract the file to /usr/lib/chromium-browser/plugins I am told that permission is denied.

Two:

Where do I enable plugins?

With the latest version of chromium, you no longer need to use the enable flag option. Also it picks up Java and Flash that are currently installed in your FF directories..

darco

---

### Post by Blakefreak on 2009-09-04
Let's say that didn't happen...

---

