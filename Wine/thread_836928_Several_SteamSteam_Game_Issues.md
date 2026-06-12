---
title: "Several Steam/Steam Game Issues"
date: 2008-06-22
forum: Wine
---

### Post by V0X on 2008-06-22
I have a few issues running Steam and Steam Games with Wine. I'm running Wine 1.0 on Ubuntu Hardy 8.04. Here are my problems in the order they appear.

[LIST=1]
[*]When I first log in, only one or two of my games appear in the My Games list. After around thirty seconds all my other games appear at once.
[*]If I try to play one of the games that is there initially, I get an error message saying I don't have permission to play that game. If I try to play the game after all the others have loaded, I can play it fine.
[*]Sometimes I get an error telling me the game is not available or that the registry is in use by another process.
[*]During gameplay in Source games, unless I add the launch option: ```
-dxlevel 81
``` I get black squares where the health and ammunition should appear.
[/LIST]

Please help!

Other info: I have a nVidia GeForce 8800 GTS with the most recent drivers installed through ENVY.

---

### Post by Void1106 on 2008-09-20
i get the same thing sometimes. i crash because of an explosion in garry's mod and it screws me over.

---

### Post by aoanla on 2008-09-21
1. Steam is just slow at this for some reason. Just give it 30 seconds, yeah?

2. See 1. I don't think there's a way to improve this. (I'm not actually sure it's Wine's fault, either - Steam can be a bit slow on Windows systems, too.)

3. Yeah. That's Steam, too. (There's an entry in the Steam tech support thing about it, as it happens on Windows machines, too.)

4. This, on the other hand, is Wine's fault. The Wine DX9 stuff has issues with Source engine games for some reason. Apparently, some people have had success with the procedure for copying over certain Windows DirectX libraries to Wine, but I've never done that. Most of us just use -dxlevel 81 .

---

