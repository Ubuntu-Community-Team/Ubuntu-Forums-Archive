---
title: "wireless problem"
date: 2007-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tig3rzhark on 2007-12-05
I have a problem with my broadcom 4318 wireless card.  The card works for a while but after a few restarts, it fails to connect to my router.  The restricted drivers are already installed and they were working fine for a while.

I'm using gusty (the new ubuntu os).  I know that it has a lot of bugs but this is ridiculous.

I tried using the ndiswrapper to install a different driver and it was working fine for a while.  But I had to directly connect to the router to download the necessary software to reenable my connection to the router.

Please tell me that there is a solution to my problem.

---

### Post by Origin on 2007-12-05
There is a solution to your problem.

I just don't know what it is.

I have the same wireless card, the same OS (gutsy x64) and the same problem.

---

### Post by NullHead on 2007-12-06
Try adding bcm43xx to /etc/rc.local .... like so ```
sudo gedit /etc/rc.local
```and make it look like this.```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sudo modprobe bcm43xx 

exit 0
``` save the file and it should work.

EDIT: You both should do this command too. ```
sudo echo 'bcm43xx' |sudo tee -a /etc/modules
```

---

