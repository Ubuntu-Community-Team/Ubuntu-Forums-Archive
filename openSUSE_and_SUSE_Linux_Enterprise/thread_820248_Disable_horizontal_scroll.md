---
title: "Disable horizontal scroll"
date: 2008-06-06
forum: openSUSE and SUSE Linux Enterprise
---

### Post by sayakb on 2008-06-06
Hello
I have just installed Suse on a HP nx6320
I guess almost everything is working fine, except for my touchpad.
My touchpad doesn't have a horizontal scroll. But somehow, Suse set the horizontal scrolling enabled. Mostly, I end up moving the finger in the horizontal scroll zone which works as "Back" if moved from right to left and "Forward" from left to right. So I keep on ending up firefox going to the previous pages I visited (like Im pressing back button). 
This is really getting irritating, I can't help it :(
Is there any solution for this?

---

### Post by kerry_s on 2008-06-06
type:
```
about:config
```

change->
```
mousewheel.horizscroll.withnokey.action     1
mousewheel.horizscroll.withnokey.numlines   1
```

---

### Post by sayakb on 2008-06-06
Seems to work good for firefox :D
Is there anything that can fix this globally/entirely in SuSe?

---

### Post by kerry_s on 2008-06-06
you want to disable it altogether right?

edit your /etc/X11/xorg.conf (must be edited as root)
put
Option "HorizEdgeScroll" "false"

in the synaptics section.

---

### Post by sayakb on 2008-06-06
Thanks. Though I also installed KSynaptics :)

---

