---
title: "ATLAS / libatlas help (for refocus)"
date: 2009-06-27
forum: x86 64-bit Users
---

### Post by dh003i on 2009-06-27
I want to use the [ATLAS / libatlas libraries to optimize the refocus mathematical libraries]("http://refocus.sourceforge.net/doc.html#atlas"). Refocus is a GIMP plugin that corrects images where here is motion blur. 

However, I really don't know where to start. The instructions are entirely confusing and almost useless. Ubuntu has the packages for libatlas3gf-base, which I installed. Ok, so now what? The refocus manual says I need to 

> Make ATLAS generate its libraries. For instructions see the ATLAS documentation. Depending on your system, this may take a long time. During the installation you have to select a name to identify your configuration. In the following examples we will use Linux_PII as the chosen name.

Ok, so ATLAS documentation -- [3 The ATLAS configure step]("http://math-atlas.sourceforge.net/atlas_install/atlas_install.html#SECTION00040000000000000000") -- doesn't tell me a damn useful thing about how to do this; I don't know where the SRCdir or BLDdir are.

PS: It occurs to me that maybe nothing more need be done other than installing the libatlas libraries via apt-get. I will e-mail the author of refocus and ask.

---

