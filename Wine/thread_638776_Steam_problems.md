---
title: "Steam problems"
date: 2007-12-12
forum: Wine
---

### Post by Dapman01 on 2007-12-12
I got steam to install.  After I input my steam password it says
This application is trying to show an HTML page.  Wine needs Gecko (Mozilla HTML engine) to be installed to show the page.  Click install if you want Wine to automatically download and intall Gecko.

It has the option to click the install button, but I can't click it
Any help will be great

---

### Post by Beren Camlost on 2007-12-12
Open a terminal and enter the following:
```
wine iexplore [URL="http://winehq.org"]http://winehq.org
```[/URL] 
[FONT=monospace]This will install gecko. Once installation finishes, run Steam again.
[/FONT]

---

