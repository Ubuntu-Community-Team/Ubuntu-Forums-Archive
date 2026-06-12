---
title: "Mysql don't start"
date: 2005-12-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Leonida on 2005-12-03
I've installed mysql with sudo apt-ger install mysql-server, but it don't start, I get this error:

~$ sudo /etc/init.d/mysql start
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

My syslog say:
```

edubuntu mysqld_safe[6213] started
edubuntu mysqld[6217] InnoDB: No valid checkpoint found.
edubuntu mysqld[6217] InnoDB: If this error appears when you are creating an InnoDB database,
edubuntu mysqld[6217] InnoDB: the problem may be that during an earlier attempt you managed
edubuntu mysqld[6217] InnoDB: to create the InnoDB data files, but log file creation failed.
edubuntu mysqld[6217] InnoDB: If that is the case, please refer to
edubuntu mysqld[6217] InnoDB: http://dev.mysql.com/doc/mysql/en/Error_creating_InnoDB.html

edubuntu mysqld[6217] 051204  1:00:45 Can't init databases
edubuntu mysqld[6217] 051204  1:00:45 Aborting
edubuntu mysqld[6217] 
edubuntu mysqld[6217] 051204  1:00:45  InnoDB: Warning: shutting down a not properly started
edubuntu mysqld[6217] InnoDB: or created database!
edubuntu mysqld[6217] 051204  1:00:45 /usr/sbin/mysqld: Shutdown Complete
edubuntu mysqld[6217] 
edubuntu mysqld_safe[6223] ended
edubuntu /etc/init.d/mysql[6288] 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
edubuntu /etc/init.d/mysql[6288] ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
edubuntu /etc/init.d/mysql[6288] error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
edubuntu /etc/init.d/mysql[6288] Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
edubuntu /etc/init.d/mysql[6288] 
```

---

### Post by Leonida on 2005-12-03
Sorry, same problem as here:
[http://ubuntuforums.org/showthread.php?t=78614](http://ubuntuforums.org/showthread.php?t=78614)

Edit: Solved installing mysql-server 4.1 from Universe.

---

