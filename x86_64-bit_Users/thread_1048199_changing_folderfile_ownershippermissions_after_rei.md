---
title: "changing folder/file ownership/permissions after reinstall"
date: 2009-01-23
forum: x86 64-bit Users
---

### Post by capnthommo on 2009-01-23
hi everybody (sorry, i think i posted in the wrong place maybe should be beginners questions?)
i just reinstalled from 32 into 64 bit ubuntu.  before reinstall i saved all my data files to a dvd.  I have just loaded therm onto the new system and find that all the permissions/ownerships are now /root - i guess this is because they were created on the old installation (i reinstalled partly to get rid of old partitions and clutter.
these are data files that i work with.  i have them on my home/nigel directory and need to switch all these owner/permts to me not root.
is there a terminal command such as 
```
 chown home/nigel.........
```
that will make all these changes and repeat it to all the files in all the folders in all the folders etc (is this what recursively means?  if it is then recursively).
i am the only user on this single machine and i am not on a network so there is no issue of other users here.  i just want permanent control of my data/music/images.  just the things that would normally not require a ```
sudo or gksudo
``` command.
i know it can be done with ```
 sudo nautilus 
``` but i have trouble with this way.
can anybody help please.
happy to post any other info you need - just aks
cheers
nigel

---

### Post by sisco311 on 2009-01-23
```
sudo chown -R $USER\: $HOME
```

or
```
sudo chown -R nigel\: /home/nigel
```
assuming that nigel is your user name and /home/nigel is your home directory.

EDIT:
oh, and:
```
chmod 755 /home/nigel
chmod 644 /home/nigel/.dmrc
```

for more info take a look here:[http://ubuntuforums.org/showthread.php?t=976610]("http://ubuntuforums.org/showthread.php?t=976610")

---

### Post by Bölvaður on 2009-01-23
I may switch path and user name... Im on a windy machine here in the uni.

sudo chown /home/ -R nigel

-R means it will change owner of every file in the directory and then this same command will be done to every directory that it finds in the current directory. Recursive means that the command activates it self (perhaps with different arguments.. like here it thanges the path).

then:

sudo chmod 755 /home/ -R

755 is binary representation of Read Write Execute (4 2 1) so 7 would bee RWX rights, but 5 would be RX.

---

### Post by capnthommo on 2009-01-23
thanks for the speedy replies - looks like just what i was looking for.  i shall try later on.
thanks again
 nigel

---

### Post by capnthommo on 2009-01-23
Yes, thanks again guys.
it gave me a couple of refusal messages (dont have permission and file doesnt exist etc) but it seems to have worked anyway.  
even if it doesnt work then it's not the end of the world, i assume that future created files will have permission/ownership down to me and so if it became a problem i could just copy the data into a new file with a new name and 'save as'.  thanks though, i think it has done it.
cheers
nigel
):P

---

### Post by sisco311 on 2009-01-23
> **capnthommo said:**
> Yes, thanks again guys.
it gave me a couple of refusal messages (dont have permission and file doesnt exist etc) but it seems to have worked anyway.  
even if it doesnt work then it's not the end of the world, i assume that future created files will have permission/ownership down to me and so if it became a problem i could just copy the data into a new file with a new name and 'save as'.  thanks though, i think it has done it.
cheers
nigel
):P

let me guess:
> chown: cannot access `/home/username/.gvfs': Permission denied

You can ignore that error message. Gvfs is a virtual file system with backends for things like sftp, ftp, ...

---

### Post by capnthommo on 2009-01-23
hi sisco, it was something like that (not totally certain it was gvfs but cold have been).  and it still seems to show me as owner and allow me to edit so i am a happy camper.
thanks again
nigel

---

