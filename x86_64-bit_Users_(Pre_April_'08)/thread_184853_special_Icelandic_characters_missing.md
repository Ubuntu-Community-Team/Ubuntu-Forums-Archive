---
title: "special Icelandic characters missing"
date: 2006-05-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by denni on 2006-05-30
Have searched the posts on this and still been unable to solve it.  The problem is that some special Icelandic letters like í ó ú and <> are missing and when choosing Icelandic while setting up phpbb and squirrelmail many letters came out as they where Chinese.  have been fiddling around with dpkg-reconfigure localeconf and dpkg-reconfigure localepurge.  As this is a server everything is in console.

The output of lacale is;
LANG=is_IS.UTF-8
LANGUAGE=is_IS:is:en_GB:en
LC_CTYPE="is_IS.UTF-8"
LC_NUMERIC="is_IS.UTF-8"
LC_TIME="is_IS.UTF-8"
LC_COLLATE="is_IS.UTF-8"
LC_MONETARY="is_IS.UTF-8"
LC_MESSAGES="is_IS.UTF-8"
LC_PAPER="is_IS.UTF-8"
LC_NAME="is_IS.UTF-8"
LC_ADDRESS="is_IS.UTF-8"
LC_TELEPHONE="is_IS.UTF-8"
LC_MEASUREMENT="is_IS.UTF-8"
LC_IDENTIFICATION="is_IS.UTF-8"
LC_ALL=

so how came that those characters are missing?

---

