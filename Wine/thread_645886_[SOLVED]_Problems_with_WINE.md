---
title: "[SOLVED] Problems with WINE"
date: 2007-12-20
forum: Wine
---

### Post by tech9 on 2007-12-20
Well...

I decided to give WINE another shot here...

I tried installing Office 2003, just to see if I could get wine to work...

but I get this error

Warning: could not find DOS drive for current working directory '/home/AMD', starting in the Windows directory.
wine: cannot find '/media/cdrom0/SETUPPRO.EXE'

Perhaps my wine install was corrupt... when I click to browse the c:\ drive , I get nothing.

any help would be appreciated :)

---

### Post by cogadh on 2007-12-20
Did you run winecfg to create your Wine "fake Windows" drive and configure Wine before trying to install Office?

EDIT - Almost forgot, Access, OneNote, Frontpage, Infopath and Outlook don't work in Wine, so all you will really get from Office is Word, Excel, Powerpoint and Publisher. You can already get that functionality from Open Office without bothering with Wine.
[http://appdb.winehq.org/appview.php?iVersionId=3214](http://appdb.winehq.org/appview.php?iVersionId=3214)

---

### Post by tech9 on 2007-12-20
> **cogadh said:**
> Did you run winecfg to create your Wine "fake Windows" drive and configure Wine before trying to install Office?

I did... I created a virtual c drive, but when I exit wine and go back in... I do not see the drive that I just created...

Thanks for the response :)

---

### Post by cogadh on 2007-12-20
The "drive" is a hidden directory in your home folder, you'll need to unhide files in order to actually see it. However, if you did run winecfg and you are still getting those errors, something may have been corrupted when it was created. Just delete the .wine directory in your home folder and try recreating it.

---

### Post by tech9 on 2007-12-20
> **cogadh said:**
> The "drive" is a hidden directory in your home folder, you'll need to unhide files in order to actually see it. However, if you did run winecfg and you are still getting those errors, something may have been corrupted when it was created. Just delete the .wine directory in your home folder and try recreating it.

Sweet!

Deleting the .wine directory worked... when I loaded the wine config ... it automatically recreated the .wine with the drive_c folder.

You are the MAN - cogadh!!!

Thanks :)

---

### Post by cogadh on 2007-12-20
Glad to help. :)

Make sure you mark the original post as "SOLVED" (Thread Tools > Mark this thread as solved), it helps keep things cleaned up around here.

---

### Post by tech9 on 2008-08-05
> **cogadh said:**
> Glad to help. :)

Make sure you mark the original post as "SOLVED" (Thread Tools > Mark this thread as solved), it helps keep things cleaned up around here.

all set my friend!

---

