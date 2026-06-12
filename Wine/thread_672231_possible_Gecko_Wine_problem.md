---
title: "possible Gecko Wine problem?"
date: 2008-01-19
forum: Wine
---

### Post by wog on 2008-01-19
I have wine 0.9.53 and Gutsy.

I did ```
wine iexplore
``` and ended up with a big window filled with a big expanse of white and no way of knowing if it was done installing. After about five minutes I closed the window and tried it again, getting the same big white window.

Is Gecko installed right? What am I really supposed to be seeing?

---

### Post by luisromangz on 2008-01-19
I recommend you to use IE4Lin, it automagically download and install IExplorer and configures it.

By the way, I don't think IExplorer uses gecko while running in Wine, because then it would show webpages the way Firefox does, and it doesn't (which is why IE4Lin is useful to test  the crappiest browser to us webdevelopers).

---

### Post by PhilOSparta on 2008-01-19
> I did ```
wine iexplore
``` and ended up with a big window filled with a big expanse of white and no way of knowing if it was done installing. After about five minutes I closed the window and tried it again, getting the same big white window.

Is Gecko installed right? What am I really supposed to be seeing?

I just got wine installed and then did the same thing with the same result.  After much searching etc.  I found that it's a "one shot" application.

Try this from a terminal:    wine  iexplore.exe  [http://ubuntuforums.org](http://ubuntuforums.org)
That worked.  If you want another URL, you have to exit out and give it the one shot again.

---

### Post by wog on 2008-01-19
> **PhilOSparta said:**
> I just got wine installed and then did the same thing with the same result.  After much searching etc.  I found that it's a "one shot" application.

Try this from a terminal:    wine  iexplore.exe  [http://ubuntuforums.org](http://ubuntuforums.org)
That worked.  If you want another URL, you have to exit out and give it the one shot again.

So it** is** installed. I wasn't sure.

Thank you! :)

---

### Post by wog on 2008-01-19
> **luisromangz said:**
> I recommend you to use IE4Lin, it automagically download and install IExplorer and configures it.

By the way, I don't think IExplorer uses gecko while running in Wine, because then it would show webpages the way Firefox does, and it doesn't (which is why IE4Lin is useful to test  the crappiest browser to us webdevelopers).

My understanding is that there's a whole raft of things that won't run unless IE is installed somewhere, so I was just trying to install it. I'm not sure I actually need the whole thing, which is what I assume ie4lin is, right?

---

