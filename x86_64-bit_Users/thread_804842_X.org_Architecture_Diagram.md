---
title: "X.org Architecture Diagram"
date: 2008-05-23
forum: x86 64-bit Users
---

### Post by millie95 on 2008-05-23
I've been somewhat confused by the acronyms and architecture of the Xorg server for years, so I've put together a map (PDF, zipped) of what I understanding of it. Interested in any comments or feedback.

---

### Post by Vadi on 2008-05-23
Wow, thank you. Extremely helpful.

---

### Post by millie95 on 2008-05-24
Thanks for the feedback. Here is a link to version 2, which covers a bit more topics.

[http://stashbox.org/122385/xorg%20architecture2.pdf](http://stashbox.org/122385/xorg%20architecture2.pdf)

:guitar:

---

### Post by Vadi on 2008-05-24
If it's no secret, what did you use to create the graph?

---

### Post by lefevre00 on 2008-05-24
As long as I can recall, EXA was introduce by Zack Rusin, former Trolltech employee.

[http://en.wikipedia.org/wiki/EXA](http://en.wikipedia.org/wiki/EXA) .

He actually work on Gallium 3D for Tungsten Graphic, and pushed another acceleration achitecture named Glucose ([http://zrusin.blogspot.com/2006/08/glucose-and-graphics.html](http://zrusin.blogspot.com/2006/08/glucose-and-graphics.html)) that other at 
Tungsten Graphic found interesting (mean : contribute code).

Keith Packard created Xrandr (1.1, 1.2 and actually working on 1.3)

---

### Post by chrisccoulson on 2008-05-24
You must have put a lot of time in to this, but I'm not going to pretent I understand it ;)

---

### Post by millie95 on 2008-05-24
> **Vadi said:**
> If it's no secret, what did you use to create the graph?

Cmap Tools, from [http://cmap.ihmc.us/](http://cmap.ihmc.us/)

---

### Post by dupe576 on 2009-05-16
Very cool.  I've been spending some time this weekend trying to understand some of these concepts.  I'm still confused but this is nice and helps a bit.

---

### Post by vincen on 2009-07-23
May I ask you where have you found the documentation for the topics you covered (very effectively) in your graph?

Thanks

---

### Post by markbuntu on 2009-07-25
That is very cool and very enlightening.

It makes me wonder why the compiz will not run on latest ati driver (9.7) when xinerama is used for multiple monitors on multiple gpus (randr1.2 is currently incapable of this task).

The offscreen pixmap capability does not seem to be compromised. Perhaps it is compiz looking for randr but finding xinerama and not knowing what to do. But that cannot be since the big desktop mode also disables randr, at least it did with the previous driver and that did not effect compiz.....but ati claims to have fixed some randr problems with his release....so maybe the driver is somehow losing the composite extensions when it switches to xinerama but the Xorg.0.log says they are loaded and offscreen rendering space is available...or maybe compiz is not seeing them anymore....

Hmmm....

So many questions are now ponderable when viewing these charts.

kudos to you millie95

---

### Post by For The People on 2009-07-26
Wow man! This is really amazing.... I'm a visual learner so this really helps a lot...

---

