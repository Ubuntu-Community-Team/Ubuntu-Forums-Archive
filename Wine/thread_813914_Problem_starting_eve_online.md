---
title: "Problem starting eve online"
date: 2008-05-31
forum: Wine
---

### Post by oscar2296 on 2008-05-31
Hi, I'm having problems with starting eve on my ubuntu laptop. The official linux cedega version wont start at all, it crashes after the splash screen. So i downloaded the windows version and ran it in wine. I get to the login screen, but I cant scroll down the window that says "Scroll down to continue." Also there is no text in it. Without being able to scroll it down, I cant login. Any suggestions to what I might do to fix it?

---

### Post by softdel on 2009-04-25
For the record FIX: You need to have the 'Arial' font installed.

> apt-get install msttcorefonts
cd ~/.wine/drive_c/windows
mv Fonts Fonts.old
ln -s /usr/share/fonts/truetype/msttcorefonts/ Fonts

---

