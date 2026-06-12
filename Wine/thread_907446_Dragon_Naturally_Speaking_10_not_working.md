---
title: "Dragon Naturally Speaking 10 not working"
date: 2008-09-01
forum: Wine
---

### Post by ft566 on 2008-09-01
I recently used wine to install the program Dragon Naturally Speaking by Nuance. The install seemed to go alright but when I try to open the program it shows the startup screen and then nothing happens. An icon appears on the panel briefly showing thats its running, but then it dissapears. I'm not sure if this is a common thing or not but any help would be appreciated.

---

### Post by Marc Ament on 2008-10-21
Sorry, I don't have a solution; I have the same problem, using Dragon Naturally Speaking 10 Preferred and WINE 1.0 on Hardy.  WineHQ shows a success test ("silver") for DragonNS 10 Standard (not Preferred) and using WINE 1.0-rc5, so I assume we're going something wrong.

---

### Post by Etrruugo on 2008-10-21
Bump!                        thx   !   &#12288;Her chores were never-ending. Sewing clothes for her family on the old Singer treadle machine, cooking meals and baking bread, planting and tending a vegetable garden, milking the goats and scrubbing soiled clothes on a washboard. But she was happy. Her family and their well-being were her highest priority.&#12288;&#12288;Every day after chores and school, Reuben scoured the town, collecting the hessian nail bags. On the day the two-room school closed for the summer, no student was more delighted than Reuben. Now he would have more time for his mission.&#12288;&#12288;All summer long, despite chores at home weeding and watering the garden, cutting wood and fetching water&#8212;Reuben kept to his secret task.&#12288;&#12288;Then all too soon the garden was harvested, the vegetables canned and stored, and the school reopened. Soon the leaves fell and the winds blew cold and gusty from the bay. Reuben wandered the streets, diligently searching for his hessian treasures.&#12288;&#12288;Often he was cold, tired and hungry, but the thought of the object in the shop window sustained him. Sometimes his mother would ask: &#8220;Reuben, where were you? We were waiting for you to have dinner.&#8221;&#12288;&#12288;&#8220;Playing, Mum. Sorry.&#8221;&#12288;&#12288;Dora would look at his face and shake her head. Boys.&#12288;&#12288;Finally spring burst into glorious green and Reuben's spirits erupted. The time had come! He ran into the barn, climbed to the hayloft and uncovered the tin can. He poured the coins out and began to count.&#12288;&#12288;Then he counted again. He needed 20 cents more. Could there be any sacks left any where in town? He had to find four and sell them before the day ended.&#12288;&#12288;Reuben ran down Water Street.&#12288;&#12288;The shadows were lengthening when Reuben arrived at the factory. The sack buyer was about to lock up.&#12288;&#12288;&#8220;Mister! Please don't close up yet.&#8221;&#12288;&#12288;The man turned and saw Reuben, dirty and sweat stained.&#12288;&#12288;&#8220;Come back tomorrow, boy.&#8221;&#12288;&#12288;&#8220;Please, Mister. I have to sell the sacks now&#8212;please.&#8221;The man heard a tremor in Reuben's voice and could tell he was close to tears.&#12288;&#12288;&#8220;Why do you need this money so badly?&#8221;&#12288;&#12288;&#8220;It's a secret.&#8221;&#12288;&#12288;The man took the sacks, reached into his pocket and put four coins in Reuben's hand. Reuben murmured a thank you and ran home.&#12288;&#12288;Then, clutching the tin can, he headed for the shop.&#12288;&#12288;&#8220;I have the money,&#8221; he solemnly told the owner.&#12288;&#12288;The man went to the window and retrieved Reuben's treasure.Thsale is a professional, loyal and reliable wow gold supplier online, we pioneered selling cheap wow gold. Welcome to thsale buy world of warcraft gold Buy Cheap WoW Gold, World of Warcraft Gold, Please look here! We are a Great MMORPG company. wow money and wow items,which is very cheap WOW Gold&#65281;All US Server 24.99$/1000G on sell! Cheap wow gold,rs powerleveling,wow power leveling,Buy Cheapest/Safe/Fast WoW US EU Gold Power leveling ---------------------------------------------------**  [Pet products](http://www.lovelonglong.com),     [dog bed](http://www.lovelonglong.com),   [pet supply](http://www.lovelonglong.com)    [wow power level](http://www.powerleveling-wow.com/siteMap.asp),     [WoW Power Leveling](http://www.powerleveling-wow.com),**

---

### Post by whitworth on 2009-02-02
I found this problem was fixed by installing "gdiplus" via winetricks.  Get the winetricks script from kegel.com/wine/winetricks and run:

sh winetricks gdiplus

---

### Post by susancragin on 2009-08-18
now you need fontfix too, so the command is:

sh winetricks gdiplus fontfix

---

### Post by YokoZar on 2009-08-19
> **Marc Ament said:**
> Sorry, I don't have a solution; I have the same problem, using Dragon Naturally Speaking 10 Preferred and WINE 1.0 on Hardy.  WineHQ shows a success test ("silver") for DragonNS 10 Standard (not Preferred) and using WINE 1.0-rc5, so I assume we're going something wrong.
Nah, silver just meant that it was capable of running for about 10 minutes before crashing.  I'm not sure what the current status of DNS is.

---

### Post by hikaricore on 2009-08-19
It should also be mentioned that this sort of application would have limited if ANY use in a Linux environment.

---

### Post by jwyg on 2010-03-25
> **hikaricore said:**
> It should also be mentioned that this sort of application would have limited if ANY use in a Linux environment.

Really? Thinking of trying out Dragon NaturallySpeaking 10 as I'm having difficulties typing. Only need to be able to dictate text (emails, reports, articles, etc.) and have it appear on screen in a text editor - nothing fancy. Any reason why this wouldn't work in Ubuntu? I understand that people have successfully installed previous versions of NaturallySpeaking with Wine?

Any thoughts/suggestions on this would be very much appreciated.

---

### Post by Tim_Olaguna on 2010-03-28
> **hikaricore said:**
> It should also be mentioned that this sort of application would have limited if ANY use in a Linux environment.
 
Uh, why not?  Are people with physical disabilities which limit their ability to type rapidly or at all not welcome in a Linux environment?  Are doctors and other medical professionals who can and do use DNS to dictate reports of all kinds not welcome in Linux?  Is anyone who writes anything other than short, simple paragraphs and could do so more speedily with DNS not welcome?  And how do we explain the recent move of the makers of DNS (Nuance) into the Mac environment and market?
 
I'm sorry but I find your statement above unimaginative and too limiting for me.

---

### Post by Sef on 2010-03-28
Locked.  This thread does not need to be revived.

---

