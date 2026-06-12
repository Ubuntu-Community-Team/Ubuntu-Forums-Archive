---
title: "WoW DVD unmounting issue"
date: 2008-05-30
forum: Wine
---

### Post by Shaitok on 2008-05-30
Hello, I'm really new to Linux (a few weeks) and I had everything running fine with Ubuntu 8.04 32-bit version Wine, and World of Warcraft (issues with Ventrilo not being able to speak or hear but that is besides the point of this post)

So I decided to try out the 64-bit version since I'm running a 64 bit processor. I have Wine installed again with no problems, and my video is checking out okay to install WoW. 

The problem I'm having now is that I'm installing from DVD and need to get the unhide option in. The only information I can find to do this is via the following command:

```
sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/ 
```

I did this fine on the original install in the 32-bit version, but now I cannot get the drive to unmount in order to be able to use that command to mount it and get this when I try it anyway:

```
shaitok@Shaitok:~$ sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/
mount: /dev/scd0 already mounted or /media/cdrom0/ busy
mount: according to mtab, /dev/scd0 is mounted on /media/cdrom0
```

When I go into the computer folder and right-click, the unmount option is not available. I don't know if I failed to install a package that I had on the previous install or not.

Please help this Linux noob, I don't want to go back to microsuck.:lolflag:

---

### Post by Shaitok on 2008-05-31
Is there no one that can help me fix this problem?:confused:

---

### Post by werries on 2008-05-31
type into terminal
```
sudo umount /media/cdrom0 
```

---

### Post by Shaitok on 2008-05-31
Thanks so much werries, I figured it was something simple, I thought I had tried that before, must have had the arguements wrong for it.

---

