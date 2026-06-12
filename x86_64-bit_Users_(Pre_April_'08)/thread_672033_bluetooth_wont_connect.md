---
title: "bluetooth wont connect"
date: 2008-01-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by MikeSz on 2008-01-19
There seem to be a few threads on this but none have helped.  I have a Samsung D830 and a bluetooth dongle for my laptop and although the two seem to detect each other, they will not connect.  My laptop detects my phone (ive been through all the settings on it to ensure that it is activated and allows connections etc) and I get the message in the attached screenshot.  Ive installed virtually everything I can find in synaptic concerning bluetooth and obex but the two just wont talk to each other!  

Can anyone help?

---

### Post by John Jason Jordan on 2008-01-19
> **MikeSz said:**
> There seem to be a few threads on this but none have helped.  I have a Samsung D830 and a bluetooth dongle for my laptop and although the two seem to detect each other, they will not connect.  My laptop detects my phone (ive been through all the settings on it to ensure that it is activated and allows connections etc) and I get the message in the attached screenshot.  Ive installed virtually everything I can find in synaptic concerning bluetooth and obex but the two just wont talk to each other!
Try Blueman. It's not in Synaptic, but you can download and install the .deb. Blueman is the missing bluetooth utility for Linux. I didn't bookmark where the .deb file is, but google should turn it up. For further instructions search the forums for "blueman" and you will find it discussed at length.

---

### Post by MikeSz on 2008-01-19
Thanks for that - ive had a look and it looks just the trick.  Unfortunately I have run into a bit of dependency hell :-)  It wants bluez-utils, which is fine, but that then creates conflicting dependencies with 3.19 and 3.24-oubuntuo!!!

Il keep playing but any ideas??

---

### Post by John Jason Jordan on 2008-01-19
> **MikeSz said:**
> Thanks for that - ive had a look and it looks just the trick.  Unfortunately I have run into a bit of dependency hell :-)  It wants bluez-utils, which is fine, but that then creates conflicting dependencies with 3.19 and 3.24-oubuntuo!!!
Il keep playing but any ideas??
I'd suggest trying to install the .deb file with gDebi. Also try this thread:

[http://ubuntuforums.org/showthread.php?t=559089&highlight=blueman](http://ubuntuforums.org/showthread.php?t=559089&highlight=blueman)

---

### Post by samib on 2008-01-20
I am very new to Linux and Ubuntu and searching Forums did not come up with an answer to my connection problem. Thought I would share this with you, it may not help immediately but may later. 

I installed Bluez and loading went ok. I have two dongles and Nokia 6600 and Nokia 6103 phones. When testing  communication found that either type was detected ok and  files could be transferred  from my desktop computer ( running Gutsy AMD64) to either of my phones.

Trying to send files the other way  however only resulted in the message - unable to connect.

By chance found that the only problem was the Obex file server needed to be launched manually. I have now set up  preferences -  sessions to launch this at start up, and connection is now easily established.

---

