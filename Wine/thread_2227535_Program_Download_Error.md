---
title: "Program Download Error"
date: 2014-06-02
forum: Wine
---

### Post by gordon99 on 2014-06-02
I am trying to install a program (Pairs Scorer) on my D: drive (NTFS) via Wine. The launch icon is showing up on my data drive OK drive but the following error message comes up when I click it - Details: Failed to change to directory '/home/gordon/.wine/dosdevices/d:/media/gordon/_data/PairsScorer' (No such file or directory). i am dual booting Ubuntu 14.04 and Windows 7. Have I configured Wine incorrectly or made some other elementary error? By the way, don't get any funny ideas. Pairs Scorer is about finding the winner in the game of bridge and not about having ones way with the opposite ( or same) sex.

---

### Post by Vladlenin5000 on 2014-06-02
I'm not sure but I think it isn't possible to install outside the folder WINE allocates inside your /home. Other drives/partitions can be made visible for WINE but they'll all appear as Windows "network drives". Plus, the drive letter will be different.

Now, some questions... First and foremost why <snip> are you complicating things so much? You already have Windows. Install your Windows programs in Windows!!
However, if for some weird/mystical/whatever reason you want it installed also in Ubuntu, why add an additional layer of difficulty by deviating from the default C:\Programs\... (whatever...) options in the software installer? You're already installing it in an emulated environment. Is it because of the "security privileges in recent Windows releases" they mention in the software's page? It doesn't affect you because the emulated environment is more like XP, not Vista or Seven. Follow their advice if you're installing it in your Windows Seven only. Plus, this is a VERY BAD EXCUSE for BAD CODE (I can't stress it enough).

Now, the bad news... You're on your own.Pairs Scorer hasn't been tested on WINE yet. There are good chances it won't work at all even if it "install" without errors.



PS - I strongly recommend you edit your thread's title. "Program download error" says nothing about your actual problem. As a matter of fact it has nothing to do with downloads and as such is misleading.

---

### Post by deadflowr on 2014-06-02
Moved to Wine Sub-forum

---

### Post by gordon99 on 2014-06-02
Well Vladlenin5000, I suppose you might also ask why I bothered to install Ubuntu when I already have wonderful Windows. Well the answer to that question is that i was told that Linux OSs were better in many ways than Windows and I wanted to see for myself. Now, to answer the question you so forceably asked. I thought that by moving the programs I use regularly in Windows to Ubuntu I would get a better feel for the new OS. If Pairs Scorer doesn't work in Ubuntu so be it. As far as the threads title is concerned I suppose I could have titled it "Pairs Scorer and Linux" but would this encourage a greater response? I doubt it. Thanks for your interest and information anyway.

---

### Post by Vladlenin5000 on 2014-06-02
Linux is indeed better in many ways, probably a lot more than you currently think. However it isn't a super OS capable of running software coded for other OSs. Emulators exist but they have limitations. WINE lists and classifies according to their performance several Windows software that can run using wine. I suggest you check it first to know if it's at least worth to try. If already listed as not working or working badly don't waste your time.

"Pairs Scorer in WINE" would be a more appropriate title and certainly would encourage a greater response although most of the replies would probably be "forget it". Anyway, now that you know you don't need to change the "drive" where it'll be installed you can try running the installer via WINE and note down any errors. Then - and only then - somebody *might* be able to help you.

---

