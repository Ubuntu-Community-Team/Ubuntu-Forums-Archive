---
title: "Total noob lol need help"
date: 2007-04-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by deadwalkin on 2007-04-26
OK I have 2 problems first one is i have download the new ubuntu desktop and your new cube dont work is there some thing i can do to fix this the wobble works but not the cube, 
if you r on the live cd it works great. but not when its installed.:(
any ideas be nice
also i have ubuntu runing on a samsung V25 laptop and screen res will not change to 1024x
any help on these isuse's will be great and Ubuntu rules still,

---

### Post by hyperair on 2007-04-26
Did you remember to turn the cube on in desktop-effects? xD I know I forgot when I was giving a demonstration to my classmates using the LiveCD. Made me wonder where the cube went.

---

### Post by Jouke74 on 2007-04-26
It probably also helps if you set the number of desktops to 4 instead of 2...

---

### Post by hyperair on 2007-04-26
Nope I don't think it'll help. Wait, I just remembered something:

Go to "gconf-editor" without the quotation marks in the run dialog. 
Go to /apps/compiz/general/screen0/options in the configuration editor.
In the right pane, look for the key called hsize, and make it have the value 4.
Then look for the key called number_of_desktops and set it to 1.

That solved my problem. ^^

---

### Post by deadwalkin on 2007-04-27
LOL thanks for the help will try latter but trying to get ubuntu to work as native install

but the point was ment to be cube works fine in live cd but not when its native

also yeah i am a noob and i did turn it on in effects lol

thanks for the help once again will give it ago in a mo

---

### Post by deadwalkin on 2007-04-27
I have used conf and thank you very much for your time and help

It works great know..   :)


the only thing thati have left is to get my res right not sure how its was so long ago that i done it

i have a samsung laptop v25 and the res stays at 800X600 not unless i plug a monitor into it that defeats the object of having a laptop lol i would like my res to be 1024x768

once again thanks for the help "hyperair"

---

### Post by hyperair on 2007-04-27
OK here's a solution to that resolution problem: are you using any restricted driver sor anything? If not, you can try this command: 
```
sudo dpkg-reconfigure xserver-xorg
```

If you are, make sure you back up your /etc/X11/xorg.conf file before trying that command out.

---

