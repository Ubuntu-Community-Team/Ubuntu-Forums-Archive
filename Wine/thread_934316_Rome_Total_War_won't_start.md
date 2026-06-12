---
title: "Rome: Total War won't start"
date: 2008-09-30
forum: Wine
---

### Post by ifflejink on 2008-09-30
So, I installed Rome: Total War, and attempted to play it, only to have the game not start and give me the following error message in the terminal:

```
system.reg is not a valid registry file
userdef.reg is not a valid registry file
user.reg is not a valid registry file
fixme:service:QueryServiceObjectSecurity 0x133e48 4 0x32ed74 512 0x32f184 - semi-stub
fixme:service:SetServiceObjectSecurity 0x133e48 4 0x32ef74
err:service:service_send_control service protocol error - failed to read pipe r = 0  count = 0!

```

It still happens, even after upgrading the game to the latest patch, 1.5. Can anyone help me out here?

---

### Post by geezerone on 2008-09-30
I thought the 1.5 patch was buggy.

I would be interested to know how you installed it and if you installed the windows format app, gamespy and direct x 9 (the latter shows as missing DLL) ?

When I start it shows missing animations?

---

### Post by ifflejink on 2008-09-30
The game doesn't start at all, actually. There isn't even an error message displayed, just those terminal results.

But, no, I did not install the Windows format app (I don't think), Direct X 9 was already on the computer, and I didn't install Gamespy. I could try reinstalling Direct X.

---

### Post by geezerone on 2008-10-01
I tried on a different PC and doesn't start for me. Errors are relating to D3D graphics. 

Gonna use Windows as trying to get this to work is like flogging a dead horse. Wine is a nice idea but too flaky to be relied upon.

---

