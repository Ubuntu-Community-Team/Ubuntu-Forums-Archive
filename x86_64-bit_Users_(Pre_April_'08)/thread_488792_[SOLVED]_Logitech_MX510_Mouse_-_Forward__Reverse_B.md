---
title: "[SOLVED] Logitech MX510 Mouse - Forward / Reverse Buttons - Help Enable Them..."
date: 2007-06-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-06-30
I've read through some of the previous posts about the Logitech MX510 Mouse already.  The problem is most of them assume you already have basic knowledge on editing certain files (which I don't).

I would like someone to walk me through activating the forward/reverse side buttons for my internet/file browsers.  I know it works in Linux because I booted off a LiveCD of Puppy-Linux and it works by default.

Any help is appreciated.  Thanks.

---

### Post by John.Michael.Kane on 2007-06-30
This guide [**HOWTO: Get 7 working buttons on MX510**]("http://ubuntuforums.org/showthread.php?t=485175&highlight=Logitech+MX510") is as step by step as you can get.

You going to have to get dirty theres no other way. Even if one of the members posted in a type this type that fashion theres still room for errors.

The best thing to remember if you mess up your xorg config is.
```
alt + f2
```
Then
```
sudo dpkg-reconfigure xserver-xorg
```

And retry the guide again.

---

### Post by crjackson on 2007-06-30
I don't really call that getting too dirty.

It was cut/paste and IT WORKED PERFECTLY!:D

Thanks for you help :p

---

### Post by John.Michael.Kane on 2007-06-30
No problem. Glad it worked out.

---

### Post by crjackson on 2007-07-08
**I just realized that my forward/back buttons work, but I lost my scroll up/down buttons in the change.  How do I add them back?**

---

