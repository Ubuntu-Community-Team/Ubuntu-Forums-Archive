---
title: "Wine program disappears from Unity launcher"
date: 2012-05-14
forum: Wine
---

### Post by kblood on 2012-05-14
Hello,

I am running Ubuntu 12.04 with Unity, and Wine 1.5 from the PPA. On my desktop machine, when I launch a Windows program using Wine, the Wine icon appears briefly on the Unity Launcher, and then disappears. It also doesn't show in the list of programs when I use Alt-Tab.

This problem doesn't happen in a different machine.

Does anyone have any idea on how to fix this? Anyone has this problem?
Google, AskUbuntu and UbuntuForums show me no results, but maybe I missed it.

Thanks.

---

### Post by Butthead on 2012-05-15
I wonder if this is directly related to the problems I'm having With Wine 1.5.3?

I do have a Wine icon in the startup menu, but none of the game icons (Unreal Tournament G.O.T.Y.) show up for me in the sub-menus (they show up as a blank piece of paper with a question mark overlayed on it). :confused:

The game does start and run for me though, so it's not completely hopeless. :-k

---

### Post by kblood on 2012-05-15
I don't think it's related. My problem was that the Wine icon disappears from the launcher, so if I minimize the window, I can't go back to that program in any way.

I deleted my ~/.wine folder and all the wine files from ~/.local/share/applications/, reinstalled the Windows program that I needed, and now it works fine, so I guess this is "solved".

---

### Post by Butthead on 2012-05-16
Funny, my missing game icons started slowly appearing by themselves in the Wine sub-menu too? :confused:

Maybe if I just wait long enough, they'll all eventually show up. :P

---

