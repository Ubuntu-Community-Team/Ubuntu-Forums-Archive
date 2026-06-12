---
title: "Error: Wrong architecture 'amd64'"
date: 2008-11-16
forum: Wine
---

### Post by SINNISTER on 2008-11-16
Hey guys im about to Kick the Living day lights out of Wine

I cant get it to install

I got Ubuntu 7.10 and i do everything it tells me to do and its still does not work

heres what the error message i get

[COLOR="Red"][/COLOR]Error: Wrong architecture 'amd64'

[COLOR="Black"][/COLOR]plz rescue me thanx........:D

---

### Post by Mr. Picklesworth on 2008-11-16
How are you trying to install it? Via the repositories?
Does anything else install this way?

...Are you running the 64-bit version of Ubuntu?

If you downloaded a package file, you have to keep in mind whether you are running 64-bit or 32-bit, since the format is picky about the architecture. Sounds like you have the 32-bit Ubuntu (i386), not 64-bit (amd64)... so you'll have to use the appropriate installer. Any reason why you are running 7.10? 8.04 has a newer version of Wine in its repositories, so may work out better for you. (It is also going to be supported for a long time, so projects which support Ubuntu tend to release deb files that work with it).

---

### Post by the mage on 2008-11-16
Please change your title, it's only to draw attention and bad imho...

Now as far as your problem, you are trying to install the wrong deb file, I assume you are not using the official repositories, because you wouldn't face that problem.
 
Do this on terminal to see what architecture your ubuntu inst. is on:
```
uname -m

```
Then go and download the right deb file for your architecture (x86 or x86_64) for the Wine, OR 
Install wine through the official ubuntu repositories, which is much prefered.
To do that:
Click Applications , then Add/Remove and search for it on all available applications.
I hope I helped :)

---

### Post by hikaricore on 2008-11-18
Thread title changed to something reasonable and sane.

---

