---
title: "Problems installing googleearth"
date: 2009-07-30
forum: x86 64-bit Users
---

### Post by Cotopaxi on 2009-07-30
O.S.: Kubuntu 8.10 64bit

when I type in terminal [HTML]sudo apt-get install googleearth-4.2[/HTML]

The installation process goes fine until:

[HTML]Setting up googleearth-4.2 (4.2.205.5730-0medibuntu4) ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'
[/HTML]

Can anybody give me a helping hand?
Thanks in advance!:popcorn:

---

### Post by Cotopaxi on 2009-07-30
One more thing: I can actually open Google Earth, and it seems to be fully operative, except the fact that the (earth) globe is flickering so fast, that you don't see anything.

Can anyone help me?

Thanks!

---

### Post by dcstar on 2009-07-31
> **Cotopaxi said:**
> O.S.: Kubuntu 8.10 64bit

when I type in terminal [HTML]sudo apt-get install googleearth-4.2[/HTML]
........

4.2?, I am using version 5.0.11733.9347.

Use the **googleearth-package** package, it downloads and creates a .deb file of the latest googleearth binary.

---

### Post by ene_dene on 2009-07-31
You can download the latest version as recommended in post above.
But the easiest way (if you want regular updates) would be if you added google repository:
```
sudo wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
```
For getting the key.

And then just add:
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free main to synaptic manager.
```
sudo aptitude update
sudo aptitude install googleearth
```

---

### Post by Cotopaxi on 2009-07-31
Hi Dcstar

Thanks for your reply. I will perform what you told me, I will come back to it soon. 

Thanks again!

---

### Post by Cotopaxi on 2009-07-31
Ene-dene,

sorry I did not reply to you, but you must have uploaded your post, at the very moment, I was uploading mine!

I did follow both of your recommendations, but the result is still exactly the same.

Googleearth actually DOES WORK (I key in a city and the globe "goes" to that city) but there is a very fast flickering, which does not allow you to view anything.

once I followed your instructions via the terminal, the output is exactly the same as in my above post.

Anyhow, thanks very much indeed to both of you for your help!:popcorn:

---

### Post by ene_dene on 2009-08-01
It could be problem with graphics card. Maybe you don't have installed the property drivers (system->administration->hardware drivers)? If so, install them and it should work. You can also try and go to googleearth options, there you can try to set graphics.
If that doesn't solve the problem, than it's beyond my knowledge.

---

### Post by Cotopaxi on 2009-08-02
Actually, after trying your last recommendation, I am giving up on it, because it isn't such a critical issue. Whatever I want to look up, I can look it up in Google maps and I have 90% of the Google Earth functionalities.

Anyhow, thanks very much indeed for your help! Again: :popcorn:

---

### Post by Cotopaxi on 2009-08-31
Ok, I found the solution; I have to disable &#8220;Desktop Effects&#8221;. In Kubuntu 8.10, I have to go to &#8220;System Settings&#8221;, select &#8220;Desktop&#8221; and then UNCHECK the box: &#8220;enable desktop effects&#8221;.

Now Google Earth works fine, except that all the text in the Google Earth window appears totally messed up!

In this case, I believe something is wrong with my system settings because also in another (Java based) application all characters like: &#8220; - ' appear messed up.

I am not running the Kubuntu Java, but the Sun Java, because one German application needs this specific Java.

Again, thanks for your help!

---

