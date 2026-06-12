---
title: "SSH server shuts down under intensive I/O from Java"
date: 2007-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by trulsb on 2007-07-19
Hi!
I have implemented an application in Java which uses a lot of I/O using the java.nio-library. I run it on a 7.04 Server version of Ubuntu (64-bits). My java version is 1.5.0_11. I have experienced various problems with SSH while running this application. My main problem now is that I am not able to diagnose the problem very well. I will therefore try to explain what happens, and hope that someone has heard about similar problems, or may help me to diagnose the problem in a better way.

I use my application to index a lot of documents in a B-tree, and have several SSH-shells connected to the server. When the indexing file becomes larger than 4 GB, there will be quite a heavy I/O-load in the system (which is expected). When the file exceeds 6GB, i usually experience the most fatal problem. The shells connected via SSH will not respond, and after waiting for several minutes they disconnect. I tried to log in on the actual server at the same time. I was allowed to input my user name and password, and the welcome messages was printed, but I did not get any shell.

When running smaller experiments, I have experienced less fatal problems. When I try to connect with a new shell during a run, it will sometimes not allow me to connect. It then gives me the error message:

ssh_exchange_identification: Connection closed by remote host

I have tried to take a look at /var/log/syslog and /var/log/messages, but I do not find any useful information (My experience with finding useful information in such logs is unfortunately limited).

My main question is: What is wrong, and how do I fix it? If anybody wonders, the filesystem is ext3.

But, realising that the above question is probably difficult to answer, I should probably ask where you would advise me to look to find more information about the problem. The problem as I see it is that the source of the problem might be in several places. It might be in my own application, but it seems fairly likely that this is not the cause, as there is no exception in the application (Java is usually quite good at throwing exceptions:)). The problem may be an I/O call in SSH that has a timeout, which causes it to fail when the I/O subsystem is under very heavy load. (This seems unlikely though, because i can not connect at the server itself either). 

It might be a bug in Java. And it may of course be that the file system actually fails. There are probably a lot of other possibilities as well, but I hope that someone with more experience might help me investigate the most probable causes first... Any ideas?

All help is very much appreciated!


Truls

---

