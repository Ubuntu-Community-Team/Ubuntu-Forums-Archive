---
title: "COD4 Wine"
date: 2008-10-28
forum: Wine
---

### Post by Mattarov on 2008-10-28
OK, so i have been trying to get cod4 working on my ubuntu system through wine. I just get round to managing it by installing wine 1.0.1 and then updating it again with wine_1.1.4+3dmarkPatch-0~getdeb1_i386.deb. (To fix the well known 'not enough textures for direct x 9...' error on start-up)

I then run it and it finally works.

However all is not well as I closed it and now when I try and run it again and I get that direct x error message again. (5 mins after closing previous, working attempt). :confused:

I am absolutely stumped as to why this is happening to me and annoyed that i have spent countless says and plenty of hours today trying to make this work and it then gives me a glimpse of working and messes up, so you can understand my frustration and so absolutely any help would be greatly appreciated.

Thank you in advance,

Matt

---

### Post by Mattarov on 2008-10-29
C'mon...... no1 can help?....

---

### Post by Dark9204 on 2008-10-30
Look at the wine AppDB
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12804](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12804)

You could ether install a later version that doesn't need the patch. Or you could compile wine 1.0.1 from source with the patch "For wine 0.9.58-1.0.0" in the DB

Also. Make sure that you're using the proprietary graphics driver. Go to System->Administration->Hardware Drivers.

---

