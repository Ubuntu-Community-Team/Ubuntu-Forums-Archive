---
title: "[Solved] Firefox Crashes in Wine for some sites"
date: 2008-11-13
forum: Wine
---

### Post by RT236 on 2008-11-13
Some sites I use absolutely require IE, therefore, I use Wine with Firefox for these limited sites I must access.  I just upgraded to Ubuntu 8.10.

Ubuntu 8.10
Wine 1.0.1-0ubuntu2
Firefox 3.0.4

Problem:  On certain sites, for example, chase.com and verizon.com Firefox would crash as soon as site came up.  Repeatable problem.  I tried different revs. of Firefox, did not help.

Solution:  I recalled long ago using Wine directly from WineHQ for some problems in SuSE and Ubuntu.

Site:  [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) I loaded WineHQ repository, key and then the package for Ubuntu 8.10.  This solved problem 100%.

Note, before I did this I removed, of course, previous releases of wine and wine-gecko, and also deleted .wine directory in /home.

Hope this is helpful to someone if having similar problems with Ubuntu 8.10.

---

