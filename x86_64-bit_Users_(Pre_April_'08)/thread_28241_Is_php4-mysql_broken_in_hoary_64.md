---
title: "Is php4-mysql broken in hoary 64?"
date: 2005-04-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by nomaand on 2005-04-19
I have installed mysql-server-4.1, php4 and apache2 i seem to be having a problem with the connector between mysql and php. Whenever i uncomment the
extension=mysql.so
line apache starts fine no error messages or anything, but the mysql website i have hosted returns nothing as in zero bytes back to the browser. Also no errors are produced in any of the apache logs

**note:** I have another site using php and pgsql and that site works fine
**note:** When i use the phpinfo(); command with the mysql extension uncommented the readout stops around the gateway interface under Apache Environment

---

### Post by curtishall on 2005-04-19
I am having this same problem, php4-mysql does not exist in 5.04.

---

### Post by curtishall on 2005-04-19
Okay..fixed this problem.  php4-mysql is not included in the base /etc/sources.list...delete the old and install this:
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

---

### Post by nomaand on 2005-04-20
[QUOTE=curtishall]I am having this same problem, php4-mysql does not exist in 5.04.[/QUOTE]

Maybe i did not make myself clear. i have already got php4-mysql from hoary multiverse but the extension is not working when i try to view the webpage with the extension installed the browser does not recieve anything back from the server

I am now going to try and build the extension from debsource and hope it works

If anyone with the same sort of setup and is not having the same problem please reply and i will look elsewhere for the solution

---

### Post by nomaand on 2005-04-20
I have fixed the problem it ended up being the i had another version of apache other than the one that comes with ubuntu hoary in the end all i had to do was recompile php using the right apxs tool

---

### Post by Drain on 2005-05-17
I've had the same problem - when I type "php -m" at the command line, mysql doesn't show up as a module, despite having installed it through apt-get. Can someone help walk me through a solution?

---

### Post by Drain on 2005-05-31
[QUOTE=Drain]I've had the same problem - when I type "php -m" at the command line, mysql doesn't show up as a module, despite having installed it through apt-get. Can someone help walk me through a solution?[/QUOTE]

Well, after a few weeks of waiting, as I was about to recompile the source into a new package, I came across a post in the (yup, you guessed it) Ubuntu Forums: [http://ubuntuforums.org/showthread.php?t=12918](http://ubuntuforums.org/showthread.php?t=12918)

About 9 posts down it is mentioned that you can run the following:

```
$ sudo dpkg-reconfigure php4-mysql
``` 

Answer yes to the questions, and ta-daaa, mysql shows up as a php module when you type php -m at the CLI.  \\:D/ 

And in about 20 minutes, I'll have have transferred my webpage from my old host to my new server.  :smile:

---

