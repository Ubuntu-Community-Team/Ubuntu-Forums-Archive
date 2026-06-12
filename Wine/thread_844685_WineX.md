---
title: "WineX"
date: 2008-06-29
forum: Wine
---

### Post by jarrhed on 2008-06-29
Ok so I wanted to compile winex because I want tosee if its any good and I go to cvs repository of winex  and it asks for a password and I couldnt find anything on a password anywhere. WineX was updated a month ago according to the cvs logs on the transgamangin website. Any help is appreciated

---

### Post by cogadh on 2008-06-30
[http://www.cedega.com/cvs/](http://www.cedega.com/cvs/)

Even if they have updated it, I still wouldn't bother with it. I've never heard of anyone finding it to be anywhere near as functional as Wine's own implementation of DirectX.

BTW - What made you think the code had been updated? I haven't looked through the whole thing yet, but the only thing that I have seen so far that has been updated within the last year was the license document.

---

### Post by jarrhed on 2008-06-30
It says here [http://lists.transgaming.org/pipermail/winex-cvs-logs/](http://lists.transgaming.org/pipermail/winex-cvs-logs/)
WineX was updated May 2008! So i thought it might be worth it to try it

---

### Post by cogadh on 2008-06-30
Look at the actual list of updated files (linked to from that page):
```
Modified Files:
	LICENSE configure.ac 
Log Message:
Import usp10 from WineHQ
```
All they did was update the license, modify some makefiles, then import more stuff taken from Wine. No real changes to speak of, or at least nothing that you can't already get by just using Wine.

---

