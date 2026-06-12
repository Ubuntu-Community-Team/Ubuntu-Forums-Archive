---
title: "Can't start WoW"
date: 2007-11-29
forum: Wine
---

### Post by Majskorven on 2007-11-29
I got some problem to start my World of Warcraft, i have installed the game but when i'm trying to start it it wont... I get this message in the terminal:

X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  469
  Current serial number in output stream:  470

---

### Post by justin whitaker on 2007-11-29
> **Majskorven said:**
> I got some problem to start my World of Warcraft, i have installed the game but when i'm trying to start it it wont... I get this message in the terminal:

X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  469
  Current serial number in output stream:  470

Drivers. What card are you using, and what drivers have you installed?

---

### Post by Majskorven on 2007-11-29
I'm using a Mobile Intel(R) 965 Express Chipset Family and i haven't installed any new drivers... It worked with Windows XP

---

### Post by 11hjpphty76lkjj on 2007-11-29
Setting up WoW can be a process. but it can work.  Have you looked here?

[https://help.ubuntu.com/community/WorldofWarcraft?highlight=%28worldofwarcraft%29](https://help.ubuntu.com/community/WorldofWarcraft?highlight=%28worldofwarcraft%29)

and here:

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting?highlight=%28worldofwarcraft%29](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting?highlight=%28worldofwarcraft%29)

The first one does work, I've done it.  But I did it with an Nvidia video card. I don't have any experience using an onboard card..

Hope this helps.

---

### Post by Majskorven on 2007-11-29
> **kalosaurusrex said:**
> Setting up WoW can be a process. but it can work.  Have you looked here?

[https://help.ubuntu.com/community/WorldofWarcraft?highlight=%28worldofwarcraft%29](https://help.ubuntu.com/community/WorldofWarcraft?highlight=%28worldofwarcraft%29)

and here:

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting?highlight=%28worldofwarcraft%29](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting?highlight=%28worldofwarcraft%29)

The first one does work, I've done it.  But I did it with an Nvidia video card. I don't have any experience using an onboard card..

Hope this helps.

Yes i've tried, didn't work :S:/

I have the same problem with my CS 1.6 Lan version but I got to work once and now it will not start :S

---

### Post by 11hjpphty76lkjj on 2007-11-29
If you run:

```
glxinfo | grep rendering
```

what is the result?

---

### Post by Majskorven on 2007-11-29
> **kalosaurusrex said:**
> If you run:

```
glxinfo | grep rendering
```

what is the result?

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

But I played wow when i haved XP so my graphic card shoulden't fail..

---

### Post by 11hjpphty76lkjj on 2007-11-29
Well the problem isn't your video card per se, it's the driver. You may want to look up your card and how to enable direct rendering. Once you get direct rendering working with your video card you should be golden.  But that's the primary problem at this point.

---

### Post by Majskorven on 2007-11-29
> **kalosaurusrex said:**
> Well the problem isn't your video card per se, it's the driver. You may want to look up your card and how to enable direct rendering. Once you get direct rendering working with your video card you should be golden.  But that's the primary problem at this point.

hmm okej, so what should i google?? My graphiccard name and rendering?

---

### Post by 11hjpphty76lkjj on 2007-11-29
Yeah..or search in ubuntuforums.  Someone may have asked the same thing before.  Good luck!

---

### Post by Majskorven on 2007-11-29
Okey! Thank you!

---

