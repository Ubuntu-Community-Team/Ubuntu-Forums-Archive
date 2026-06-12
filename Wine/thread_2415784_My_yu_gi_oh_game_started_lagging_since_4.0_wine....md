---
title: "My yu gi oh game started lagging since 4.0 wine..."
date: 2019-03-31
forum: Wine
---

### Post by milosx72 on 2019-03-31
I have this very very old laptop which I use to code and play yu gi oh power of chaos trilogy games. Everything worked fine on lubuntu 18.04 and wine 3.5 i believe. I wanted to switch to lubuntu 18.10 and try lxqt but since then, scrolling cards in my deck constructor inside a game just takes like 5-6 second for each scroll. Like i scroll one tick down, and game freezes for 5 seconds before it scrolls down. It's not that big of a deal but takes a lot of time to manage my deck. This didn't happen before, so I assumed it's fault in lubuntu 18.10. So I try to install xubuntu 18.04 and same error is happening, which is safe to assume that wine 4.0 is the problem or causing it. Is there a way I can install older version of wine so I can play these games without this weird lag? That's the only windows app I run literally I don't really care which version I run as long as yu gi oh works. Thanks!

---

### Post by thenailedone on 2019-03-31
()ubuntu 18.04 shows:

[https://packages.ubuntu.com/search?keywords=wine&searchon=names&suite=bionic&section=all](https://packages.ubuntu.com/search?keywords=wine&searchon=names&suite=bionic&section=all)
> Package wine-stable
bionic (18.04LTS) (otherosfs): Windows API implementation - standard suite [universe] 
3.0-1ubuntu1: all

So if you install Wine-stable you should be running Wine 3.0 (but this may not be the issue that you are facing).

---

