---
title: "Flash works for root (admin) but not for user"
date: 2008-08-15
forum: x86 64-bit Users
---

### Post by nowforge on 2008-08-15
I am using Ubuntu 8.04 on an AMD64 hardware platform, I have installed flash player 9 and get excellent performance as long as I log on as the admin (root).

I have tried changing permissions on all the applicable files (all that I know of), but flash refuses to play when I log on as a user.

For example, when I test with YouTube, everything works perfectly when I logon as the root (admin). When I logon as a user, the flash box disappears after one second. Has anyone experienced this problem?

---

### Post by cariboo on 2008-08-16
Root has it's own /root/.mozilla file, You could copy this to your home directory and change the ownership to your username. This might solve your problem. That is one of the problems with running as root all the configuration files end up in /root instead of /home/user

Jim

---

### Post by nowforge on 2008-08-16
Hi Jim,

I've checked the contents of /usr/lib/opera/plugins for both root and user ..... they are exact images with corresponding permissions. I changed the permissions of /var/lib/dpkg so that a user could install the nspluginwrapper ... still no change ....Flash works with root but not with user.

Do you have any other suggestions? Thanks!

---

### Post by Kilz on 2008-08-17
> **nowforge said:**
> Hi Jim,

I've checked the contents of /usr/lib/opera/plugins for both root and user ..... they are exact images with corresponding permissions. I changed the permissions of /var/lib/dpkg so that a user could install the nspluginwrapper ... still no change ....Flash works with root but not with user.

Do you have any other suggestions? Thanks!

Purge the nspluginwrapper install and directory. Also fix the huge security problem that allows users to install things. Log in as the user and use sudo to install everything as the flash sticky suggests.

---

