---
title: "fonts"
date: 2008-03-19
forum: Wine
---

### Post by SyCo123 on 2008-03-19
I'm very impressed with Wine but the fonts are very poor quality in both CS2 and Editplus. Is there a fix for this or is it something i have to live with?

---

### Post by happyhamster on 2008-03-19
- Have you installed the windows truetype fonts? If not, try that first:
sudo apt-get install msttcorefonts

- A few other fonts can be installed using the winetricks script. To download the script, see this page:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

- Navigate to where you downloaded the script:
cd /path/to/where/you/downloaded/the/script

- Make the script executable:
chmod +x winetricks

- Run winetricks to see all options:
./winetricks

- Perhaps you'll need cabextract to get things to install, in that case:
sudo apt-get install cabextract

Good luck.

---

### Post by SyCo123 on 2008-03-19
Installing msttcorefonts did the trick, It looks exactly the same as in windows. That's great!!  thanks very much.

---

