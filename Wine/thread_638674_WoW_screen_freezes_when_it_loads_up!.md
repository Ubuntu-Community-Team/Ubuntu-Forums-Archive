---
title: "WoW screen freezes when it loads up!"
date: 2007-12-12
forum: Wine
---

### Post by Nando-san on 2007-12-12
Hi guys, I got the latest version on wine, WoW will start up GREAT! i can see my characters,etc... but when the loading page comes, when it's finished it just stays there.... freezes in the load page. I used to ha ve Windows Vista here, and it would run perfectly, i have an INTEL 945 graphics card.. can any1 help me? PLIZ!!!! i really wanna play LOL!

I did this:

Edit your wtf/Config.wtf file and remove the following line:

SET gxApi "opengl"



Run WoW as usual and login once. After that quit WoW and readd that line.

This switches WoW to Direct3D mode for the hardware survey.

this was told in: [http://forums.worldofwarcraft.com/thread.html;jsessionid=800C5D0AA3B5446BA247773F3047D12C?topicId=1230504023&postId=12305436865&sid=1](http://forums.worldofwarcraft.com/thread.html;jsessionid=800C5D0AA3B5446BA247773F3047D12C?topicId=1230504023&postId=12305436865&sid=1)

I ran the game but OH SO LAGGY! and graphics were missing, well... IT WAS AWFUL... any help?

---

### Post by gazj on 2007-12-12
the opengl switches directx mode off, and rund wow in opengl mode.  I would try anything on theis page from step 6 down (anything above step 6 is specific to gentoo)

[http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine)

the regsitry edit tip, will have the biggest performance increase, most likely will double your fps

have fun :D

---

### Post by Nando-san on 2007-12-12
thanks! but before I read this i just installed WINE again and i think i uncheked the 3d option in wineconfig... the game now plays fine, BUT it's laggy... i have to turn all goodies off for it to run smooth. Also, it maybe the drivers or something, but like i said i had this game running on Vista with all the effects,etc... it ran perfectly... now it's laggy...any tips?

---

