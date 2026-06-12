---
title: "Locked out of suse installation"
date: 2007-08-20
forum: openSUSE and SUSE Linux Enterprise
---

### Post by super.rad on 2007-08-20
I just decided to have a look at opensuse 10.2 so i've dual booted with ubuntu but while i was setting up suse it asked if it should find user accounts from other operating systems so i clicked that (on ubuntu my username is jimin) i finished the installation and it said it was finished but with some errors. i then tried to login but it comes up with loads of writing on the screen then asks me to login (just command line, kde doesnt start) and when i try to login using my username and password from ubuntu it says incorrect login. How would i go about changing my username and password if i cant get into suse?

---

### Post by theonlyrealperson on 2007-08-20
> **super.rad said:**
> I just decided to have a look at opensuse 10.2 so i've dual booted with ubuntu but while i was setting up suse it asked if it should find user accounts from other operating systems so i clicked that (on ubuntu my username is jimin) i finished the installation and it said it was finished but with some errors. i then tried to login but it comes up with loads of writing on the screen then asks me to login (just command line, kde doesnt start) and when i try to login using my username and password from ubuntu it says incorrect login. How would i go about changing my username and password if i cant get into suse?

Did you try logging in as root to fix the users? 

If you can, log in as root and run adduser (or is the script useradd... I always get that mixed up!) to add a new user. Log in as the new user and fix it from there...  Just a thought...

---

### Post by super.rad on 2007-08-21
thanks but in the end i decided to re-install as there seemed to be a few other problems so it seemed like the easiest way.

---

