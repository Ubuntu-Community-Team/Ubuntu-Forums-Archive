---
title: "MythTV, help setting up? please..."
date: 2006-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonah1980 on 2006-07-19
hi could anyone please help me setup myth-tv.

i've installed the packages from the Moshen.de 64bit repository i found in these forum pages.

but then i've ended up in a right mess! i tried to follow myth guides but support seems to be seriously lacking...

ok so it's all installed so when i type mythtv at the prompt it starts up after loads of error messages:

> QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-19 19:41:14.096 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-19 19:41:17.083 Unable to connect to database!
2006-07-19 19:41:17.083 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-19 19:41:17.140 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-19 19:41:17.196 Failed to init MythContext, exiting.

that kind of thing but loads and loads of it!!

i tried following an instruction i found somewhere to reset mysql and change the password or something but not sure what i did and it didn't work.

so now don't know what to do.

after the errors the setup screen comes up for you to put username, pass, localhost etc in - tried leaving initial settings here and tried root/myuserpassword etc but it's not getting me anywhere.

thanks for any help anyone can offer.

---

### Post by RAOF on 2006-07-19
Aaah.  It's been a while since I set up MythTV, but I remember having that problem.  I don't have access to my box now, so this is from memory, but:
1) In /etc/mythtv/mythtv.txt (or something like that) there is a line which contains the password mythtv will use for accessing the database.
2) You can google "mysql setup password" and get the MySQL online handbook thing.

Then, all you need to make sure is that the database password & the one stored in /etc/mythtv/mythtv.txt is the same.

Sorry about the vague directions.  I hope it helps.

---

### Post by jonah1980 on 2006-07-20
whatever i seem to do i get this kind of error! i can't access anything to even change the password - i've been trying 6 hours last night and half hour so far this morning and not getting anywhere with it - mysql is a massive pain in the rear!!

> jonah@jonah-desktop:~$ mysqladmin -u root password 'passwordyouwant'
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

---

### Post by RAOF on 2006-07-20
You need to add "-p" if you want to use a password.  For example, this works (for me):
```
mysql -u mythtv -p
```

---

### Post by jonah1980 on 2006-07-20
jonah@jonah-desktop:~$ mysql -u mythtv -p
Enter password:
ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES)
jonah@jonah-desktop:~$

---

### Post by RAOF on 2006-07-20
Did you enter the right password :)?

---

### Post by jonah1980 on 2006-07-20
as far as i know, i put my user/sudo password in. but i don't know what other pass to use!

tried mythtv as password also but this gave me same error

---

### Post by RAOF on 2006-07-20
Your user password will **not** be the right password there.  I'm just googling for a MySQL startup guide...

---

### Post by jonah1980 on 2006-07-20
thanks a lot, i've tried a few of these mysql guides and got nowhere, it's nice to have someone trying to help. i've had endless people in myth irc room just telling me to read the FAQ and howtos - which of course i tried to do and it didn't work! hehe thanks again.

---

### Post by RAOF on 2006-07-20
Ok.  Can you get into mysql at all?  Does "mysql -u root" work?

Where **is** that good MySQL guide... I just can't seem to find it!

If you can get access to the mysql prompt, you might want to try 
```
mysql> SET PASSWORD FOR mythtv = PASSWORD('mythtv');

```
or something.

I seem to also remember a FLUSH_PRIVILEGES command somewhere, but I can't seem to find the reference...

---

### Post by jonah1980 on 2006-07-20
tried these out:

> jonah@jonah-desktop:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
jonah@jonah-desktop:~$ sudo mysql
Password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
jonah@jonah-desktop:~$ sudo mysql -u
mysql: option '-u' requires an argument
jonah@jonah-desktop:~$ mysql -u sudo
ERROR 1045 (28000): Access denied for user 'sudo'@'localhost' (using password: NO)
jonah@jonah-desktop:~$


not sure how i get the prompt so i just put this in:

