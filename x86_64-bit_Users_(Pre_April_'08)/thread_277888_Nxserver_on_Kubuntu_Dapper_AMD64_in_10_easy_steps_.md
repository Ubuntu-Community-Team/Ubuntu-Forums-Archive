---
title: "Nxserver on Kubuntu Dapper AMD64 in 10 easy steps - Solved"
date: 2006-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Marman on 2006-10-15
Hi All,

I had to figure this out today for a client, so I thought I would share my experience here to save others some time. It took two hours of failure and frustration to finally come up with a 10-15 minute feel-good recipe ;)

First a bit of background -  The target system is an up to date kubuntu dapper with automatix installed.

I tried installing nxserver/freenx via tarball and deb from nomachine.com and various other links that asked you to put some kanotix  repositories in your apt sources file and they all failed miserably. 

Here is what did work:

First become root:

sudo -s
cd /root

 Then copy and paste each of these commands into a terminal window one at a time and wait for each to complete.

1) 
wget [http://64.34.161.181/download/2.1.0/Linux/FE/nxserver_2.1.0-9_i386.deb](http://64.34.161.181/download/2.1.0/Linux/FE/nxserver_2.1.0-9_i386.deb)

2) 
wget [http://64.34.161.181/download/2.1.0/Linux/nxnode_2.1.0-7_i386.deb](http://64.34.161.181/download/2.1.0/Linux/nxnode_2.1.0-7_i386.deb)

3)
wget [http://64.34.161.181/download/2.1.0/Linux/nxclient_2.1.0-6_i386.deb](http://64.34.161.181/download/2.1.0/Linux/nxclient_2.1.0-6_i386.deb)

4)
wget [http://ftp.us.debian.org/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-22_i386.deb](http://ftp.us.debian.org/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-22_i386.deb)

5)
dpkg --force-architecture -i libstdc++2.10-glibc2.2_2.95.4-22_i386.deb

6)
dpkg --force-architecture -i nxclient_2.1.0-6_i386.deb

7)
dpkg --force-architecture -i nxnode_2.1.0-7_i386.deb

8)
dpkg --force-architecture -i nxserver_2.1.0-9_i386.deb

9)
/usr/NX/scripts/setup/nxserver --install

10) This is the most important output, you must see the line that states that the "NX Server is running"

root@kubuntu-box:~#  /usr/NX/bin/nxserver --status
NX> 900 Connecting to server ..
NX> 110 NX Server is running.
NX> 999 Bye.

Now connect as any normal user on the system using nxclient software. The new nxserver uses pam so any user already configured on the system can connect remotely without having to do any "nxserver --adduser" or other commands.

cheers
-m

---

### Post by RAOF on 2006-10-16
> **Marman said:**
> ...
5)
dpkg --force-architecture -i libstdc++2.10-glibc2.2_2.95.4-22_i386.deb
...

That is a terribly bad idea.  This will **replace** any existing 64bit libraries with 32bit ones, and hence break all 64bit programs depending on those libraries!

A better plan is to **extract** the deb, with ```
dpkg --extract libstdc++2.10-glibc2.2_2.95.4-22_i386.deb
```
and then copy the .so files into the /usr/lib32 directory.

---

### Post by kleeman on 2006-10-16
Here is another option:
Goto

[http://www.math.nyu.edu/faculty/kleeman/amd64/](http://www.math.nyu.edu/faculty/kleeman/amd64/)

and then follow this README file:

This directory contains some modified seveas debs for installing the client and
server for freenx. To us them:

1) Add the seveas repository to your /etc/apt/sources.list file. See [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) for instructions
2) sudo dpkg -i nxlibs_1.4.92+1.5.0-11ubuntu1+0.local.1_all.deb nxagent_1.4.92+1.5.0-11ubuntu1+0.local.1_all.deb libxcompext1_1.4.92+1.5.0-11ubuntu1+0.local.1_all.deb libxcomp1_1.4.92+1.5.0-11ubuntu1+0.local.1_all.deb libstdc++2.10-glibc2.2_2.95.4-24+0.local.1_all.deb
3) sudo apt-get freenx
4) Download the nxclient deb from the repository and install it using "sudo dpkg -i --force-architecture"

This is an ugly hack but hey it work flawlessly ;-)

Only one dpkg force here!

---

### Post by Marman on 2006-10-17
Raof,

I agree with you regarding the "bastardization" of this package: libstdc++2.10-glibc2.2_2.95.4-22_i386.deb - It is not something I would normally do, however, the package is *not* a part of the regular kubuntu sources nor is it anything that we are using or intend to use for any other purpose than to get the Nxserver package to work - period. 

The only goal we had in mind  was to give the many developers working on our project immediate access to a gui environment on the server asap.

This tip was intended to assist anyone with the "immediate" need for a working nxserver implementaton until such time as a production-level solution was provided. 

If you don't like the approach taken, you are free not to use it.

cheers
-m

---

### Post by RAOF on 2006-10-17
> **Marman said:**
> Raof,

I agree with you regarding the "bastardization" of this package: libstdc++2.10-glibc2.2_2.95.4-22_i386.deb - It is not something I would normally do, however, the package is *not* a part of the regular kubuntu sources nor is it anything that we are using or intend to use for any other purpose than to get the Nxserver package to work - period. 

The only goal we had in mind  was to give the many developers working on our project immediate access to a gui environment on the server asap.

This tip was intended to assist anyone with the "immediate" need for a working nxserver implementaton until such time as a production-level solution was provided. 

If you don't like the approach taken, you are free not to use it.

cheers
-m

Oh, I wasn't aware that the package didn't contain libraries normally found in an Ubuntu install.  If it was built entirely to satisfy NXServer library dependencies, and doesn't contain libraries other programs may use, then sure, --force-arch won't break things.

But if it **did** contain libraries that other things use, (and its name does suggest that it at least contains a libstdc++ :)), then using --force-arch will break anything that uses the library.  On the other hand, extracting the package using --extract and manually copying the libraries into /usr/lib32 is totally safe.

I'm not against installing 32bit libraries on a 64bit system.  You just need to be careful not to overwrite existing 64bit libraries with the 32bit version, which installing a 32bit package --force-arch will generally do.

---

### Post by zzarr on 2006-11-16
Hello!

I get this print out what/how ever I do:

NXPROXY - Version 1.5.0

Info: Proxy running in client mode with pid '21950'.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using cache parameters 4/262144/8192KB/8192KB.
Info: Using adsl link parameters 8192/16/10/50.
Info: Using pack method 'no-pack' with session 'unix-console'.
Info: Using ZLIB data compression level 3.
Info: Using ZLIB data threshold set to 32.
Info: Using ZLIB stream compression level 6.
Info: Using remote ZLIB data compression level 3.
Info: Using remote ZLIB stream compression level 6.
Info: No suitable cache file found.
Info: Starting X protocol compression.
Info: Established X server connection.
Info: Using shared memory support in X server.
Info: End of session requested by signal '15' 'SIGTERM'.
Info: Shutting down the link and exiting.
Warning: Parent process appears to be dead. Exiting watchdog.

What is wrong?

I have followed all tutorials and done everything.

Port 22 is open on my router/firewall.

The local proxy connects to the remote proxy, do thay need a connection in the other way to (it's not possible where I'm now).

Please help me!

Greetings Zzarr

---

