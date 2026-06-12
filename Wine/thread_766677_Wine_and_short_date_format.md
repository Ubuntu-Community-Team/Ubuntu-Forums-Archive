---
title: "Wine and short date format"
date: 2008-04-25
forum: Wine
---

### Post by Terrycymru on 2008-04-25
Since upgrading to Hardy yesterday I have lost the UK short date format DD/MM/YYYY for all applications and now have the US format MM/DD/YYYY. I have a thread about this in the Desktop Environment forum and am still seeking a solution.

I am writing here about a fix I have found to override the system settings for wine applications. I've found a solution that works for me in Quicken and Agent. Some apps take the short date format from ~/.wine/drive_c/windows/win.ini and some take it from ~/.wine/user.reg so it is necessary to amend both. 

In user.reg look for sShortDate= under [Control Panel \\ International] and change to sShortDate="dd/MM/yyyy" .

In win.ini look for sShortDate= under [intl] and change to sShortDate="dd/MM/yyyy" .

---

### Post by Terrycymru on 2008-04-26
I spoke too soon. Agent has held the settings but Quicken has now reverted to US short date format. Weird!

---

### Post by Terrycymru on 2008-04-29
The setting in user.reg somehow got overwritten. I have reset it to the required format and Quicken now shows UK short date format. (Agent newsreader was already working OK.)

---

### Post by Terrycymru on 2008-04-30
Entered in error. Now deleted.

---

### Post by herrfurher on 2010-11-21
Thanks for this great post I have been having this irritating problem for so long. Thanks :KS

---

### Post by Terrycymru on 2010-11-21
> **herrfurher said:**
> Thanks for this great post I have been having this irritating problem for so long. Thanks :KS

Glad you found it useful. This post may be helpful too:
[http://ubuntuforums.org/showthread.php?t=766231](http://ubuntuforums.org/showthread.php?t=766231)

In fact, it is probably the solution to try first.

---