> jonah@jonah-desktop:~$ SET PASSWORD FOR mythtv = PASSWORD('mythtv');
bash: syntax error near unexpected token `('
jonah@jonah-desktop:~$


i knew that wouldn't work but not sure what else to try at the moment.

---

### Post by RAOF on 2006-07-20
[Here's how to set a new MySQL root password]("http://www.debianhelp.co.uk/mysqlroot.htm").

Then do 
```
mysql -u root -p
```
to get the mysql> prompt.  Then enter the SET PASSWORD... stuff there.

---

### Post by mirak63 on 2006-07-20
do sudo -s then you can log into mysql

look for info in /usr/share/doc/mythtv or in [http://lcoalhost/doc](http://lcoalhost/doc) if you have apache running.

---

### Post by jonah1980 on 2006-07-20
ok guys you got me a lot closer, i got the mysql prompt and stuff, here's what happened:

> jonah@jonah-desktop:~$ mysql -u root
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1 to server version: 5.0.22-Debian_0ubuntu6.06-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> use mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> update user set password=PASSWORD("mythtv") where User='root'; Query OK, 0 rows affected (0.00 sec)
Rows matched: 0  Changed: 0  Warnings: 0

mysql> flush privileges;
Query OK, 0 rows affected (0.01 sec)

mysql> quit
Bye
jonah@jonah-desktop:~$ /etc/init.d/mysql stop
Stopping MySQL database server: mysqldcat: /var/run/mysqld/mysqld.pid: Permissio n denied
...failed.
Could not open required defaults file: /etc/mysql/debian.cnf
Fatal error in defaults handling. Program aborted
Killing MySQL database server by signal: mysqldmysqld(15437): Operation not perm itted
mysqld: no process killed
jonah@jonah-desktop:~$ /etc/init.d/mysql start
Starting MySQL database server: mysqldcat: /var/run/mysqld/mysqld.pid: Permissio n denied
cat: /var/run/mysqld/mysqld.pid: Permission denied
.
cat: /var/run/mysqld/mysqld.pid: Permission denied
.
cat: /var/run/mysqld/mysqld.pid: Permission denied
.
cat: /var/run/mysqld/mysqld.pid: Permission denied
.
cat: /var/run/mysqld/mysqld.pid: Permission denied
.
cat: /var/run/mysqld/mysqld.pid: Permission denied
.
cat: /var/run/mysqld/mysqld.pid: Permission denied
.
cat: /var/run/mysqld/mysqld.pid: Permission denied
.
cat: /var/run/mysqld/mysqld.pid: Permission denied
.
cat: /var/run/mysqld/mysqld.pid: Permission denied
.
cat: /var/run/mysqld/mysqld.pid: Permission denied
.
cat: /var/run/mysqld/mysqld.pid: Permission denied
.
cat: /var/run/mysqld/mysqld.pid: Permission denied
.
cat: /var/run/mysqld/mysqld.pid: Permission denied
.
cat: /var/run/mysqld/mysqld.pid: Permission denied
...failed or took more than 6s.
        Please take a look at the syslog.
Could not open required defaults file: /etc/mysql/debian.cnf
Fatal error in defaults handling. Program aborted
jonah@jonah-desktop:~$


But still got permission denied... where from here? thanks for your help.

---

### Post by RAOF on 2006-07-20
> 
jonah@jonah-desktop:~$ mysql -u root
Welcome to the MySQL monitor. Commands end with ; or \g.
Your MySQL connection id is 1 to server version: 5.0.22-Debian_0ubuntu6.06-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> use mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A
...

Hey!  You don't have **any** password set on your root MySQL account.  That makes it easy!

```
jonah@jonah-desktop:~$ mysql -u root
mysql> SET PASSWORD FOR mythtv = PASSWORD('mythtv');
mysql> flush privileges;
mysql> quit

