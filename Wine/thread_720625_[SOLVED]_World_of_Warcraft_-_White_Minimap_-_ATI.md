---
title: "[SOLVED] World of Warcraft - White Minimap - ATI"
date: 2008-03-10
forum: Wine
---

### Post by Resonance378 on 2008-03-10
Please mark this Solved.

**SUMMARY:** The white minimap in World of Warcraft, when indoors, is not a Wine issue it is an ATI Driver issue.

The white minimap issue is not a Wine issue it is due to the way pbuffers are supported in the ATI Catalyst driver in OpenGL mode.

For a full read on the issue:
[http://bugs.winehq.org/show_bug.cgi?id=11826](http://bugs.winehq.org/show_bug.cgi?id=11826)

This has been tested on Ubuntu 7.10, ATI Catalyst 8.0,8.1,8.2, and Wine Version(s) 0.9.48 - 0.9.57 when using:

-opengl in the wine command line launch OR
SET gxAPI "opengl" in the WoW config.wtf file.

---

### Post by oldweasel on 2008-05-21
Question - has anyone tried this with the ATI 8.5 drivers? Same issue?

---

### Post by dre_in_ham on 2008-12-02
using 8.04 i didnt have this issue but now on 8.10 i do. However the framerate is greatly improved so i will live with it for now!
Im using wine 1.1.9 with a fully updated hardy 8.10 on a radeon x1600. Will gladly give you version numbers if you give the commands i need to enter, since my version numbers never seem to change, even after updates. Must be checking the wrong places....

---

