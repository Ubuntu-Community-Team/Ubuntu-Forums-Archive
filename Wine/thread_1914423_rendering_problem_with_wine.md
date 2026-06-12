---
title: "rendering problem with wine"
date: 2012-01-24
forum: Wine
---

### Post by 5PUTN|K on 2012-01-24
I'm trying to get a game running on wine and I think there is a problem with directx
I did all that was written [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19203") but when I launch the game the characters do not render at all, there is no one just a shadow on the ground(everything else works perfectly and it feels like it's running faster than it runs on windows)
then, to see whats wrong i ran the game in the terminal with this:
```
wine "/home/deniz/.wine/dosdevices/c:/Program Files/Cryptic Studios/Star Trek Online.exe"
```
this time nothing renders properly but you can at least see the characters even if they aren't rendered properly  and the terminal says:
```
err:d3d:wined3d_event_query_test Event query created despite lack of GL support
err:d3d:wined3d_event_query_ops_get_data The GL event query failed, returning D3DERR_INVALIDCALL
```
a friend told me that compiz sometimes causes problems like this because it disables direct rendering, so i checked it
```
deniz@deniz-laptop:~$ glxinfo | grep rendering
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
```
I deleted compiz completely and got it to say yes but nothing changed
any ideas??

---

### Post by thatguruguy on 2012-01-25
You need to provide more information.  For instance, you need to tell us the version of Ubuntu you're running, the graphics hardware you have, and whether you have the proper proprietary drivers installed for your graphics hardware.

---

