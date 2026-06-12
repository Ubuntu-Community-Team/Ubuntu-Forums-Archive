---
title: "Render 3D in Maple 17 using WINE"
date: 2013-10-31
forum: Wine
---

### Post by totallynuts on 2013-10-31
Hi folks,

I recently installed Maple 17 on my machine. Since there were some licensing issues due to an older version previosly installed I installed the Win 32bit version of Maple using wine. Everything works perfectly except whenever I try to generate a 3D plot I get the following error:

Maple is unable to render 3D graphics.
Your operating system, graphics, or video driver may require updating.
See "gldriver" in the help system for more information.
IllegalArgumentException
Width (0) and height (0) must be > 0

I don't have this problem when plotting 3D with Mathematica (NOT using wine however), so I think that this is related to the wine and its internals, which I am completely unfamiliar with. So any help regarding my issue would be greatly appreciated :)

I am using Ubuntu 13.04 and Wine 1.6.

Thank you very much!

Regards, 
nuts

---

### Post by Mark Phelps on 2013-10-31
The Maple website has a FAQ that addresses 3D issues: [http://www.maplesoft.com/support/faqs/detail.aspx?sid=79311]("http://www.maplesoft.com/support/faqs/detail.aspx?sid=79311")

You might have to run the actual linux version to get what you need.

---

