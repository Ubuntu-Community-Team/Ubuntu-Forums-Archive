---
title: "Problems installing WINE from PPA"
date: 2014-03-28
forum: Wine
---

### Post by paul116 on 2014-03-28
Hello everyone,

I'm using Ubuntu and Firefox, and am trying install Wine.

First, I added the WineHQ PPA Repository, and this is what I see in my Ubuntu Software Center (my apologies that my screenshots are so tiny; I don't know how to make them bigger!) :[SIZE=2]
[ATTACH=CONFIG]251523[/ATTACH][/SIZE]

Then I clicked on the "apt://Wine_1.6" link, and this is what I got:

[ATTACH=CONFIG]251524[/ATTACH]

Finally, I clicked on "Choose" and got this:

[ATTACH=CONFIG]251525[/ATTACH]

So, now I'm stuck.  I believe I'm trying to find Firefox, right?  Where do I go from here?

Many thanks for your assistance!

---

### Post by Kris_Spencer on 2014-03-28
Since you have the repo in there, it's probably easier to just use the  terminal. Don't worry, it's not so bad and you only have to do it once.  Copy paste this:

sudo apt-get update && sudo apt-get install wine1.6

---