```
and you should be done!

I hope that works.  I'm off to sleep :).  If it doesn't, anyone else, feel free to step in :)

---

### Post by jonah1980 on 2006-07-20
ok i did that and then i started mythtv back up again and got these errors:

> Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:07:57.890 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:07:57.946 Database not open while trying to load setting: GuiOffsetX
2006-07-20 14:07:57.947 Unable to connect to database!
2006-07-20 14:07:57.947 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:07:58.006 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:07:58.066 Database not open while trying to load setting: GuiOffsetY
2006-07-20 14:07:58.067 Unable to connect to database!
2006-07-20 14:07:58.067 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:07:58.126 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:07:58.182 Database not open while trying to load setting: GuiResolution
2006-07-20 14:07:58.183 Unable to connect to database!
2006-07-20 14:07:58.183 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:07:58.242 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:07:58.298 Database not open while trying to load setting: GuiWidth
2006-07-20 14:07:58.299 Unable to connect to database!
2006-07-20 14:07:58.299 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:07:58.358 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:07:58.414 Database not open while trying to load setting: GuiHeight
2006-07-20 14:07:58.415 Unable to connect to database!
2006-07-20 14:07:58.415 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:07:58.474 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:07:58.530 Database not open while trying to load setting: MenuTheme
2006-07-20 14:07:58.531 Unable to connect to database!
2006-07-20 14:07:58.531 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:07:58.590 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:07:58.650 Database not open while trying to load setting: QtFontBig
2006-07-20 14:07:58.650 Unable to connect to database!
2006-07-20 14:07:58.651 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:07:58.710 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:07:58.766 Database not open while trying to load setting: QtFontMedium
2006-07-20 14:07:58.766 Unable to connect to database!
2006-07-20 14:07:58.767 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:07:58.826 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:07:58.882 Database not open while trying to load setting: QtFontSmall
2006-07-20 14:07:58.888 Unable to connect to database!
2006-07-20 14:07:58.888 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:07:58.946 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:07:59.002 Database not open while trying to load setting: HideMouseCursor
2006-07-20 14:07:59.003 Unable to connect to database!
2006-07-20 14:07:59.003 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:07:59.062 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:07:59.118 Database not open while trying to load setting: RunFrontendInWindow
2006-07-20 14:08:00.137 Unable to connect to database!
2006-07-20 14:08:00.137 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
2006-07-20 14:08:00.142 Joystick disabled.
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
QSqlQuery::exec: database not open
2006-07-20 14:08:00.198 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:00.255 Unable to connect to database!
2006-07-20 14:08:00.255 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:00.314 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:00.370 Unable to connect to database!
2006-07-20 14:08:00.370 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:00.430 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:00.487 Unable to connect to database!
2006-07-20 14:08:00.487 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:00.546 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:00.602 Unable to connect to database!
2006-07-20 14:08:00.602 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:00.662 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:00.718 Unable to connect to database!
2006-07-20 14:08:00.719 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:00.778 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:00.834 Unable to connect to database!
2006-07-20 14:08:00.834 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:00.894 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:00.950 Unable to connect to database!
2006-07-20 14:08:00.951 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:01.010 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:01.066 Unable to connect to database!
2006-07-20 14:08:01.066 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:01.126 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:01.182 Unable to connect to database!
2006-07-20 14:08:01.182 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:01.242 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:01.298 Unable to connect to database!
2006-07-20 14:08:01.298 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:01.358 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:01.414 Unable to connect to database!
2006-07-20 14:08:01.414 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:01.474 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:01.530 Unable to connect to database!
2006-07-20 14:08:01.530 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:01.590 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:01.646 Unable to connect to database!
2006-07-20 14:08:01.647 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:01.706 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:01.762 Unable to connect to database!
2006-07-20 14:08:01.763 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:01.822 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:01.878 Unable to connect to database!
2006-07-20 14:08:01.879 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:01.938 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:01.994 Unable to connect to database!
2006-07-20 14:08:01.994 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:02.054 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:02.110 Unable to connect to database!
2006-07-20 14:08:02.110 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:02.170 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:02.226 Unable to connect to database!
2006-07-20 14:08:02.227 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:02.286 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:02.343 Unable to connect to database!
2006-07-20 14:08:02.343 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:02.402 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:02.458 Unable to connect to database!
2006-07-20 14:08:02.458 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:02.518 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:02.574 Unable to connect to database!
2006-07-20 14:08:02.574 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:02.634 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:02.690 Unable to connect to database!
2006-07-20 14:08:02.690 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:02.750 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:02.806 Unable to connect to database!
2006-07-20 14:08:02.806 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:02.866 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:02.922 Database not open while trying to load setting: Language
2006-07-20 14:08:05.794 Unable to connect to database!
2006-07-20 14:08:05.794 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:05.854 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:05.910 Database not open while trying to save setting: Language
2006-07-20 14:08:05.910 Unable to connect to database!
2006-07-20 14:08:05.910 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:05.970 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:06.026 Database not open while trying to load setting: Language
2006-07-20 14:08:06.038 Unable to connect to database!
2006-07-20 14:08:06.038 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:06.098 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:06.154 Database not open while trying to save setting: Language
2006-07-20 14:08:06.155 Unable to connect to database!
2006-07-20 14:08:06.155 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:06.214 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:23.291 Writing settings file /home/jonah/.mythtv/mysql.txt
2006-07-20 14:08:23.293 DBPassword is not set in mysql.txt
2006-07-20 14:08:23.317 Unable to connect to database!
2006-07-20 14:08:23.317 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'root'@'localhost' (using password: NO)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-07-20 14:08:23.375 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-07-20 14:08:23.430 Failed to init MythContext, exiting.
jonah@jonah-desktop:~$


the interface started. i put user as root, pass as nothing and just clicked next to rest of settings and it went back to terminal - from which i've pasted the errors above.

---

### Post by RAOF on 2006-07-20
You should probably edit the mysql.txt file, and make sure that the password in there matches the password you've set for mythtv.

I've got one in /home/mythtv/.mythtv/mysql.txt, and the top of it looks like...
```
DBHostName=localhost
DBUserName=mythtv
DBPassword=mythtv
DBName=mythconverg
DBType=QMYSQL3

