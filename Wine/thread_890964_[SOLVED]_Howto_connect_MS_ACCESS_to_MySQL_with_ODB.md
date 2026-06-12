---
title: "[SOLVED] Howto connect MS ACCESS to MySQL with ODBC in wine?"
date: 2008-08-15
forum: Wine
---

### Post by joris1977 on 2008-08-15
In my spare time I volunteer in a small bookshop. Recently we moved our main computer to Ubuntu. Our book catalogue is in an MS ACCESS database (Office 2000.) and this is working real nice in Crossover Office. 

It would be useful to get a multiple user setup for the database, so more people could work on this database at the same time. To achieve this i want to move the tables to MySQL and use MS ACCESS as a front end for the database. 

I tested MS ACCESS as a front end for MySQL on a windows box and that worked nice. Problems start when i try to do the same thing in ubuntu. The mysql-connector-odbc doesn't want to install in crossover office. So using native ODBC doesn't seem to be in option. Although [http://wiki.winehq.org/NativeOdbc](http://wiki.winehq.org/NativeOdbc) claims different. 

Ok, no problemo, i use the unixodbc. That should work as is mentioned here: [http://www.codeweavers.com/support/docs/wine-user/config-odbc](http://www.codeweavers.com/support/docs/wine-user/config-odbc)

Setting up the unixodbc was not really easy but with the help of this two threads:
[http://webaj.com/how-setup-mysql-dsn-datasbase-source-centos-myodbc-and-unixodbc-command-line.htm](http://webaj.com/how-setup-mysql-dsn-datasbase-source-centos-myodbc-and-unixodbc-command-line.htm)
[http://ubuntuforums.org/showthread.php?t=226109&highlight=unixodbc+ubuntu](http://ubuntuforums.org/showthread.php?t=226109&highlight=unixodbc+ubuntu)

I am able to get this:

joris@ace:~$ isql -v adresses
+---------------------------------------+
| Connected!                            |
|                                       |
| sql-statement                         |
| help [tablename]                      |
| quit                                  |
|                                       |
+---------------------------------------+
SQL> 

so that seems to be ok. 

But how do i go from here? If i understand it right, crossover/wine redirect every ODBC call to the UNIXODBC driver. Similar to how the printing system is working in wine/crossover. 

Problem is how do i tell ACCESS to make ODBC calls. There is no mysql driver in ACCESS, so i cannot connect the linked tables to an ODBC source that will make a call to a ODBCUNIX source.

Maybe i am missing something really obvious here, because i couldn't find a single post with someone who has the same problem. So if someone can help me out, than that would be much appreciated!

---

### Post by markar on 2008-08-16
i have some informaiton about Howto connect MS ACCESS to MySQL with ODBC in wine there is link for it

---

### Post by joris1977 on 2008-08-16
thanks for your reply Markar. Before i posted this topic, i searched on a lot of places for an answer. That included the wine and MySQL website, but of course i could have overlooked something. It would be great if you could provide a link....

---

### Post by joris1977 on 2008-08-25
So I fixed it, with a little help from the kind support people from Crossover Office. Here's how I did it in Crossover Office:

1  Install Internet explorer in Crossover Office. It will suggest to make  a new windows 98  bottle. That is ok. After that, install Office 2000 in the same bottle.

2 Install MDAC. You can grab this from the Microsoft site. Find it here: [http://www.microsoft.com/downloads/details.aspx?familyid=78CAC895-EFC2-4F8E-A9E0-3A1AFBD5922E&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=78CAC895-EFC2-4F8E-A9E0-3A1AFBD5922E&displaylang=en) I could validate with Internet Explorer from Crossover Office.     

3 Install Windows Installer 2.0 You can download it here: [http://www.microsoft.com/downloads/details.aspx?FamilyID=CEBBACD8-C094-4255-B702-DE3BB768148F&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=CEBBACD8-C094-4255-B702-DE3BB768148F&displaylang=en) This was the step I didn't know about and why the windows mysql connector wouldn't install.

4 Go to the mysql website and download the windows mysql connector 3.51. you can find it here: [http://dev.mysql.com/downloads/connector/odbc/3.51.html#win32](http://dev.mysql.com/downloads/connector/odbc/3.51.html#win32) Install the connector.

That was it, now you can set up a ODBC connection between Mysql and ACCESS.  There is special ODBC tab in Crossover -> Select the bottle and click on the Configure button. Now click on the Control Panel tab. There is a ODBC icon. Click on the icon and it will launch the  ODBC Data Source Administrator. From here you can setup your MySQL Connections and they should be visible to Access. It works the same way as in windows.

I know this are the ubuntu wine forums, Crossover Office is build on wine but easier to configure. To get this working in wine you will probably need to take some extra steps. But maybe this thread points you in the right direction.

---

