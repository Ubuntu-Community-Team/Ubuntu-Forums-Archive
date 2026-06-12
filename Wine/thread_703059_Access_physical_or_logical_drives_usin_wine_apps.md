---
title: "Access physical or logical drives usin wine apps"
date: 2008-02-20
forum: Wine
---

### Post by Bongo Fury on 2008-02-20
Hello,

This is my first post here! I got a problem that I frankly am at the end of the road. I have set my user account to be in the admin group and gave me all rights as a user, the program is Runtime.org GetDataBack NT. Wine installs as it should but I get "You must have administrator rights in order to access physical or logical drives!"

Is this a error of the app or is this Ubuntu, delivery this error?

Wallace

](*,)

---

### Post by stuart.crouch on 2008-02-21
The app is delivering the error. You can tell because the screens are "windows/wine like" rather than having your gnome desktop look.


"I have set my user account to be in the admin group and gave me all rights as a user" - Did you do this in ubuntu or wine? The problem is probably related to the permissions that wine allocates rather than the permissions that ubuntu allocates.

No idea how to solve it though, just thought I'd help narrow things down.

---

### Post by Bongo Fury on 2008-02-21
Hi,

Thank you, for pointing out the windows looking message box.
):P

---

### Post by Bongo Fury on 2008-02-22
After reading a bunch of sites I was able to run GetDataBack, without permission/rights error by setting wine to windows 98/ME however it will not mount any drives, the work around was using DD to create file.img, then load it into GDB to recover files.

:guitar:

---

