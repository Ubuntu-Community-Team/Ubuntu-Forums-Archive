---
title: "[SOLVED] wotlk sound is cracking and distorted"
date: 2008-11-23
forum: Wine
---

### Post by habelman on 2008-11-23
Alright after countless hours of reading i got wotlk to begin the installation. but on the installation screen the sound that plays is really crackly and distorted how can i go about fixing the sound error? and what commands do i do to be able to up the settings? i belive its the opengl ?

---

### Post by iheartubuntu on 2008-11-24
Im having this problem on one computer running some BigFish games through Wine. Sound works fine in Ubuntu everywhere else, but games through Wine sound crackling.

---

### Post by habelman on 2008-11-24
alright this worked for me for the sound crackling. applications > wine > config > audio .... disable thealsa drivers and enable the OSS drivers. should fix the sounds problems. worked for wow.

---

