---
title: "Hibernate/Suspend shuts PC down, slaughters swap?"
date: 2006-07-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Anything Generic on 2006-07-17
I'm just trying to conserve some electricity here and keep the temperature of my room down in the middle of summer.  I recently tried both the Suspend and Hibernate features of Xubuntu 6.06, however each one goes to a black screen and shuts the PC down!  The hibernate feature actually uses the HD's for half a minute and then shuts the PC down.

After a hard boot, my swap partition is no longer available.  Conky, the usage reporter on my desktop used to say 0/1.5GB  0% in use.  It now says 0/0 no swap% in use.  What happened to my swap?  How do I get it back?

I don't even care about suspend/hibernate at this point.  I'll shut my PC down instead, I would just like my swap partition back.  I've cold booted several times now, and my swap is still missing! :(

---

### Post by ahaslam on 2006-07-17
I had a simialr problem. Suspend/Hibernate is not working for many of us.
To get your swap working again, you may need to fromat it.

Try (repalce hda3 with your swap partition):

# sudo mkswap /dev/hda3
# sudo swapon /dev/hda3

If that doesn't work check that it's correctly entered in your fstab file.


Tony.

---

### Post by Anything Generic on 2006-07-17
eric@ubuntu:~$ sudo mkswap /dev/mapper/nvidia_egbeaddb7
Setting up swapspace version 1, size = 1612115 kB
no label, UUID=7310393d-612b-4124-84d9-c590727486c2
eric@ubuntu:~$ sudo swapon /dev/mapper/nvidia_egbeaddb7

/dev/mapper/nvidia_egbeaddb7    none            swap    sw         0 0

^ That's what I have in my fstab.  Is it okay that the mount point is "none"?


The swap works again at least and is shown as 0/1.5  0% in Conky. Thank you so much :D

---

### Post by ahaslam on 2006-07-17
Yep, mount point of none is how it's meant to be :)

No worries mate, I had the same problem a couple of days ago ;)


Tony.

---

### Post by Anything Generic on 2006-07-17
Thanks again!

---

### Post by canuckdissident on 2006-07-25
Based on the reply earlier in the thread - is there an open bug report for the hibernate issue trashing the swap file?

---

### Post by canuckdissident on 2006-07-25
> **Anthony Haslam said:**
> I had a simialr problem. Suspend/Hibernate is not working for many of us.
To get your swap working again, you may need to fromat it.

Try (repalce hda3 with your swap partition):

# sudo mkswap /dev/hda3
# sudo swapon /dev/hda3

If that doesn't work check that it's correctly entered in your fstab file.


Tony.

Sorry, this was the post I was referring to above

---

