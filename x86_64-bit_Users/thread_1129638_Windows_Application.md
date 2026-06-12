---
title: "Windows Application"
date: 2009-04-18
forum: x86 64-bit Users
---

### Post by nkingcade on 2009-04-18
I have installed these window applications before. It appears that I am missing something. Here's what I have done:

1. Installed ms core fonts.

2. Installed Wine

3. Added the application executable to the application area in Wine.

4. Added comctl32 library for the application to use in Wine.

5. Ensured that the executable was attached to the proper operating library in Wine.

This is what the system returns when I attempt to load the application:

[/media/Mikey/KingdomStuff/install2008watcheng/autorun.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/Mikey/KingdomStuff/install2008watcheng/autorun.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/Mikey/KingdomStuff/install2008watcheng/autorun.exe or
          /media/Mikey/KingdomStuff/install2008watcheng/autorun.exe.zip, and cannot find /media/Mikey/KingdomStuff/install2008watcheng/autorun.exe.ZIP, period.


Anyone seen this before. Thanks in advance.

Neal

---

### Post by stchman on 2009-04-19
Remember, WINE does not run 100% of Windows applications 100% of the time.

---

### Post by nkingcade on 2009-04-19
I have run these applications on a number of versions of ubuntu including this one (9.04) This occured during an upgrade of the daily beta. I thought someone may have had the same experience.

Neal

---

### Post by Yellow Pasque on 2009-04-19
What version of WINE did you install?

---

### Post by nkingcade on 2009-04-19
I did an apt-get and installed 1.0.1. Thanks.

neal

---

