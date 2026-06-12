---
title: "How do I install Adobe Reader 9 and Adobe Air on Ubuntu 9.04?"
date: 2009-07-09
forum: x86 64-bit Users
---

### Post by Klaw117 on 2009-07-09
Ok, I've looked all over Google and I can't figure out how you install Adobe Reader 9 on Ubuntu 9.04 x86_64. Can someone help me with that?

Also, I tried to follow the guide to install Adobe Air here: [http://ubuntuforums.org/showthread.php?t=1051402](http://ubuntuforums.org/showthread.php?t=1051402) but when I reach step 3, I'm not sure how to do the part that says "*(note may need to chmod +x AdobeAIRInstaller.bin, and will need sudo access)*." Again, please help. I'm a complete newbie to Ubuntu.

By the way, can you install Adobe Shockwave on Ubuntu? I'm guessing not since adobe.com didn't offer a download for Linux.

---

### Post by wojox on 2009-07-09
Go to the adobe website and choose diffrent operating system and look for .deb files.

Shockwave choose your browser.

---

### Post by jocko on 2009-07-09
> **Klaw117 said:**
> Ok, I've looked all over Google and I can't figure out how you install Adobe Reader 9 on Ubuntu 9.04 x86_64. Can someone help me with that?

Also, I tried to follow the guide to install Adobe Air here: [http://ubuntuforums.org/showthread.php?t=1051402](http://ubuntuforums.org/showthread.php?t=1051402) but when I reach step 3, I'm not sure how to do the part that says "*(note may need to chmod +x AdobeAIRInstaller.bin, and will need sudo access)*." Again, please help. I'm a complete newbie to Ubuntu.

By the way, can you install Adobe Shockwave on Ubuntu? I'm guessing not since adobe.com didn't offer a download for Linux.
For acrobat reader, enable the medibuntu repos. [Instructions here]("https://help.ubuntu.com/community/Medibuntu"). After that you'll find the package "acroread" in synaptic. Install it.
The command you need for the air installer is (if the file is on your desktop):
```
cd ~/Desktop
chmod +x AdobeAIRInstaller.bin
```It does NOT require sudo access, so just run the command. Then to run the actual installer:
```
sudo ./AdobeAIRInstaller.bin
```
Shockwave does not appear to have any linux version.

---

### Post by Yellow Pasque on 2009-07-09
The jaunty repo of medibuntu doesn't have acroread in it right now. Use the karmic package (the dependencies will work fine for jaunty): [http://packages.medibuntu.org/karmic/acroread.html](http://packages.medibuntu.org/karmic/acroread.html)

---

### Post by Klaw117 on 2009-07-09
Thank you everyone! They're working now.

---

### Post by Corvair on 2009-07-12
I have also a problem installing acroread on my desktop, with my new upgrade to 8.10.
I was able to install acroread without a problem on my laptop, amd64

This is what I get when installing from Synaptic:

acroread-fonts:
 Depends: acroread (>=9.1) but it is not installable

How can I correct this?

Thank you for reading me.

---

### Post by GhettoYhetti on 2009-07-30
This link is pretty much self-explanatory and will get you what you want.  [http://blogs.adobe.com/acroread/2009/04/adobe_reader_now_available_thr.html](http://blogs.adobe.com/acroread/2009/04/adobe_reader_now_available_thr.html)

---

### Post by Corvair on 2009-07-30
Thanks you for the information.

---

