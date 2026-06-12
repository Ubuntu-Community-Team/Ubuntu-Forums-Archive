---
title: "Firefox32 opens 'talkback' upon launch and 'talkback' stays open"
date: 2007-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Stochastic on 2007-11-04
Okay so everytime I open my Firefox32 I get another app opening called talkback.

the about of this program says > 
SupportSoft Talkback 2.2 (Build @@BUILD@@)
Copyright C 1997-1998 SupportSoft, Inc.

Vendor: MozillaOrg
Product: Firefox2
etc....

[http://www.supportsoft.com](http://www.supportsoft.com)

The program has two windows; one is normal size with menus etc.. and is responsive in the sense that you can open menus, but nothing seems to ever happen beyond that, the other window that opens is a small titlebar about 3mm wide.  Gnome tells me that the second window is called > Welcome to Mozilla Feedback Agent - Step 1 of 3.  How do I prevent this file from opening?

In Gnome System Monitor I look at the 'talkback' files and notice that
/home/ME/.mozilla/firefox/6pev8qzc.default/XPC.mfasl
/home/ME/.mozilla/firefox/6pev8qzc.default/.parentlock
/usr/local/firefox32/extensions/talkback@mozilla.org/components/talkback/talkback
/dev/null
are all open objects.
which of these files are safe to erase without breaking anything other than talkback?

---

