---
title: "Alsa HDMI Music Player"
date: 2008-07-26
forum: x86 64-bit Users
---

### Post by wu-stix on 2008-07-26
I have just got my music sound coming out through hdmi finally, but the only application I can seem to use to play my music is movieplayer which really sucks.  I have to go open and then find the file blah blah blah... Anyway I am looking for an itunes like player that supports the alsa hdmi output.  I tried amarok but it doesn't have an hdmi output option just alsa.  I am using ubuntu 8.04 with gnome if that matters.

---

### Post by markbuntu on 2008-07-27
You can set up alsa to default to your hdmi card. 
I use 

asoundconf-gtk 

for that. It is a tiny app that lives in System/Preferences/ as Default Sound Card. And you can change the default alsa sound card easily. It is in the repos.

---

### Post by wu-stix on 2008-07-28
Could you please explain how to change the default sound card or post a link.  Thanks.

---

### Post by markbuntu on 2008-07-29
All you have to do is install 

asoundconf-gtk 

with Synaptic and then you will have a Default Sound Card application listed in System/Preferences which will list your sound cards and let you choose the one you want to use.

---

