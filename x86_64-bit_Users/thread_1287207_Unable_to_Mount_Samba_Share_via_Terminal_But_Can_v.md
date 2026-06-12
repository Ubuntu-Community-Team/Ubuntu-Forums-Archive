---
title: "Unable to Mount Samba Share via Terminal But Can via GUI"
date: 2009-10-09
forum: x86 64-bit Users
---

### Post by decryption on 2009-10-09
I'm trying to mount a samba share via ssh remotely. The target is a NAS appliance that my Mac can see fine and connect to without needing authentication. The same NAS also appears and can mount, read and write to in the Ubuntu GUI file browser without needing any authentication.

When I run **smbclient -L 192.168.1.4**, this is the output:
```
bafs@bafs:~/filez$ smbclient -L 192.168.1.4
Enter bafs's password: 
Domain=[ECHUCA] OS=[Unix] Server=[Samba 3.0.34]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (Griff-NAS)
	webroot         Disk      
	media           Disk      Media Server Share
Domain=[ECHUCA] OS=[Unix] Server=[Samba 3.0.34]

	Server               Comment
	---------            -------
	GRIFF-NAS            Griff-NAS

	Workgroup            Master
	---------            -------
	ECHUCA               GRIFF-NAS

```

When I try to mount the **media** share, using: **mount.cifs //192.168.1.4/media /home/bafs/griff** I am prompted for a password (the only password I have set on the NAS is to log in to the admin page and it doesn't work here). No matter what password I enter, this is what I get:

```
bafs@bafs:~/filez$ mount.cifs //192.168.1.4/media /home/bafs/griff
Password: 
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
bafs@bafs:~/filez$ 

```

Does anyone have any ideas?

---

### Post by conufsed on 2009-10-09
Is your username 'bafs'

If not set it with -U <correct username>

---

### Post by decryption on 2009-10-09
I have tried using the username admin (which is what I use to log in to the NAS), but it doesn't work. The Macs and Windows boxes and even Ubuntu itself can see and mount the share without a password - so how can I do what the Ubuntu GUI does, but with the command line?

Trying the -o guest option just goes directly to permission denied - without a password prompt.

```
bafs@bafs:~/filez$ mount.cifs //192.168.1.4/media /home/bafs/griff/ -o guest
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

---

### Post by Andrew G on 2009-10-09
From the looks of [http://vijayk.blogspot.com/2008/09/cifs-mount-error-13-permission-denied.html](http://vijayk.blogspot.com/2008/09/cifs-mount-error-13-permission-denied.html) you need to be specifying the domain of the server, as that's the cause of error 13 (in modern client kernels at least).

---

### Post by decryption on 2009-10-09
> **Andrew G said:**
> From the looks of [http://vijayk.blogspot.com/2008/09/cifs-mount-error-13-permission-denied.html](http://vijayk.blogspot.com/2008/09/cifs-mount-error-13-permission-denied.html) you need to be specifying the domain of the server, as that's the cause of error 13 (in modern client kernels at least).

I gave that a shot and this happened:

```
bafs@bafs:~/filez$ sudo mount -t cifs //192.168.1.4/media ~/griff -o username=guest,domain=ECHUCA
Password: 
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

```

bafs@bafs:~/filez$ sudo mount -t cifs //192.168.1.4/media ~/griff -o guest,domain=ECHUCA
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
bafs@bafs:~/filez$ 

```

---

### Post by neg2led on 2009-10-09
Can you create users for SMB auth on the NAS appliance? If so, create a user (With a password) called bafs on it and try connecting that way (without specifying a user or domain) and using the newly-created user's password.

[edit]

Waitwaitwait. Shouldn't it be \\192.168.1.4\media ?! / = local FS \ = server location or something

[/edit]

--neg

---

### Post by decryption on 2009-10-09
> **neg2led said:**
> Can you create users for SMB auth on the NAS appliance? If so, create a user (With a password) called bafs on it and try connecting that way (without specifying a user or domain) and using the newly-created user's password.

--neg

Can't create a user on the NAS. Don't have access to it remotely.

---

### Post by neg2led on 2009-10-09
>  Waitwaitwait. Shouldn't it be \\192.168.1.4\media ?! / = local FS \ = server location or something

--neg

---

### Post by fmartinez78228 on 2009-10-09
I don't know if this helps, but I have a file server with both SAMBA (Windows Machines) and NFS (Mac Clients) that shares different directories depending if your using SAMBA or NFS. 
Either way when I mount a directory via the command line for example on my Mac, I can use the following command.
```
sudo mount servername:/ShareName /FolderPathToMount
```

---

### Post by decryption on 2009-10-09
> **fmartinez78228 said:**
> I don't know if this helps, but I have a file server with both SAMBA (Windows Machines) and NFS (Mac Clients) that shares different directories depending if your using SAMBA or NFS. 
Either way when I mount a directory via the command line for example on my Mac, I can use the following command.
```
sudo mount servername:/ShareName /FolderPathToMount
```

Thanks for the post, but that's what I tried in my first post and it didn't work - with the command asking me for a password (but a password is not set).

---

