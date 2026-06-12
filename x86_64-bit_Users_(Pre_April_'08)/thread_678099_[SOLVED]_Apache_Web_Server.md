---
title: "[SOLVED] Apache Web Server"
date: 2008-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Majorflam on 2008-01-25
I'm looking for a web server application that would allow me to design and build websites locally, before uploading them to their servers.

In Windows I use XAMPP as it provides me with php and mysql which is what I need. Unfortunately XAMPP doesn't work in 64 bit versions of Linux.

Is there a similar program that could work for me?

---

### Post by Majorflam on 2008-01-25
OK, I ran this command to install LAMP

```

sudo apt-get install ssh mysql-server apache2 php5 libapache2-mod-auth-mysql php5-mysql

```

The problem is that I can't seem to start apache. I've tried the command:

```

sudo /usr/sbin/apache2ctl start

```

However this doesn't work, it returns:

```

sudo: /usr/sbin/apache2ctl: command not found

```

Any help would be appreciated.

---

### Post by XplOzIOn on 2008-01-25
Hello apache should start automaticly

go to [http://localhost/]("http://localhost/") It should open

---

### Post by Majorflam on 2008-01-27
I got apache running fine. However a strange thing is happening now:

I need the mod rewrite rule working, and I've got it all configured fine. After configuration it seemed like apache wasn't reading the .htaccess files.

Then I discovered that the htaccess files aren't there! So, I opened up gFTP to download the access files... and they are showing in the left pane as being there!

Can anyone explain this?

TIA.

---

### Post by Majorflam on 2008-01-27
Can anyone explain this, or maybe point me to a particular forum if this one isn't relevant for my question?

It's driving me nuts!

---

### Post by Kilz on 2008-01-27
> **Majorflam said:**
> I got apache running fine. However a strange thing is happening now:

I need the mod rewrite rule working, and I've got it all configured fine. After configuration it seemed like apache wasn't reading the .htaccess files.

Then I discovered that the htaccess files aren't there! So, I opened up gFTP to download the access files... and they are showing in the left pane as being there!

Can anyone explain this?

TIA.

What are the permissions on the file? if the file is not readable by everyone it will not show up in the web server.

---

### Post by Majorflam on 2008-01-27
> **Kilz said:**
> What are the permissions on the file? if the file is not readable by everyone it will not show up in the web server.

I can't view the permissions because it doesn't show up. The only place I can see it, is in gFTP when I'm browsing the left pane. If I attempt to chmod in the left pain, it shows as 777 which is fine, no?

I can't understand why this .htaccess file isn't viewable in the directory when I'm browsing normally.

---

### Post by hessiess on 2008-01-27
try ctrl +h to un-hide it

---

### Post by Kilz on 2008-01-27
> **Majorflam said:**
> I can't view the permissions because it doesn't show up. The only place I can see it, is in gFTP when I'm browsing the left pane. If I attempt to chmod in the left pain, it shows as 777 which is fine, no?

I can't understand why this .htaccess file isn't viewable in the directory when I'm browsing normally.

could be because its a hidden file, it starts with a "."

---

### Post by Majorflam on 2008-01-27
ctrl -h did the trick.

Thanks a million guys.

---

