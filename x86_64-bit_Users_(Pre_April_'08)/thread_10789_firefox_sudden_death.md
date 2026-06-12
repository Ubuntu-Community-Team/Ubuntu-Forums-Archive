---
title: "firefox sudden death"
date: 2005-01-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by dmallery on 2005-01-11
hi

been happily using my ubuntu-64 for maybe a month now.  yesterday, firefox started dying silently during different parts of the eBay listing process.  it clears the window and no attempt to file a bug occurs.

one place where it repeatedly happens is selecting a gallery picture from a pull-down list.

this is disturbing because of its sudden appearance.  i have been using it heavily for some time.  i looked at the apt upgrades for the day, and they were only about exim.  apt gave me a new kernel this morning, but the problem persists.

anyone else see firefox burnouts?

 thanks

dave mallery

---

### Post by Dylanby on 2005-01-11
Firefox has never been too reliable for me under Ubuntu 64.
So much so that I swtiched my default to Mozilla browser.

When it crashes I get:
```
*** loading the extensions datasource
Segmentation fault
```

---

### Post by remmelt on 2005-01-16
i have the same thing, when i start up ff and type a 'g' in the googlebox, it crashes silently. this went away after i deleted everything from cache etc, in edit, prefs, privacy, clear all.

maybe it has to do with the googlebox trying to display a listbox with previous entries? other letters did seem to work though...

---

### Post by minio on 2005-01-16
[QUOTE=remmelt]i have the same thing, when i start up ff and type a 'g' in the googlebox, it crashes silently. this went away after i deleted everything from cache etc, in edit, prefs, privacy, clear all.

maybe it has to do with the googlebox trying to display a listbox with previous entries? other letters did seem to work though...[/QUOTE]
I have the same thing as you but with 'p'. Same solution.

---

### Post by Eklöf on 2005-01-16
[QUOTE=remmelt]i have the same thing, when i start up ff and type a 'g' in the googlebox, it crashes silently. this went away after i deleted everything from cache etc, in edit, prefs, privacy, clear all.

maybe it has to do with the googlebox trying to display a listbox with previous entries? other letters did seem to work though...[/QUOTE]


THANK YOU. I almost love you, as I have gone nuts about this stupid bug for a few days. Very annoying. After clearing all, it seems to work.

/ Jonas

---

### Post by dmallery on 2005-01-20
[QUOTE=Dylanby]Firefox has never been too reliable for me under Ubuntu 64.
So much so that I swtiched my default to Mozilla browser.

When it crashes I get:
```
*** loading the extensions datasource
Segmentation fault
```[/QUOTE]
 so i switched to mozilla which is more stable, but just crashed silently in the eBay/PayPal label printing cycle (where firefox crashed a lot.)

btw, my firefox does NOT crash in the google box like others have found.

question:  how do i find out about the work going on in 64-bit firefox?  does it have its own bugzilla?

thanks to all

dave mallery

---

### Post by Eklöf on 2005-01-20
I want to know how to backport FF and TB 1.0 
I found a howto but it doesn't seem to work for AMD64

---

