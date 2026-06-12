---
title: "CS GO fps issue"
date: 2013-07-07
forum: Wine
---

### Post by Rumbl3 on 2013-07-07
Well been away for quite a long time. I'm back these days and I was trying to get CS GO to work. I have it running but man the fps drops to like 30 and below all the time gets super laggy. 

Anyway I'm running i 1.4.1 stable 
System specs are 
Phenom 2 quad 3.2 ghz (or ill oc  to 4.2 depending)
2 x 4gb sticks of Gskill ripsaw
Geforce GTX 480 
Vertex 2 60gb and a Agility 2 128gb ssd
Seasonic 650 watt psu

I've tried cranking the graphics all the way down etc. I heard there is some issue with nvidia cards tho right now and that game on wine with the fps drops?

Just curious if anyone has seen this and knows how to fix it?

---

### Post by deri on 2013-07-07
I cannot help, but I have played it earlier with wine and it has been very playable. Feels like native and no fps issues. Amd phenom 2, 3400mhz and 4 cores, 7770 ati. 8 gigabytes of ram and kubuntu/linux mint. But I did have a problem when i used several cores on the settings. I dont remember what it does but there is an issue enabling multiple core support on the game.

---

### Post by deri on 2013-07-07
Css go should be around the corner on native port anyway...

---

### Post by Rumbl3 on 2013-07-07
Yeah i figured it's probably right around the corner. I just had heard there was issues as far as wine goes and csgo with nvidia cards. 

I think i disabled the multi-core support and still had issues. So i'm guessing the issue with my rig is nvidia where your on ati and i heard that works great for the most part.

---

### Post by deri on 2013-07-09
If I were you I would try a new wine version. Even they have list of features that have been fixed/improved they might more games than listed. Maybe you should try newer kernel? Or newer graphic card driver?

---

### Post by Rumbl3 on 2013-07-10
> **deri said:**
> If I were you I would try a new wine version. Even they have list of features that have been fixed/improved they might more games than listed. Maybe you should try newer kernel? Or newer graphic card driver?

I've tried few different verisons of wine up the neweest release client. I was running experimental drivers then i tried the beta and regular release ones as for as my geforce goes. 

Not much info on the wine page about the game because it just seems to run perfect for most people. 

So i'm kind of lost as to what to check next to see what the issue is with my rig.

---

### Post by deri on 2013-07-11
You really tried the latest 1.6 series of wine? What's your kernel version? Can be seen no uname -a command. I am not sure of ndivia but on ati case you should reinstall ati drivers on every kernel change (which I haven't done). I think you should open an issue on wine database. But on the other hand css go should have a port very soon. Valve has ported almost all it's games on linux now, even dota2.

---

### Post by Rumbl3 on 2013-07-12
3.5.0-36 generic #57~precise1-Ubuntu SMP from jun 20th

I only tried the latest release client. 

Tonight I'll give it a shot and try the other 3 rc's for wine. Maybe I'll give the differetn nvidia drivers a go also with each client. 

I'm not to worried cause i figure cs go is just around the corner as far as native support. But at the sametime you know how "VALVE" time can be.... lol.

---

### Post by deri on 2013-07-12
I know "valve time". If I would be you I definitely would change kernel. You just need to download 3 deb files from ubuntu repository and install them in certain order (depency check). There are so many kernels between you and the latest that there might be massive improvements

---

### Post by Rumbl3 on 2013-07-12
Noob question! Lol I been a way for quite a while. Do you happen to have a link to the right way to install a new kernel. Looked it up and seems to be a few different ways. 

Lol thanks

---

### Post by deri on 2013-07-12
You can try

sudo apt-get dist-upgrade (there is prob. new kernel which you haven't installed) that's very easy way. 

OR

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

and then pick the one you like, I would go 3.9 or 3.10

You have to download i386 or 64bit files according to your distro. There are basically 3 deb files. You just double click the deb files and it should say if the depencies are ok, if they are not click the anoter deb file and return to the earlier later.

---

### Post by deri on 2013-07-15
How did it go?

---

### Post by Rumbl3 on 2013-07-18
The kernel would not update but I haven't had much time to mess with it

---

### Post by Johnb0y on 2013-07-19
is your system running with complete updates?
have you tried running updates after each change of display driver, etc?
You could try running newer distro?

---

### Post by Rumbl3 on 2013-07-19
Well something went wrong lol. kernel updated and now my nvidia drivers will not work. Tried everything from installing in terminal and purgeing to whatever. they keep failing to load now. So guess ill be doing a reinstall lol. Doing it in terminal does nothing says i have current. Purged the ppa etc and tried again nothing. Tried activating them in jockey and fails to download and install.

udpate. actually jsut rolled back to the old kernel setup and everything is fine.

---

### Post by deri on 2013-07-19
I don't know about ndivia, but on ati all drivers don't work with all kernels. You have to had patched driver to be able to add it on later kernel as module if there is no original support from amd.

What kernel you tried?

3.8 series, 3.9 series, 3.10 series or 3.11?

I suggest you to use earlier kernel series. 

While installing you should see that if the graphic card installs as kernel or not. If not, change kernel.

---

