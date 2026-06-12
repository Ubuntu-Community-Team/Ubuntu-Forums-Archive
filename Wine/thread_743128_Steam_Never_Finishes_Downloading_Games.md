---
title: "Steam Never Finishes Downloading Games"
date: 2008-04-02
forum: Wine
---

### Post by joseph.brower on 2008-04-02
I've got steam installed (using the packaged wine that comes with 8.04) and it runs great.  The only problem is when I try to install a game, it downloads, gets all of the way to 99 percent and then stops.  Occasionally I will see it start downloading at about 1K/s.  I thought maybe it was my connection, but when I start downloading another game it goes fast (200+ K/s).  If I try to launch a game that is at 99 percent, it says it will start after it is finished, but it says that it is unable to connect to the steam servers.  Anyone else experiencing this or know what I can do to fix it?

---

### Post by blazercist on 2008-04-02
A couple of things to try:

1. Steam won't work or connect to servers if your machine is the DMZ on the network so check your router settings and make sure its not.

2. Try asking in the AppDB on winehq.org   go there click AppDB and search for Steam.

3. You should always post the wine version number when you ask questions about wine (you can find this by typing wine --version in console) as well as the command you are using to start the application (if you are just using the menu in your main menu bar just specify that)

4. I can play steam games just fine with wine 0.9.58 on Gutsy Gibbon 7.10 so it may be that Hardy has a regression in it thats not fixed yet because its BETA or it could be that the wine version in the Hardy repos is broken or old.

---

### Post by joseph.brower on 2008-04-03
It worked!  I checked my router and I was a DMZ... odd.  Either way, it is working now.  Thanks a ton for the help!

---

