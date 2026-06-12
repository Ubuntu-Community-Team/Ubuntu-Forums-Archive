---
title: "can't remove wine-0.9.49"
date: 2008-03-11
forum: Wine
---

### Post by emu5088 on 2008-03-11
hi,
    I have removed wine using the package manager and also removed it in the terminal to make sure it was completely gone (using sudo apt-get remove) and even deleted the .wine folder. when I try to remove it in terminal, i get a message saying there is no application to remove, so it all seemed well.
    Well, when i type "wine --version" it says "wine-0.9.49" (i thought i removed it!?) Perplexed, i installed the newest version using the package manager. and when i checked the version again, it still says it's version 0.9.49. It seems no matter what i do, i still have version 9.49. Any help on how to get rid of this and get the newest version would be appreciated. I've tried purging it and updating it too, as was suggested in other forums. No Luck. I'm using Gusty Ubuntu.
-emu5088

---

### Post by insineratehymn on 2008-03-11
Is there anything you need to autoremove?

sudo apt-get autoremove

You can find out where the actual executable you are using is located by typing:

which wine

That will echo the absolute path of the "wine" command, or whatever one it can find in its path.

Finally, after you know where that is, update your indexing database:

sudo updatedb

Then locate all instances of wine:

locate wine

Delete everything you see that involves wine. (Please be careful here.)

Then install wine, either with the ones in aptitude (which should install 0.9.57) or go get the actual source from [http://www.winehq.com](http://www.winehq.com) and build it yourself.

---

### Post by emu5088 on 2008-03-12
hey,
 I did everything you said and it worked! Thanks a bunch.
 Will I have to do this for almost all other programs I wish to uninstall, to make sure everything is gone?
-emu5088

---

