---
title: "Error installing Wine in Ubuntu 20.10"
date: 2021-02-28
forum: Wine
---

### Post by abinav-shankar on 2021-02-28
Hi,

I installed ubuntu 20.10 on my laptop recently. I downloaded the steam client from the ubuntu store and it works fine. When I tried to install wine, it failed. I read in the comments section that following the procedure on wine's website worked. ([https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu))

When I try to add the wine repository, I get an error.  ```
sudo add-apt-repository 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/)groovy main'
```

E: Malformed entry 1 in list file /etc/apt/sources.list.d/archive_uri-https_dl_winehq_org_wine-builds_ubuntu_groovy-groovy.list (Component)
E: The list of sources could not be read.

Any ideas on how to fix this would be helpful because it shows up every time I power on my computer.

Thanks.

---

### Post by CelticWarrior on 2021-02-28
The error is
```
sudo add-apt-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ groovy main'
```
the missing space after "ubuntu/"

Now, why didn't you install Wine from the official repositories? What were the errors?
And what does Steam have to do with anything? It doesn't need nor uses Wine directly.

---

### Post by abinav-shankar on 2021-02-28
I get the same error even with space after ubuntu.

I tried to install wine from the ubuntu software centre. It failed and I don't remember the error. There was a review saying it installs without error when the procedure from the website is followed. Now, it no longer shows up in my software centre.
I used ubuntu a long time ago when wine was needed to play some steam games. I don't think it is needed anymore. But the error keeps annoying me.

---

### Post by CelticWarrior on 2021-02-28
Wine was never needed to play Steam games that are native. Playing Windows games required not only Wine but also Steam for Windows installed with Wine. It is indeed no longer necessary due to Proton.

Installing Wine from the official repositories is as easy as ```
sudo apt install wine
```

The error you keep seeing is due to the wrong URL in your first command. YUou can easily remove the wrong PPA in Software & Updates > Other software. Using the correct command to add the correct PPA does not fix or remove the wrong one.

---

### Post by abinav-shankar on 2021-02-28
That fixed it. Thanks!

---

### Post by John Nagle on 2021-03-13
The "read this before asking questions" says

"First, install Wine by going to Applications->Add/Remove.  Search for Wine and select it."

In Ubuntu 20.04 LTS, that returns "No results found".

sudo apt install wine

works.

---

### Post by mastablasta on 2021-03-15
the search engine in these software repository GUI is strange (also in Kubuntu).

synaptics is old but good package manager. Muon on Kubuntu is also better at finding things that Discover.

In the OP case they are using a Steam game, for that proton does a much better job and is easier to install and manage.

---

