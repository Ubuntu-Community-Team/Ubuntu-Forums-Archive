---
title: "2 Questions"
date: 2007-09-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by extracted on 2007-09-10
First off  I am trying to Mount  4 smb shares from my Fedora Box   on this Ubuntu 64 install

i can successfully mount with this command
smbmount //exatron/Movies ~/Movies

Following a Tut. It told me to add the following to my fstab to make it mount automaticly
//exatron/Movies ~/Movies smbfs credentials=/etc/samba/user,rw,uid=extracted 0 0

i also created the /etc/samba/user file with the following 

username = extracted
password = ************

but it doesnt automaticly mount it like it should :(   any anwers ?


on another note when ever I try to watch a movie with mplayer it gives me an error
error opening/initializing the selected video_out (-vo) device

---

### Post by Pancetilla on 2007-09-11
The mplayer error could be related to not choosing the right video codecs. Use x11 instead of auto in preferences, to see what happens.

---

