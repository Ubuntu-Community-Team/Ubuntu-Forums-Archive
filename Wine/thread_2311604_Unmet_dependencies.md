---
title: "Unmet dependencies"
date: 2016-01-28
forum: Wine
---

### Post by paulkruger on 2016-01-28
I have tried all kinds of posted "solutions" but still get this error. I am to be considered a newbie although I have toyed with Linux for ten years, am really trying to eliminate Windows and work with Ubuntu as my default OS.  To do that there are still a couple programs I need to open which are not available in Linux unless I can use WINE.  Most important is Quickbooks which has all my business billing info and no means to export to Gnucash unless I manually recreate everything which would be a real hassle.

Here is the error re. unmet dependencies which I cannot figure out how to fix?

( Note to developers, please provide better text error messaages with more help on solving a problem rather than just saying something is wrong thus filling up forums. !)

The following packages have unmet dependencies:

```
unity-control-center: Depends: libpulse-mainloop-glib0 (>= 1:0.99.1) but 1:4.0-0ubuntu11.1 is to be installed
                      Depends: libpulse0 (>= 1:0.99.1) but 1:4.0-0ubuntu11.1 is to be installed
                      Depends: libxi6 (>= 2:1.2.99.4) but 2:1.7.1.901-1ubuntu1.1 is to be installed
wine1.6: Depends: wine1.6-amd64 (= 1:1.6.2-0ubuntu4) but 1:1.6.2-0ubuntu4 is to be installed
         Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu4) but it is a virtual package

```
//////

---

### Post by howefield on 2016-01-28
Post moved to it's own thread.

---

### Post by matt_symes on 2016-01-28
Hi

> **paulkruger said:**
> I have tried all kinds of posted "solutions" but still get this error. I am to be considered a newbie although I have toyed with Linux for ten years, am really trying to eliminate Windows and work with Ubuntu as my default OS.  To do that there are still a couple programs I need to open which are not available in Linux unless I can use WINE.  Most important is Quickbooks which has all my business billing info and no means to export to Gnucash unless I manually recreate everything which would be a real hassle.

Here is the error re. unmet dependencies which I cannot figure out how to fix?

( Note to developers, please provide better text error messaages with more help on solving a problem rather than just saying something is wrong thus filling up forums. !)

```
The following packages have unmet dependencies:

unity-control-center: Depends: libpulse-mainloop-glib0 (>= 1:0.99.1) but 1:4.0-0ubuntu11.1 is to be installed
                      Depends: libpulse0 (>= 1:0.99.1) but 1:4.0-0ubuntu11.1 is to be installed
                      Depends: libxi6 (>= 2:1.2.99.4) but 2:1.7.1.901-1ubuntu1.1 is to be installed
wine1.6: Depends: wine1.6-amd64 (= 1:1.6.2-0ubuntu4) but 1:1.6.2-0ubuntu4 is to be installed
         Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu4) but it is a virtual package
```

//////

Please post the output of

```
grep "^[^#]" /etc/apt/sources.list{,.d/*}
```

and 

```
cat /etc/lsb-release
```

This'll show use your sources and release.

Please post the output back here using code tags like this

[noparse]```
terminal output
```[/noparse]

to get output like this

```
terminal output
```

I have edited your previous post for you to add code tags.

Kind regards

---

