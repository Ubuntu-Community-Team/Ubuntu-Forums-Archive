---
title: "installed programs do not show up"
date: 2014-06-02
forum: Wine
---

### Post by gdesilva on 2014-06-02
Hi, I installed wine on my Ubuntu Studio 14.04 and the installation was successful. Then I installed MS Office using Winetricks and installed DVDShrink as well - both installations were successful. However, I cannot see installed apps under wine. If I right click on a document then it gives me the option to open with Libreoffice or MS Word but there is no menu items for the Windows apps.

How could I have the Windows apps get listed in the menu? I recall in 13.04, they used to appear under Wine.

Many thanks

---

### Post by gdesilva on 2014-06-02
If you run into this problem the solution that worked for me is this.

I started Settings Manager -> Main Menu and had a look at the Wine entry.

Lo and behold all the Windows apps I installed were listed there under a folder called Programs which is what I expected to see. Incidentally, this Program folder was the first item under Wine menu. My Program sub folder had other sub folders such as DVD Shrink, MS Office etc but did not have any programs per se.

After trying to tweak all sorts of things (there isn't much to tweak anyway), I just added another item (not a folder) to the Programs sub folder. Then, magically not only Programs showed up but also all the sub folders and items within the sub folders showed up. However, if I removed the dummy item I added in the Programs folder then Programs folder and all the sub folders simply disappeared!

I did not like to leave a dummy program item in the folder Programs so I just thought of moving Programs folder down the hierarchy in the Wine folder. When I did this, Programs appeared again and so did all the sub folders and items within those sub folders.

So, all you would need to do is to move the Programs folder one level down in the Wine folder contents list and you will start to see Programs and all its sub folders and program items within those sub folders.

Obviously, this is some sort of a bug but this solution will provide a quick work around.

---

