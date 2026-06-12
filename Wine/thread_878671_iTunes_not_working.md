---
title: "iTunes not working"
date: 2008-08-03
forum: Wine
---

### Post by /////// on 2008-08-03
Through WINE, I have installed iTunes 7.3.054. The installation went fine but after it, whenever I try to boot iTunes it just shows 'Loading iTunes' for a bit in the panel at the bottom then it disappears and nothing loads. When I try to load it through terminal I get this: 'err:module:attach_process_dlls "odbc32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\iTunes\\iTunes.exe" failed, status c0000005'
How do I make iTunes work?

---

### Post by billgoldberg on 2008-08-03
Itunes doesn't work on linux.

Not through wine nor natively.

You can take a look at this program: [el tunes]("http://el-tunes.com/"). (look for the torrent link in the bottom).

It will let you play your drm infected itunes songs.

If you just need itunes for putting songs on you ipod, take a look in applications -> add/remove.

Make sure you pick "all available packages" in the top and search for "ipod".

There are lots of tools that should come up to manage your ipod.

---

### Post by /////// on 2008-08-03
nvm, I got iTunes to load but it won't detect my iPod. Any ideas?

---

### Post by Swarms on 2008-08-03
Bill what are you on about? iTunes works for playing music, buying from the store etc.

> **/////// said:**
> nvm, I got iTunes to load but it won't detect my iPod. Any ideas?

But sadly there is no build in USB support in wine. Patches has been made but not added to the final program I think.

Try to search google for "wine + usb support" and post your progress in here. :)

---

### Post by hackins on 2008-08-04
> **/////// said:**
> nvm, I got iTunes to load...
how u did that, now i got the same issue=(( its my first wine running but another winxp apps are running okay=)
pls write what youve done to get through

---

### Post by /////// on 2008-08-05
> **hackins said:**
> how u did that, now i got the same issue=(( its my first wine running but another winxp apps are running okay=)
pls write what youve done to get through

Download winetricks (search it up in google) then use that to download the odbc32.dll. It should install by itself after download and after that your iTunes should be able to work

---

### Post by ooobuntooo on 2008-08-05
Try one of the iTunes alternatives for Linux!

---

### Post by blueamcat on 2008-08-05
I've actually kept a version of Windows for DualBoot just because my iPod isn't recognized in Ubuntu. At least last I checked. I've got the 32GB iPod Touch. But, I was thinking I might jailbreak it anyway. That's what my boyfriend did, and he can transfer stuff wirelessly now. Pretty sweet!

---

### Post by loboc on 2008-08-05
i used myfairtunes to strip my drm from my itunes albums  and switch over to amarok amarok has a store adn amazon has a linux download manager for their store as well

---

### Post by ooobuntooo on 2008-08-05
It was a bit painful leaving iTunes, but I had no choice!
I now use gtkpod because of the support for iPod album art.
I never used the iTunes store, I only use Limewire PRO.

Is it possible to manage an ipod in WMware?

---

### Post by /////// on 2008-08-06
> **ooobuntooo said:**
> 
Is it possible to manage an ipod in WMware?

Yes, I have successfully been using Itunes in VirtualBox under Windows XP. However, when I started using Virtual Box, it wouldn't detect my USB drives. I googled (or searched the forums can't remember which) for an answer and I found out that you have to add some group thing. Hope it works for you

---

### Post by ooobuntooo on 2008-08-07
> **/////// said:**
> Yes, I have successfully been using Itunes in VirtualBox under Windows XP. However, when I started using Virtual Box, it wouldn't detect my USB drives. I googled (or searched the forums can't remember which) for an answer and I found out that you have to add some group thing. Hope it works for you

Thanks, I can't live without iTunes!

---