...
```
Other places you might look for this file include /etc/mythtv, and ~/.mythtv

---

### Post by sebz2005 on 2006-07-21
[FONT=Verdana][SIZE=2]First open mysql.
Create the mythtv user.
[/SIZE][/FONT][FONT=Verdana][SIZE=2]```
GRANT ALL PRIVILEGES ON *.* TO 'mythtv'@'localhost'
IDENTIFIED BY 'root_pass' WITH GRANT OPTION;
``` 
[/SIZE][/FONT][FONT=Verdana][SIZE=2]Next, give it a password:
```

SET PASSWORD FOR 'mythtv'@'localhost' = PASSWORD('mythtv');
``` 
Create the database:

```
CREATE DATABASE mythtv;
``` 
And Voila!
Hope this helps.[/SIZE][/FONT]

---

### Post by teet on 2006-07-23
[http://www2.truman.edu/~dat725/htpc_single.html#htpc3](http://www2.truman.edu/~dat725/htpc_single.html#htpc3)

If you're still having problems...the easiest solution would be to wipe out your system and start again (since you could spend hours trying to fix something you flubbed up earlier).  If that's not an option, try to uninstall mysql as completely as possible and then give "my" guide a go (I actually copied these sections from another site).  It should work.  

-teet

---

### Post by chessforce on 2006-07-24
> **jonah1980 said:**
> ok i did that and then i started mythtv back up again and got these errors:



the interface started. i put user as root, pass as nothing and just clicked next to rest of settings and it went back to terminal - from which i've pasted the errors above.

Try executing /etc/init.d/mysql with sudo (i.e. `sudo /etc/init.d/mysql <command>`).

If that does not work, try the following:
```

sudo mysqld_safe

