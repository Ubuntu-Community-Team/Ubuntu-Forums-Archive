---
title: "No mkswap command"
date: 2008-02-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by thaumielx72 on 2008-02-16
Well, this is different.

When I attempt to use the mkswap command I get the error message:
sudo: mkswap: command not found

Any suggestions?

Thanx in advance.

---

### Post by gsmanners on 2008-02-16
That's weird. Try this:

apt-cache policy util-linux

If you have util-linux, I would reboot and look for rootkits using a live CD.

---

### Post by jpkotta on 2008-02-16
I bet it's not in your PATH.  It should be in /sbin.

```
sudo /sbin/mkswap <file>
```
or
```
export PATH=$PATH:/sbin
sudo mkswap <file>
```

---

### Post by thaumielx72 on 2008-02-17
Appreciate your trying to help, but when I saw that it also did not know what the fdisk command was I figured I better just reload from scratch.

Everything's fine now but let that be a lesson for me to remember:  Be careful of some of the suggestions you get on forums.  I was trying to get IcedTea to work and I believe I may have dropped my system back to a 32 bit mode of some kind.

Thank goodness for my 4gb flash stick so I didn't lose anything.  Fortunately I already had my data there as it also would not mount that drive either.

Well, on the bright side I have a fresh new install of Ubuntu.

(Oh BTW - I couldn't get Hardy Heron to recognize my laptop screen.  It's a Toshiba Satellite.  I'm sure they'll get all the kinks worked out before April.)

---

### Post by jpkotta on 2008-02-17
I recommend making a separate partition for /home.  That way, you can reinstall as much as you want and your data and most settings will remain untouched.  

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by thaumielx72 on 2008-02-18
Good point.

Say, I have 4gb available from the flash memory stick.  Is it possible (or advisable) to place the /home partition there?  How often does it read from there?  Wouldn't  that be like having all the system files on a RAM disk.

I was reading about Readyboost and possible Linux variations of that idea.  There seems to be some debate as to the usefulness of this idea.  What is the general consensus of the Ubuntu community?

I'm using it right now as a swap partition.  Since I upgraded my notebook's memory to 4 gb  it hasn't come close to touching the swap.  This might be a better use for the flash stick on a day to day basis, correct?

---

### Post by thaumielx72 on 2008-02-18
Ok, I was confused by the difference between /home and the system files.  I should have read your link first.  Still, keeping the system files on flash memory seems like a good idea.  If it's going to be reading them with any consistency during operations.  But I suppose it would just be in the cache, anyway.

---

