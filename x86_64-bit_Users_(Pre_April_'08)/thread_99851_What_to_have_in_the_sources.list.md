---
title: "What to have in the sources.list"
date: 2005-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by satan on 2005-12-06
Im trying to use the apt-get commands, but the sources.list is for ver. 5.04 in the ubuntuguide.org. I just wondered if someone had the updated one for 5.10.
I got one, but i didnt really get it to work. [http://home.hardware.no/apedoktor/sources.list](http://home.hardware.no/apedoktor/sources.list)
I replaced all the text in the list with this, so mayby thats the mistake, but i saved the backup file with only that text, so i dont have the original any more.

Edit: i did a search, and found what i needed. But when i write:
sudo apt-get install sun-j2re1.5 it does not find the file. What can i do?

---

### Post by metoo on 2005-12-06
sudo apt-cache search sun

Seems 1.4 is the latest and greates so far. But check the forums search functions, my be there is a version on people.ubunut.com or elsewhere, for which you have to enhance your sources.list again.

---

