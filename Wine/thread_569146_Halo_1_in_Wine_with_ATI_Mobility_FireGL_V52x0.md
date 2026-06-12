---
title: "Halo 1 in Wine with ATI Mobility FireGL V52x0"
date: 2007-10-06
forum: Wine
---

### Post by 1212jtraceur on 2007-10-06
I'm trying to get Halo working. I've followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=486986"), but have had no luck.

I'm using wine 0.9.46, because it is the version that works the most. The splash screen shows for a split second, but then I get a mostly black screen with a little blue, all jagged (the menu, I think). Two warnings and one fatal error later, it tells me that my hardware is below the recommended spec, and that my driver "is know to have serious issues with the game" (I'm using fglrx).

It thinks my graphics card is a "16M ATI Rage 128", when it is actually either an ATI Mobility FireGL V5200 or anATI Mobility FireGL V5250 (I'm on a Thinkpad T60p).

I know ati cards/drivers don't play well with wine, but does anyone have any idea of how to fix this?

Thanks,
1212jtraceur

---

### Post by gwoodard on 2007-10-07
go to terminal to winecfg to Graphics and emulate virtual desktop

(Recommend 1024x768 )

---

### Post by 1212jtraceur on 2007-10-07
Ok, when I do that, I get a small window with the title "ERROR - failed to-" (I can't see the rest...) and the content text "Success" even before the Halo splash, which doesn't show up afterward.

---

### Post by gwoodard on 2007-10-08
Well there is the "Cedega" Route, Usually Wine has problems with Halo (or some newer game for PCs)

---

### Post by lordhebe on 2007-10-09
Cedega will probably have just as many problems (if not more so) for running Halo as wine, because it's not a supported game.

Besides your graphics card doesn't even meet the windows requirement, so the chances of getting it running through wine is very VERY thin, ATi card or not.

---

### Post by 1212jtraceur on 2007-10-09
Yeah, I don't really want to pay for Cedega, especially if it won't work...I don't think my card is too weak. I have a friend on Windows who runs it well with the same card. It's just incompatible with Wine, I think. Thanks for the help.

---

### Post by inf4my on 2007-12-10
I also have a t60p and cant get games to work on wine. The card definitely meets the specs for Halo 1 on windows. I can play all of orange box and other games at medium/high levels quite well.

---

### Post by aaabbb on 2007-12-10
Wine might be loading default drivers for all of one company's card series...I don't really know...

---

### Post by freakinjonathan on 2008-03-23
yeah i have halo for windows and gave it a try, but and the installer popped up and it said 
"could not load Pidgen.dll"

---

### Post by eragon100 on 2008-03-23
I played halo under wine a few months ago, it worked fine. But I have a GeForce 7 :)

And though I can't help you with this, you might have more succes posting this in gaming & leisure

---

