---
title: "How can FF fonts be changed to small?"
date: 2008-05-08
forum: x86 64-bit Users
---

### Post by Sef on 2008-05-08
Moved from [this thread]("http://ubuntuforums.org/showthread.php?t=786407") posted by DachaArh:

I need help with Firefox 3.0b5, on linux my fonts are too large in firefox ( on toolbars etc..) and I like small fonts, can I change this and how ?

---

### Post by killall-9 on 2008-05-09
Hello!

Press  left "Strg/ctrl" and use your Mousewheel for change the size of your fonts.Firefox 3  will remember for every fonts size on any webside you set.

---

### Post by gaussian on 2008-05-09
In order to affect Firefox UI, you will need to play with the file ~/.mozilla/firefox/ABCDEFG/Chrome/userChrome.css

where ABCDEFG=random characters

I am by no means expert on this, but I would recommend you google userchrome and mozilla to get more info. I changed some settings long time ago, mine looks like this:
```

* {
    font-family: Verdana !important;
    font-size: 10pt !important;
  }
/* The following four lines were added by KDE */
scrollbarbutton[sbattr="scrollbar-up-top"] { display: -moz-box !important; }
scrollbarbutton[sbattr="scrollbar-down-top"] { display: none !important; }
scrollbarbutton[sbattr="scrollbar-up-bottom"] { display: -moz-box !important; }
scrollbarbutton[sbattr="scrollbar-down-bottom"] { display: -moz-box !important; }

```

---

