---
title: "Wine windows stay on top"
date: 2008-02-04
forum: Wine
---

### Post by siddartha on 2008-02-04
Hello,

I upgraded to 7.10 and with the latest wine from the wine repositories and I discovered that the wine apps/windows stay on top. It's ok for a single window application, but for apps that generate extra views/options/windows the app is becoming unusable. How do I turn this 'feature' off?

Cheers,
Sidd

---

### Post by AndyCooll on 2008-02-04
Look in the wine configuration, by typing in the command line:
```
winecfg
```

I'm sure there's an option in one of the tabs to untick "Always display ..." (Sorry to be a bit vague, but I'm not at my Linux box at the moment)

:cool:

---

### Post by hyperair on 2008-02-04
Always stay on top? I don't understand what you mean. Wine windows are stilll windows handled by the window manager and as such you can make them stay at the top or not according to your whims and fancies.

---

### Post by siddartha on 2008-02-04
> **hyperair said:**
> Always stay on top? I don't understand what you mean. Wine windows are stilll windows handled by the window manager and as such you can make them stay at the top or not according to your whims and fancies.

In my case, than, the default window manager does set up the always on top flag. And this is only for the wine applications. The rest are normal. Of course, it can be inhibited by right clicking on the top window bar, and deselecting always on top. Yet, I think this is an unneeded effort.

---

### Post by siddartha on 2008-02-04
> **AndyCooll said:**
> Look in the wine configuration, by typing in the command line:
```
winecfg
```

I'm sure there's an option in one of the tabs to untick "Always display ..." (Sorry to be a bit vague, but I'm not at my Linux box at the moment)

Nope. Nothing like that in the configuration.
Anyway, there is no need for the command line in the 7.10 as there is a new entry in the Wine menu below applications.

---

### Post by hyperair on 2008-02-04
Hmm, you must have changed some setting somewhere in order for that to happen, because I certainly don't see anything of that sort. Try making sure that "allow window manager to control windows" is checked under the Graphics tab in winecfg.

---

### Post by siddartha on 2008-02-05
> **hyperair said:**
> Hmm, you must have changed some setting somewhere in order for that to happen, because I certainly don't see anything of that sort. Try making sure that "allow window manager to control windows" is checked under the Graphics tab in winecfg.

Well, it is and it always has been. If I need something like no window management I go for a clean X with just the terminal.

---

### Post by hconnellan on 2008-06-23
This may be too late a reply but if anyone else would like to know, the option you are looking for is winecfg -> graphics -> alow the window manager to control the window.

---

### Post by RealG187 on 2009-07-09
[http://ubuntuforums.org/showthread.php?p=7487367](http://ubuntuforums.org/showthread.php?p=7487367)

I am having the same issue, I made no changes to allow this to happen, it only happens with one app, so far...

---

### Post by DOMS on 2012-05-19
> **hconnellan said:**
> This may be too late a reply but if anyone else would like to know, the option you are looking for is winecfg -> graphics -> alow the window manager to control the window.

This fixed it for me.

Thanks you very much!

Also, I know this is an old thread, but it comes up at the top of a Google search, so leaving this here will help others.

---

