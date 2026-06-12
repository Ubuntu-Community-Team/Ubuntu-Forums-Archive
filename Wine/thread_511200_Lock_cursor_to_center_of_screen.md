---
title: "Lock cursor to center of screen?"
date: 2007-07-27
forum: Wine
---

### Post by noerrorsfound on 2007-07-27
I'm trying to play the game SWAT 4 using Wine, and it works perfectly except for [a bug that stops your mouse once it reaches the side of the game screen]("http://bugs.winehq.org/show_bug.cgi?id=6971"). Playing in fullscreen does not fix this, but I'm thinking if I could find an application to lock my cursor in the center of the screen, I would be able to look around completely in this game. The only problem is I need to be able to turn this off easily so I can continue using my mouse when I exit the game.

If anyone has some programming experience and can create an application with a hotkey to lock/unlock the mouse, that would be great!

This is the **only** bug keeping SWAT 4 from being completely playable.

**Edit:**
I do have "Allow DirectX apps to stop the mouse leaving their window" checked.

---

### Post by piepolitb on 2007-11-30
HI! how did you get swat works with wine? I just got an orrible message in a dialog box at half intro

```
SWAT Build Number: 31973

Access Violation caused General protection fault!

History: UGameEngine::Draw <- UWindowsViewport::Repaint <- UWindowsClient::Tick <- ClientTick <- UGameEngine::Tick <- UpdateWorld <- MainLoop->GenerateExtraCrashInfo [(GLevel: 'myLevel' PendingLevel: '(NULL)' NetMode: 'NM_Standalone'] <- MainLoop
```

could you help me?

---

### Post by cogadh on 2007-11-30
If you locked the cursor in the center of the screen, then you wouldn't be able to move. In games, movement actions taken with the mouse are technically cursor movements, so if you lock the cursor, you lock your movement. 

You can work around the bug by turning the mouse sensitivity in game up to a higher setting, but it won't work perfectly, i.e. the limit is still there, it will just take a lot more mouse movement to reach it.

Apparently the Wine devs do have a fix for the problem, its just not ready for general public consumption yet. Be patient, we will likely see it in one of the next few Wine releases.

---

### Post by piepolitb on 2007-12-02
great! it works! :guitar:

just upgrading wine this morning:lolflag:

hope this can help someone

---

