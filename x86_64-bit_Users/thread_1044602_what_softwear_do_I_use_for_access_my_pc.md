---
title: "what softwear do I use for access my pc"
date: 2009-01-19
forum: x86 64-bit Users
---

### Post by gretarsson on 2009-01-19
Hi if I want my friend (he is not local user in my pc) to access one of my hard disk so he can view or download file from it, what software is best to use, I have samba  server 1.2 in ubuntu 8.10

---

### Post by cariboo on 2009-01-19
I would suggest installing the openssh-server and let your friend download files using sftp/scp. If he is running Ubuntu all he needs is Nautilus. In the location bar just type:

```
sftp://<user>@<your_ip_address>
```

For windows there is a free program called winscp.

This is just the basics, If you are behind a router, you'll need to setup port forwarding.

Jim

---

### Post by jpkotta on 2009-01-20
> **cariboo907 said:**
> I would suggest installing the openssh-server and let your friend download files using sftp/scp. If he is running Ubuntu all he needs is Nautilus. In the location bar just type:

```
sftp://<user>@<your_ip_address>
```

For windows there is a free program called winscp.

This is just the basics, If you are behind a router, you'll need to setup port forwarding.

Jim

This is what I do for my friends.  They are not very technical, and use Windows+WinSCP, but they can download and upload with no major problems.  I restrict them to writing to only a single directory with regular Unix permissions.

---

