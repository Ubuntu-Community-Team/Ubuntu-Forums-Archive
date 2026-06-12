---
title: "Apache server issues"
date: 2006-02-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by jstingray on 2006-02-20
I am a newbie to Linux, downloaded Ubuntu Breeszy Badger a few months ago.
so far so good, my installation runs just fine on my windows box (dual boot with XP Pro).
Here''s my problem:
I went to Ubuntu because i was having problems getting Windows, Apache, MySQL and PHP to play nice together.
Since then I stared using Windows IIS and everything works fine. I'm learning PHP, so this is the enviorment I need.
However, I am still intrigued with Ubuntu. I have installed Apache2 server, mySQl, and PHP, but when i try to go to localhost (127.0.0.1 ) in my browser, it shows me the file, but doesn't serve the page. If I click on the file, it is the default Apache html file. I also can't get any other html files to come up at all. i've saved a few to the docroot folder that I assume is my apache installation, come the browser says up 'can't find file'
This might be a simple thing for you expierienced users, but I'm baffled!
Please help.

---

### Post by slazh on 2006-02-21
Could you post your Apache2 config?

---

### Post by jstingray on 2006-02-21
That's part of the problem! I don't know how to configure Apache, or find where to edit it. I assume it's the 'httpd.conf' file, but I don't see anything that helps.
I'm a Windows user, so I'm used to the GUI that comes with nearly all Windows apps.
I'm not entirely clueless, I did get ClamAV and Firestarter installed and working via the monitor, but going to Linus commands is like centigrade vs fahrenheit . I have trouble getting most downloads like the Flashplayer plug in to install.
the actual page that the browser show is 'index of files' on 127.0.0.1 when I go to localhost in Firefox.
I appreciate any help more expereinced Ubuntu user can offer!

---

### Post by slazh on 2006-02-21
Are you sure you put your files in the right directory?

In your httpd.conf look at the line that says "DocumentRoot".
For example;
```
DocumentRoot /var/www
```

You'll have to put all your .html / .php etc files in there, or you could change that directory. If you change it, make sure you restart apache;
```
$ sudo /etc/init.d/apache restart
```

---

### Post by jstingray on 2006-02-21
Thanks, I'll try it later this PM!

---

