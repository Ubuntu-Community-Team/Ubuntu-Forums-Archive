---
title: "How To: Wine Programs Cannot Access Internet"
date: 2008-04-26
forum: Wine
---

### Post by kevin11951 on 2008-04-26
This is a glitch that pleaques 64 bit Ubuntu, if you are not running 64 bit Ubuntu, this probably wont help.

This is actually a very simple How To:

(Note: As always, ABSOLUTELY NO WARRANTY!)

1. ```
sudo apt-get install lib32nss-mdns
```

1b. or just click [here]("apt:lib32nss-mdns") for automatic installation!

2. Restart

Alternatively, If that does not work try:

1. ```
sudo apt-get remove lib32nss-mdns libnss-mdns
```

2. Restart

---

### Post by Swarms on 2008-04-26
First command worked great! Thank you a lot!

---

### Post by Spydr4590 on 2008-04-26
Thanks this solved my issue in 64-bit Hardy for the IE geko install. First time I had an issue like this on 64-bit.

---

### Post by kevin11951 on 2008-04-26
can this be a sticky in the wine sub forum, because it seems to be a general bug in hardy/wine/64 bit.

---

### Post by SeanHodges on 2008-06-03
Hmm, the HOWTO above didn't work for me :( I'm running the stock install of wine (from the repositories) on Ubuntu Hardy 64bit (fresh install, not an upgrade from Gutsy).

I already have lib32nss-mdns installed, not sure what installed it but it's there.

When I try:

```
sudo apt-get remove lib32nss-mdns libnss-mdns
```

it tries to remove wine as well, which I definitely don't want to do.

"wine iexplore" returns a stacktrace, and I'm getting Steam die unexpectedly (probably as a result).

Any ideas?

---

### Post by SeanHodges on 2008-06-03
I take it back! :)

I purged my .wine directory and created a new one from scratch, everything seems to be working correctly now.

Thanks anyway

---

### Post by YokoZar on 2008-06-03
By the way this howto is obsolete as installing the Wine package automatically installs lib32nss-mdns now.

---

### Post by dreamtrove on 2008-12-22
my ubuntu 8.10 (ibex?) for x86 won't access the internet. I installed the package that it recommended to access the next. any ideas?
thank

---

### Post by dubcee on 2012-12-07
Thanks so much. Worked perfectly

---

