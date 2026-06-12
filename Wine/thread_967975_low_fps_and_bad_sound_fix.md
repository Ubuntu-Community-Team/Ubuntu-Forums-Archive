---
title: "low fps and bad sound fix"
date: 2008-11-02
forum: Wine
---

### Post by Trap3d on 2008-11-02
First low fps.
Probably the fault is drivers assuming you have just installed your ubuntu you probably forgot to install the drivers or just haven't upgraded them in a while so do that now.
**System > Administration > Hardware drivers** and select the newest driver release for your graphics card and press Activate.
Worked for me.

Second about the bad audio.
This works if you are using 1.1.7. if any other it still might work if you have ever installed 1.1.7.
First you'll have to get rid of your current wine so do that.
**System > Administration > Synaptic packet manager**, there find wine and check complete removal, then go to home folder (**Places > Home folder**)btw the folder is hidden so turn show hidden folders on  and delete your .wine folder ([COLOR="Red"]**you might want to backup your games & apps and other stuff you have installed under wine from that folder as when you delete it [SIZE="5"]they will be lost unless backuped[/SIZE]**[/COLOR])
Then remove every single thing related to your wine in the Software sources(**System > Administration > Software sources**)
Now all you have to do is install wine from your Add/Remove apps in Applications tab and voila you should have normal sound once again tought do not upgrade it to 1.1.7 let it stay 1.0.1.
Yet again it worked for me.

---

