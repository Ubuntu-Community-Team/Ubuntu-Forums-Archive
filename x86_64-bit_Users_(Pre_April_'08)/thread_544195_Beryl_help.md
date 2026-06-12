---
title: "Beryl help"
date: 2007-09-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by DaGGer on 2007-09-06
Lets see I've posted about beryl not working before and well I've done what I can about it.  Now i've entered these commands:

```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

and

```
Beryl
```

both went well, it said that I passed everything but still it locks up every so often. i haven't found a one thing that sets it off.  Some times it will last a few days without anything happening and then some times it will happen a few minutes after I turn it on. i really like it and i want to get it working without having it crash on me.

---

### Post by afonic on 2007-09-06
Well I think Beryl is supposed to crash as it is still alpha. I had various problems when using it. However with just Compiz from Ubuntu everything worked fine.

Compiz Fusion in the other hand, seems fine. :)

---

### Post by DaGGer on 2007-09-06
ok well I've tried to install that before but I had problems. Can you tell me how to install it or a how to on it.

---

### Post by John.Michael.Kane on 2007-09-06
> **DaGGer said:**
> ok well I've tried to install that before but I had problems. Can you tell me how to install it or a how to on it.

You can try this, if your still looking to install beryl. 

Step 1
Make sure your gpu drivers are properly installed.

Step 2
```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

Step 3
```
sudo aptitude install beryl emerald-themes beryl-manager
```

Step 4
reboot the machine, and log back in.

Step 5
Press alt+f2, and type beryl-manager into the box that shows up.

Step 6 Work around should the title bars be missing
Right click on Beryl Manager>Advanced Beryl Options>Rendering Path>Copy.

---

### Post by DaGGer on 2007-09-06
Well no I've got beryl installed and emerald installed. the thing is that when I run beryl for it will freeze the system. I can still listen to anything playing, watch anything thats playing. What ever is running before it freezes still plays but I can't  click on anything and I can't ctrl+alt+backspace to restart. BUt the clock keeps moving like nothing happened.

---

### Post by DaGGer on 2007-09-07
anyone, I'd like to get something working. i'll try compiz or compiz fusion. Anything really.

---

### Post by John.Michael.Kane on 2007-09-07
> **DaGGer said:**
> anyone, I'd like to get something working. i'll try compiz or compiz fusion. Anything really.

Have you tried what I posted? If that has not helped I would begin debugging the problem backwards. Starting with removing beryl compiz, As well as the gpu driver your using, and making sure the system it self is stable, and does not lockup.

Next I would reinstall the gpu driver, and recheck system stability, If the system checks out ok without having beryl/compiz/etc installed then move to reinstalling beryl.

Then proceed with rechecking the system again.

Another item worth checking that is sometimes known to cause system issues are your memory. You may want to memtest the ram overnight, and make sure there is no issue there.

---

### Post by DaGGer on 2007-09-07
Ok well I just did what you said to do in the other post. its running so far. I'll let you know if anything happens. Hopfully this works. Well thanks for your help. I know its not my graphics or my computer. its Beryl not working with anything else thats the problem.

---

### Post by DaGGer on 2007-09-07
well it still locked up just like before.

---