```

P.S. If you are running MySQL version >=5.0 with the MythTV AMD64 packages from the official Ubuntu repositories, you might run into MySQL errors due SQL commands issued by MythTV conflicting with the MySQL reserved keyword "repeat".  Thus, a downgrade to MySQL 4 may be needed or you can follow the instructions at [http://www.ubuntuforums.org/showpost.php?p=1292653&postcount=158](http://www.ubuntuforums.org/showpost.php?p=1292653&postcount=158)

---

### Post by RAOF on 2006-07-24
> **chessforce said:**
> ...
P.S. If you are running MySQL version >=5.0 with the MythTV AMD64 packages from the official Ubuntu repositories, you might run into MySQL errors due SQL commands issued by MythTV conflicting with the MySQL reserved keyword "repeat".  Thus, a downgrade to MySQL 4 may be needed or you can follow the instructions at [http://www.ubuntuforums.org/showpost.php?p=1292653&postcount=158](http://www.ubuntuforums.org/showpost.php?p=1292653&postcount=158)

Or an upgrade to the MythTV found in my AMD64 repository ;)

---

### Post by jonah1980 on 2006-07-25
to be honest i'm a bit lost to what i even stared trying to do now! it's cos i don't get that much time so have to keep coming back to it.

reading the guides and suggestions made i wonder if i can use myth as my current system is. alot of folk seem to set up a new partition and install the tv card first!

do i need a different partition?

also i'm not sure my tv card even works, it's already in my machine and i've got rid of windows for good.

it's a pinnacle pctv hybrid pro pci - can anyone recommend how to install this as different guides are based on different cards and driver sets but i don't know and can't really find anything about my card...

This is what i get when i try to get into mysql at the moment, though i did get the prompt last week somehow, but not sure how i did:

> jonah@jonah-desktop:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
jonah@jonah-desktop:~$


---

### Post by sebz2005 on 2006-07-25
Instead of putting the -u root at the end, type mysql only. See what that brings up.

---

### Post by jonah1980 on 2006-08-02
jonah@jonah-desktop:~$ mysql
ERROR 1045 (28000): Access denied for user 'jonah'@'localhost' (using password: NO)
jonah@jonah-desktop:~$

---

### Post by SDMF on 2006-08-03
I have similar problems with mythtv and mysql, but i have access to the mysql promt. Are you sure that you use "sudo su" before?

---

### Post by jonah1980 on 2006-08-06
here's what i get with the sudo su before:

> jonah@jonah-desktop:~$ sudo su mysql
Password:
jonah@jonah-desktop:~$ mysql
ERROR 1045 (28000): Access denied for user 'jonah'@'localhost' (using password: NO)
jonah@jonah-desktop:~$


---

### Post by phenolholic on 2006-08-09
Hello,
I'm following Hyams HOWTO of installing MythTV. In the part that mentions opening up 'localhost' from browser and changing password, and after trying to go into the 'phpmyadmin' directory, I get:

Cannot load mysql extension. Please check your PHP configuration. - Documentation

I ignored this, and kept on with the installation. After loading mythtv-setup, I get a Database Configuration menu, which says 'Myth could not connect to your database. Please verify the correct information' 
asking me for my login, password, host name, database, and database type. On the /home/mythtv/.mythtv/mysql.txt file, this is the information on there:

DBHostName=localhost
DBUserName=admin
DBPassword=
DBName=mythconverg
DBType=QMYSQL3

I tried going into mythtv-setup and putting in admin and leaving the passwd field blank on that database configuration menu, but no luck.

I also tried:
mysql -u root

and got the mysql> prompt and entered:
SET PASSWORD FOR admin = PASSWORD('mythtv');

and got this response:
ERROR 1133 (42000): Can't find any matching row in the user table

I've verified the services are running and indeed Apache2 and MySQL both are running. Any help would be appreciated. Thanks in advance

---

### Post by rakesh574 on 2006-08-20
I have the same problem until I edit the mysql.txt file in the /root/.mythtv/
the password there was different there.

---

### Post by rhpot1991 on 2006-08-21
> **phenolholic said:**
> Hello,
I'm following Hyams HOWTO of installing MythTV. In the part that mentions opening up 'localhost' from browser and changing password, and after trying to go into the 'phpmyadmin' directory, I get:

Cannot load mysql extension. Please check your PHP configuration. - Documentation

I ignored this, and kept on with the installation. After loading mythtv-setup, I get a Database Configuration menu, which says 'Myth could not connect to your database. Please verify the correct information' 
asking me for my login, password, host name, database, and database type. On the /home/mythtv/.mythtv/mysql.txt file, this is the information on there:

DBHostName=localhost
DBUserName=admin
DBPassword=
DBName=mythconverg
DBType=QMYSQL3

I tried going into mythtv-setup and putting in admin and leaving the passwd field blank on that database configuration menu, but no luck.

I also tried:
mysql -u root

and got the mysql> prompt and entered:
SET PASSWORD FOR admin = PASSWORD('mythtv');

and got this response:
ERROR 1133 (42000): Can't find any matching row in the user table

I've verified the services are running and indeed Apache2 and MySQL both are running. Any help would be appreciated. Thanks in advance


You need to create the mythtv mysql user and give it a password, you may also need to create the database.  Someone posted how to do it on the previous page.

---

### Post by lambretta on 2006-08-23
Save your self the heart ache. I think follow these steps (although its not Ubunto friendly) should get you there if you havn't already.

1.  Make sure your TV capture card is supported by Linux ([www.linuxtv.org/wiki/index.php/PCI_devices_DVB-T](www.linuxtv.org/wiki/index.php/PCI_devices_DVB-T))
2. Download Mythdora or Knoppmyth
3. Insert into CD drive (WARNING: it will HOSE your existing installed OS and all files)
4. Let it build your mythtv system for you (as long as your card is Linux supported 
5. Enjoy the MythTV goodness.

---

### Post by RiCkY82 on 2006-11-20
Be sure to do "sudo apt-get install libqt3-mt-mysql" so you get the mysql driver to access the database. Took me a while to find out.

Also make sure you've run the mysql script to create the database and user. After that run mythbackend. This will create the tables.

Then you need to run mythtv-setup.

Hope this helps :)

---

### Post by jonah1980 on 2006-11-20
what's the mysql script?

---

### Post by stefansjs on 2006-11-23
I was having the same problems.  I managed to set the mysql password and get that to work, but then the same errors with mythtv-setup.  The instructions that sebz gave worked, but now when I run sudo mythtv-setup I get a screen with a background but nothing on it.  The output in the terminal is:

2006-11-23 20:59:56.765 Using runtime prefix = /usr
2006-11-23 20:59:56.837 DPMS is not supported.
2006-11-23 20:59:56.892 New DB connection, total: 1
2006-11-23 20:59:56.901 Connected to database 'mythconverg' at host: localhost
2006-11-23 20:59:56.905 Total desktop dim: 1024x768, with 1 screen[s].
2006-11-23 20:59:57.451 Using screen 0, 1024x768 at 0,0
2006-11-23 20:59:57.474 Current Schema Version: 1160
Xlib:  extension "RANDR" missing on display "localhost:10.0".
DisplaResX: Unable to XRRgetScreenInfo
2006-11-23 20:59:58.488 Total desktop dim: 1024x768, with 1 screen[s].
2006-11-23 20:59:59.054 Using screen 0, 1024x768 at 0,0
2006-11-23 20:59:59.057 Switching to square mode (G.A.N.T.)
2006-11-23 21:00:00.056 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2006-11-23 21:00:22.119 Joystick disabled.


I don't mind so much about the joystick being disabled seeing as i don't have one, but it would be nice if mythtv would work.  Right now i'm running mythtv-setup remotely using xforwarding to XWin-32.  i'm not sure if it's xwin that's causing the problem or not.
please help

---

### Post by RAOF on 2006-11-23
If you're doing it remotely, you probably want to wait a **long** time before giving up on it.  It's probably just messing with your remote X server for fun.  There don't seem to be any fatal errors in the output you posted.

---

