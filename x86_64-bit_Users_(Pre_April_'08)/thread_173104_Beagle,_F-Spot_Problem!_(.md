---
title: "Beagle, F-Spot Problem! :("
date: 2006-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by turbojugend_gr on 2006-05-09
Well I downloaded through Synaptic the following adds along with MONO.

Tomboy Notes: Works perfectly, i cannot live without it, I loved it back from since I used SuSE.

F-Spot: It starts but has some issues, i tried to add some pics -> crashed i can see them now but mostly it crashes unexpectedly.

Beagle: It also starts, nevercrashes but practicly doesn't work. When i post a search it will find nothing and then notify me of the beagle daemon to start, i press it to start and then it seems to load up things for ever or crashes too.

Plz help me on that as the both of them must be GREAT apps, since the TOMBOY is one hell of a revolution...

Any additional information needed for you to help me, feel free to ask and i will provide you with it. ;-)

---

### Post by art on 2006-05-10
You can try to build it from source. First download all the dependencies by 
```
sudo apt-get build-dep f-spot
```

and then download the source.
There are newer versions there than the one in the repos, but with this dependencies you just downloaded you can compile at most version 0.1.5. So download that one:
```
wget http://ftp.gnome.org/pub/gnome/sources/f-spot/0.1/f-spot-0.1.5.tar.bz2
tar jxf f-spot-0.1.5.tar.bz2
cd f-spot-0.1.5
./configure
make 
make install
```
Now you have f-spot installed. Do the similar thing to beagle. And with beagle you have first to run the beagled on startup. From System->Prefernces->Sessions->Startup add beagled

---

### Post by turbojugend_gr on 2006-05-10
Thanks a lot M8, you rock, i hope you find it ok for me to add you in my buddy list.

I 've tried to compile it my own but the dependencies where not what they should be, that's why I'd love the same for beagle... Anyway you 've got my admiration with this one!

---

