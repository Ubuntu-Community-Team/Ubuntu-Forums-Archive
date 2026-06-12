---
title: "64-bit Hardy, Firefox and Flash"
date: 2008-09-22
forum: x86 64-bit Users
---

### Post by camasterson85 on 2008-09-22
I installed the 64 bit version of Hardy.  I have Flash running with nspluginwrapper on Firefox64, this barely works, it crashes constantly, especially if you are viewing more than one flash site at a time or switching back and forth.  I also have installed Firefox32.  The flash works great in this case but Firefox32 does not play well with themes that are applied in the desktop environment.  For example, some themes remove the border around a text box for input, you just have to guess where it is.  Also, some buttons were missing, again, you could guess at it and find them.  Even before I applied any themes, system icons such as folders would be missing when browsing for attachments.  

Is there anything I can do to make one of these options work right for me?  Flash is pretty much a necessity for the frivolous tasks that I use my computer for.  If I can't get it to work I am considering installing the 32bit Ubuntu.

Thanks,
Alan

---

### Post by TriSwords on 2008-09-22
I just typed in 

```
sudo apt-get install flashplugin-nonfree
``` 

and its working for me.

64 bit Ubuntu 8.04 with Firefox.

---

### Post by tuxxy on 2008-09-22
You could try upgrading the Flash version, but as with triswords the flashplugin-nonfree runs great for me.

Also heres a link to the [64-Bit user-group]("http://ubuntuforums.org/group.php?groupid=258")

---

### Post by camasterson85 on 2008-09-23
Actually, I did the exact same thing that you guys did.  Many times I get a gray box where I should be seeing flash content.  Is version 9.0 r124 the most up to date package?

---

### Post by TriSwords on 2008-09-23
Thats the version I am running. 

A while back before I reinstalled Ubuntu I could not get flash to work at all, even with the apt-get and nspluginwrapper. However after reinstalling the apt-get worked right away. I never could figure out what was causing it.

I tried nspluginwrapper first and it failed, maybe it caused a conflict?

---

### Post by Kilz on 2008-09-23
Even the flash 10 beta has the grey box problem, and its not easy to install. I think this is an issue with the nspluginwrapper and having multiple flash enabled websites or pages open in multiple tabs or windows. The simple solution is to refresh or only open one at a time.
To fix firefox 32 you can install the 32bit theme engine with [gitlibs]("http://ubuntuforums.org/showthread.php?t=474790") and its ability to install the package with its -p option as long as you know its name.

---

### Post by tuxxy on 2008-09-23
When you see the greybox refresh the page a few time sand it should load.

---

### Post by behanj on 2008-09-25
Hi,

I got Flash 9 working on my Ubuntu Hardy 64 in Firefox 3.0.2.

This is where I got the fix from - Last post on second page.
[http://ge.ubuntuforums.com/showthread.php?p=5852730#post5852730](http://ge.ubuntuforums.com/showthread.php?p=5852730#post5852730)

I installed Firefox with Ubuntuzilla.

Hope this can help someone else.

---

### Post by Kilz on 2008-09-25
> **behanj said:**
> Hi,

I got Flash 9 working on my Ubuntu Hardy 64 in Firefox 3.0.2.

This is where I got the fix from - Last post on second page.
[http://ge.ubuntuforums.com/showthread.php?p=5852730#post5852730](http://ge.ubuntuforums.com/showthread.php?p=5852730#post5852730)

I installed Firefox with Ubuntuzilla.

Hope this can help someone else.

Be aware that by doing so you are in fact installing a 32bit version of firefox and that all other plugins like media player (vlc, mplayer, totem) and java will also need to be 32bit. This is ok if you installed the 32bit version of Ubuntu. But if you didnt , you will need to manually install them, you will not be able to do so with synaptic or apt.

---

### Post by behanj on 2008-09-26
Thanks for the heads up Kilz.
I didn't realise that I had installed 32bit Firefox.

---

### Post by yadidone on 2008-09-26
After burying his mother nine months earlier, a client of the local mortuary finally had enough money to purchase the expensive coffin he'd originally wanted. So we exhumed the body and transferred his deceased mother into the new steel casket. "What's so special about this coffin?" I asked the funeral director. He replied, "It has a lifetime warranty."&#30333;&#30300;&#39118;&#27835;&#30103;&#26159;[&#30333;&#30300;&#39118;](http://www.curevitiligo.com)&#21307;&#38498;&#26368;&#20027;&#35201;&#30740;&#31350;&#35838;&#39064;&#65292;&#26377;&#30528;&#22810;&#24180;&#30333;&#30300;&#39118;&#27835;&#30103;&#30340;&#37051;&#24202;&#32463;&#39564;&#65292;&#30740;&#21046;&#20986;&#20102;&#22810;&#31181;&#27835;&#30103;&#30333;&#30300;&#39118;&#30340;&#29305;&#25928;&#33647;&#29289;&#12290;&#31361;&#30772;&#20102;&#30333;&#30300;&#39118;&#19981;&#27835;&#20043;&#35823;&#21306;&#12290;The [vitiligo](http://www.cureforvitiligo.com) pamphlet vitiligo is a skin, an introduction to vitiligo by the vitiligo society.&#20854;&#20182;&#30149;&#20363;&#65306;[&#32959;&#30244;](http://www.gzph.net)&#65292;[&#20057;&#32925;](http://www.gzph.net)&#65292;[&#24515;&#33039;&#30149;](http://www.gzph.net)

---

### Post by ColmCille on 2008-10-01
> **Kilz said:**
> Be aware that by doing so you are in fact installing a 32bit version of firefox and that all other plugins like media player (vlc, mplayer, totem) and java will also need to be 32bit. This is ok if you installed the 32bit version of Ubuntu. *But if you didnt , you will need to manually install them, you will not be able to do so with synaptic or apt*.


Could you give me a hint on how to do that, please? 

Where do I get them, and how do I manually install them?

Thank you.

---

