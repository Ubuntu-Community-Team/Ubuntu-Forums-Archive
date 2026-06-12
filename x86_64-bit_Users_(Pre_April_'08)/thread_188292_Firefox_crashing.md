---
title: "Firefox crashing"
date: 2006-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by sweeper on 2006-06-03
I finally got RealPlayer installed, but now Firefox (latest vesion) keeps crashing. It does it when I cick on downloads or try to listen to the BBC?

---

### Post by JoWilly on 2006-06-03
[QUOTE=sweeper]I finally got RealPlayer installed, but now Firefox (latest vesion) keeps crashing. It does it when I cick on downloads or try to listen to the BBC?[/QUOTE]

CLOSING this thread for you as you got it fixed now ;) 
[U]
THREAD CLOSED[/U]

---

### Post by henriquemaia on 2006-06-04
> **JoWilly]CLOSING this thread for you as you got it fixed now  said:**
> 
THREAD CLOSED[/U]

Is there something we are missing here? :)

If he found the solution, is good to post it here so others will know it in the future.  Just a thought...

---

### Post by sweeper on 2006-06-04
[QUOTE=henriquemaia]Is there something we are missing here? :)

If he found the solution, is good to post it here so others will know it in the future.  Just a thought...[/QUOTE]

The solution is in my 'Realplayer' thread.

---

### Post by JoWilly on 2006-06-04
[QUOTE=henriquemaia]Is there something we are missing here? :)

If he found the solution, is good to post it here so others will know it in the future.  Just a thought...[/QUOTE]

Yep, you are right. I forgot to post the fix. :) 

The problem was that the realplayer32 plugin was crashing firefox64 when real media was needed. The fix was to manually delete the 2 realplayer plugin files (nphelix) in /usr/lib/firefox/plugins.

---

### Post by henriquemaia on 2006-06-04
[quote=JoWilly]Yep, you are right. I forgot to post the fix. :) 

The problem was that the realplayer32 plugin was crashing firefox64 when real media was needed. The fix was to manually delete the 2 realplayer plugin files (nphelix) in /usr/lib/firefox/plugins.[/quote]

Great. Thanks. If you are reading this post, the solution is on the previous post, ;)

---

