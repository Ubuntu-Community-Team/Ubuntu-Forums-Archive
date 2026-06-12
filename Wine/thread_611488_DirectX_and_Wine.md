---
title: "DirectX and Wine"
date: 2007-11-13
forum: Wine
---

### Post by Cardamar on 2007-11-13
Alright. Here's the problem;
I hear everyone all over the place talking about changing the DirectX mode a program runs in. Well, I've looked all over the place and can't find how to do that. The problem here is that Team Fortress 2 seems to be running at DirectX level 6 on my computer. Needless to say, that's a bit outdated. All I need to know is how to set it to 9. Any help is a appreciated. (=
Thanks,
Cardamar~

---

### Post by cogadh on 2007-11-13
From within Steam, right-click on the game, select properties and click on the "Set launch options..." button (I don't have Steam open in front of me, so I may be a little off on what the button actually says). Enter "- dxlevel 90" in the field, without the quotes, and the game will be forced to run in DX 9 mode.

Alternatively, open a terminal, cd to Steam's install directory and run this:
```
wine steam.exe -applaunch 440 -dxlevel 90
```

---

