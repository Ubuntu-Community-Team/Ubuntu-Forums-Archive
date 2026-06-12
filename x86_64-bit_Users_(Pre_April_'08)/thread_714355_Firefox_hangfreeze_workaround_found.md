---
title: "Firefox hang/freeze workaround found"
date: 2008-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by masken on 2008-03-03
I have had problems with Firefox freezing/hanging since I started using Ubuntu and Linux for the first time during 2007.

The symptoms were that I had no control over the GNOME desktop, except that I could move the mouse pointer. I could provoke the system to freeze by fiddling with the search field at the top right corner of Firefox (entering and deleting characters quickly). Watching videos on youtube or browsing sites with lots of contents also had a significant probability of hanging the system. Nothing seems to be logged in the system logs when the freeze occurs.

**I discovered that starting Firefox with the X11 option [FONT="Courier New"]--sync[/FONT] seems to solve the problem.**


AMD Athlon64
ATI Radeon X800 graphics card.

---

### Post by soxs on 2008-03-04
WOW! Will give it a try! Thx
Edit: This seems to work, at least for me it does...

---

### Post by Yellow Pasque on 2008-03-04
Thank you for sharing.

---

### Post by Danyl on 2008-03-13
Can someone explain how you go about doing this, ie starting firefox with the x11 option?

---

### Post by chrism66 on 2008-03-14
I believe you can go to your firefox icon go into the properties and put the --sync at the end of the command line.

---

### Post by Danyl on 2008-03-14
Sweet. Thanks Chrism.

---

### Post by enchantedsky on 2008-03-18
Your solution seems to have made my Firefox more stable. So far, no random  crashes while on Youtube.

My question is this: What exactly does --sync do? How does it change Firefox? I did a Google search, but found no relevant information. Thanks.

---

### Post by tlink on 2008-03-18
I'm hoping this solves my random firefox lockups, but it only happens every other day.  Here's to hoping.

---

