---
title: "Display chinese in wine emulated application"
date: 2008-07-05
forum: Wine
---

### Post by Olnex on 2008-07-05
I have to use a Windows application which displays Chinese characters, on Windows, I have to set Control Panel -> Regional and Language Options -> Advanced -> Language for non-Unicode programs to "Chinese (PRC)" in order to get it correctly displayed, so how to achieve the same effect under wine? Thanks a lot!!!

---

### Post by chenzero on 2008-12-27
Don't know if this problem was solved or not.
I also encountered this kind of problem. please try
'export LANG=zh_CN.UTF-8' before start 'wine'
Good luck!

---

