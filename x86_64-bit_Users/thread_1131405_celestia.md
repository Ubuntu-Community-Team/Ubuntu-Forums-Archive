---
title: "celestia"
date: 2009-04-20
forum: x86 64-bit Users
---

### Post by sidious1741 on 2009-04-20
I'm running intrepid.  I tried out celestia and got some really weird problems.  It seems to work fine yet the display does some weird flashing.  It's hard to describe but to some up, celestia's display is wacky.  Any ideas?

---

### Post by Slim Odds on 2009-04-20
Is it the only app that's giving you problems?

Have you tried any others?

Try Stellarium... see if that works

---

### Post by jespdj on 2009-04-21
What graphics card do you have and what drivers are you using? Are you using a proprietary driver to get hardware 3D graphics acceleration support?

Do you have desktop effects (Compiz) enabled? Try disabling the desktop effects and see if it runs better; some 3D graphics programs don't work well when desktop effects are enabled.

---

### Post by Slim Odds on 2009-04-21
> **jespdj said:**
> Do you have desktop effects (Compiz) enabled? Try disabling the desktop effects and see if it runs better; some 3D graphics programs don't work well when desktop effects are enabled.

Celestia works fine with compiz, etc.

---

### Post by Thelasko on 2009-04-21
> **Slim Odds said:**
> Celestia works fine with compiz, etc.

That depends on the graphics card.

---

### Post by Slim Odds on 2009-04-21
> **Thelasko said:**
> That depends on the graphics card.

Perhaps, but if compiz is working properly, celestia should not pose any problems.

---

### Post by Thelasko on 2009-04-21
> **Slim Odds said:**
> Perhaps, but if compiz is working properly, celestia should not pose any problems.

Compiz is supposed to be disabled if it's incompatible with your graphics card.  If that's what you mean by "working properly" then you are correct.

The OP may have overridden this feature in Compiz and therefore caused problems.  I know my Intel 965 is only capable of the basic effects.  If I turn it up any higher there are problems similar to this.

---

### Post by sidious1741 on 2009-04-21
> **jespdj said:**
> What graphics card do you have and what drivers are you using? Are you using a proprietary driver to get hardware 3D graphics acceleration support?

Do you have desktop effects (Compiz) enabled? Try disabling the desktop effects and see if it runs better; some 3D graphics programs don't work well when desktop effects are enabled.

I had the default appearance setting (System>Preferences>Appearance>Visual Effects>Normal).  I tried changing that to normal and it works fine.  However though I am thankful that it finally works, I still wonder why I haven't found anyone else report the problem.  Anyway, As for if I've had other display problems, mednafen did some really weird stuff (even log me out when i closed it).  To get mednafen to work in the past I have done a sequence of logging on and off till it works.  I tried it now and it worked on the first try.

If anyone's still wondering about the graphics card, I'm using the default card built into a Compaq sr5310f which is a Intel GMA 950 Dynamic Video Memory Technology 3.0.  Other than that, will use normal graphics until Jaunty comes out in 2 DAYS!!! :D

Thanks a lot

---

### Post by sidious1741 on 2009-04-21
I meant for the Visual Effects, I changed it to none

---

### Post by Thelasko on 2009-04-22
I've heard the Intel drivers on Intrepid are buggy.  The ones for Hardy are better.  Let's hope they fix it for Jaunty.

---

