---
title: "SCIM support in Edgy 64-bit?"
date: 2006-11-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by HeresJohnny on 2006-11-02
Hello everyone,

I'm having a devil of a time figuring this out.  I upgraded to Edgy (clean install, 64-bit) because I type in English and Korean and my two primary apps (OOo and Firefox) don't work with SCIM (they have issues because of the C++ branches in which they were compiled, or so I'm told).  With FF 2.0, at least, I'd hoped they had fixed that particular problem.  However, after installing Edgy, I can't get 'language support' installed; the message from 'Add/remove' says that the app is not supported for my configuration.  I don't know of another way to install input method languages, the app on the system panel won't allow me to add any languages at all, and I have no idea how to proceed.  Is anyone else having this problem, and have they solved it?  Any advice is, as always, appreciated.

EDIT:  Okay, never mind, I'm a damn fool, but a happy one.  It turns out my language support did not install completely, and that prevented me from setting up SCIM properly.  This is what I did:
1.  I enabled all repositories and changed my default server to Ubuntu main (was set at US server).
2.  I consulted the following webpage:  [http://www.mrbass.org/linux/ubuntu/scim/]("http://www.mrbass.org/linux/ubuntu/scim/") for the terminal commands (it's for Hoary, but it will work):  I copied/pasted each command, line by line, for installing and then for adding SCIM to startup for X11
3.  I installed afterward the packages that Terminal recommended:  in my case, it was sudo apt-get install ttf-unfonts, followed by sudo apt-get install ttf-alee.  Your system may recommend others, or none at all.
4.  I went back into System>Administration>Language Support, and (after inputting my password) it then detected that Language Support was incomplete.  I reinstalled the missing pieces, added support for Korean, and closed the program.
5.  I opened the SCIM setup utility and reviewed the settings.  I didn't see anything amiss there, so I closed it and opened FF 2.0.  When I hit shift+space, I saw the SCIM icon come up immediately.  I changed into Korean, and I was good to go!
6.  Checked OpenOffice after that, and was also good to go!  (I think I set up the CJK settings in OOo earlier, though.  If you haven't, you'll need to go to tools>options>languages and set them up.  Enable CJK languages, and you should be able to work right away)
7.  I can now type in Korean whenever I need to, in whatever program I need.  KUDOS to Ubuntu for getting this right!  Now my wife will probably use Ubuntu more, and I'll have an excuse to install it on my home desktop too!!!
&#50500;, &#51652;&#51676; &#54665;&#48373;&#54616;&#45796;.  &#50500;&#51452;&#49884;&#50896;&#54616;&#44172;...

---

