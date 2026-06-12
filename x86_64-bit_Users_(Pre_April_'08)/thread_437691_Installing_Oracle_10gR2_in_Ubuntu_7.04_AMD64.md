---
title: "Installing Oracle 10gR2 in Ubuntu 7.04 AMD64"
date: 2007-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by TerminaT on 2007-05-09
Hi everyone!!!

   After hours of trouble I just finished installing Oracle 10gR2 on my laptop Turion64 with Ubuntu 7.04 AMD64 installed. 

1. You need to install compat libraries and 32-bit libraries.

[FONT="Arial Black"]"sudo apt-get install gcc libaio1 lesstif2 lesstif2-dev make libc6 libc6-i386 libc6-dev-i386  libstdc++5 lib32stdc++6 lib32z1 ia32-libs"[/FONT]

2. Configure the Kernel with Oracle values in /etc/sysctl.conf.

[FONT="Arial Black"]# Oracle stuff
kernel.shmall = 2097152
kernel.shmmax = 2147483648
kernel.shmmni = 4096
kernel.sem = 250 32000 100 128
fs.file-max = 65536
net.ipv4.ip_local_port_range = 1024 65000
net.core.rmem_default = 262144
net.core.rmem_max = 262144
net.core.wmem_default = 262144
net.core.wmem_max = 262144
vm.swappiness=10[/FONT]

3. Create the users and groups.

[FONT="Arial Black"]"sudo groupadd nobody
sudo groupadd oinstall
sudo groupadd dba
sudo useradd -s /bin/bash -g oinstall -G dba oracle
sudo passwd oracle"[/FONT]

4. Set the limits in /etc/security/limits.conf.

[FONT="Arial Black"]* soft nproc 2047
* hard nproc 16384
* soft nofile 1024
* hard nofile 65536[/FONT]

5. Add a few symlinks to avoid any script problems:

[FONT="Arial Black"]sudo ln -s /usr/bin/awk /bin/awk
sudo ln -s /bin/true /bin/rpm
sudo ln -s /usr/bin/basename /bin/basename
sudo ln -s /lib/libgcc_s.so.1 /lib/libgcc_s.so
sudo mkdir -p /u01/oracle/10g
sudo chown -R oracle:oinstall /u01/oracle/10g
sudo chmod -R 775 /u01/oracle[/FONT]

6. Before execute runInstaller run this:

[FONT="Arial Black"]export LDEMULATION=elf_i386[/FONT]

7. Execute runInstaler and finish the instalation:

./runInstaller -IgnoreSysPrereqs

I wish that guide help everybody.

---

### Post by s_raghu20 on 2007-06-19
Dear TerminaT,

Thanks for your valuable suggestions/experiences.

I am trying to install Oracle 10g on my Dell Inspiron Pentium-4.  Initially I had hiccups with starting the installation itself. Later when I got through with that, I got into problems with make.

I tried to follow your suggestions, especially with respect to downloading extra packages from the repository. However, I did not find all the right packages mentioned by you.  May be I am making some mistake, but neither I could find packages mentioned by you in synaptic package manager, nor the apt-get command work for me.

Could you please shed some more light on this for me.  Also, will it make a difference that my system is a an intel based 32bit one, whereas your experience has been with a 64bit system. Just wondering, no knowledge.

Looking forward to ideas, suggestions etc..

I have started a similar post on this topic on oracle forums too... 
[here]("http://forums.oracle.com/forums/thread.jspa?messageID=1909438&#1909438") is the link..

regards
raghav..

---

### Post by Rmantingh on 2007-10-15
Has anyone tried this on Ubuntu Gutsy 7.10 ?
I keep getting errors during the linking phase of the installation
suggesting there's something wrong with the libraries?

Example:
/usr/bin/ld: i386 architecture of input file `/opt/oracle/product/10gR2/sysman/lib//libnmadbg.a(snmadbg.o)' is incompatible with i386:x86-64 output

Any ideas, anyone?

---

### Post by aqm74 on 2007-12-01
Hi TerminaT,

Do I need to install 32-bit libraries if I am going to install 64-bit Oracle? I don't think so, but kindly confirm and explain:)

---

### Post by shadowplane676 on 2008-02-19
i have been trying to install oracle 10g on my Feisty Kubuntu, and i keep getting an error when i try and run the installer script. i get "~/installer/.oui permission denied" when my oracle user owns the folder AND has execute permissions. .oui is also owned by oracle, with execute permissions. i have no idea why it wont work with all the permissions in line.....

any ideas? im coming up blank on the web too :( kinda need oracle for a database class this semester

---

### Post by Rmantingh on 2008-02-22
I've had a similar problem long time ago but can't for the life of me remember how I fixed it :-(
Make sure that:-
- you run the installer as user oracle
- oracle user has been created with main group "oinstall" and "dba" as secundary group
- all files/directories belong to user oracle and group "oinstall"

Sorry if I can't be more helpful.

---

### Post by shadowplane676 on 2008-02-26
got all that. oracle user w/ primary group of oinstall, secondary groups of dba, admin and users, and everything has the right ownership but it still hates me and wont let me run the installer.

---

### Post by springbokmarine on 2008-05-27
I receive the same error here. Ubuntu 8.04 64 bit, Core 2 Quad. All the permissions are correct.

---

