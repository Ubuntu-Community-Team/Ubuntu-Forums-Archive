---
title: "Windows software connect to sql db"
date: 2013-03-05
forum: Wine
---

### Post by mihaiirimus on 2013-03-05
Hi,
First off all I'm new to Ubuntu.
At the office we have a system erp that is made to run under windows platform.
From financial reason we will try to use as a platform Ubuntu 12.10.
So ... 
I install the Ubuntu and WIne, then erp software, 
The erp can't connect to the server. (server is install on windows xp sp3).
Is any chance to connect the ERP (install in Ubuntu on Wine) to the sql database from server ?

---

### Post by slickymaster on 2013-03-05
[Squirrel SQL]("http://squirrel-sql.sourceforge.net/") is a universal SQL client, released under the GNU Lesser General Public License.

---

### Post by Mark Phelps on 2013-03-06
If you told us WHICH Windows ERP package (and the version) you're trying to use, that would help.

---

### Post by SeijiSensei on 2013-03-06
[unixODBC]("http://www.unixodbc.org/") might be a possibility, but I don't have a clue how it would interact with wine.

Oh, and if by "financial reasons" you mean you don't want to pay for a Windows license, then you don't know how to value your time correctly.  Spending hours and hours trying to configure a Linux box to do something a Windows box would do right away means you value your time at close to zero.

---

