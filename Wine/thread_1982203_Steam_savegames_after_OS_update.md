---
title: "Steam savegames after OS update"
date: 2012-05-18
forum: Wine
---

### Post by ahso4271 on 2012-05-18
Hi 
I've played Rage on Ubuntu 10.04 and ~/.wine is a softlink to another disc. 
Now after mounting, softlinking that very same .wine on my new 12.04 steam starts but shows no saved games. 
What to do? Thanks

---

### Post by cogadh on 2012-05-18
Where was "My Documents" linked to in Wine? By default, it is mapped to your home directory and if you overwrote your home directory in your 12.04 upgrade, you probably lost those saved games. Many games use the "My Games" folder or create their own folder in "My Documents" to store saved games.

---

