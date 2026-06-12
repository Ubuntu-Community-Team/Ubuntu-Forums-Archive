---
title: "php4-mysql issue"
date: 2006-07-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by cefs99 on 2006-07-03
Hi All,

I am running Breezy on AMD64 server and just migrating from RHEL3.

I am running php4.4 and mysql 4.1 that are installed via apt-get. I am using mysql 4.1 instead of 5.0 because all the existing mysql data files are 4.1 based so  a virtual link will allow me to continue using data file without upgrading to 5.0.

The problem I am experiencing is that the mysql support of php4 in Breezy, the package php4-mysql,  is using libmysqlcient12 which doesn't support the new password algorithm of mysql 4.1. Is there any compiled version of php4-mysql that using libmysqlclient14? Or I have to upgrade to php5?

Thanks,

Lee

---

### Post by cefs99 on 2006-07-03
Now I had installed php5 but found out even php5-mysql still using libmysqlclient12. And the setting in /etc/mysql/my.cnf:

old_password=1

seems doesn't work. The error message is still:

Warning: mysql_connect() [function.mysql-connect]: Client does not support authentication protocol requested by server; consider upgrading MySQL client in


Does this mean I have to compile php5-mysql with libmysqlclient14?

Thanks,

Lee

---

