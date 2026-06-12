---
title: "Wine Display Issues"
date: 2011-12-29
forum: Wine
---

### Post by cbanakis on 2011-12-29
Not too optimistic about getting help with this, but you never know.

I have an app that I am trying to run in wine.
It is extremely specialized industry software, so there is no known discussion about it.
The program is called Metrix(2.7.1) made by Lithotechnics.  [http://www.lithotechnics.com/](http://www.lithotechnics.com/)

Just for fun, I tried to install it on my Ubuntu computer at work, and much to my surprise, it seems to "technically" work perfect.

However, it is very difficult to use, because the screen (in the app) either goes black, or shows my wallpaper.

If I hover the mouse over buttons, they clear up, and if I shrink the app down to just the top tool bar, then expand, it seems to clear up the whole app.

But then once I click on something, the screen goes black again.

I have a similar problem with photoshop CS5, so I was thinking it there may be a fix for photoshop, that will also fix this.  Not sure if they are truly related though.

Are their any settings in wine that could possibly remedy this?

I already tried every combination of settings on the "Graphics" tab under Wine Configuration with no success.

I also have winetricks, but I'm not sure how or what to do with it.

Any ideas would be appreciated.

Thanks

---

### Post by cbanakis on 2012-01-06
any ideas?

---

### Post by philinux on 2012-01-06
Can't help but, moved to Wine forum.

---

### Post by cottfcfan on 2012-01-06
Could be a compiz issue.
Try running the program with compiz turned off.

---

### Post by cbanakis on 2012-01-06
Thanks.

I actually did look for a wine forum, but I didn't see one.

> **philinux said:**
> Can't help but, moved to Wine forum.

---

### Post by samigina on 2012-01-06
Run the software within a wine virtual desktop, you can configure it in the wine settings.

---

### Post by cbanakis on 2012-01-06
Excellent thought.

Works perfect now, but...
(No Compiz = Boring, awkward GUI)  :(

Any guesses on a specific Compiz setting that could be posing the problem, so I can just disable that?

Obviously, I can figure it out through a rigorous course of trial and error, but it would save me a ton of time if I had a starting point.

Thank you very much for your idea.

> **cottfcfan said:**
> Could be a compiz issue.
Try running the program with compiz turned off.

---

### Post by cottfcfan on 2012-01-07
What exactly is the problem?
Are you getting like shaded black boxes on your desktop?
Are you using an intel graphics card?
The reason i'm asking is I managed to fix my issue, but I don't want to recommend something to you, when your issue might be something different.

---

### Post by cbanakis on 2012-01-08
Thanks for the reply.

I am using an Intel Graphics card.

the issue is, the application window, is either solid black, or it sorta grabs a screen shot of my desktop, and fills the window with that.  (if that makes sense)

if I hover the mouse over buttons in the application window, the buttons clear up.

Same thing with lists from the file menu.

If I resize the application window, it seems to clear everything up, but once I do anything, it reverts back to the black overlay.

> **cottfcfan said:**
> What exactly is the problem?
Are you getting like shaded black boxes on your desktop?
Are you using an intel graphics card?
The reason i'm asking is I managed to fix my issue, but I don't want to recommend something to you, when your issue might be something different.

---

### Post by cottfcfan on 2012-01-08
Ok. Open up CCSM. Go to Animations, at the top click "close animation".
Then double click the middle option (should be fade).
A new window opens called edit, click the + sign, make sure "type" says Window Match. In "value" type Wine (note capital W) Tick the Invert Box then click "Add". Close CCSM and try your program again.

---

### Post by cbanakis on 2012-01-10
I think I see where you are going, and I like it.

This is basically to prevent certain effects from being active in wine applications?

I have customized compiz quite a bit though.

the options don't seem the same on my compiz, as in yours.
I have might have a newer/older version?

When I double click on the option, this is what I get...

--------------------
Close Effect 
[Burn]

Duration 
[120]

Window Match 
[(type=Menu | PopupMenu | DropdownMenu | Combo | Dialog | ModalDialog | Normal)]

Options
[ ]
--------------------

Then when I click on the +, I get...
--------------------
Type (Drop Down Menu \/)
<Window Class>
<Window Title>
<Window Name>
<Window ID>
<Window Role>
<Window Type>

Value
[ ] |Grab|

Relation (Drop Down Menu \/)
<And>
<Or>

Invert
(Checkbox)
--------------------

Hopefully, all the above nonsense helps you to help me.  :)

Is this something I should just do to all my Compiz options, just to be safe?

Thanks for your post

> **cottfcfan said:**
> Ok. Open up CCSM. Go to Animations, at the top click "close animation".
Then double click the middle option (should be fade).
A new window opens called edit, click the + sign, make sure "type" says Window Match. In "value" type Wine (note capital W) Tick the Invert Box then click "Add". Close CCSM and try your program again.

---

### Post by cottfcfan on 2012-01-11
That looks fine.
My instructions in the previous post still stand.
Just remember, this worked for me,it may not for you, but either way it shouldn't do any harm to try.

---

### Post by cbanakis on 2012-01-11
Thanks for all your help.

Looks like theres gonna be some trial and error here, but at least I know where to start now.

Thanks again.

> **cottfcfan said:**
> That looks fine.
My instructions in the previous post still stand.
Just remember, this worked for me,it may not for you, but either way it shouldn't do any harm to try.

---

### Post by cottfcfan on 2012-01-12
There shouldn't be a problem, I got the instructions from the Wine website, its simple enough, just follow exactly as I posted above, and you should be fine.

---

