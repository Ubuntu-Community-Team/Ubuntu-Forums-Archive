---
title: "DAZ3D PostgreSQL connection non-sense"
date: 2020-05-17
forum: Wine
---

### Post by jrcj38 on 2020-05-17
Everybody on any forum/mailing list/chat group is probably very tired of this. I know I am. I've tried every solution I can find and no joy with this.

I'm running Ubuntu 18.04 (yes, I know 20.04 is supposed to be out. One catastrophe at a time, please), Wine 3.0.1, and DAZ studio 4.12 something. DAZ uses it's own PostgreSQL as a CMS for Smart Content. Apparently, it's supposed to start up and communicate with DAZ Studio via a port which can be set in the DAZ Studio preferences. No joy, fails every time to connect. I've tried; reinstalling PostgreSQL, changing the port, using netstat -tunlp to see if anybody else is using either port I've tried (no one else is), using a completely non-privileged account.  DAZ's log are particularly useless since all it says is there was a failure to connect. I tried running the DAZ PostgreSQL alone and that's where it does gripe about being run from a privileged account. (tried a non-privileged one as I said). These are all possible solutions found on the web. From where I sit it looks like the problem is with PostgreSQL starting up. It just never shows up in the process list that I can find meaning it fails really early on. Some of the solutions, i.e. stuff I've tried about, have worked for others. No one has worked for me. I know Wine has a few glitches. It's unclear that this is one of them. DAZ Studio runs OK on macos. Macos seems to have become bloatware. My new linux system is bigger, badder, fast, has more RAM and 6 cores with 2 threads so it renders faster. But I can not use the Smart Content properties of DAZ because PostgreSQL won't start up. Nobody seems to have an answer for this. In desperation I thought I'd bother the Wine forum. I'd appreciate any help anyone might have. Thank you.

---

### Post by jrcj38 on 2020-05-17
Huh, addendum. Don't know if this is related or not. I know that some things run well on Wine and some don't so much. Best way to tell is to try and I have had WinSCP running very well in years past for example. I just tried running the PostgreSQL 12.3 installer exe on Wine 64 bit 3.0.1. It failed. Seems to be looking for ntlm_auth which, it claims, is part of winbind. I wanted to see if PostgreSQL, the real thing, would fire up at all. Would have been an interesting test. Can't even install the Win10 version of PostgreSQL this way.

---

### Post by SeijiSensei on 2020-05-17
How did you install PostgreSQL?  In 18.04, the [usual commands]("https://hostadvice.com/how-to/how-to-install-postgresql-database-server-on-ubuntu-18-04/") are
```

sudo apt update
sudo apt install postgresql postgresql-contrib

```

I've installed PG many times on Ubuntu, and every time it just starts up as expected.  I just installed the postgresql-12 package on my 20.04 machine.  Afterwards, if I run "ps ax | grep post" I get these results:
```

  80021 ?        Ss     0:00 /usr/lib/postgresql/12/bin/postgres -D /var/lib/postgresql/12/main -c config_file=/etc/postgresql/12/main/postgresql.conf
  80023 ?        Ss     0:00 postgres: 12/main: checkpointer   
  80024 ?        Ss     0:00 postgres: 12/main: background writer   
  80025 ?        Ss     0:00 postgres: 12/main: walwriter   
  80026 ?        Ss     0:00 postgres: 12/main: autovacuum launcher   
  80027 ?        Ss     0:00 postgres: 12/main: stats collector   
  80028 ?        Ss     0:00 postgres: 12/main: logical replication launcher   

```
The first entry represents the server itself; the others are maintenance programs that start automatically.

---

### Post by jrcj38 on 2020-05-18
For the native ubuntu PostgreSQL, yes. DAZ Studio has it's under Windows  that in installed by the DAZ specific installer DIM under the  .wine/drive_c/Program Files/DAZ 3D/PostgreSQL CMS/ directory. Tht's the  one DAZ Studio tries to use.

---

### Post by jrcj38 on 2020-05-18
For the native ubuntu PostgreSQL, yes. DAZ Studio has it's own under Windows  that in installed by the DAZ specific installer DIM under the  .wine/drive_c/Program Files/DAZ 3D/PostgreSQL CMS/ directory. Tht's the  one DAZ Studio tries to use.

---

