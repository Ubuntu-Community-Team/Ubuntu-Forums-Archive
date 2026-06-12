---
title: "OpenOffice.org2 Base problem"
date: 2005-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Janfi on 2005-10-16
Hi,

I'm using Breezy, with latest updates on my ibook.
When I try to create a new database with OpenOffice base, everything going fine until I click on "Tables" to create tables and insert datas.

An error message appears :
"libhsqldb2 : file not found"

If i click another time on "tables", the message is (translated from french) :
"Unable to establish a connection to the source database "Newdatabase2".
and 
"com.sun.star.sdbcx.comp.hsqldb.StorageFileAccess".

Any ideas ? Many thanks for help.

---

### Post by khc on 2005-10-16
Works for me

---

### Post by Janfi on 2005-10-17
> Works for me

It works on an ibook too ?
I've this problem with Breezy Preview, and again with Breezy final. I make a fresh install with no more success.
Have you make any modifications, or software installation ?

Thanks.

---

### Post by craks on 2005-10-17
[QUOTE=Janfi]It works on an ibook too ?
I've this problem with Breezy Preview, and again with Breezy final. I make a fresh install with no more success.
Have you make any modifications, or software installation ?

Thanks.[/QUOTE]
yes, it works fine for ibook g4, you may try install breezy release version

---

### Post by Janfi on 2005-10-18
Thanks for the response.
It makes me crazy, my installation is a breezy release without any modification !

I need to use base to switch my students from MS Office to OpenOffice...

---

### Post by Janfi on 2005-10-18
ARRRRRRRG. I've found the solution \\:D/ 

After searching and searching the problem is in the /usr/lib/openoffice2/program directory.
There is a file called "libhsqldb2.so"
The solution was to simply create a symbolic link called "libhsqldb2" to this file.

```
cd /usr/lib/openoffice/program
```
then
```
sudo ln -s libhsqldb2.so libhsqldb2
```

And it works.

Now the question is : why I must do that with my fresh clean install of breezy release, instead other users no need this ??

---

### Post by Calgarian on 2005-10-23
Just tried your work around and found one small typo. When you do the cd go to /usr/lib/openoffice2/program to do the link. Then it works fine, but I agree with your comment that this should not be necessary for a fresh install - by the way I'm on i386 version not the ppc version.

---

### Post by rawler on 2005-10-23
Hey, just wanted to confirm the problem. It's the same for me.

A sidenote worthy to mention is that I installed Ubuntu Hoary and then replaced apt-sources with Breezy-sources.

After creating the symlink, it seems to work allright.

---

### Post by Zettt on 2006-01-02
Works with OpenOffice.org 2 too. 
But you have to cd to 

```
cd /usr/lib/openoffice2/program
```
then
```
sudo ln -s libhsqldb2.so libhsqldb2
```

Just for the correctness...

---

### Post by lutosdemayo on 2006-01-03
I have problems with my base too. Every time i try to connect to MySQL database using jdbc, base always exits. I did not have any problems with this up until i upgrades to the full version on openoffice.org 2. The KDE crash handler says The application libkab1 crashed and caused the signal 6 (SIGABRT). 

Do you guys here know what this means.

---

