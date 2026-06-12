---
title: "vertical 'spread' problem, printing to Canon MP620 in 8.04"
date: 2008-12-19
forum: x86 64-bit Users
---

### Post by javahollic on 2008-12-19
Anyone managed to get hooked up with Canon MP620?  Im using the sourceforge [cups-bjnp]("http://sourceforge.net/projects/cups-bjnp/") driver and managed to build it for Ubuntu 8.04 x86_64, however, Im getting strange vertical 'spread' showing up as white horizontal lines.  The standard ubuntu test page reaches the bottom of an A4 sheet just after the 'Magenta' text.  This is true for graphics and text alike.

Probably a cups-bjnp bug, I should log an issue but can't face re-registering with source-forge tonight.  Wondering if anyone has seen/fixed this?

Cheers,
andy

---

### Post by javahollic on 2009-01-19
Just dawned on me that I didn't need the bjnp at all.  On 64bit linux, you just need to force the driver architecture, see [The Canon PIXMA Linux Blog]("http://mp610.blogspot.com/2008/10/canon-pixma-scanners-are-now-network.html") for background.

PPD:
I just got the latest (modified jan09) MP620 compatible ppd from [sourceforge]("http://sourceforge.net/project/showfiles.php?group_id=210977"), and followed instructions...

Following files from [Canon support site for the MP610]("http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP610%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&"):

COMMON:
* dpkg --force-architecture -i cnijfilter-common_2.80-1_i386.deb
* dpkg --force-architecture -i cnijfilter-mp610series_2.80-1_i386.deb

SCANGEAR
* dpkg --force-architecture -i scangearmp-common_1.10-1_i386.deb
* dpkg --force-architecture -i scangearmp-mp610series_1.10-1_i386.deb

**Initially** you have to setup the printer via USB for 'network' parameters, once done.  I have it printing fine direct on USB2 and also via WEP network.  Scanning is a different story though... another day.

---

