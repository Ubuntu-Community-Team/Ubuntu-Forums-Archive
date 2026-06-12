---
title: "ODBC, postgresql, Open Office"
date: 2007-06-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by zedmaster on 2007-06-05
Hello!  I've been trying to connect to my local postgresql database with OpenOffice 2.2.  Here's the rundown:

Ubuntu 64, Fiesty

Postgresql 8.1 is set up, with a database and user

odbc-postgresql is installed, along with unixodbc

Open Office is the normal install for 2.2




When I try to do an ODBC connect it says:

"[UNIxODBC][DriverManager] Datasource name not found, and no default driver specified"


That's it.  The only other thing I'll mention is that I didn't do anything to set up ODBC.  All I did was install odbc-postgresql in synaptic.  The only thing I actually spent time configuring was postgresql, according to the postgresql.org manuals.  Everything else is just as it came.  

Can anyone give me a clue as to how to get connected to my DB?

Matthew

---

### Post by mrfreddy on 2007-06-05
You're going to have to google how to configure your /etc/odbc.ini, /etc/odbcinst.ini & your own users version of those.

Checkout [this thread]("http://svr5.postgresql.org/pgsql-odbc/2006-06/msg00109.php")

Sorry I can't be of more help at the moment. Too busy.

(It's a crying shame the sdbc library doesn't install under x86_64. I must ask if anyone has compiled it themselves one day...)

Update 20070613: An interim bugfix postgresql sdbc has been released. See [http://ubuntuforums.org/showthread.php?p=2840860]("http://ubuntuforums.org/showthread.php?p=2840860").

---

