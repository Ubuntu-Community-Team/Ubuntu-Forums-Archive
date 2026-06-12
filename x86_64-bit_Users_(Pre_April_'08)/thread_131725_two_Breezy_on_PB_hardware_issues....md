---
title: "two Breezy on PB hardware issues..."
date: 2006-02-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by jlgoolsbee on 2006-02-17
First, how do I reconfigure the sound setup (like having it reconfigure the x-server by running 'sudo dpkg-reconfigure xserver-xorg')?  I think that part got botched on the initial install, as I can not get sound working at all.

Second, I want to edit the temperature at which my fan spins up at, located in the file '/sys/devices/temperatures/limit_adjust'.  However, even when I try to 'sudo vi' edit it, I get an 'E667 fsync failed' error, and when I tried to do it in gedit with gnome-sudo, I got this error:

(gedit:4067): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

WTF mates?

I guess a third issue would be that sleep mode doesn't work (don't know if that's related to either of the above), but that's not really of much concern to me since I have Breezy on my external drive, and don't see myself taking that along with me for daily use... but it would still be nice if it worked.

---
1.33 Ghz 12" Powerbook
OS X "Tiger" 10.4.5
Ubuntu "Breezy Badger" 5.10 on external FW HD

---

### Post by jlgoolsbee on 2006-02-21
Is there no one out there that knows the answer to any of these questions?

I had heard wonderful things about the Ubuntu community, and while I realize the number of users installing Ubuntu on their 12" PB's is a slim number, surely someone out there knows something about these issues?

---

### Post by ssam on 2006-02-21
not sure about the sound. maybe sudo dpkg-reconfigure alsa or gstreamer

for editing /sys/devices/temperatures/limit_adjust it may be that vi can't edit it because it is not a real file. you could try geting a root shell (sudo su) and running
```
echo "what you want in the file" > /sys/devices/temperatures/limit_adjust
```

the ">" directs the output from echo into the file, overwritting what was there before.

with sleep i think radeon based powerbook are better than nvidia. it may be fixed in a newer kernel. you could try a dapper flight (beta) [live cd]("http://cdimage.ubuntu.com/releases/dapper/"). and maybe file a bug if it still does not work.

---

### Post by jlgoolsbee on 2006-02-22
Thank you for replying!

Editing /sys/devices/temperatures/limit_adjust with the echo statement appeared to work (as evidenced by running 'more /sys/devices/temperatures/limit_adjust' immediately after and seeing my value, "-2" there), yet after a reboot it was back to "0"...

Also, sudo dpkg-reconfigure alsa and gstreamer revealed that neither is installed on my system in the first place?  So now the question is... how do I get them?

---

