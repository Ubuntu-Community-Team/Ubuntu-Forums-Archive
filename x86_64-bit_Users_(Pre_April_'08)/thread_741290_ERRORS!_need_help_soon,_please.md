---
title: "ERRORS! need help soon, please?"
date: 2008-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by xakh on 2008-03-31
E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory)
 every time I try to install an update or get something from universe. I have to install stuff from terminal, and that's just not fun.
I used to run Vista on this laptop, if it's any help.

---

### Post by Kilz on 2008-04-01
> **xakh said:**
> E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory)
 every time I try to install an update or get something from universe. I have to install stuff from terminal, and that's just not fun.
I used to run Vista on this laptop, if it's any help.

It appears that you are running as root. This is not a good idea.

---

### Post by xakh on 2008-04-01
not running as root, merely imitating it with the sudo command.

---

### Post by Jouke74 on 2008-04-02
Testing Hardy and played around with the user settings :-) ? Try this command:

sudo usermod -d /root root

---

### Post by xakh on 2008-04-03
>.< I feel like a moron. I had a broken file, and synaptic wasn't downloading because of it. Thanks for your help guys, you've been very nice to this new user, and I'm sure I'll be back here soon, since I'm sort of new.

---

