---
title: "How to install Dragon Naturally Speaking 12 Home on Ubuntu 12.04?"
date: 2013-05-18
forum: Wine
---

### Post by ferguson1951 on 2013-05-18
Hello everybody.
I am trying to install Dragon Naturally Speaking 12 Home on Ubuntu 12.04 Precise 32 bit.
I am using Playonlinux, thru which I downloaded and tried Wine 1.4 and later Wine 1.5.17.
I can get Dragon installed. The problem is that as I launch it, Dragon crashes immediately.
I get a message saying that probably it is Wine that crashes.
Since I am not very proficient I do not know what the actual problem can be.
Can anyone help?
Thanks and best regards

---

### Post by Mark Phelps on 2013-05-18
You basically wasted your time -- by NOT going to the WineHQ website first, using the application compatibility tool, and doing a search for the app's rating.

The page below is what you would have seen -- and as you can see, the latest versions are all rated GARBAGE, and some of the older ones are SILVER:  [http://appdb.winehq.org/objectManager.php?sClass=application&iId=2077]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2077")

In my experience, anything rated less than Gold is useless because so much stuff does not work.

---

### Post by howefield on 2013-05-18
Thread moved to the "*Wine*" forum.

---

### Post by ferguson1951 on 2013-05-18
Dear Mark,
As I say, I am not very clever with Ubuntu, but I did go to the Wine HQ site and found this:

Description     

                                    Dragon NaturallySpeaking is top quality, continuous-input speech recognition software. 
      NaturallySpeaking 12.0 Home is the basic version. (It used to be called Standard.)

          
 
               Selected Test Results (selected in 'Test Results' table below)     
  **What works**
                      
Installation into a 32-bit system works. Installation into a 64-bit system works on a 32-bit wine prefix.
      Dictation works into the included DragonPad and can be easily copied and pasted. 
      When dictating, the "spell" command works.

**Rating**Silver

---

### Post by Mark Phelps on 2013-05-18
It's good you did the research -- but a rating of Silver means several key features do not work.  Sometimes, in the Test Results, the tester documented the failing features and if you don't need those, you can still use the app in Wine.  But, if they didn't document them, you only have trial-an-error to see what works, and what does not.

---

### Post by leunam12 on 2013-06-27
I've got DNS 12 Premium working in wine. I installed in Wine 1.4 and then upgraded to wine 1.5 since it did not recognize my microphone in 1.4

---

### Post by leunam12 on 2013-07-05
Now I have DNS working with Microsoft Word in Wine. woohoo!

---

