---
title: "Trouble understanding: Keyboard layout"
date: 2006-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by tactus on 2006-05-27
Hi, my first post here.

I've been a Linux lurker for a long time, tested different distros etc, but I am mainly OS X user at the moment. Now here is the deal.

I can't figure out how to properly set up the norwegian keyboard on my PowerBook 12" in Ubuntu. In YDL it was all plug and play. Maybe I had to pick my language or whatever thought. In the latest Suse, all I had to do was to start YaST and pick the correct layout there and it worked correctly everywhere. Now in Ubuntu (running dapper rc at the moment) only "Generic pc-105 (int) PC" is "complete", meaning I can get access to the basic characters I need and I can pick my no-existant windows key as third-level-chooser. But ofcourse the layout is all wrong. If I pick the "Macintosh" layout, some characters slip into the right keys but then I can't switch between consoles (ctrl+alt+f#), third-level choosers doesn't work, and I don't know what.

The macintosh layout seems to be broken. I am currently in dapper, but it was the same back when I tested Ubuntu 5.10.

So what am I missing here about setting up keyboard layout in Ubuntu? What is the official steps? :-k

Thanks a million.

---

### Post by Rxke on 2006-05-27
For international users, keyboard layout for ppc is utterly, completely absolutely broken. Don't start me about it.

For example: I'm Belgian, but have to choose the French layout after install (they're both the same in the flemish talking part, but Ubuntu chooses something...Weird, so the @ key isn't where it belongs etc.)

Now when I change that so it works, I can't even use my alt- keys anymore, grrrrr...

And if you know pipe symbol and straight brackets, squiggly brackets are all under the alt-combination keys, you understand I do A LOT of copy/pasteing (luckily the ctrl key works, sigh...)

The weird thing is, for some people it works 100%, for some not... So bugreports always get reactions like 'for me it works, are you sure you chose the right layout during install?"
yesssss I did, aaarh! ;)

---

### Post by tactus on 2006-05-28
Thanks for the feedback. I guess this means I am not alone with this issue.

A couple of questions remainds:

1) Where do I fill the bug?

2) I am not saying I will, but say you want to fix this on your own, where do you find resources about how keyboard layouts works in Ubuntu?

----

One other strange thing I am noticing, maybe you know something about this. Mac keyboards traditionally have the alt/option key swapped with the windows(?)/command key (at least the ones I've used). I am trying to swap these so the PC layout work better with my PowerBook keyboard. So I did this:
```
 xmodmap -pke > .xmodmaprc
```
to create a preference file.
I then used xev to find the right key nummer, and swapped the option and command key like this:
> !keycode  64 = Alt_L Meta_L
keycode 64 = ISO_Level3_Shift
and this
> !keycode 115 = ISO_Level3_Shift
keycode  115 = Alt_L Meta_L
Everything looks fine doesn't it? But now my thirdlevel key died! What is up with that? :-k

This is all very confusing.

---

