---
title: "Team Fortress 2?"
date: 2008-05-26
forum: Wine
---

### Post by leodido on 2008-05-26
I could install steam and TF2 with no problem but when i launch the game that's what i get :

[IMG]http://i269.photobucket.com/albums/jj70/euphorik99/Screenshot-TeamFortress2.png[/IMG]

I can join a game but it lags a lot and i'm missing some part of the hud that are black

---

### Post by aoanla on 2008-05-26
Yes. If you'd looked at the AppDB entry for TF2, or searched this forum for topics, you'd know that this is because you're running in DirectX 9 mode, and for some reason, the shaders TF2 uses are currently broken in Wine.

You want to, in Steam, add "-dxlevel 81" to the Launch Options (in the Properties for Team Fortress 2), minus the quotes.

---

