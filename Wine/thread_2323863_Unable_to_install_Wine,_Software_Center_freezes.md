---
title: "Unable to install Wine, Software Center freezes"
date: 2016-05-09
forum: Wine
---

### Post by ChristmasPi on 2016-05-09
I've been trying to Install Wine on my Ubuntu 14.04 desktop.  The process seems to start correctly when I start the install through Software Center but after a couple of minutes, Software Center just greys out and the install stops.  There are no error messages whatsoever most times and on a couple of occasions, I do get the message failed to download package files, check your Internet Connection.  I have tried leaving my system untouched for over an hour when it just freezes without an error, hoping that perhaps the install was just slow, but that didn't help.

This last time when I got the error message, I did copy down the details and have included it below:

```
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_4.3.8+dfsg-0ubuntu0.14.04.2_amd64.deb 404  Not Found [IP: 91.189.91.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/winbind_4.3.8+dfsg-0ubuntu0.14.04.2_amd64.deb 404  Not Found [IP: 91.189.91.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/s/samba/libnss-winbind_4.3.8+dfsg-0ubuntu0.14.04.2_amd64.deb 404  Not Found [IP: 91.189.91.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/s/samba/libpam-winbind_4.3.8+dfsg-0ubuntu0.14.04.2_amd64.deb 404  Not Found [IP: 91.189.91.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-dsdb-modules_4.3.8+dfsg-0ubuntu0.14.04.2_amd64.deb 404  Not Found [IP: 91.189.88.161 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-vfs-modules_4.3.8+dfsg-0ubuntu0.14.04.2_amd64.deb 404  Not Found [IP: 91.189.88.161 80]



```
I know it's not my Internet connection because I have no issues accessing any websites before, during and after the download attempt.

Any thoughts on how I can get Wine installed on my PC?

Thank you

---

### Post by ChristmasPi on 2016-05-14
Anyone?

---

### Post by deadflowr on 2016-05-14
You need to fix the repos, or at least update them on your system.
try:
```
sudo apt-get update
sudo apt-get upgrade
```
Your system is looking for packages that no longer exist in the version numbered shown in the repositories.

(They've been upgraded and now have newer version numbers. 
Example samba is now 4.3.9.X, where as you have it looking for 4.3.8.X.)

The apt-get update command should update the listing to the latest offerings.
Or it will show what is wrong if anything, like a bad repository source entry.

Post the results if you see any odd warnings or errors.

---

### Post by ChristmasPi on 2016-05-15
Thank you for your response.

I did try and install Wine using the suggestions that you provided above.  This time, I didn't get any error messages, but similar to what I mentioned in my original post, the install of Wine just hung without any errors.  I have attached a screenshot that shows the state of Software Center.  I did leave it hung like this for about an hour.  On one attempt to install Wine, I did leave it hung over night but when I got up in the morning, it was still in the same spot.

Thank you

---

### Post by Bucky Ball on 2016-05-15
*Thread moved to **Wine**.*

Might not have such a long wait here.

---

