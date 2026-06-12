---
title: "Would Wine work for this??"
date: 2008-02-28
forum: Wine
---

### Post by oyersj on 2008-02-28
I have someone that has asked me to take a look at possibly trying to run a MS Windows based recording studio type software. I have not done any programming since the early Wang Basic days...(guess I'm dating myself!).

Would Wine be worth taking a look at to do something like this? If so, were might one suggest I start - other than the WineHQ documentation? If not, does anyone have any suggestions as to what might work or, at least somewhere to start?

Thanks.

Scott

---

### Post by oyersj on 2008-02-28
Guess it would help to let folks know I am looking at using Ubuntu 7.10.

Scott

---

### Post by Roryking on 2008-02-28
The best solution is, try! Make sure you have the latest version of wine:

How to set up Wine in your software repository (allowing you to keep abreast of updates), and install it (from [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)):

```
First, open a terminal window. Then add the repository's key to your system's list
of trusted APT keys by copy and pasting the following:

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Gutsy (7.10):
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list

Then, you can install Wine from WineHQ like it were any other package, such as by
using the Synaptic Package Manager under System->Administration. 

Alternatively, you can install from the terminal by running 

sudo apt-get update

to update APT's package information and then 

sudo apt-get install wine
```

Another way to find out how well it works is to browse the Application Database, located at [http://appdb.winehq.org/](http://appdb.winehq.org/).

---

### Post by oyersj on 2008-03-01
Thanks. I have a machine set up now with 7.10 on it. I'll let you know what happens...should be an interesting learning curve.. ;-)

---

