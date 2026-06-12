---
title: "Wrong Custom Loading Pointer in Synaptic"
date: 2009-04-30
forum: x86 64-bit Users
---

### Post by TheGreen-ishKnight on 2009-04-30
I'm using a custom pointer, Obsidian, which I found on gnome-look.org. This cursor theme has its own loading pointer, which looks fine in all programs except Synaptic. For some reason the loading cursor in Synaptic looks like a giant version of the default Ubuntu loading circle pointer.

I had this problem in Hardy (x86 and x86_64), Intrepid (x86_64), and now a clean install of Jaunty (x86_64). I installed the Obsidian pointer theme by accessing "Appearance" in the System menu, clicking the Install button, and selecting the theme archive. I've tried a number of other cursor themes and they all have the same problem.

Has anyone else experienced this? Or found a solution?

---

### Post by rossmoore on 2009-07-09
I have the same problem. I've always just ignored it, but it is weird. Let me know if you find a solution!

---

### Post by Rog-Mahal on 2009-07-09
Same problem here, and it only happens in Synaptic. Does it warrant a bug report?

---

### Post by rossmoore on 2009-07-09
Probably - would you know where/how to file it? I have a launchpad account, butI don't really understand the bug filing mechanism.
And this discussion is filed in x86 64-bit, but I'm running 32-bit so it's not related to that.

---

### Post by Nikos.Alexandris on 2009-11-01
> **rossmoore said:**
> Probably - would you know where/how to file it? I have a launchpad account, butI don't really understand the bug filing mechanism.
And this discussion is filed in x86 64-bit, but I'm running 32-bit so it's not related to that.

Same problem here since so long! I think I know the reason: if you go in **System** > **Preferences** > **Appearance** > **Theme** (tab) > **Customize** > **Pointer** and have **Obsidian** selected you will notice the **Size** field below which, for some reason, can't be set to small (actually it can't to be set to anything, it's disabled).

That's all I think... :-?

---

