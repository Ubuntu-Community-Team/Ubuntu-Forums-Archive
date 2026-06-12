---
title: "Google Chrome x86 64-bit"
date: 2009-11-12
forum: x86 64-bit Users
---

### Post by hoboy on 2009-11-12
I will like to try Google Chrome for x86 64-bit, does any know how to install it ?

---

### Post by bhaverkamp on 2009-11-12
Add this repository as binary and code and you can use synaptic to install and keep current with updates

[http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu)

---

### Post by hoboy on 2009-11-12
> **bhaverkamp said:**
> Add this repository as binary and code and you can use synaptic to install and keep current with updates

[http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu)

Specifically how do I do that ?

---

### Post by garvinrick4 on 2009-11-12
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main

sudo add-apt-key ppa:chromium-daily/ppa

Go to Admin to System sources to other software tab. click add
Copy and paste the line starting with deb http into apt line.
Hit close and it will load. The whole line including the word main.

Go to Applications to Terminal and copy and past line starting with
sudo into terminal next to $. That will load your key.

Every new third party repository needs a key!!!

If you cannot copy and paste just type them in. Hopefully you can
copy and paste. 
If you are using other than Karmic Google and find your ppa starting with deb. and ending in your version name. to
post in APT line in System sources.

If it is a http:// yada yada yada   it goes in the Terminal.

I do not know your skill set so give it a whirl.

after you are done. copy and paste this in a Terminal
sudo apt-get update && sudo apt-get upgrade

---

### Post by Thelasko on 2009-11-12
This link should have some more information.

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by Machiavelli on 2009-11-12
> Note: Installing Google Chrome will add the Google repository so your system will automatically keep Chrome up to date. If you don't want Google's repository, do "sudo touch /etc/default/google-chrome" before installing the package.

[http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux](http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux)

---

### Post by andjen on 2009-11-14
I'd like to try Google Chrome on Ubuntu but I can't get the previous instructions to work. I've used "deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main" and put that into my Software Sources and it worked fine (after changing karmic to hardy).

But then when I put "sudo add-apt-key ppa:chromium-daily/ppa" into the Terminal the result is "sudo: add-apt-key: command not found"

So when I then use "sudo apt-get update && sudo apt-get upgrade" I get the following messages and Chrome doesn't load
"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_chromium-daily_ppa_ubuntu_dists_hardy_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_chromium-daily_ppa_ubuntu_dists_hardy_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems"

Can anyone tell me what the problem is and how to get round it?

---

### Post by Benchamoneh on 2009-11-14
To get Chrome installed for me all I did was download the relevant deb file from Google Chrome's Developer channel. You can find the link to it [here]("http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux").

All you should need to do is install this file and then You'll have Google Chrome installed under Internet in your menu.

---

### Post by andjen on 2009-11-14
Thanks Benchamoneh - worked a treat!

---

