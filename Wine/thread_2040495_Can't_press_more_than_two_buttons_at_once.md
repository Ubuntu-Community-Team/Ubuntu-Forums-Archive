---
title: "Can't press more than two buttons at once"
date: 2012-08-11
forum: Wine
---

### Post by Stonecold1995 on 2012-08-11
When I'm playing a video game through Wine, I've noticed that I can't press any more than two buttons at once.  If three or more keys are depressed, they just won't be detected.  This is very annoying in games where have to press one button to shoot, another to move, and then a third for extra features like bombs that I need very quickly, because I have to let go of one of the other two to press it.  I'm specifically thinking of Touhou Project, which becomes a pain to play when I try to use a bomb to defend myself just to have the game "ignore" the button press because I already have two buttons pressed...

Is there any way to fix this?  I'm using Kubuntu 12.04 with Wine 1.5.10, btw.  **And this seems to happen with every program, not just games.**  Is this a known bug or do I have to edit a configuration file somewhere to allow me to press multiple keys?  Is there any work around?

I really need help with this, because I love video games but nearly all of them are unplayable with a two-button at once limit. ;_;

---

### Post by Arcanius on 2012-08-11
Are you sure that the specific combination of keys works on your keyboard? Most keyboards have a key rollover limitation, and therefore certain combinations of 3 keys or more won't register at a time.
Try to test this combination to make sure it isn't just a keyboard matrix "issue" as opposed to software. I don't recall ever having problems with key rollover in Wine, but I know that my keyboard will never bring such issues to the table.

---

### Post by Stonecold1995 on 2012-08-11
The combination that first gave me trouble was Shift+Z (prevented X from being pressed) or Z+up/down/left/right (prevented X from being pressed).  It also happens with other key combinations, but this is what I first noticed it with.

Do you know of any keyboard testing software (something that simply displays keys being pressed) for Windows so I could run it through Wine to see if any key combos work?  Kubuntu allows me to press many keys at once, so I know it's not a hardware issue or that specific key combination.

---

