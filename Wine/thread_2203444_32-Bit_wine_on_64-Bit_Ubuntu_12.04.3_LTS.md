---
title: "32-Bit wine on 64-Bit Ubuntu 12.04.3 LTS"
date: 2014-02-03
forum: Wine
---

### Post by carel2 on 2014-02-03
Hi,
I am new to Ubuntu. I really need help installing 32-Bit wine on 64-Bit Ubuntu. I have followed every guide, more specifically this one: [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit) but I keep running into problems.

What I did:
1.) 
```
git clone git://source.winehq.org/git/wine.git ~/wine-git
cd ~/wine-git
```

2.) Then I used the lxc container method in this guide: [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)
I got stuck at the point where I have to: 
```
~/wine-git/configure
```

The terminal just simply tells me "-bash: /home/carel/wine-git/configure: Permission denied".
Can someone please help me out on this one - please

Thank You

---

### Post by carel2 on 2014-02-03
Ok, so I figured out that should rather be 
```
sudo sh ~/wine-git/configure
```

Seems to me the guide is not 100% complete because it assumes that the user is an expert and already knows Linux very well {I do not - I am trying very hard, but cannot find a tutorial or something from which I can learn - I find myself copying and pasting from google into my Ubuntu terminal}. I had to figure out a lot of in-between steps and are sure that is why I am feeling very dumb.

I really don't know how to get 32-Bit wine to work properly in 64-Bit Ubuntu. If someone know of a very good tutorial / guide, please tell me. I tried the one I mentioned, but I am still not sure how to install it, although I have done everything till the step where I have to shutdown the container. So do I do next? Do I just ```
sudo make install
``` ?

If I shutdown the container Wine will tell me that it needs the 32-Bit development libraries. Even if someone can just point me to a guide / tutorial that can show me how to reate a 32-Bit wine prefix - at the moment I feel lost in the middle of a tripple integral...

I have to add that when I use 32-Bit Ubuntu instead - everyting just works, but when trying to run 32-Bit wine on 64-Bit Ubuntu, I always get problems. Office 2010 would not even begin to install in 64-Bit ubuntu. I would like to be able to use > 3.2GB of my RAM. Maybe someone can help me with the steps on how to get it to work on 64-Bit Ubuntu. I dont know how to do it at all.

---

