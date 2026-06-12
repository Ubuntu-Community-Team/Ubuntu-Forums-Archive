---
title: "warcraft 3 lan"
date: 2012-02-28
forum: Wine
---

### Post by Sahasrahla on 2012-02-28
I've looked around on the official wine page but I'm not quite understanding exactly what it is I'm supposed to be doing. The problem is that I can't have lan games with other computers. From what I've read it has something to do with the way that linux handles packets or something to that effect. 
lucid lynx
gforce fx 5500
I believe gs optiplex 260 mobo. it's a dell.

I will continue to search for the answer to my problem elsewhere and will post the solution once I find it. I will be forever grateful to anybody that could show me the solution.

---

### Post by Sahasrahla on 2012-02-28
If you try to play using the Local Area Network option, and do not see a game hosted from your machine on another or vice versa, and you are in the same subnet, this is likely caused by not having a default gateway. The game relies on sending UDP packets to the broadcast address and Linux will not send them unless there is a default gateway or another rule to handle them. To fix it, there are two methods:

Add a default gateway. 
- OR - 
Route 255. 255. 255. 255 to your local network.

See Wine Traffic #62 for another description of the issue. This is not considered a bug.

This is from the wine web page. I'm not quite sure how you go about doing this. 
op

---

