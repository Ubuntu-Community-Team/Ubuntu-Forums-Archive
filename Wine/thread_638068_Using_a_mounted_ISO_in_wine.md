---
title: "Using a mounted ISO in wine"
date: 2007-12-11
forum: Wine
---

### Post by dethredic on 2007-12-11
Ok, I made an .iso of one of my CD's so I will not have to put it in every time I want to play. I have then mounted it with AcetonelSO2 and with the mount.sh script. When I launch my game it can't fine the CD.

I go into the wine preferences and then devices. I see a z drive that was not there before so I assume it is from AcetonelSO2. I set it to a CD drive, but I can't choose auto, I am stuck with manual (values are 0, 0 as of now)

This still does not work. Any ideas?

---

### Post by dethredic on 2007-12-12
bump

---

### Post by cogadh on 2007-12-12
I don't know about Acetone, but all you usually need to do is mount the ISO like a normal drive, then set up Wine to access the mount as a CD-ROM drive:
```
mount -r -t iso9660 game.iso /media/isodrive
```
You can set up the mount point to be called whatever you want (I just used "isodrive" for simplicity).

---

### Post by dethredic on 2007-12-13
Hmm, this does not seem to work:

This is what I went through

```



```

Any other ideas?

---

### Post by cogadh on 2007-12-13
First, you need to create the directory where the ISO is to be mounted:
```
sudo mkdir /media/isodrive
```
Make sure Wine has that directory added and configured as a CD-ROM drive, then change directories to wherever the ISO is:
```
cd /path/to/ISO
```
Then you can mount the ISO:
```
sudo mount -r -t iso9660 frozenthrone.iso /media/isodrive
```
After that, Wine should see it no problem.

---

### Post by dethredic on 2007-12-13
Ok I did all of that with no errors until the end

Edit: ok, when i used proper capitalization this was returned:

mount: /home/sadasd/Desktop/FrozenThrone.iso is not a block device (maybe try `-o loop'?)

---

### Post by cogadh on 2007-12-14
Ah crap, I forgot the whole loop thing. Try this instead:
```
mount FrozenThrone.iso /media/isodrive/ -t iso9660 -o ro,loop=/dev/loop0
```

---

### Post by dethredic on 2007-12-14
Ok, it got mounted and the icon is on my desktop. That is good.

Now, I went into configure wine-> device tab, and did the auto select devices. Nothing new came up, so I added a new device and in the location I put in /media/isodrive/ and set it to CD-Drive. That did not work.

Then I tried /media/isodrive/FrozenThrone.iso but that did not work either. Finall I tried /media/isodrive/isodrive and that did not work.

What should I do next?

---

### Post by cogadh on 2007-12-14
I'm not sure why that didn't work, except for maybe the order you did that in. I usually create the drive in Wine first and point it at the /media/isodrive directory, then mount the ISO.

---

### Post by dethredic on 2007-12-15
hmm, switching the order did not help

---

