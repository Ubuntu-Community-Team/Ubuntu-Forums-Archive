---
title: "Recommend an SQL database."
date: 2009-08-12
forum: x86 64-bit Users
---

### Post by Plan B on 2009-08-12
Learning SQL @ school using M$ SQL Server.

Would like to run the linux equivalent at home on Ubuntu 64.  I know very little about this at the mo, still learning, but will go on to do the M$ certs for SQL Server.

---

### Post by Maheriano on 2009-08-12
Just use MySQL and administrate with PHPMyAdmin.

---

### Post by Plan B on 2009-08-13
Will give them a go.


Thanks.:cool:

---

### Post by huwnet on 2009-08-13
You can also look at [PostgreSQL](http://www.postgresql.org/)

---

### Post by NoReflex on 2009-08-13
As huwnet stated above you should look into PostgreSQL for a few reasons:
- it's more SQL standard compliant than MySQL
- it's not owned by a company unlike MySQL which in owned by Sun which is owned by Oracle (the future of MySQL is uncertain to me)
- MySQL still has some performance issues (sub-queries, index usage decision, temporary table access) and data integrity issues (replication breaks).
MySQL is still a very good product but in my opinion PostgreSQL is a better choice.
Just my 0.02 $.

Best wishes,
NoReflex

---

### Post by Plan B on 2009-08-18
> **huwnet said:**
> You can also look at [PostgreSQL](http://www.postgresql.org/)

I d/l the bin file from your link provided.  Can't run it. From the installation instructions...[http://www.enterprisedb.com/learning/pginst_guide.do]("http://www.enterprisedb.com/learning/pginst_guide.do")...     I tried > sudo ./postgresql-8.4.0-1-linux-x64.binon the file in my home folder, and got > sudo: ./postgresql-8.4.0-1-linux-x64.bin: command not found

---

### Post by NoReflex on 2009-08-20
You can find postgresql in Ubuntu's repostories as well (you can install it with sudo apt-get install postgresql).
If you want to install the version from PostgreSQL's site you should probably try:
sudo su (enter your password)
chmod +x postgresql-8.4.0-1-linux-x64.bin
./postgresql-8.4.0-1-linux-x64.bin or sh postgresql-8.4.0-1-linux-x64.bin

Good luck,
NoReflex

---

### Post by Plan B on 2009-08-25
Ah luverly.

Worked fine.  Just needed the execute permissions.
Thank you very big.
:)

---

### Post by ad_267 on 2009-08-25
You should install applications from the Ubuntu repositories rather than downloading them from their websites. See [Installing Software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware").

---

### Post by Slim Odds on 2009-08-25
> **ad_267 said:**
> You should install applications from the Ubuntu repositories rather than downloading them from their websites. See [Installing Software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware").

I was going to say the same thing. +1

Always check the repositories first. There's no reason not to use the stuff that's in there.

---

