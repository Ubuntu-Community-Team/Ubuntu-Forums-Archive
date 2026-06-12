---
title: "Hardware driver failure"
date: 2009-01-24
forum: x86 64-bit Users
---

### Post by darkrandomkid on 2009-01-24
I'm using a HP dv5t with a Nvidia 9600M graphics card.

When I boot Kubuntu normally, it takes an absurd amount of time to boot, and I get dumped to a console login screen instead of the KDE login.  When I login and run startx, it starts KDE, but neither my trackpad nor a USB mouse work.  

When I start Linux through the recovery console, it takes an absurd time to get through "loading hardware drivers" and fails afterwords.  When I start KDE, I get the same results as above.

I earlier had a problem with even starting Linux, where I received the "\dev\etc access denied" bug, but I was able to fix this.

EDIT: I am have no problems with the liveCD version, just my installed version. 

HELP!

-DRK

EDIT: Solved!

---

### Post by cariboo on 2009-01-24
Go to your hard drives manufacturers web site and download the diagnostic tools and run them on your hard drive. This will give you an indication of the health of your hard drive.

Jim

---

### Post by darkrandomkid on 2009-01-24
I tried that, and the hard drive seems to be in perfect health.  It's getting really frustrating.

---

### Post by cariboo on 2009-01-25
You have something failing, or it wouldn't dump to a text screen. Have you checked /var/log/messages using something like this:

```
cat /var/log/messages | grep fail
```

the above must be done in a terminal, and will print out every line that has the word fail in it. If you could paste the output of the above command, we may be able to help.

Jim

---

### Post by darkrandomkid on 2009-01-25
Frustratingly enough, there is nothing output when I run that command. 

Could it have something to do with my hardware drivers? That's where startup seems to hang up.

---

### Post by darkrandomkid on 2009-01-27
OK, I reinstalled Kubuntu, and all of my problems are gone. Thanks for trying to help, though!

-DRK

---

