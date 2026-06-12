---
title: "dual disk installation"
date: 2008-06-02
forum: Wine
---

### Post by lafferjm on 2008-06-02
Well i did everything that was specified in the stickies and couldn't find a solution so i figured i would post my question.  I have command & conquer generals for windows, and wanted to install it using wine.  The problem is it requires two disks to install.  When the installation process gets to installing the second disk it tells me i can't eject the volume because the media is being used by an application.  Is there any way to bypass this little speed bump?

---

### Post by JoshuaRL on 2008-06-02
I've have this same problem.  I haven't tried this myself but I've heard that you can copy the contents of the CD or DVD into a fresh folder on the desktop.  Then when it asks you to change disks, delete the contents of that folder and paste in the contents of the second CD.  That way it reads from the same location.

Makes sense, but I haven't tried it.  Sorry, and hope this helps.

---

### Post by prshah on 2008-06-03
> **lafferjm said:**
>   The problem is it requires two disks to install.  When the installation process gets to installing the second disk it tells me i can't eject the volume because the media is being used

Open a terminal (Applications-Accessories-Terminal), then give the following commands ```

wine eject

```

This is a known problem (2CD install problem) and known working workaround. Sometimes, you may have to give the above command twice for the eject to happen. 

Then insert second CD, close drive and continue.

---

