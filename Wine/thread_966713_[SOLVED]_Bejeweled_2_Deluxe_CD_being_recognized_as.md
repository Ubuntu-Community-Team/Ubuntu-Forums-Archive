---
title: "[SOLVED] Bejeweled 2 Deluxe CD being recognized as an audio CD???"
date: 2008-11-01
forum: Wine
---

### Post by Virtualboxbuntu on 2008-11-01
This doesn't exactly belong in Wine but I don't really know where else to put it. If the mods know a better section, please move it.

I'm in the process of migrating my mother to Ubuntu from Vista. There are three programs she wants:

-Internet Explorer (Firefox+Vista-Aero theme is good enough)
-Spider Solitaire (Aisleriot or whatever it's called has it)
-Bejeweled 2 Deluxe

The computer is dual-booting and Bejweled works flawlessly in Vista. However, when I insert the B2D CD in the drive, Ubuntu opens Rythmbox and starts playing the soundtracks. The reason for this, I suspect, is that the installation CD is also a normal audio CD that can be played in a normal CD player. When I browse the CD in nautilus, all I see are the audio files. So as far as Ubuntu is concerned, I inserted an audio CD in the drive.

How can I install this game in Wine for my mother? Should I mount the Vista partition and copy the installed game from Program Files?

My mother's tried others like Jools but they don't cut it.

---

### Post by doorknob60 on 2008-11-01
I experienced this too...I don't remember how I fixed it, but I got a pirated version and it worked XD I didn't consider it illegal because I owned the CD game. I think I endfed up getting the CD to work once though... EDIT: Hmm, my Arch automounts it perfectly (unlike Ubuntu and I think Debian too). I'd try manually mounting it. Try typing this in the terminal:
```
sudo mount /dev/cdrom
```

IIRC, Audio CDs don't and can't get mounted, so maybe once it gets mounted it can read that data. There's probably a bug prevent HAL from automounting this particular CD, although it's certainly not present in Arch.

---

### Post by david_kt on 2008-11-01
Open terminal (Application > Accessories > Terminal) and copy and paste below command:

```
ls /media/cdrom0
```

What is the list there? You could copy and paste the terminal output here. Highlight the output using mouse and press <ctrl> <shift> C to copy. To paste to browser just press <ctrl> V as usual.

DK

---

### Post by Virtualboxbuntu on 2008-11-01
ls /media/cdrom0 doesn't give me anything. It's blank.

Doorknob60's suggestion worked though. Thank you!

You guys are way better than the people at Yahoo! Answers :lolflag:

---

### Post by david_kt on 2008-11-02
> **Virtualboxbuntu said:**
> ls /media/cdrom0 doesn't give me anything. It's blank.

Doorknob60's suggestion worked though. Thank you!


That's right. If ls /media/cdrom give you nothing, than the next step is Doorknob60's suggestion as that's mean the cdrom is not mounted yet.

DK

---

### Post by Bios Element on 2008-11-02
> **Virtualboxbuntu said:**
> You guys are way better than the people at Yahoo! Answers :lolflag:
I should take that as an insult....*snickers* Kidding. Really though this seems to be a bug accross all OS inculding Windows. It did that with my(read: dad's) old Bejeweled Disk as well.

---

