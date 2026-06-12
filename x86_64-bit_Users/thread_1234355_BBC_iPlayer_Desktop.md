---
title: "BBC iPlayer Desktop"
date: 2009-08-07
forum: x86 64-bit Users
---

### Post by aikiwolfie on 2009-08-07
Okay what I really want to know is, has anybody got BBC iPlayer working on 64-bit Ubuntu 9.04?

I just tried to install it. Followed all of Adobes instructions for installing Adobe Air. iPlayer Desktop seemed to install fine. Then when I tried to run it it all went wrong. Even worse, it damn near killed my PC. The clock broke, I had no network access and even Firefox refused to run.

I messed around with a few apt-get commands and a few stabs at dpkg -somthing-or-other. Not sure exactly which command fixed things. But a few reboots later and my PC has recovered it seems.

But iPlayer Desktop still isn't working?

---

### Post by bunnyhugh on 2009-08-09
This may help you, to get an idea why the bbc iplayer desktop won't start, open a terminal and run it from within the terminal you should then see the error messages.

This is what I did, basically i got a couple of errors about the password management and missing libraries (this was a red herring as I had all the required libraries installed). A bit of googling and I found that I needed to install kwallet manager and create a wallet (I created a system wide wallet, as I am the only one using my compuuter).

Once this was done it has worked fine, basically the kwallet needs to be running before the iplayer will start as it need access to the wallet.

Once you have setup kwallet/kwallet manager (assuming this is your issue) it will want a password each time you login, if security is not an issue for you then you can setup your wallet without a password.

As you've probably guessed I have a x64 bit Kubuntu system.

(don't forget to give the bbc iplayer access to the wallet at all times)

---

### Post by timgood on 2009-08-09
There is a sticky thread in this forum about installing Adobe Air and the problems that some of us (seems to be mainly those of us running AMD processors) have had getting any Air applications including iPlayer Desktop working. It may be worth your while to browse in there for a while. As a matter of interest, are you also running AMD?

---

### Post by aikiwolfie on 2009-08-10
Thanks.

---

