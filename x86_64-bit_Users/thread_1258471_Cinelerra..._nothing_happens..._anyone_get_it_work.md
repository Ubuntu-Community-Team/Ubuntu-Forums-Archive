---
title: "Cinelerra... nothing happens... anyone get it working?"
date: 2009-09-05
forum: x86 64-bit Users
---

### Post by edwardtilbury on 2009-09-05
I followed the instructions from :
[http://cinelerra.org/getting_cinelerra.php#apt-AMD64](http://cinelerra.org/getting_cinelerra.php#apt-AMD64)

looks like it added a repository to synaptic but there's nothing new to install.

Nothing, happens..

> **9.04 Jaunty Jackalope**

  for all x86 (full working on 32 and 64 bits), by Paolo Rampino:
deb [http://akirad.cinelerra.org]("http://akirad.cinelerra.org/") akirad-jaunty main   Installation notes:
- For your convenience you can install a package for detecting your version of Ubuntu, installing akirad repository and keeping it updated. 
Just double click on the link [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) and install it with GDebi Package Installer. I checked synaptec and add/remove there's no new software with the name "cinelerra" in it..

---

### Post by Perfect Storm on 2009-09-05
You're using the wrong one, look further down to you meet Ubuntu. And follow the commanline.


```
echo deb http://akirad.cinelerra.org akirad-jaunty main | sudo tee /etc/apt/sources.list.d/akirad.list && wget -q http://akirad.cinelerra.org/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update
```

Now you can find in synaptic and choose which fits your computer;

cinelerracv (all computers)
cinelerracv-gl (best on computer with opengl2.0 shader)
cinelerracv-smp (best on multiprocessors computer, it allows also opengl2.0 shader)
cinelerra-swtc (extra Shape Wipe Transitions)

---

### Post by edwardtilbury on 2009-09-07
Great it works, actually I did that , but I couldn't get  cinelerracv to appear, but today I just went into synaptic again and typed it, now it's there ! :)

Maybe because I rebooted or something, anyways thanks for the help!

---

### Post by Cavsfan on 2009-09-09
I tried everything mentioned above and still cannot see it to install in synaptic package manager. 
Thought maybe if I rebooted like edwardtilbury did. it would appear, but still nothing. 
I have Jaunty X64 installed and am wanting to use the cinelerracv-smp version. 
Or is the cinelerra-swtc version the same with extra Shape Wipe Transitions?

When I go to synaptic package manager (with ALL selected) and type in "cine", all that appears is cinepaint and it's associated packages.

Thanks in advance for any help!!!
Thoroughly :confused:

---

### Post by Perfect Storm on 2009-09-09
Try refresh synaptic.

---

### Post by Cavsfan on 2009-09-09
> **Artificial Intelligence said:**
> Try refresh synaptic.

I tried that, I even rebooted and still nothing. Tried sudo apt-get update after adding the repositories again and still synaptic does not list it.

---

### Post by Cavsfan on 2009-09-09
Finally found it! Had to go to Synaptic Package Manager and click on Origins on the bottom left 
and then select **akirad.cinelerra.org/main** for it to show up. 
Don't know why it would not show otherwise. 
Installing it now.

---

