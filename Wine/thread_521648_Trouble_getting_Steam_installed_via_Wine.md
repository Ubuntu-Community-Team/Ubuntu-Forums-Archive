---
title: "Trouble getting Steam installed via Wine"
date: 2007-08-09
forum: Wine
---

### Post by Nexus... on 2007-08-09
Well I can successfully install Steam no problem but when it get up to 26% it says "You may only have one copy of Steam open" the only button to press is "ok" I press that and it closes it.....

Any help is appreciated.

---

### Post by nickajeglin on 2007-08-10
I have the exact same problem. Stupid me didn't see this thread so I started a new one for it. ](*,)

---

### Post by Daveth on 2007-08-10
look in Section 7 Troubleshooting of this guide:

[http://www.linuxnewsblog.com/2007/07/steam-half-life-half-life-2-counter.html](http://www.linuxnewsblog.com/2007/07/steam-half-life-half-life-2-counter.html)

points to a sharing violation, with an alleged fix

---

### Post by cogadh on 2007-08-10
With "alleged" being the key word. That fix has never worked for me, I am only able to get past the 26% error by copying the Steam install off of my Windows partition, then deleting the ClientRegistry.blob file and starting Steam. It runs perfectly normally after that.

---

### Post by nickajeglin on 2007-08-10
try this:

1. Completely uninstall wine and delete .wine directory

2.Reinstall wine, reinstall steam with the newest version from their site.

3. Try it, it'll stick at 26%

4. Do "alleged" fix: that thing with steamtemp.exe it'll make your Steam.exe disappear. 

5. do: "wine start SteamInstall.msi" again and select repair when it asks.

It worked for me.

---

### Post by cogadh on 2007-08-10
I don't know that the uninstall/reinstall of Wine is really necessary, especially if you already have the latest Wine. Just deleting the .wine driectory destroys all traces of the previous Steam install, but for someone like me who already has a half dozen other games already installed and running, it would proabably be better to use WINEPREFIXCREATE to make a second .wine type directory just for Steam. Other than that, good fix! :)

---

### Post by nickajeglin on 2007-08-10
I just came over from windows like three days ago, so I'm sort of stumbling my way around. I just posted exactly what I did because I really don't know what exactly it is that I did. :)

---

