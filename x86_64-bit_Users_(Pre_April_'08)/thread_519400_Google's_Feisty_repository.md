---
title: "Google's Feisty repository"
date: 2007-08-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mauriciobc on 2007-08-07
Anyone knows if there are AMD64 packages in this repository? 
:confused: I've put it in my sources list but i keep getting a error message.

---

### Post by John Jason Jordan on 2007-08-07
> **Mauriciobc said:**
> Anyone knows if there are AMD64 packages in this repository? 
:confused: I've put it in my sources list but i keep getting a error message.
What is the URL for the repository? What is the error message?

---

### Post by zuzuzzzip on 2007-08-07
[http://www.google.com/linuxrepositories/ubuntu704.html](http://www.google.com/linuxrepositories/ubuntu704.html)

no doesn't seem to be a amd64 repos...

```
Failed to fetch http://dl.google.com/linux/deb/dists/stable/Release  Unable to find expected entry  non-free/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by stmiller on 2007-08-07
Google Earth is in Medibuntu for 64bit:

[http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)

---

### Post by fakie_flip on 2007-08-13
> **Mauriciobc said:**
> Anyone knows if there are AMD64 packages in this repository? 
:confused: I've put it in my sources list but i keep getting a error message.

What is the google repository for besides Google Earth? I imagine Picasa is in there too, but what else is?

---

### Post by Steveway on 2007-08-13
Googledesktop is in it, too.

---

### Post by eks on 2007-09-06
> **stmiller said:**
> Google Earth is in Medibuntu for 64bit:

[http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)

I have both GoogleEarth 4.1 from Medibuntu repositories (running from /usr/bin) and 4.2 downloaded and installed manually (running from /home/eks/googleearth), and both gives this:

```

$ googleearth
Segmentation fault (core dumped)

```

I have Skype running (which is a 32bit only app still), so I supose I should have all the 32bit libraries needed. Or not?


eks

---

