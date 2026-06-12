---
title: "Problems whit installation of amns0.95, unreconize &quot;make&quot; comand"
date: 2006-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ragnarog on 2006-03-08
Hi!

Hi!
At first I'm runing ubutno 5.10 under atlhon 64b system.

I'm trying to run the last amsn release but all i do seems it doesn'work. I run de configure file and it works fine, finally. The i try to execute amsn

./amsn

And it returns this mensage:
"You can't load TkCximage. This is now needed to run aMSN. Pleasecomplie amsn first, instructions of how to complie are located in teh file Install"

Ouch! I didn't see the line that tells me that i must type the "make" comand after execution of configure.
Well i do it and... surprese my console don't reconize the make comand! What can i do? This are my first steps in linux and i don't know all comands.

the comands lines:

[list][i]root@Outdoor:/data/amsn/amsn-0.95# ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for prefix by checking for wish... /usr/bin/wish
checking tcl build dir... using tcl library in /usr/lib/tcl8.4
checking tk build dir... using tk library in /usr/lib/tk8.4
checking for main in -lstdc++... yes
checking for X... libraries , headers in standard search path
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for ftello... yes
checking for fseeko... yes
checking for getpt... yes
checking for strcasestr... yes
checking for memmem... yes
checking for dlopen... no
checking for pthread_create in -lpthread... yes
checking if mmx should be used... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating utils/linux/capture/config.h
config.status: utils/linux/capture/config.h is unchanged

compile time options summary
============================

X11 : yes
Using Libng : yes
Tcl : 8.4
TK : 8.4
DEBUG : no

root@Outdoor:/data/amsn/amsn-0.95# make
bash: make: command not found [/i][/list]

Can any one help me? i asked for the problen in amsn forum and they said to me that it's a system problem...

Any idea that what is wrong or something i can do?

---

### Post by andrewsawyer on 2006-03-08
Try 'apt-get install build-essential' first.

---

### Post by Ragnarog on 2006-03-09
Hei!

It works! Thanks! I'm running amsn, finaly!

---

### Post by andrewsawyer on 2006-03-09
No worries.

---

