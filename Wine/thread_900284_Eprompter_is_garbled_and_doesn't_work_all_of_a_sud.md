---
title: "Eprompter is garbled and doesn't work all of a sudden"
date: 2008-08-25
forum: Wine
---

### Post by dai_vernon on 2008-08-25
I installed ePrompter (a minimalist email notifier) in wine yesterday,  The setup worked fine, and so did the program after the setup was done.  Upon reboot I run it again and the window is a garbled mess or a black screen.  It is failing to work, though the system tray icon is fine.  When I run it from a terminal I get either nothing (in which case the window is a black rectangle, or this, when the window is garbled:

```
taylorh@taylorh-laptop:~$ '/home/taylorh/.wine/drive_c/Program Files/ePrompter/ePrompter.exe'
fixme:ole:OLEPictureImpl_Load Failure while reading picture header (hr is 0, nread is 0).
fixme:ole:OLEPictureImpl_Load Failure while reading picture header (hr is 0, nread is 0).
fixme:ole:OLEPictureImpl_Load Failure while reading picture header (hr is 0, nread is 0).
fixme:ole:OLEPictureImpl_Load Failure while reading picture header (hr is 0, nread is 0).
fixme:ole:OLEPictureImpl_Load Failure while reading picture header (hr is 0, nread is 0).
fixme:ole:OLEPictureImpl_Load Failure while reading picture header (hr is 0, nread is 0).
fixme:ole:OLEPictureImpl_Load Failure while reading picture header (hr is 0, nread is 0).
fixme:ole:OLEPictureImpl_Load Failure while reading picture header (hr is 0, nread is 0).
fixme:ole:OLEPictureImpl_Load Failure while reading picture header (hr is 0, nread is 0).
fixme:ole:OLEPictureImpl_Load Failure while reading picture header (hr is 0, nread is 0).
fixme:ole:OLEPictureImpl_Load Failure while reading picture header (hr is 0, nread is 0).
fixme:ole:OLEPictureImpl_Load Failure while reading picture header (hr is 0, nread is 0).
fixme:ole:OLEPictureImpl_Load Failure while reading picture header (hr is 0, nread is 0).
fixme:ole:OLEPictureImpl_Load Failure while reading picture header (hr is 0, nread is 0).
fixme:ole:OLEPictureImpl_Load Failure while reading picture header (hr is 0, nread is 0).
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
```

with the last 2 lines appearing when the program is quit from a right click on the system tray icon.

This happens regardless of desktop effects settings and regardless of what version of windows Wine is emulating.  What is the problem?

---

### Post by dai_vernon on 2008-08-25
I fixed the problem, but I'm not sure why it worked.  Here's what I did:
The original method of executing the program was saying '/home/taylorh/.wine/drive_c/Program\ Files/ePrompter/ePrompter.exe'.  I wrote a script that navigates to the file and says wine epropmpter.exe.  That works.

Why does it work?

---

