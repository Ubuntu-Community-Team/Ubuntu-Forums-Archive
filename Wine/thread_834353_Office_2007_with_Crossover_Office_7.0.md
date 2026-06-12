---
title: "Office 2007 with Crossover Office 7.0"
date: 2008-06-19
forum: Wine
---

### Post by chrisby on 2008-06-19
I tried the crossover office 7.0 demo today to see if there was any performance improvement over wine.  What a disappointment!

1. Powerpoint will now save as pptx and will do a slide show for more than 2 slides.

2. PowerPoint still will not render the creation of objects in real time. 
(even if you can get it to draw a line, you will have a black box over all of the slide while you drawing it)


3. The equation editor works but not well.  for example \pi_4 draw pi with the 4 in the middle of it instead of as a subscript.

4. PowerPoint crashed after 4 minutes of use.

This product seems slightly more usable then plain wine, but not $70 worth

What other bugs are you people finding with office 2007?

---

### Post by cogadh on 2008-06-19
You do realize that CrossOver is basically just Wine with a nice frontend and few application-specific tweaks, right? You are basically paying for that plus professional tech support and upgrades. Also, it's only $70 if you buy the Pro version (includes CX Games, multi-user support, and enterprise enhancements). For a regular single user, you probably just want the Standard version, which is only $40.

That being said, both CrossOver and Wine get basically the same results when running Office 2007:
[http://appdb.winehq.org/appview.php?iVersionId=4992](http://appdb.winehq.org/appview.php?iVersionId=4992)

---

### Post by Kinst on 2008-06-19
Wow, you can do equation editor?

---

### Post by chrisby on 2008-06-19
cogadh:

> **chrisby said:**
> 

This product seems slightly more usable then plain wine, but not $70 worth

What other bugs are you people finding with office 2007?


Obviously if I stated that it is only slightly more usable than plain wine, I realize that it is a front end for wine.  Thats why this is posted in the wine section.  Through the post it should also be obvious that I have it installed with plain wine.  Yes, it bottles applications for you, configures dll overrides, and installs necessary pieces to help applications work better.

If you installed office 2007 with crossover 7, please leave a comment with bugs you have found, otherwise there really isn't a point to your post.

---

### Post by Lesterchakyn on 2008-09-24
> **Kinst said:**
> Wow, you can do equation editor?

[http://www.codeweavers.com/support/forums/general/?t=26;mhl=40153;msg=40153#msg40153](http://www.codeweavers.com/support/forums/general/?t=26;mhl=40153;msg=40153#msg40153)

Unfortunately, I was searching all over the place for this, and as it seems, OLE functionality (needed for eqn editor and objects in general) is currently broken in Crossover (and it seems in the wine tree in general).

This has made me stop using Office 2007 on Wine and return to Virtualbox and Windows :(

---

### Post by chrisby on 2008-09-24
> **Lesterchakyn said:**
> [http://www.codeweavers.com/support/forums/general/?t=26;mhl=40153;msg=40153#msg40153](http://www.codeweavers.com/support/forums/general/?t=26;mhl=40153;msg=40153#msg40153)

Unfortunately, I was searching all over the place for this, and as it seems, OLE functionality (needed for eqn editor and objects in general) is currently broken in Crossover (and it seems in the wine tree in general).

This has made me stop using Office 2007 on Wine and return to Virtualbox and Windows :(

I gave up as well and went back to vmware.  The crossover method just doesn't provide enough functionality, and office 2007 will probably be dated by the time they get things working right.:(

---

