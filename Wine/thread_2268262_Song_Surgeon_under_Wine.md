---
title: "Song Surgeon under Wine"
date: 2015-03-07
forum: Wine
---

### Post by jared28 on 2015-03-07
Hi  I'm a little bit new to the whole linux and wine thing, and I'm trying to get it set up for a friend of mine. One of the programs he uses a lot is called Song Surgeon. It does advanced key changing and speed changing of music, among other things. He won't use an alternative program as he's already paid for this one. It's windows or mac only, and I installed it under wine. However, when I open it, it asks me if I'm a customer or demo version. I choose demo (I don't have his license key on hand), and it says something about an integrity check. Then it quits. I ran it in a terminal and here's what I got:  

err:module:import_dll Library gdiplus.dll (which is needed by L"C:\\Program Files\\Song Surgeon 4\\SongSurgeon4.exe") not found err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Song Surgeon 4\\SongSurgeon4.exe" failed, status c0000135 

Anyone know how to fix this?

---

### Post by Mark Phelps on 2015-03-09
> One of the programs he uses a lot is called Song Surgeon.

Then, you should have checked the WineHQ application compatibility page to see how well it runs.  Unfortunately, it's not listed -- meaning it has not been tested with the results entered into the database.  You are basically on your own to make this work -- an especially difficult situation.

Sorry, but as a long-time user of both Windows and Linux, my advice is unless the Windows app you want to use is rated Gold in the WineHQ website, you should really stay with Windows for using that app.

---

### Post by Bucky Ball on 2015-03-09
> **Mark Phelps said:**
> ... unless the Windows app you want to use is rated Gold in the WineHQ website, you should really stay with Windows for using that app.

Yes. Pity, as Audacity will do the things you mention (used by hobbyists and pros alike). Why are they wanting to switch?

---

### Post by MartyBuntu on 2015-03-13
> **Bucky Ball said:**
> ...Audacity...


One of the best and most useful applications of any operating system I've ever used **ever!**

---

