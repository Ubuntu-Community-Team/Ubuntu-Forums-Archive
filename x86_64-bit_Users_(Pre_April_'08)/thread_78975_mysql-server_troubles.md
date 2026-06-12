---
title: "mysql-server troubles"
date: 2005-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by sgtnoodle on 2005-10-19
Yo,

So I just aquired a g4 mac, and I put ubuntu on it. I am trying to make it a forum server, so I installed apache2, php5, and mysql-server. Unfortionately, mysqld errors. It does not seem to be able to create the database. 

InnoDB: No valid checkpoint found.
InnoDB: If this error appears when you are creating an InnoDB database,
InnoDB: the problem may be that during an earlier attempt you managed
InnoDB: to create the InnoDB data files, but log file creation failed.
InnoDB: If that is the case, please refer to
InnoDB: [http://dev.mysql.com/doc/mysql/en/Error_creating_InnoDB.html](http://dev.mysql.com/doc/mysql/en/Error_creating_InnoDB.html)
051019 10:25:15 Can't init databases
051019 10:25:15 Aborting

051019 10:25:15  InnoDB: Warning: shutting down a not properly started
                 InnoDB: or created database!
051019 10:25:15 mysqld: Shutdown Complete


/var/lib/mysql/mysql/ is empty. 

Output from mysql_install_db

Preparing db table
Preparing host table
Preparing user table
Preparing func table
Preparing tables_priv table
Preparing columns_priv table
Installing all prepared tables
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)

I do not think permissions are the issue because I have even tried chmod 777 on the directory.

Any ideas?

---

### Post by wolfie85032 on 2005-11-17
Any luck on this?  I'm having the same issue.

---

### Post by sgtnoodle on 2005-11-17
Nope.

I installed debian on the mac. It isn't as pretty, but the server side works well.

---

### Post by tktreload on 2006-02-26
any body found a solution for this particular problem... I'm setting up nagios and i need the database to complete the setup.

---

### Post by shawn12345 on 2006-02-26
probably permissions. You have to run the create tables script as mysql or su. You also have to start the server as mysql or su users. mysql would be better.

just ps -al |grep mysql 
to see if its running. If not reread install.txt

also just advice...unless you have like a million users..and if the package supports it, myisam will be much easier for a new user and much easier to back up. you can backup myism with just copying the file.

later

---

### Post by tktreload on 2006-02-27
I did attempt making the tables as root, but that does not work, and mysql can't start without the tables.
Any way I installed debian stable and that works fine.

---

