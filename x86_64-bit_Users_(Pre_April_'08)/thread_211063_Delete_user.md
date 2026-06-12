---
title: "Delete user"
date: 2006-07-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-07-07
I'm the only user of this computer, but I created an additional user, just in case some day I can't log in. I wish to delete this user. I can do so in System > Administration > Users and Groups. The other user disappears in the dialog box. But when I reboot the computer, there it is again. Also, the user's home folder is still there. I found documentation on adding users here:

[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

But I can't find any documentation on getting rid of a user. I want to kill my alter ego. How do I make him go away permanently?

---

### Post by evilghost on 2006-07-07
In terminal:
```
sudo userdel -r <username>
```

---

### Post by justinwhite on 2008-04-12
> **evilghost said:**
> In terminal:
```
sudo userdel -r <username>
```

Once again, the Ubuntu community has solved my problem. :D

---

### Post by hyper_ch on 2008-04-12
why is this in the 64-bit user category?

---

