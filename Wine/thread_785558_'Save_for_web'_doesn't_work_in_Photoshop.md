---
title: "'Save for web' doesn't work in Photoshop"
date: 2008-05-07
forum: Wine
---

### Post by Scooter7 on 2008-05-07
Hi,

I have Photoshop CS2 running well in wine (for the most part; see [http://ubuntuforums.org/showthread.php?t=784888](http://ubuntuforums.org/showthread.php?t=784888) for details), but I tried 'file -> save for web', and it didn't do anything, at all.   I've read that in the past (i.e, with Photoshop 7), to fix this, you have to run a Windows installation of Photoshop in wine, or something.   This isn't really an option for me, however.   Is there another fix/workaround?

Thanks in advance,

---

### Post by illepic on 2008-06-02
I am having the same issue.  I've installed directly from the demo exe.  I have to send my finished PSD files to a Windows machine to push them out to web formats.  Feels so... dirty :P

---

### Post by Dylnuge on 2008-06-02
Same here. I use GIMP to open the files and then use the save as command, it works quicker then sending it to a windows or mac.

---

### Post by nityananda on 2009-03-13
I found solution for save for web here: 
[http://www.contentwithstyle.co.uk/content/wine-photoshop-save-for-web](http://www.contentwithstyle.co.uk/content/wine-photoshop-save-for-web)

In my case I needed to change number to 8.0 and put '\' instead of '/'. So now I am starting Photoshop CS by this command and save for web works good:
```
wine "c:\program files\adobe\Photoshop 8.0\Photoshop.exe"
```

---

