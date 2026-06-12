---
title: "[SOLVED] Wine + Space Empires IV"
date: 2008-06-18
forum: Wine
---

### Post by plinydogg on 2008-06-18
Hi everyone,

I'm having trouble getting Space Empires IV to work even though the winehq.org appdb says it should work. The demo version works fine but the registered version, which requires some sort of Internet-based activation, doesn't. 

Whenever I try to run it I get an error saying "error while unpacking program, code C. Please report to author."

Does anyone know how to fix this problem. The developer and distributer of the game have been completely nonresponsive so far. 

Thanks in advance!

---

### Post by plinydogg on 2008-06-18
bump

---

### Post by plinydogg on 2008-06-18
Here's the response I got from the a-holes at Strategy First:

"Hello,

You will need to run the game with a Windows OS.

Regards,

Strategy First Technical Support"

---

### Post by plinydogg on 2008-06-18
Someone in another forum said that the Internet-based registration isn't necessary if one purchases the disk version of the game as opposed to the digital download. Can anyone confirm this?

---

### Post by plinydogg on 2008-06-18
Problem solved. Here's how:

(1) Find the folder you installed the game in;
(2) Open the "settings.txt" file found in the /data/ subdirectory;
(3) Change "Allow CD Music" to "FALSE";
(4) Save and you're good to go!

---

### Post by shkkmo on 2011-01-21
SE4 runs okay for me under wine with ubuntu 10.04, but my Eee PC screen is too short and the game interface runs off the bottom.

---

