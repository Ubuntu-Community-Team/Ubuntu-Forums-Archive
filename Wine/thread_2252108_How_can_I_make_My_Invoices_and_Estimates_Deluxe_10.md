---
title: "How can I make My Invoices and Estimates Deluxe 10 work"
date: 2014-11-09
forum: Wine
---

### Post by phyloah on 2014-11-09
I am trying to get My Invoices and Estimates Deluxe 10 to work under Ubuntu 14.04 with Wine. I managed to get it to install from the CD using Play on Linux and pointed the link to the MIED.exe. The program starts and then just freezes up on the account selection sceen with no account to select and it won't let me create one. I only need to use this program to generate Estimates and would like to use my existing database in whatever program I end up using.

I am a new Linuz user and my windows Vista will no longer boot for me. I have it on a separate hard drive that I can read but not boot from.

Any help would be appritiated.

---

### Post by ibjsb4 on 2014-11-09
A search of the wine data base shows Estimates Deluxe to have a bronze rating.  Not very good :(

[https://appdb.winehq.org/objectManager.php?sClass=application&iId=6263](https://appdb.winehq.org/objectManager.php?sClass=application&iId=6263)

---

### Post by tgalati4 on 2014-11-09
If you can't get WINE to work with your Estimator, then I would do the following:

Find a working Windows machine and put Estimator on it.  Pull up your database and try to export it to CVS or XML or some other readable format.

Put the readable database on a USB stick then pull the data into another database program in Linux.  Then generate your Invoices in LibreOffice with tables pulled from the database.

How many clients/years of history does this data cover?

I would look into making a linux server and using a CRM such as SugarCRM:  [http://sugarcrm.org](http://sugarcrm.org)

If the database is small, then just  create a new database with new clients--going forward--using LibreOffice Base and creating your custom forms in Writer or Calc.  Print out your old database in a binder, or put into Base as you have time.

---

