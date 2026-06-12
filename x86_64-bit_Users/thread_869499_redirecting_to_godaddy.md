---
title: "redirecting to godaddy?"
date: 2008-07-24
forum: x86 64-bit Users
---

### Post by jamfix on 2008-07-24
im running the most updated 8.04 64 bit 
firefox keeps sending me to page parked free by godaddy or what ever it is
even when i open an email on yahoo item on ebay and so on 
truthfully im not the most advanced ubuntu user by can anyone 
tell me whats going on here?

---

### Post by Stunts on 2008-07-25
If you were in windows I'd say spyware.
May some firefox exploit?
Do you get the same issue if running a different browser? (say, epiphany)

```
 sudo apt-get install epiphany
```

How are you connected to the internet? Do you have a router? Do you use a LAN? or is it a direct connection?

You can also try to clear all firefox private data. (Tools -> Clear private data...)
Hope this helps.

---

### Post by Yellow Pasque on 2008-07-26
- What add-ons do you have?
- Enter about:config in the URL bar and do a search/filter for "godaddy"

---

### Post by ProbablyX on 2008-07-26
If you can't sort things out, you could try and move your Firefox settings to a backup folder, then see if it still happens.

If you close firefox, enable hidden folders in Nautilus/Dolphin and rename ".mozilla" to ".mozilla.bak"
**or** run in a terminal
> 
cd ~
mv .mozilla .mozilla.bak


Then start Firefox, and it will load without your settings. Did it work?

Afterwards, to get your bookmarks etc back, remove the new .mozilla folder and rename .mozilla.bak back to .mozilla
**or** with a terminal:
> 
cd ~
rm -r .mozilla
mv .mozilla.bak .mozilla


If you're not used to terminals I'd suggest to do it with the file manager, as explained above.

---

