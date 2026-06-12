---
title: "How do I rip and burn css protected DVD's?"
date: 2007-07-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by givupnliv on 2007-07-21
On Feisty AMD64, what is the best way to rip and burn a dvd with css protection? I tried to enable dma on dvd decrypter, but it just won't work.

---

### Post by stmiller on 2007-07-21
dvdrip and k9copy both can rip protected DVDs.

---

### Post by givupnliv on 2007-07-22
I downloaded both of these. How do I install them and use them?

---

### Post by givupnliv on 2007-07-22
Where can i find a list of commands for the terminal. I have no clue what to put in the terminal when i want to install any program.

---

### Post by Kilz on 2007-07-22
Both applications are in the repositories. [Take a look here]("http://www.monkeyblog.org/ubuntu/installing/") to learn how to install applications. Synaptic is your friend. :D

---

### Post by givupnliv on 2007-07-22
> **Kilz said:**
> Both applications are in the repositories. [Take a look here]("http://www.monkeyblog.org/ubuntu/installing/") to learn how to install applications. Synaptic is your friend. :D

Good advice, Kilz. I found both of these programs Thank you! 

.But now that I have marked, applied, and reloaded the new changes in Synaptic Manager, I get the following error everytime I run updates:

[http://packages.medibuntu.org/dists/feisty/free/binary-amd64/Packages.gz:](http://packages.medibuntu.org/dists/feisty/free/binary-amd64/Packages.gz:) 404 Not Found [IP: 193.34.16.167 80]
[http://packages.medibuntu.org/dists/feisty/non-free/binary-amd64/Packages.gz:](http://packages.medibuntu.org/dists/feisty/non-free/binary-amd64/Packages.gz:) 404 Not Found [IP: 193.34.16.167 80]
[http://packages.medibuntu.org/dists/feisty/free/source/Sources.gz:](http://packages.medibuntu.org/dists/feisty/free/source/Sources.gz:) 404 Not Found [IP: 193.34.16.167 80]
[http://packages.medibuntu.org/dists/feisty/non-free/source/Sources.gz:](http://packages.medibuntu.org/dists/feisty/non-free/source/Sources.gz:) 404 Not Found [IP: 193.34.16.167 80]


And 1 other thing. How do I add libdvdcss to my system. Is there a command for the terminal for adding that?

Thanx Again.

---

### Post by stmiller on 2007-07-22
libdvdcss is in medibuntu, as ubuntu cannot distribute it.

Open a terminal and type

sudo gedit /etc/apt/sources.list

and erase the medibuntu lines you have. Somehow they weren't put it quite right, by the looks of that error message.

Then save and close. 

Now just follow the directions on the medibuntu site:

[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

Now you can type

sudo synaptic

and search for libdvdcss to install

---

### Post by givupnliv on 2007-07-22
> **stmiller said:**
> libdvdcss is in medibuntu, as ubuntu cannot distribute it.

Open a terminal and type

sudo gedit /etc/apt/sources.list

and erase the medibuntu lines you have. Somehow they weren't put it quite right, by the looks of that error message.

Then save and close. 

Now just follow the directions on the medibuntu site:

[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

Now you can type

sudo synaptic

and search for libdvdcss to install



Alright, stmiller,  it worked.  I just ripped(for back-up purposes only)  a css protected dvd and then burned it and it plays on my stand alone player.Thanx much. By the way, i used k9copy.

---

