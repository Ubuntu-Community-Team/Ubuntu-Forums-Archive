---
title: "browser divx/media in swiftfox"
date: 2007-06-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by jmac19 on 2007-06-11
I'm running swiftweasel with both flash and java working thanks to the Kilz's script, i tired using the mplayer plugin so i could watch clips on [http://stage6.divx.com/](http://stage6.divx.com/) but it doesn't work keeps buffering but plays nothing i can use the media player connectivity plugin with the firefox from the repos but doesnt launch vlc with swiftweasel or any browsers from the script, though it does launch realplayer so i can use the bbc's site with swiftfox....any ideas or solutions ?

---

### Post by Kilz on 2007-06-12
> **jmac19 said:**
> I'm running swiftweasel with both flash and java working thanks to the Kilz's script, i tired using the mplayer plugin so i could watch clips on [http://stage6.divx.com/](http://stage6.divx.com/) but it doesn't work keeps buffering but plays nothing i can use the media player connectivity plugin with the firefox from the repos but doesnt launch vlc with swiftweasel or any browsers from the script, though it does launch realplayer so i can use the bbc's site with swiftfox....any ideas or solutions ?

You could remove the mplayer plugin from the /usr/lib32/firefox32/plugins folder and copy in the vlc plugins that should be in either /usr/lib/firefox/plugins or /usr/lib/mozilla/plugins. You could also try leaving the mplayer plugins there, but they might conflict with the vlc one.

---

### Post by jmac19 on 2007-06-12
thx for the reply already tried that cant get it to work, u know if any one has got the mplayer plugin working on 64bit?

---

