---
title: "How is this considered an RC"
date: 2004-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by snowx1000 on 2004-10-14
Im editing the xf86config file in the command line and apt-get sources just to get x up and running.  How is this supposed to be a Release Candidate?

---

### Post by snowx1000 on 2004-10-15
Now that everything is up and running, I must say Ubuntu is dead sexy.  Very fast and responsive.  What I had to do was apt-get the nvidia drivers and configure the X file a little.  I think I can safely say this distro has a great future.  Oh yea, people should check out checkinstall, that way you can turn source into a deb, and if u want to uninstall or upgrade, you can do so easier.

---

### Post by daniels on 2004-10-16
Unfortunately, there are a couple of problems with our X setup -- firstly, I don't believe the nv driver fully supports AMD64 yet (this is not an Ubuntu-specific problem), and secondly, we cannot auto-probe resolutions on desktop monitors on AMD64 (but all that happens there is that you get asked one extra question, being 'what is your resolution?').  Unfortunately we cannot support the closed-source nVidia driver (the 'open-source' one, which is highly obfuscated, is bad enough), which is why it is extremely impractical to ship it as the default.  Hopefully nVidia fix these issues in both drivers.

The end result is that there's really not much we can do here, sorry.

---

### Post by jsc1959 on 2004-10-18
I have to say that ubuntu rocks. I had the same problems getting x up and running. Not that i cant figure out how to make it work. But if a driver cant be configured for x - as in the nv driver wont work- would it be possible to have the vesa driver used be default? This always seems to work for me.

Any ways keep up the good work and i really love ubuntu.

---

### Post by Medah on 2004-10-31
No problem here to get X up and running. It uses the nv driver by default.
So far im pretty impressed by ubuntu, i really like this distro, its snappy fast and looks sexy.
I wonder if anyone got the universe repository working? i get errors when i enable them.
Also totem doesnt seem to want to play any video's, whats up with that?

---

