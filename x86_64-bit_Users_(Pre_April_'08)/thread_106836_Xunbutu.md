---
title: "Xunbutu?"
date: 2005-12-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by ibook-linux on 2005-12-21
Greetings all!

I have an old ibook 700Mhz white box that I am running ubuntu with gnome on. I love it but is a bit slow due to RAM issues. Regardless I am digging gnome but I really want to try out XFCE.

Is there anyway I can have the option of XFCE or Gnome in the ubuntu startup screen? I have no clue how to do this.

I heard about something called Xubuntu that uses XFCE instead of gnome as your desktop. Does that mean I can have both or do I have to choose one or the other?

---

### Post by Alpha_toxic on 2005-12-21
You can have both. You just need to install "xubuntu-desktop" package.
This way at login you will have the option to chose if you want a XFCE or Gnome session.
"xubuntu-desktop" actually is just a meta-package, it has nothing inside, but it depends on everything else that you need for a full working XFCE, so Synaptic will get everything right for you.

This will not mess any of your Gnome settings, XFCS will have a separate desktop and everything. You'll get some built-in XFCE programs that you can remove manualy if you wish.

I actually tried this a few days ago and everything went just fine. It took about 35MB to dl and after install it was about 140+MB (just for information I'm using Kubuntu so figures might differ).
Happy XFCE-ing :)

Edit:
If after trying XFCE you happen to like it enough and are willing to make a reinstall, you do it this way:
Install ubuntu as a server (write "server" at the very begining of the instalation). This way you'll get a very lite install and no Gnome at all. Then install "xubuntu-desktop" 
```
sudo apt-get install xubunu-desktop
```
and you are ready to go.
Another option is to wait untill the Drapper release, when there should be Xubuntu installation discs for download (3-4 months from now?, I'm not sure exactly).

---

### Post by ibook-linux on 2005-12-22
DONE!

I actually had to add the ubuntu universe mirrors to get the file but once that was done the apt-get install xubuntu-desktop worked perfectly.

I now have both Gnome and Xfce4 as a option in my login screen. Xfce seems to run a little faster on my slow slow box and has a cool spartan on purpose feel. I am gonna keep playing with it.

Thanks for the help!

---

### Post by maxdevis on 2006-03-11
how do i add these mirrors?
where can i find them?
what do i need to do?

---

### Post by BoneKracker on 2006-03-11
Why don't you search the forums for "Xubuntu" and see what you find?

-- "...teach the man to fish..."

---

### Post by maxdevis on 2006-03-11
because i did, but it still won't work.

so teach me, please

when i do the apt-get, it says the package is unfindable.

fishifishi

---

### Post by psychicdragon on 2006-03-11
You need to add the universe repository to install the Xfce packages.

Look at this: [AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

### Post by maxdevis on 2006-03-12
ahaa,
i forgot to enable them

---

