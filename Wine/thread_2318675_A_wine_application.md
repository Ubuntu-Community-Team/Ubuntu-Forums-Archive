---
title: "A wine application?"
date: 2016-03-28
forum: Wine
---

### Post by Federica on 2016-03-28
Good afternoon, everyone. I have a weird problem with wine. If I navigate to the "open with..." table, I have multiple entries named "a wine application" (see image below). There is a way to solve the problem? I've already tried [this solution]("http://ubuntuforums.org/showthread.php?t=1245777&p=7845982#post7845982"), but I don't have (or I couldn't find) the multiple entries described in said forum post. Basicly my question is: how I can get ride of all those entries?


Thank you!


[ATTACH=CONFIG]268037[/ATTACH]

---

### Post by howefield on 2016-03-28
Thread moved to the "*Wine*" forum.

---

### Post by alex_32 on 2016-03-29
Hello,

As far as I can remember: In your folder **/home/user/.local/share/applications** there should be** wine.desktop **files without icons which appear in your menu, and you have to delete those so that they do not appear in your menu.
However, be careful and do not delete shortcuts for the programs you are using.

---

### Post by howefield on 2016-03-29
> **Federica said:**
> .. but I don't have (or I couldn't find) the multiple entries described in said forum post.

Just in case the reason for not being able to find the files and you aren't aware, the period in the file path/name ( ~/.local/share/applications) indicates a hidden folder. 

Use the Ctrl + h keys to toggle showing hidden files/folders, or "Show Hidden Files" from the Files > View menu.

---

### Post by Federica on 2016-03-29
> **howefield said:**
> Just in case the reason for not being able to find the files and you aren't aware, the period in the file path/name ( ~/.local/share/applications) indicates a hidden folder. 

Use the Ctrl + h keys to toggle showing hidden files/folders, or "Show Hidden Files" from the Files > View menu.

I was aware it's indicates a hidden folder, but for some reasons last time I couldn't find the file anyway.  Anyway, I marked the topic as solved, because I was able to retrive the file this time and delete all the surpluse. Thank you very much both of you. :D

---

