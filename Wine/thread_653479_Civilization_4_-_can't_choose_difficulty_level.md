---
title: "Civilization 4 - can't choose difficulty level"
date: 2007-12-29
forum: Wine
---

### Post by BaffledMollusc on 2007-12-29
I've been trying to play Civilization IV under Ubuntu 7.10 with an X800 graphics card, and every thing works apart from a few minor and one major issue.

The major issue is that I can't choose the difficulty level. When I play and am going through the "new game" choices, the screen switches directly from the "Choose World Size" screen to the "Choose Civilization" screen. The "Difficulty" and "Game Speed" screen is missing. Why this particular screen is missing when all the others are present baffles me. 

Anyone seen this before?

I'm using Wine 0.9.51, and have tried both the 1.61 and 1.74 patches for the game. Both have the same issue.

Further info if it's relevant: I'm using the native versions of d3dx9_26, msxml3 and msxml3r, using fbo rather than pbuffer, GLSL is disabled.

---

### Post by BaffledMollusc on 2007-12-30
I've found what appears to be the problem, and am posting the solution here in case others have the same problem.

I was wrong in my first post - the "Choose Difficulty" screen appears *after* the "Choose Civilization" screen. If I choose "Random Civ" I get the difficulty screen; choosing any specific Civ will lead to a white screen that presumably is the difficulty screen, but is now unreadable.

This appears to be because on the difficulty screen there is an animated model of the chosen leader's head, *unless* the "random civilization" option was chosen, in which case there's simply a non-animated place holder. It's odd that the leader's head breaks things at this place but nowhere else in the game, but there you are.

To get around this problem I set GLSL to "enabled" rather than "disabled" in the registry. This fixes the problem, although it causes the game to run choppily, so I found it best to save the game after I'd started playing and then set GLSL back to "disabled".

I'm guessing the issue is due to some combination of the X800 card and the binary drivers for it interacting strangely with the heads' skin shader for a particular lighting model.

---

