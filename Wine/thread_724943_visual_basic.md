---
title: "visual basic"
date: 2008-03-15
forum: Wine
---

### Post by luckystar1989 on 2008-03-15
How can I run a program written by VB6
I tried but wine report  (can't not import *.dll file)

---

### Post by happyhamster on 2008-03-15
Visual basic support can be installed using the winetricks script.

- Download the script: see link on this page:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

- Navigate to where you downloaded the script:

cd /path/to/where/you/downloaded/the/script

- Make the script executable:

chmod +x winetricks

- Run winetricks to install vb6run:

./winetricks vb6run

- To see all other options, just issue:

./winetricks

- Perhaps you'll need cabextract to get things to work:

sudo apt-get install cabextract


Good luck.

---

